# Ansible Base Role

[![Build Status](https://travis-ci.org/rossedman/ansible-role-base.svg?branch=master)](https://travis-ci.org/rossedman/ansible-role-base)

This role is intended to setup base packages as well as configure swapfile, timezones, and automatic updates

##Requirements

This role currently has only been tested with CentOS7, Ubuntu 12.04 >=, Debian Jessie and Debian Wheezy.

##Role Variables

These are the default variables that are exposed for all kernel versions:

```
homebase_timezone: "America/Chicago"
homebase_swap_size: "1G"
homebase_swap_file: true
homebase_swap_location: /swapfile
```

These are the variables that are exposed for Debian/Ubuntu:

```
---
general_packages:
  - build-essential
  - curl
  - git
  - git-core
  - gcc
  - make
  - ntp
  - unattended-upgrades
  - update-notifier-common
  - unzip
  - wget
shell_editors:
  - nano
  - vim
update_security: true
update_updates: false
update_proposed: false
update_backports: false
update_blacklist:
  - vim
```

These are the variables that are exposed for Redhat:

```
---
general_packages:
  - curl
  - git
  - git-core
  - gcc
  - libselinux-python
  - make
  - ntp
  - unzip
  - wget
shell_editors:
  - vim-X11
  - vim-common
  - vim-enhanced
  - vim-minimal
  - nano
update_type: security
```

##Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

- hosts: servers
  roles:
     - { role: rossedman.Homebase, homebase_timezone: "America/Chicago", homebase_swap_size: "1G" }
