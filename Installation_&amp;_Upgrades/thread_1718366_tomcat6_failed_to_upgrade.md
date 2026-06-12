---
title: "tomcat6 failed to upgrade"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by ksharlandjiev on 2011-03-31
Please help me out with the following problem:


root@d510:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up tomcat6 (6.0.28-2ubuntu1.2) ...
sed: -e expression #1, char 123: unknown option to `s'
dpkg: error processing tomcat6 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tomcat6
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

