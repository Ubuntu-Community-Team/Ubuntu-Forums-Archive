---
title: "upgrade to fiesty?"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by north zulch computer geek on 2007-04-21
hey, im on dapper on an AMD K6 474 mhz, 384 mB of RAM (i know, outdated), should i attempt to upgrade to fiesty?

never got around to edgy... but i heard it was bad, like more unstable than winME.

thanks...

---

### Post by bwhite82 on 2007-04-21
Hi there, Edgy is rock solid, you'd be safer upgrading to it. I would hold off on upgrading to feisty until they fix a lot more bugs. (You need only see all of the support questions on here). At any rate, you would need to upgrade to Edgy first anyways, before you even upgraded to feisty.

---

### Post by raja on 2007-04-21
I have gone from dapper to edgy to feisty and my impression is that things only get better. I think you should give it a try unless you have some customised setup. I dont think it is true that edgy was unstable. It may not had many new features since the interval from dapper to edgy was small.

---

### Post by north zulch computer geek on 2007-04-21
thanks, yall.

---

### Post by skyjacker on 2007-09-25
Question: when gutsy is released, I plan on using it. Based on my hard drive partitions, do I have to re-format hda3,4,5, or do I just use the live cd and "install". hd1,2 is used for Win Xp (I dual boot) for now.
This is my HD 
Disk /dev/hda: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

   Device Boot      Start         End      Blocks   Id  System 
/dev/hda1   *         490        4137    29302560    7  HPFS/NTFS 
/dev/hda2               1         489     3927861    b  W95 FAT32 
/dev/hda3            4138        9565    43600410   83  Linux 
/dev/hda4            9566        9729     1317330    5  Extended 
/dev/hda5            9566        9729     1317298+  82  Linux swap / Solaris

---

### Post by raja on 2007-09-25
> **skyjacker said:**
> Question: when gutsy is released, I plan on using it. Based on my hard drive partitions, do I have to re-format hda3,4,5, or do I just use the live cd and "install". hd1,2 is used for Win Xp (I dual boot) for now.


Assuming you want to do a fresh install of Gutsy and replace the existing linux that is installed, you dont have to partition the disk. You will have to set the mount points and format the partitions. 
If you are planning to set up a separate home partition (which is a good idea in my opinion), that may be a reason to repartition.

---

