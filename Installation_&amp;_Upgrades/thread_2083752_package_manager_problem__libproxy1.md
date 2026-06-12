---
title: "package manager problem : libproxy1"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by annesab on 2012-11-13
Hi, 
I'm using Ubuntu 12.04 precise, 

I cannot use apt-get install anymore, the problem seemed to come from libproxy1, which I removed (with --purge). Now I get , running apt-get install -f, 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-fluendo-mp3:i386 patchutils liboil0.3:i386 dpatch
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libproxy1
The following packages will be upgraded:
  libproxy1
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
2 not fully installed or removed.
Need to get 0 B/56.1 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing libproxy1 (--configure):
 libproxy1:amd64 0.4.7-0ubuntu4 cannot be configured because libproxy1:i386 is in a different version (0.4.7-0ubuntu4.1)
dpkg: error processing libproxy1:i386 (--configure):
 libproxy1:i386 0.4.7-0ubuntu4.1 cannot be configured because libproxy1:amd64 is in a different version (0.4.7-0ubuntu4)
Errors were encountered while processing:
 libproxy1
 libproxy1:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

What can I do ? 

thanks for your help.

---

