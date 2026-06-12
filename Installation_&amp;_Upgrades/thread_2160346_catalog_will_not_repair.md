---
title: "catalog will not repair"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by jgw on 2013-07-06
I have just done a clean install of 12.04.2   When installing I told the installer to use the whole drive which, in theory, wiped out the existing installation.  After the installation, with, as far as I could tell no errors (downloaded new iso, burned a dvd, etc. for install).  Then came the updates and there were a pile of them (235 I think).  Whilst doing the updates I was told that the catalog was bad and needed repairing (I will list the details below).  After that I did an apt-get install -f which also failed (see below).  The error references packages for oubuntu10.? although I installed 12.04.02   My suspicion is that even though I told the installer to use the entire drive, and everything was supposed to be cleaned out that might have not happened?

Anyway, any help would be appreciated, thank you.....................

PACKAGE INSTALL FAILURE
(Reading database ... 143151 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10.3 (using .../libc-bin_2.15-0ubuntu10.4_i386.deb) ...
Unpacking replacement libc-bin ...
dpkg: error processing /var/cache/apt/archives/libc-bin_2.15-0ubuntu10.4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc-bin_2.15-0ubuntu10.4_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.4); however:
  Version of libc6 on system is 2.15-0ubuntu10.3.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured

APT-GET
name@name-desktop:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
name@name-desktop:~$ sudo apt-get install -f
[sudo] password for name: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc-bin libc6
2 upgraded, 0 newly installed, 0 to remove and 260 not upgraded.
1 not fully installed or removed.
Need to get 0 B/5,072 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 143151 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10.3 (using .../libc-bin_2.15-0ubuntu10.4_i386.deb) ...
Unpacking replacement libc-bin ...
dpkg: error processing /var/cache/apt/archives/libc-bin_2.15-0ubuntu10.4_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc-bin_2.15-0ubuntu10.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jgw on 2013-07-06
I decided to install yet again.  This time I was able to install the 272 updates without a hitch.  Something peculiar must have happened the first time around.

---

