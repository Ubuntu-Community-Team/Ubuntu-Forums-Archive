---
title: "ubuntu-12.04 unable to deploy JUJU with wordpress"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by saurabh4485 on 2012-09-19
Hi,

I am running Ubuntu-12.04 server with MASS & JUJU.
I configured two nodes also.

**My conf is below :**
===================================
MASS server : 2 NIC 
              eth0 : 192.168.10.171
              eth1 : public ip
Node1       : 2 NIC  Set on DHCP
Node2       : 1 NIC  Set on DHCP   
====================================
When i am deploying the Mysql & wordpress with JUJU. I am not getting the URL of accessing the wordpress so that i can proceed the installation. 
**Please let me know the solution of this ?** 

**see the below output:**
mass@mass:~$ juju status
2012-09-19 10:40:49,386 INFO Connecting to environment...
2012-09-19 10:40:50,005 INFO Connected to environment.
machines:
  0:
    agent-state: running
    dns-name: node1
    instance-id: /MAAS/api/1.0/nodes/node-9a823e36-018e-11e2-b074-00e04c4d3802/
    instance-state: unknown
  1:
    agent-state: running
    dns-name: node2
    instance-id: /MAAS/api/1.0/nodes/node-cee819b6-018e-11e2-a57d-00e04c4d3802/
    instance-state: unknown
  2:
    instance-id: pending
services:
  mysql:
    charm: cs:precise/mysql-8
    relations:
      db:
      - wordpress
    units:
      mysql/0:
        agent-state: started
        machine: 1
        public-address: node2.localdomain
  wordpress:
    charm: cs:precise/wordpress-7
    exposed: true
    relations:
      db:
      - mysql
      loadbalancer:
      - wordpress
    units:
      wordpress/0:
        agent-state: pending
        machine: 2
        open-ports: []
        public-address: null
2012-09-19 10:40:50,402 INFO 'status' command finished successfully


Regards
Saurabh

---

