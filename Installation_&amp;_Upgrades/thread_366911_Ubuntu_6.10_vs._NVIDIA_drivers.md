---
title: "Ubuntu 6.10 vs. NVIDIA drivers"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by thecanfield on 2007-02-21
Hello All,
  Im trying to install mythtv, doing a step by step walk through and have a friend who has done this before helping me.....everything is working as advertiesd untill i get to the part where i install the NVIDIA drivers and this is the command im told to execute.

sudo apt-get install nvidia-glx nvidia-kernel-common

and this is what the output is.....notice the error at the bottom

Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-kernel-common is already the newest version.
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B/4066kB of archives.
After unpacking 12.6MB of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 1:
 EOF after field name `'
E: Sub-process /usr/bin/dpkg returned an error code (2)

so if anyone has any input or assistance it would be greatly apreciated
-ThanX

---

### Post by zvacet on 2007-02-21
Try this to install NVIDIA drivers
[http://lunapark6.com/?p=2717]("http://lunapark6.com/?p=2717")

---

