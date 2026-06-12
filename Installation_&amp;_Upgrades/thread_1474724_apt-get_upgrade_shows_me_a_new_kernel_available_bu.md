---
title: "apt-get upgrade shows me a new kernel available but I already have installed it..."
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by ToniVC on 2010-05-06
Hi,

From today apt-get upgrade shows me Linux kernel 2.6.24-27 is available:

> 
xxx@yyy:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libkpathsea4 libpq5 linux-headers-2.6.24-27 linux-headers-2.6.24-27-generic linux-image-2.6.24-27-server
  linux-libc-dev nfs-common nfs-kernel-server tzdata
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.5MB of archives.
After this operation, 4096B disk space will be freed.
Do you want to continue [Y/n]?

But I already installed this same kernel version some time ago:

> xxx@yyy:~$ uname -a
Linux yyy 2.6.24-27-server #1 SMP Fri Mar 12 01:45:06 UTC 2010 i686 GNU/Linux

How is it?

Thanks in advance.

Toni

---

### Post by dino99 on 2010-05-06
into update-manager: read the details

---

### Post by ToniVC on 2010-05-06
> **dino99 said:**
> into update-manager: read the details

I'm on a server, no graphical interface... Anyway, doing some research I've found:

> xxx@yyy:~$ sudo apt-get -V upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
   libkpathsea4 (2007.dfsg.1-2 => 2007.dfsg.1-2ubuntu0.1)
   libpq5 (8.3.10-0ubuntu8.04 => 8.3.10-0ubuntu8.04.1)
   linux-headers-2.6.24-27 (2.6.24-27.68 => 2.6.24-27.69)
   linux-headers-2.6.24-27-generic (2.6.24-27.68 => 2.6.24-27.69)
   linux-image-2.6.24-27-server (2.6.24-27.68 => 2.6.24-27.69)
   linux-libc-dev (2.6.24-27.68 => 2.6.24-27.69)
   nfs-common (1.1.2-2ubuntu2.2 => 1.1.2-2ubuntu2.4)
   nfs-kernel-server (1.1.2-2ubuntu2.2 => 1.1.2-2ubuntu2.4)
   tzdata (2010h~repack-0ubuntu0.8.04 => 2010i~repack-0ubuntu0.8.04.1)
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.5MB of archives.
After this operation, 4096B disk space will be freed.
Do you want to continue [Y/n]?


So, apparently, the upgrade is from 2.6.24-27.68 to 2.6.24-27.69... I've got no message for this upgrade on the security list, so I can assume this is not an "important" one? I mean, could I safely ignore this one and wait until next kernel security upgrade? I'm trying yo do the minimum server reboots as possible... Also, where can I find information on what this upgrade exactly do? I usually get this information from the messages I receive on the security list...

Thanks.

---

