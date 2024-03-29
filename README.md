# Playbook to update just tower's nodes operating system

Playbook cannot be executed from tower or databases nodes, because it will be rebooted all servers if need it. I will reuse the tower's inventory.

Adapted to tower version > 3.7.x

## Howto run it.

* Playbook has been done with tags, just check the tasks you want to run first.

  $ ansible-playbook -i inventory tower_update_os.yml --list-tags

* Check connectivity with the tag ping and reuse tower's inventory.

  $ ansible-playbook -i inventory tower_update_os.yml --tags ping

* Check host list where the playbook will be executed.

  $ ansible-playbook -i inventory tower_update_os.yml --list-hosts

* Run the playbook.

  $ ansible-playbook -i inventory tower_update_os.yml --tags gather_facts,stop_services,enable_repos,update_idm_packages,update_all_packages_but_tower,reboot

* Run the playbook limiting host.

  $ ansible-playbook -i inventory tower_update_os.yml --tags gather_facts,stop_services,enable_repos,update_idm_packages,update_all_packages_but_tower,reboot -l tower1.lab.example.com,tower2.lab.example.com
