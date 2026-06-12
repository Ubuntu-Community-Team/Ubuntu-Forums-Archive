---
title: "dpkg not checking Installed-Size field"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by kslnet on 2012-01-11
I've created a .deb file that works fine, except that the Installed-Size field in the control file doesn't appear to be read.  Even if there's insufficient disk space, dpkg tries to install anyway, then fails in the middle when the disk fills up.

I've checked the syntax of the control file, and nothing in the .deb appears to be wrong or corrupted.  What could be causing this?

Thanks in advance.

---

### Post by kslnet on 2012-01-12
Okay, I've tried this with .deb files I download with "apt-get -d  install", and the same thing happens.  dpkg seems to ignore the  Installed-Size field entirely.

karin@teeny-box:/var/cache/apt/archives$ sudo dpkg -I java-common_0.34_all.deb 
 new debian package, version 2.0.
 size 80318 bytes: control archive= 1941 bytes.
     881 bytes,    20 lines      control              
    3639 bytes,    42 lines      md5sums              
 Package: java-common
 Version: 0.34
 Architecture: all
 Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
 Original-Maintainer: Debian Java Mailing List <debian-java@lists.debian.org>
 Installed-Size: 484

karin@teeny-box:/var/cache/apt/archives$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              2899724   2817984         0 100% /



karin@teeny-box:/var/cache/apt/archives$ sudo dpkg -i java-common_0.34_all.deb 
(Reading database ... 124580 files and directories currently installed.)
Preparing to replace java-common 0.34 (using java-common_0.34_all.deb) ...
Unpacking replacement java-common ...
Setting up java-common (0.34) ...
Processing triggers for doc-base ...
Processing 2 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/3911: No space left on device

karin@teeny-box:/var/cache/apt/archives$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              2899724   2817984         0 100% /

What is the expected output when Installed-Size exceeds the available space?

---

