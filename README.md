ansible-role-copy
====

Copy files to remote systems. Basically a wrapper for [ansible.builtin.copy](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html).

Requirements
------------

Ansible 2.10+

Role Variables
--------------

* `copy_files` - list of files to copy, example:
```yaml
copy_files:
  - dest: /usr/local/bin/my-script.sh
    src: "{{ inventory_dir }}/../files/my-script.sh"
    owner: root
    group: root
    mode: 0755
    handlers:
      - run-something-after-copy.sh
      - another-one.sh
```
* `copy_files_no_log` - boolean to hide task output (no_log).

Dependencies
------------

N/A


Example Playbook
----------------

```yaml
- hosts: myservers
  vars:
    copy_files:
      - dest: /usr/local/bin/my-script.sh
        src: "{{ inventory_dir }}/../files/my-script.sh"
        owner: root
        group: root
        mode: 0755
        handlers:
          - run-something-after-copy.sh
          - another-one.sh
  roles:
    - ansible-role-copy
```

License
-------

GPLv3

Author Information
------------------

Vladimir Vasilev (@vladi-k)
