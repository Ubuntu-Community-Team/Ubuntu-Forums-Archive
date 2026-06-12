---
title: "[SOLVED] Using an existing sata drive"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by gargoyl3 on 2008-11-10
I have a system with 3 sata drives. The first sata was my existing kubuntu (gutsy) install and since I did not want to do an in-place upgrade I change my second drive to be my boot drive and installed 8.10 on the new drive.

That has been successful and now I want to get the data off my original drive. If I plug the original boot drive into a spare sata connector I can see the drive but cannot read the partition information on it.
 fdisk -l gives the following 

root@myth-tv:/dev# fdisk -l sdc

Disk sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk sdc doesn't contain a valid partition table
 

If I swap the drive cable back the original install boots Ok.

Sorry guys IO error (Idiot Operator) the screen printing on the mobo was very confusing especially with 6 stat connectors as to which was which. Once I got that right i figured out the problem.

---

