---
title: "Ubuntu Server Error Code 1"
date: 2013-02-28
forum: Installation &amp; Upgrades
---

### Post by noahtk1 on 2013-02-28
Hi,

When updating or upgrading in any respect, or working with MySQL, I get the error displayed below.  This instance of the error displayed is from the apt-get upgrade:

nk@klinetelCP:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y 
Setting up mysql-server-5.5 (5.5.29-0ubuntu0.12.04.1) ...
start: Job failed to start
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.5
E: Sub-process /usr/bin/dpkg returned an error code (1)
nk@klinetelCP:~$

---

### Post by noahtk1 on 2013-02-28
Solved with: sudo apt-get purge -f mysql-server mysql-common

---

