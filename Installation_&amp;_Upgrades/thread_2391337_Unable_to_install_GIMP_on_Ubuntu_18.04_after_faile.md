---
title: "Unable to install GIMP on Ubuntu 18.04 after failed MariaDB installa"
date: 2018-05-08
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2018-05-08
Because the install of both mysql and mariadb is broken on my system I cannot install ANYTHING.

How do I get either mysql or mariadb installed on Ubuntu 18.04 short of erasing the disk and starting off from scratch?

```
$ sudo apt update && sudo apt install gimp
[sudo] password for jcobban: 
Hit:1 http://security.ubuntu.com/ubuntu bionic-security InRelease
Hit:2 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease        
Hit:3 http://ca.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:4 http://ca.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:5 http://ca.archive.ubuntu.com/ubuntu bionic-backports InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
7 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gimp is already the newest version (2.8.22-1).
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up mariadb-server-10.1 (1:10.1.29-6) ...
dpkg: error processing package mariadb-server-10.1 (--configure):
 installed mariadb-server-10.1 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mariadb-server:
 mariadb-server depends on mariadb-server-10.1 (>= 1:10.1.29-6); however:
  Package mariadb-server-10.1 is not configured yet.

dpkg: error processing package mariadb-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mariadb-server-10.1
 mariadb-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Xian on 2018-05-08
Read here for possible solutions:

[https://unix.stackexchange.com/questions/249530/mariadb-dependency-problems-leaving-unconfigured](https://unix.stackexchange.com/questions/249530/mariadb-dependency-problems-leaving-unconfigured)

---

### Post by kostkon on 2018-05-09
As a workaround and for better or worse you can install the snap version of Gimp:
```
sudo snap install gimp
```

Hope that helps somehow

---

