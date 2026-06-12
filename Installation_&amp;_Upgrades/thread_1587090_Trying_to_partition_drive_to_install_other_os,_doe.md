---
title: "Trying to partition drive to install other os, does this mean I have 2 drives?"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by duhfactor on 2010-10-02
Folks,

I'm a noob here, and am trying to set my machine to dual boot ubuntu and unfortunately xp because of quickbooks needed for my business. I've just begun to learn about partitioning, and wanted to be clear here, does this (below) mean I have 2 separate hard drives on this machine?

damon@damon-upstairs:~$ sudo fdisk -l
[sudo] password for damon: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42df42de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120496   967884088+  83  Linux
/dev/sda2          120497      121601     8875912+   5  Extended
/dev/sda5          120497      121601     8875881   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00cd00cd

   Device Boot      Start         End      Blocks   Id  System
damon@damon-upstairs:~$ 


I'm assuming that I can format the 80 gig one for NTSB to run xp on??

Thanks,

D

---

### Post by buntudawg on 2010-10-03
Yes.

/dev/sdb is a separate 80Gb drive.

---

