Building a simple LAMP stack and deploying Application using Ansible Playbooks.
-------------------------------------------

These playbooks require Ansible 1.2.

These playbooks are meant to be a reference and starter's guide to building
Ansible Playbooks. These playbooks were tested on CentOS 7.x so we recommend
that you use CentOS or RHEL to test these modules.

This project can create a ceph cluster by manual,
'hosts' defines the nodes in which the stacks should be configured.

        [primarymon]
        ceph1

        [monitors]
        ceph2

        [osds]
	ceph1
	ceph2

command:

        ansible-playbook -i hosts site.yml

to remove the already exsit ceph cluster,use command follow:
	systemctl stop ceph.target
	umount /var/lib/ceph/osd/ceph-*
	rm /etc/ceph -rf && rm /var/lib/ceph -rf
	yum autoremove ceph -y
	mkfs.xfs /dev/vdb -f
