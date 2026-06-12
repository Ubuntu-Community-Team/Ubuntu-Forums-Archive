---
title: "libc6 and libdb1-compat problem"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by widernet_project on 2007-04-26
Hi guys,
I'm using Ubuntu 7.04 Desktop and have some problem with two packages libc6 and libdb1-compat. When I install libdb1-compat package, there is an error message telling that I need libc6 package install first. But when I install libc6 package it displays an error: "version `GLIBC_2.4' not found ". This is the whole error message:

[I]tinguyen@tinguyen-desktop:~/Desktop$ sudo dpkg -i libdb1-compat_2.1.3-7_i386.deb 
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java5-jdk' missing, assuming package has no files currently installed.
89403 files and directories currently installed.)
Preparing to replace libdb1-compat 2.1.3-7 (using libdb1-compat_2.1.3-7_i386.deb) ...
Unpacking replacement libdb1-compat ...
dpkg: dependency problems prevent configuration of libdb1-compat:
 libdb1-compat depends on libc6 (>= 2.3.2.ds1-4); however:
  Package libc6 is not installed.
dpkg: error processing libdb1-compat (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdb1-compat
tinguyen@tinguyen-desktop:~/Desktop$ sudo dpkg -i libc6_2.3.2.ds1-20ubuntu13_i386.deb 
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java5-jdk' missing, assuming package has no files currently installed.
89403 files and directories currently installed.)
Preparing to replace libc6 2.5-0ubuntu14 (using libc6_2.3.2.ds1-20ubuntu13_i386.deb) ...
Unpacking replacement libc6 ...
Replaced by files in installed package tzdata ...
Replaced by files in installed package belocs-locales-bin ...
/bin/sh: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /bin/sh)
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/bin/sh: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /bin/sh)
dpkg: error processing libc6_2.3.2.ds1-20ubuntu13_i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
/bin/sh: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /bin/sh)
dpkg: error while cleaning up:
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 libc6_2.3.2.ds1-20ubuntu13_i386.deb[/I]

Did any of you encounter this problem before? Do you know how to solve it?
Thanks a lot.

---

### Post by zvacet on 2007-04-27
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libc6&searchon=names&subword=1&version=feisty&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libc6&searchon=names&subword=1&version=feisty&release=all")

---

### Post by widernet_project on 2007-04-30
Hi,
Thank you for your help. I figure out that if I don't use "dpkg" command, but just use "apt-get install PACKAGE_NAME" and connect with the Internet, then it works well.

---

### Post by zvacet on 2007-05-01
That is the way to install packages.You can also use **aptitude** instead of apt-get,because aptitude pull all dependencies you need with the package.

---

