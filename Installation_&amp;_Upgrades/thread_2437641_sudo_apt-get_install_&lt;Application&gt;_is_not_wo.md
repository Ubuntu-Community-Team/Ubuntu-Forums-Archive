---
title: "sudo apt-get install &lt;Application&gt; is not working! Ubuntu 16.04"
date: 2020-02-27
forum: Installation &amp; Upgrades
---

### Post by chronusbalaji on 2020-02-27
sudo dpkg --configure -a
Setting up mysql-server-5.7 (5.7.29-0ubuntu0.16.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.


dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server

---

### Post by mörgæs on 2020-02-27
I shall answer as briefly as you asked:

[https://askubuntu.com/questions/136881/debconf-dbdriver-config-config-dat-is-locked-by-another-process-resource-t](https://askubuntu.com/questions/136881/debconf-dbdriver-config-config-dat-is-locked-by-another-process-resource-t)

---

