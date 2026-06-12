---
title: "Version problem installing libc6-dev"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by Letstry12 on 2012-03-07
Hello,

I am running Ubuntu 10.04 LTS 

My first Problem:

When I try to compile with gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3 
My test c-program I get the following error:

letstry@GVP-LIN-253-134:~/gcctest$ sudo gcc conftest.c
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

I have understood that missing  crt1.o can be fixed by installation of libc6-dev.
So I tried

letstry@GVP-LIN-253-134:~/gcctest$ sudo apt-get install --fix-missing libc6-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaprutil1-dbd-sqlite3 libapr1 libaprutil1-ldap ssl-cert libaprutil1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-libc-dev
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc6-dev linux-libc-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 834kB/5,674kB of archives.
After this operation, 23.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main linux-libc-dev 2.6.32-38.85
  404  Not Found [IP: 91.189.92.179 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-38.85_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-38.85_i386.deb)  404  Not Found [IP: 91.189.92.179 80]

When I check 
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/)

linux-libc-dev_2.6.32-21.32_amd64.deb              16-Apr-2010 14:05           753K
linux-libc-dev_2.6.32-21.32_i386.deb    16-Apr-2010 15:07           753K
linux-libc-dev_2.6.32-39.86_amd64.deb              17-Feb-2012 10:56          816K
linux-libc-dev_2.6.32-39.86_i386.deb    17-Feb-2012 10:59          816K
linux-libc-dev_2.6.35-1022.33_amd64.deb         19-Sep-2010 23:05          794K

There we have 39.86 and not 38.85.

Then I habe tried

sudo apt-get install --fix-missing libc6-dev=2.6.32-39.86_i386 E: Version '2.6.32-39.86_i386' for 'libc6-dev' was not found

All variants with 2.6.32 or 2.6.32-39.86 does not help.

I have tried to adjust /etc/apt/sources.list to point to other distribution like [http://mirror.umd.edu/ubuntu//pool/main/l/linux/](http://mirror.umd.edu/ubuntu//pool/main/l/linux/) where linux-libc-dev_2.6.32-38.85_i386.deb can be found but without any positive result.

Any idea what I am doing wrong?

thanks in advance!
Andre

---

### Post by Frogs Hair on 2012-03-07
Hello and Welcome 

I found this link and I hope it helps . [http://askubuntu.com/questions/75495/libc6-dev-unmet-dependency](http://askubuntu.com/questions/75495/libc6-dev-unmet-dependency)

---

### Post by Letstry12 on 2012-03-08
thank you for the advice. unfortunatelly this does not help:


letstry@GVP-LIN-253-134:~$ dpkg -s libc6
Package: libc6
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 9360
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: eglibc
Version: 2.11.1-0ubuntu7.8


and then the same problem as before with


letstry@GVP-LIN-253-134:~$ sudo apt-get install --fix-missing libc6-dev=2.11.1-0ubuntu7.8

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaprutil1-dbd-sqlite3 libapr1 libaprutil1-ldap ssl-cert libaprutil1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev linux-libc-dev
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc6-dev linux-libc-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 834kB/5,674kB of archives.
After this operation, 23.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main linux-libc-dev 2.6.32-38.85
  404  Not Found [IP: 91.189.92.183 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-38.85_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-38.85_i386.deb)  404  Not Found [IP: 91.189.92.183 80]

---

