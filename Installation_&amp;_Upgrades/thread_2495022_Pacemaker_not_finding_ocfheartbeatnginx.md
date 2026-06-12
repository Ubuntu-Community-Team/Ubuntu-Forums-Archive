---
title: "Pacemaker not finding ocf:heartbeat:nginx"
date: 2024-02-04
forum: Installation &amp; Upgrades
---

### Post by kartik-kartik on 2024-02-04
Hi I'm getting this message:

[EMAIL="root@ubu-2:~/.ssh"]root@ubu-2:~/.ssh[/EMAIL]# crm configure primitive webserver ocf:heartbeat:nginx configfile=/etc/nginx/nginx.conf op start timeout="40s" interval="0" op stop timeout="60s" interval="0" op monitor interval="10s" timeout="60s" meta migration-threshold="10"
ERROR: ocf:heartbeat:nginx: got no meta-data, does this RA exist?
WARNING: (unpack_config)        warning: Blind faith: not fencing unseen nodes
ERROR: ocf:heartbeat:nginx: got no meta-data, does this RA exist?
ERROR: ocf:heartbeat:nginx: got no meta-data, does this RA exist?
ERROR: ocf:heartbeat:nginx: no such resource agent
Do you still want to commit (y/n)? n
[EMAIL="root@ubu-2:~/.ssh"]root@ubu-2:~/.ssh[/EMAIL]# pcs cluster status
Cluster Status:
 Cluster Summary:
   * Stack: corosync
   * Current DC: ubu-2 (version 2.1.2-ada5c3b36e2) - partition with quorum
   * Last updated: Sun Feb  4 08:34:55 2024
   * Last change:  Sun Feb  4 03:52:47 2024 by root via cibadmin on ubu-2
   * 2 nodes configured
   * 1 resource instance configured
 Node List:
   * Online: [ ubu-2 ubu-4 ]

root@ubu-2:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy
root@ubu-2:~# uname -a
Linux ubu-2 5.15.0-91-generic #101-Ubuntu SMP Tue Nov 14 13:30:08 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
root@ubu-2:~#

---

