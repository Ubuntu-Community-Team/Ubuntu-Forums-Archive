---
title: "Ubuntu 13.04 Battery meter won't install because no JDK 7?"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by Zack_Souza on 2013-09-25
Hi, I'm running Ubuntu on my laptop, so a battery gauge would be very helpful, as currently I carry around the adapter just in case.  When I try to enter
 
sudo apt-get install indicator-power

it responds with

Reading package lists... Done
Building dependency tree       
Reading state information... Done
indicator-power is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u40-0~webupd8~0) ...
Downloading Oracle Java 7...
--2013-09-25 14:07:44--  [http://download.oracle.com/otn-pub/java/jdk/7u40-b43/jdk-7u40-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u40-b43/jdk-7u40-linux-x64.tar.gz)
Resolving false (false)... failed: No such file or directory.
wget: unable to resolve host address ‘false’
download failed
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would greatly be appreciated.  Also, Im new to these forums.  Is there a better way to add all the terminal dialogue?

---

