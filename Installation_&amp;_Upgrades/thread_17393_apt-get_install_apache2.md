---
title: "apt-get install apache2"
date: 2005-02-28
forum: Installation &amp; Upgrades
---

### Post by Taggy on 2005-02-28
Executing that command leads to the following....

[I]root@taggy-laptop:/ # apt-get install apache2
Reading Package Lists... Done
Building Dependency Tree... Done
apache2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up apache2-mpm-prefork (2.0.50-12ubuntu4.1) ...
This module does not exist!
dpkg: error processing apache2-mpm-prefork (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker | apache2-mpm-prefork | apache2-mpm-perchild; however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-perchild is not installed.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php4:
 libapache2-mod-php4 depends on apache2-mpm-prefork; however:
  Package apache2-mpm-prefork is not configured yet.
dpkg: error processing libapache2-mod-php4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2-mpm-prefork
 apache2
 libapache2-mod-php4
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]


I'm a Linux-Newbie, any ideas how to fix this problem and install apache2?
Thanks in advance.

Kind regards, Taggy

---

### Post by az on 2005-02-28
try:
sudo apt-get -f install

---

### Post by Taggy on 2005-03-01
This command leads to the following:

[I]root@taggy-laptop:/home/taggy # apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up apache2-mpm-prefork (2.0.50-12ubuntu4.1) ...
This module does not exist!
dpkg: error processing apache2-mpm-prefork (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apache2:
 apache2 depends on apache2-mpm-worker | apache2-mpm-prefork | apache2-mpm-perchild; however:
  Package apache2-mpm-worker is not installed.
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-perchild is not installed.
dpkg: error processing apache2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php4:
 libapache2-mod-php4 depends on apache2-mpm-prefork; however:
  Package apache2-mpm-prefork is not configured yet.
dpkg: error processing libapache2-mod-php4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2-mpm-prefork
 apache2
 libapache2-mod-php4
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]


Maybe I did something wrong before that crashed something within the system, are there any procedures that I can do to fix such problems?

---

