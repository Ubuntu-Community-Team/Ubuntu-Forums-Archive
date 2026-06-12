---
title: "Trying to make my Linux partition larger, to no avail"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by Jarn on 2007-03-05
My Linux partition is getting full and my Windows partition is barely used. I took 15 gb off my Windows partition and planned to put it on my Linux partition. However, it wouldn't let me. My friend told me that it was something about the way they were ordered on the disk, or something like that - I didn't really get it. My partitions are ordered Backup, Windows, Empty, Linux, Swap. He suggested I just make a new partition and mount it in Linux, however I already have four primary partitions. So he suggested that since I almost never use my swap partition, I should nuke that and just use a swap partition, then make the 15gb into a new partition to mount in Linux. Does this sound like the best way to do this?

---

### Post by konungursvia on 2007-03-05
You can't resize a mounted partition. I'd go to windows, download and burn the ISO for gparted and then boot from that cd to resize what you want with no drives mounted.

---

### Post by Jarn on 2007-03-05
I tried that already, using the partitioner on the Ubuntu install disk. It wouldn't let me. It said my Linux partition was already as big as I could make it. Would a gparted one be better?

---

### Post by confused57 on 2007-03-05
> **Jarn said:**
> My Linux partition is getting full and my Windows partition is barely used. I took 15 gb off my Windows partition and planned to put it on my Linux partition. However, it wouldn't let me. My friend told me that it was something about the way they were ordered on the disk, or something like that - I didn't really get it. My partitions are ordered Backup, Windows, Empty, Linux, Swap. He suggested I just make a new partition and mount it in Linux, however I already have four primary partitions. So he suggested that since I almost never use my swap partition, I should nuke that and just use a swap partition, then make the 15gb into a new partition to mount in Linux. Does this sound like the best way to do this?

You might try the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
It uses a more up-to-date version of gparted than the Ubuntu live cd & is an excellent partitioning tool.

I think what you could do is delete the swap partition, then create an extended partition...you could then make 2 logical partitions within the extended partition, one for swap & one for data...if you have 1 Gb of ram or more, you probably don't need a swap partition.

---

### Post by Jarn on 2007-03-05
> **confused57 said:**
> It uses a more up-to-date version of gparted than the Ubuntu live cd & is an excellent partitioning tool.That worked. The gparted that is on the disk is capable of moving a partition left, and apparently the one on my Ubuntu disk isn't (it's an old disk). So it moved it left so the empty partition was to the right of it, and then it grew it. :D

---

### Post by confused57 on 2007-03-05
> **Jarn said:**
> That worked. The gparted that is on the disk is capable of moving a partition left, and apparently the one on my Ubuntu disk isn't (it's an old disk). So it moved it left so the empty partition was to the right of it, and then it grew it. :D
Glad it worked, older versions of gparted aren't capable of resizing from the front of the partition, only the end...the newer gparted live cd can resize from either end.  It's a great partitioner & it's free.

---

### Post by campidg on 2007-03-07
I'm having the same problem as Jarn.  I have tried downloading gparted but for some reason it would not download.  Someone on this thread mentioned that gparted should be downloaded using windows.  I no longer have the option of booting windows with my current grub booter.  Can someone help me out of this one?
I am running dapper on the second partition and w98 on the first partition.

Cheers,

Cam

---

### Post by Jarn on 2007-03-07
> **campidg said:**
> Someone on this thread mentioned that gparted should be downloaded using windows.They just meant because my Linux partition didn't have enough room left to save it.

---

