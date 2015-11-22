# NodeJS Ansible Role

[![Build Status](https://travis-ci.org/w3aran/ansible-role-nodejs.svg?branch=master)](https://travis-ci.org/w3aran/ansible-role-nodejs) 
[![Ansible Role : Node.js](https://img.shields.io/badge/ansible--galaxy%20install-w3aran.nodejs-blue.svg)](https://galaxy.ansible.com/detail#/role/6135)

NodeJS Ansible Role helps to install Node.js via NVM.

### Role Variables

Default settings:

```
role_nodejs_nvm_version: v0.29.0
role_nodejs_nvm_user: "{{ ansible_ssh_user }}"
role_nodejs_nvm_destination: "/home/{{ role_nodejs_nvm_user }}/.nvm"
role_nodejs_version: 4.2.1
```

### Example Playbook

#### With default settings:

```
- hosts: all
  roles:
    - ansible-role-nodejs
```

#### For different Node.js version:

```
- hosts: all
  roles:
    - role: ansible-role-nodejs
      role_nodejs_version: 0.12.7
```

#### Using Executable Path:

```
- hosts: all
  roles:
    - ansible-role-nodejs
  tasks:
    - name: Install Gulp
      npm:
         name=gulp
         global=yes
         executable="{{ ROLE_NODEJS_EXCUTABLE_PATH }}/npm"
      become:
         yes
      become_user:
         "{{ ansible_ssh_user }}"
```

#### Using Environment Path:

```
- hosts: all
  roles:
    - ansible-role-nodejs
  tasks:
    - name: Install Gulp
      npm:
         name=gulp
         global=yes
      become:
         yes
      become_user:
         "{{ ansible_ssh_user }}"
      environment:
        PATH: "{{ ROLE_NODEJS_ENVIRONMENT_PATH }}"
```
