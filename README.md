# sp6zhp-ansible

--- 
# ansible install

Debian: https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html#installing-ansible-on-debian

---
# Playbooks

## 00-debug
``ansible-playbook -i localhost, --connection=local --ask-become 00-debug/test-connection.yaml``

## 01-configure-ansible-env
### Update and upgrade your dist
``ansible-playbook -i localhost, --connection=local --ask-become 01-configure-ansible-env/update-and-upgrade.yaml``

### Install avahi-client mDNS
``ansible-playbook -i localhost, --connection=local --ask-become 01-configure-ansible-env/avahi/avahi.yaml``

### Install and configure ddclient
``ansible-playbook -i localhost, --connection=local --ask-become --extra-vars "ddns_domain=<domain> protocol=changeip ddns_login=login ddns_password=password" 01-configure-ansible-env/ddclient/ddclient.yaml``

### Install and configure docker
``ansible-playbook -i localhost, --connection=local --ask-become --extra-vars "docker_base_dir=/srv/docker" 01-configure-ansible-env/docker/docker.yaml``

### Deploy and configure portainer
``ansible-playbook -i localhost, --connection=local --ask-become --extra-vars "portainer_data_dir=/srv/portainer docker_stacks_dir=/srv/docker-compose" 01-configure-ansible-env/portainer/portainer.yaml``

### Deploy and configure semaphore
``ansible-playbook -i localhost, --connection=local --ask-become --extra-vars "semaphore_db_dir=/srv/semaphore/db docker_stacks_dir=/srv/docker-compose portainer_api_key=xxx semaphore_db_pass=xxx semaphore_admin_pass=xxx" 01-configure-ansible-env/semaphore/semaphore.yaml``

### Install and configure WGDashboard
``ansible-playbook -i localhost, --connection=local --ask-become --extra-vars "wgdashboard_dir=/srv/wgdashboard" 01-configure-ansible-env/wgdashboard/wg-dashboard.yaml``
