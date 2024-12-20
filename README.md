# IBA devops training

## HW16. Ansible. Copy file, add user, install docker on remote machine

#### Copy file to remote host
[copy_del_plbk.yml](https://github.com/voyager1122/iba_hw16/blob/main/copy_del_plbk.yml)

'''
root@ip-172-31-81-185:/etc/ansible# ansible-playbook copy_del_plbk.yml

PLAY [prod] ***************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************
[WARNING]: Platform linux on host host01 is using the discovered Python interpreter at /usr/bin/python3.12, but future installation of
another Python interpreter could change the meaning of that path. See https://docs.ansible.com/ansible-
core/2.17/reference_appendices/interpreter_discovery.html for more information.
ok: [host01]

TASK [Copy file with owner and permissions] *******************************************************************************************
changed: [host01]

TASK [Remove file (delete file)] ******************************************************************************************************
changed: [host01]

PLAY RECAP ****************************************************************************************************************************
host01                     : ok=3    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
'''

## Create user and home directory for user

[user_home_dir_add.yml](https://github.com/voyager1122/iba_hw16/blob/main/user_home_dir_add.yml)

'''
root@ip-172-31-81-185:/etc/ansible# ansible-playbook user_home_dir_add.yml

PLAY [prod] ***************************************************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************
[WARNING]: Platform linux on host host01 is using the discovered Python interpreter at /usr/bin/python3.12, but future installation of
another Python interpreter could change the meaning of that path. See https://docs.ansible.com/ansible-
core/2.17/reference_appendices/interpreter_discovery.html for more information.
ok: [host01]

TASK [Create a user 'alice' with a home directory] ************************************************************************************
changed: [host01]

PLAY RECAP ****************************************************************************************************************************
host01                     : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
'''

## Install docker, add user do the docker group
[install_docker_ubuntu.yml](https://github.com/voyager1122/iba_hw16/blob/main/install_docker_ubuntu.yml)

'''
root@ip-172-31-81-185:/etc/ansible# ansible-playbook install_docker_ubuntu.yml

PLAY [Install Docker on Ubuntu remote machine] ****************************************************************************************

TASK [Gathering Facts] ****************************************************************************************************************
[WARNING]: Platform linux on host host01 is using the discovered Python interpreter at /usr/bin/python3.12, but future installation of
another Python interpreter could change the meaning of that path. See https://docs.ansible.com/ansible-
core/2.17/reference_appendices/interpreter_discovery.html for more information.
ok: [host01]

TASK [Update apt repository cache] ****************************************************************************************************
changed: [host01]

TASK [Install required dependencies for Docker] ***************************************************************************************
ok: [host01]

TASK [Get Ubuntu version codename] ****************************************************************************************************
changed: [host01]

TASK [Add Docker GPG key] *************************************************************************************************************
ok: [host01]

TASK [Add Docker repository to APT sources] *******************************************************************************************
ok: [host01]

TASK [Install Docker CE (Community Edition)] ******************************************************************************************
ok: [host01]

TASK [Start Docker service] ***********************************************************************************************************
ok: [host01]

TASK [Verify Docker installation] *****************************************************************************************************
ok: [host01]

TASK [Show Docker version] ************************************************************************************************************
ok: [host01] => {
    "msg": "Docker version: Docker version 27.4.1, build b9d17ea"
}

TASK [Ensure the user exists] *********************************************************************************************************
ok: [host01]

TASK [Add user to group] **************************************************************************************************************
changed: [host01]

PLAY RECAP ****************************************************************************************************************************
host01                     : ok=12   changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

root@ip-172-31-81-185:/etc/ansible# gi
ginstall-info       gio-querymodules    git-receive-pack    git-upload-archive
gio                 git                 git-shell           git-upload-pack


'''
