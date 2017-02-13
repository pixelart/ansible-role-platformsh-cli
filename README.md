# Ansible Role: platform.sh CLI

[![Build Status](https://travis-ci.org/pixelart/ansible-role-platformsh-cli.svg?branch=master)](https://travis-ci.org/pixelart/ansible-role-platformsh-cli)

Installs the [platform.sh](https://platform.sh/) CLI, on any Linux or UNIX system.

## Requirements

  - `php` (version 5.5+) should be installed and working.
  - `git` should be installed and working.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    platformsh_path: /usr/local/bin/platform

The path where platform.sh CLI will be installed and available to your system. Should be in your user's `$PATH` so you can run commands simply with `platform` instead of the full path.

    platformsh_keep_updated: false

Set this to `true` to update the platform.sh CLI to the latest release every time the playbook is run.

    php_executable: php

The executable name or full path to the PHP executable. This is defaulted to `php` if you don't override the variable.

    platformsh_shell_config_path: ''
    
Since the platform.sh CLI shell config contains bash autocompletion it can't be put into `/etc/profile.d` and thus you must define a path, where to put the file to load it globally. For example on Ubuntu/Debian you can use `/etc/bash.bashrc.d` and add the following snippet to `/etc/bash.bashrc`:

    if [ -d /etc/bash.bashrc.d ]; then
      for i in /etc/bash.bashrc.d/*.sh; do
        if [ -r $i ]; then
          . $i
        fi
      done
      unset i
    fi 

## Dependencies

None (but make sure you've installed PHP).

## Example Playbook

    - hosts: phpdevs
      roles:
        - pixelart.platformsh-cli

After the playbook runs, `platform` will be placed in `/usr/local/bin/platform` (this location is configurable), and will be accessible via normal user accounts.

## Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms.

## License

MIT, see the [LICENSE](LICENSE) file.

## Author Information

This role was created in 2017 by [pixelart GmbH](https://www.pixelart.at/) and inspired by the roles of [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
