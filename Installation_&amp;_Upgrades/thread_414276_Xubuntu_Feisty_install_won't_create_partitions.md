---
title: "Xubuntu Feisty install won't create partitions"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by dgraham on 2007-04-19
I ran into this problem installing, and thought I should post the workaround in case it trips someone else up.

I used the Xubuntu desktop cd to install Feisty. Unfortunately, the installer failed when it tried to create new partitions on my disk. Turns out, the SATA disk I was installing on was magically mounting in /media, and showing up on the desktop just like a usb drive. When partitioning began, udev or something saw it had changed and mounted it, before the partitioner was finished. Adding a new entry in /etc/fstab like so:

 $ mkdir /tmp/foo
 $ sudo vi /etc/fstab
 ```
/dev/sda1 /tmp/foo ext3 defaults 0 0
```
makes it quit. Unmount the disk before performing the above.

---

### Post by ubik3001 on 2007-04-26
I saw this bug here   [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259)
Thunar ( the file manager) seems to auto mount the hard disk , so it causes the partitioner a problem.  So what i did  was wait until it did it again  ( just right before the partitioning starts, easy to notice because a file manager window pops up )   , right clicked to  the  mounted volume icon on the desktop  and unmounted it.  It carried on fine after that.

( at first i thought my boot cd was corrupt, or the drive. )

---

### Post by Mrs Harris on 2007-04-26
I'm seeing something similar with bothe i86 and amd64 Ubuntu... I'm trying to install on this [http://play.com/PC/PCs/4-/3329242/Sony_Vaio_RC202_Tower_Media_Center_PC_+_HW173DB_17_Widescreen_TFT_Monitor/Product.html]("http://play.com/PC/PCs/4-/3329242/Sony_Vaio_RC202_Tower_Media_Center_PC_+_HW173DB_17_Widescreen_TFT_Monitor/Product.html")

It gets to Prepare Partitions (5%) and then just hangs.

I'm trying to install from the live CDs over what was XP - though now it won;t boot as I've overwritten it.

Is it possible to so something similar as above on Ubuntu from the live CD?

Thanks in advance,
Mrs H

---

### Post by Anonii on 2007-07-04
That did it for me, in the PPC Xubuntu ISO.

Thanks.

---

