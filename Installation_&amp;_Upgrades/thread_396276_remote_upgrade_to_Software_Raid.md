---
title: "remote upgrade to Software Raid"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by elguaxo on 2007-03-29
Howdy! First of all, I am an absolute Ubuntu n00b. :) 

Here is my problem. I have remote SSH access to a fresh installed Ubuntu Server 6.10. The server has two 500GB SATA drives, but everything was installed only on 1 HD, the second drive was not even partitioned.
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60447   485540496   83  Linux
/dev/sda2           60448       60801     2843505    5  Extended
/dev/sda5           60448       60801     2843473+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table
```

I found this guide: [http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)

But I have problems with the first step, setting the partitions on each disk. My first drive is already partitioned, so I don't know how to change the partitions of this first drive to **fd**

Any hints? Thanks in advance!

---

