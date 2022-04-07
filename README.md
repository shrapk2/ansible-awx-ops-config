# awx-ops-config

## Description

This role is used to manage various configuration aspects of the Ansible AWX system. To include projects, workflows, and anything else required. Currently utilizes the `tower_` series of Ansible modules.

```bash
.
├── playbook.yml
├── README.md
├── ansible.cfg
└── roles
    └── awx-ops-config
        ├── defaults
        │   └── main.yml
        ├── files
        ├── meta
        │   └── main.yml
        ├── tasks
        │   └── main.yml
        └── templates
```

## Requirements

Local Requirements

- A local system capable of running Ansible
- A local system with the latest
  - Python/2.7.15
  - `ansible-tower-cli` Python module (Role attempts to install it)

## Role Variables

The role contains quite a few lists that can be defined depending on the desired execution. Tags will dictate what variables need to be defined. Consult the `defaults/main.yml` for proper syntax.

Aside from the above comment, these variables are required regardless of which tags used to properly execute this role

- tower_hostname
- tower_svc_acct
- tower_svc_passwd

A few additional "default" variables called through out the play:

- default_org_name
- default_ssh_account
- default_scm_account
- default_inventory

## Role Tags

An explanation of any tags used/required within the role

- `always`: Ansible default, skips all tasks assigned this tag
- `never`: Ansible default, skips all tasks assigned this tag
- `create_org`: Creates organization based on provided list
- `create_team`: Creates teams based on provided list
- `create_user`: Creates users based on provided list
- `remove_user`: Removes users based on provided list
- `add_user_role`: Updates a users' role based on provided list
- `remove_user_role`: Removes a users' role based on provided list
- `create_credential`: Creates credentials based on provided list
- `remove_credential`: Removes credentials based on provided list
- `create_inventory`: Creates inventories based on provided list
- `create_project`: Creates projects based on provided list
- `create_template`: Creates templates based on provided list (same list as create_project)

## Dependencies

None at this time

## Example Playbook

Below is an example of a _playbook.yml_ file that will execute each role.

```yaml
- hosts: all
  gather_facts: true
  name: This role is used to manage various configuration aspects of the Ansible AWX system.
  become: no

  vars:
    sample_var1: value
    sample_var2: value

  roles:
    - { role: awx-ops-config, tags: awx-ops-config }
```

## License

MIT

## Author Information

Kenney Sharpton II
