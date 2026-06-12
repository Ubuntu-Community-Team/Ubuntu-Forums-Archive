---
title: "Error updating Ubuntu 12.04"
date: 2014-12-07
forum: Installation &amp; Upgrades
---

### Post by Sanjucta_Ghose on 2014-12-07
Update manager tells me to update libdrm-intel1

Installed version: 2.4.46-1ubuntu0.0.0.1
Available version: 2.4.52-1~precise1


However the update fails. When I try to run apt-get -f install , I get the following message:- 

=====================================================================================
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libdrm-intel1
The following packages will be upgraded:
  libdrm-intel1
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/65.8 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing libdrm-intel1 (--configure):
 libdrm-intel1:amd64 2.4.46-1ubuntu0.0.0.1 cannot be configured because libdrm-intel1:i386 is in a different version (2.4.52-1~precise1)
dpkg: error processing libdrm-intel1:i386 (--configure):
 libdrm-intel1:i386 2.4.52-1~precise1 cannot be configured because libdrm-intel1:amd64 is in a different version (2.4.46-1ubuntu0.0.0.1)
Errors were encountered while processing:
 libdrm-intel1
 libdrm-intel1:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
=======================================================================================================

How do I resolve this?

---

### Post by nerdtron on 2014-12-07
Why do i see a 32 bit package and 64 bit package? Did you install anything not from the software center?

> libdrm-intel1:**i386 **2.4.52-1~precise1 cannot be configured because  libdrm-intel1:**amd64 **is in a different version (2.4.46-1ubuntu0.0.0.1)

---

