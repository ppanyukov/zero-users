zero-users: Zero hassle user management
=======================================

zero-users is an ansible project to perform linux user management with minimum configuration and built in validation for these configurations. Users, created using zero-users, can login to servers using key based authentication.

Prerequisites
=============

[Ansible](http://www.ansible.com): A working installation of ansible is required. See installation details [here](http://docs.ansible.com/intro_installation.html).

Features
========

* Automated user creation, deletion on configurable server groups
* Sudo access management
* Builtin configuration validation

Instructions
============

* **Configure**:

    1. Define your servers in an ansible inventory file. For examples, see the [inventory/](inventory/) directory
    2. Define users, sudo access permission in the variable file [here](roles/zero_users/vars/)
    3. Place the users ssh public key [here](roles/zero_users/files/public_keys/)

* **Execute**:

```bash
    $ ansible-playbook -v -i inventory/production.ini site.yml
```

Extra Arguments
===============

* **validate_mode**: When *validate_mode* is passed as true, the playbook does configuration validation and skips all real tasks. Default: False. Sample execution:

```bash
    $ ansible-playbook -v -i inventory/production.ini -e validate_mode=true site.yml
```

* **remove_home**: When *remove_home* is passed as true, the home directory of users being deleted is also deleted. Default: False. Sample execution:

```bash
    $ ansible-playbook -v -i inventory/production.ini -e remove_home=true site.yml
```
