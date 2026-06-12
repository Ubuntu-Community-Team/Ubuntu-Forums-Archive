---
title: "Update crash left LVM partitions unmountable"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by CatWeazel67 on 2008-07-22
Hi,

While doing a dist-upgrade the computer crashed and restarted. Now when it boots it cant mount my LVM partitions.

I had usr,var,home and tmp as LVM partitions with a normal / ext3 partition . 

When I boot vgscan shows one volume group (GroupOne) ok and lvscan shows the 4 logical volumes ( all ACTIVE )

If I try and "mount -t ext3 /dev/mapper/GroupOne-home /mnt/test" I get error EXT3-fs unable to read superblock ....

If I boot from a SystemRescue cd I can see all the partitions and data fine, so the actual file system appears undamaged.

How do I go about fixing this ? Is the problem with LVM or device mapper ? If I cant mount usr or var how would I go about reinstalling the LVM package (if that is the problem/solution) ?

Thanks for taking the time to look.

-- 
Simon

---

### Post by upchucky on 2008-07-22
do this and post the results.```
sudo fdisk -l
``` the l is the small letter L.

this will show the drive arrangement and provide info on how to set up the bootloader. the bootloader needs to know where the master boot record is, and where the grub file is to load linux and/or windows if you are trying to dual boot

---

