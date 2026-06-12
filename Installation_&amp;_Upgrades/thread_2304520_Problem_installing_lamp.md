---
title: "Problem installing lamp"
date: 2015-11-27
forum: Installation &amp; Upgrades
---

### Post by Aubdullah_Munim on 2015-11-27
I am facing problem while installing lamp on my ubuntu 14.04 LFS. my laptop is Dell inspiron 5548.

If i have enter "sudo apt-get install apache2" i will get 

 Setting up apache2-bin (2.4.7-1ubuntu4.8) ...
Setting up apache2-data (2.4.7-1ubuntu4.8) ...
Setting up apache2 (2.4.7-1ubuntu4.8) ...
ERROR: Config file dir.conf not properly enabled: /etc/apache2/mods-enabled/dir.conf is a real file, not touching it
dpkg: error processing package apache2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Errors were encountered while processing:
 apache2
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by yancek on 2015-11-27
A simpler method to install LAMP is at the Ubuntu site below.  Make sure if you use the command to include the '^' at the end of the command or it will fail.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

