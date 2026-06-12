---
title: "Problem whit GParted in Ubuntu 7.04. ("
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2007-05-13
I have successfulle splitt a 280GB (NTFS)  hdd into one NTFS-partition hdc1 and one Ext3-partition hdc2, and shuffeld data (about 140GB) from hdc1 to hdc2 two times. I Could minimize the NTFS-partition and make an ext3-partition, but the problem was that when i had make the NTFS-partition smaler and get an unallocated area. I could not make the ext3-partition bigger over the unallocated area, that where between hdc1 and hdc2.

 I get around the problem by booting i GParted Live-CD, but make the ext3-partition bigger from about 100GB to 200GB take 12h!!!!. I have now entirely removed the NTFS-partition (hdc1) and have an unallocated area of about 70GB in the beguinning of hdc.

QUESTION 1. I dont want my ext3-partition be named hdc2, but hdc1. How do I change that?

QUESTION 2. Why can't I extend ext3-partition with GParted over the unallocated area in the beguinning of hdc then I use GParted that I have installed with synaptic?

QUSTION 3. Does the extending of ext3 go faster if I use GParted in Ubuntu instead of using GParted Live-CD?

I hope you understand my bad english, if not ask, then I maybe can explane.

/Cheers Azyx

---

### Post by u.li on 2007-05-13
> QUESTION 1. I dont want my ext3-partition be named hdc2, but hdc1. How do I change that?
The partitions are numbered in the partition map of the harddisk in the order they were created. You *could* theoretically delete the partition and create a new one with **exactly** the same size at **exactly** the same position and it should work.
If you do something wrong, you could destroy all data on that partition so unless you have a real reason to do it, don't.
I don't know if there is a better way to change the partition number, I have never seen such an option in partitioning programs.

> QUESTION 2. Why can't I extend ext3-partition with GParted over the unallocated area in the beguinning of hdc then I use GParted that I have installed with synaptic?
The GParted version on the GParted LiveCD is newer than the one in ubuntu. The older version apparently does not support moving ext3 partitions.

> QUSTION 3. Does the extending of ext3 go faster if I use GParted in Ubuntu instead of using GParted Live-CD?
I don't think so, and if it does, it will not be a big difference.

---

### Post by Azyx on 2007-05-14
> **u.li said:**
> 
If you do something wrong, you could destroy all data on that partition so unless you have a real reason to do it, don't.

The GParted version on the GParted LiveCD is newer than the one in ubuntu. The older version apparently does not support moving ext3 partitions.


I don't think so, and if it does, it will not be a big difference.


I made my hdc on another computer, and when a move i to the other computer hdc is my cd/dvd-recorder, I am little bussy just now, but I will see if a may fix it after I coming home.

Ok. so it's a new thing...but even the older GPartet have the chose to move partitions....

Ok. Thanks. But now it finnished, but it tok a lot of time with Live_CD . Thanks 

/Cheers Azyx

---

