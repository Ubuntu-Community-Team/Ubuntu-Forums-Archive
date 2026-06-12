---
title: "merge free space ?"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by squallA on 2007-07-30
I have a hardhisk . i splited it to 3 partitions.  Then i installed windows XP on partition sda1. partition sda5 & sd6 : i use them to keep my data.

When i install Ubuntu 7.04 . I edited sda 5 from 14.7 GB -> 11 GB, sda 6 from 14.8 ->12 GB ----> then, it shows 2 free space T_T --> I don't want these .... --> I want to have a partition 7GB to use Ubuntu, and 512 MB to use swap files (Ubuntu) :) 

**How to do that, i need your help now :| i am waitting for you .....**

---

### Post by talby on 2007-07-30
The only way to do that is have LVM installed, and the installer needs some manual intervention to get it going the way that you want it.  There is a good guide [here, "How-To: Install Ubuntu on LVM partitions" @debuntu.org]("http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem") that shows you how to get LVM installed from the livecd and installed on the disk.

Basically you have to:

1 - install LVM2 on the live cd
2 - create your partitions manually
3 - install ubuntu, manually choosing said partitions
4 - install LVM2 on your disk *before* you reboot using chrooted environment

For step 2 I woud just create a /boot of 100mb, a swap of 512Mb and the remainder as LVM type "8e", and then create the other partition as a whole LVM type "8e" so you can "pvcreate" them both.  Then when you create the volume group just create a single "/" partition that spans them lot of them.

cheers!

---

