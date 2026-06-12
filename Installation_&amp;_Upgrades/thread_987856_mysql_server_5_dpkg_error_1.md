---
title: "mysql server 5 dpkg error 1"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by lhiggin on 2008-11-20
/var/cache/apt/archives/mysql-server-5.0_5.0.67-0ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

this error occurred when I attempted to install KDE desktop on Intrepid.

Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca mailx
The following packages will be upgraded:
  mysql-server-5.0
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/26.8MB of archives.
After this operation, 87.6MB of additional disk space will be used.
Do you want to continue [Y/n]? (Reading database ... 
dpkg: serious warning: files list file for package `mysql-server-5.0' missing, assuming package has no files currently installed.
151723 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.67-0ubuntu6 (using .../mysql-server-5.0_5.0.67-0ubuntu6_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.67-0ubuntu6_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.67-0ubuntu6_i386.deb

Please assist this newb.
Thanks Lonnie

---

### Post by qbit- on 2008-12-20
I have the same problem...
Anyone can help us?

---

