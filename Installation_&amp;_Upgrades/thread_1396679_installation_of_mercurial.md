---
title: "installation of mercurial"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by Farrukh_Kamran on 2010-02-02
hi every one ,
I just tried to install Mercurial with apt-get command, it shows following error
--------------------------------------------------------------------------------------------------------
root@ubuntu:/home/muhr# apt-get install mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mercurial is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-j2sdk1.6 (1.6.0+update18) ...
update-alternatives: error: alternative path /usr/lib/j2sdk1.6-sun/jre/plugin/i386/ns4/libjavaplugin.so doesn't exist.
dpkg: error processing sun-j2sdk1.6 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-j2sdk1.6
E: Sub-process /usr/bin/dpkg returned an error code (1)
----------------------------------------------------------------------------------------------------------------------
while i have already installed J2sdk1.6
-----------------------------------------------
root@ubuntu:/home/muhr# java -version
java version "1.6.0_18"
Java(TM) SE Runtime Environment (build 1.6.0_18-b07)
Java HotSpot(TM) Client VM (build 16.0-b13, mixed mode, sharing)

------------------------------------------------
Please suggest me how to sort out this.

---

