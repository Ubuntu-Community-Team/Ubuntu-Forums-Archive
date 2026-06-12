---
title: "broken packages"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by cg125 on 2007-11-16
hi
having trouble with mjpegtools

callum@ubuntu:~$ sudo apt-get install -f
[sudo] password for callum:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  libquicktime-dev libfame-0.9 libpvm3 mencoder dvdauthor zlib1g-dev libflac7
  netpbm libnetpbm10
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmjpegtools0c2a
The following NEW packages will be installed
  libmjpegtools0c2a
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
1 not fully installed or removed.
Need to get 0B/219kB of archives.
After unpacking 557kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 146673 files and directories currently installed.)
Unpacking libmjpegtools0c2a (from .../libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
callum@ubuntu:~$

---

