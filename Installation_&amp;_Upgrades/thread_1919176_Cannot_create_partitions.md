---
title: "Cannot create partitions"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by ABPAM on 2012-02-02
Hi!
I tried to install kubuntu on my windows 7 laptop. During the windows installation I left 50GB for kubuntu. Now when I run the kubuntu setup I see all the partitions + the free space, but when I mark it (to create a new partition from it) the Add button goes inactive. My other partitions are: SYSTEM (C:), where my windows is installed, DOCUMENTS (D:) and OTHERS (E:). How can I create a partition from the 50GB free space for kubuntu?

---

### Post by sudodus on 2012-02-02
It is probably the logic of the installer, that is not understanding what you want (or the other way around). If you run Gparted during the live session, you can prepare the partition, and then select the manual method 'something else' to select manually that partition as / (root).

*Edit: you need an extended partition with logical partitions inside it. See my next post!*

---

### Post by sudodus on 2012-02-02
Since you already have three partitions, you can only make one more on the same level, so make an ***extended partition***, and then inside it, make one partition for the file system and one swap partition (swap of the same size as your RAM).

---

### Post by ABPAM on 2012-02-03
I googled a bit more about that and I come up with a new issue. Windows 7 creates additional 100MB partition and with the D:\, E:\ and C:\ partitions it completes to 4 partitions, which kubuntu installer says is the maximum for the partition table. Now that's the main problem: How to merge windows 7 (C:\) and the system reserved partition without re-installing windows

---

### Post by mastablasta on 2012-02-03
> **ABPAM said:**
> I googled a bit more about that and I come up with a new issue. Windows 7 creates additional 100MB partition and with the D:\, E:\ and C:\ partitions it completes to 4 partitions, which kubuntu installer says is the maximum for the partition table. Now that's the main problem: How to merge windows 7 (C:\) and the system reserved partition without re-installing windows
 
 
i think you can't join those two (but this would be best asked on Windows7 forums). 
 
might be easier to backup e:\ partition to some external disk and delete it. then install on the disks free space. 
 
be careful during install as linux marks partitions differently.
 
you can use cloning tools for backing up the partition with a bit-by-bit image.

---

### Post by sudodus on 2012-02-03
> **mastablasta said:**
> i think you can't join those two (but this would be best asked on Windows7 forums). 
 
might be easier to backup e:\ partition to some external disk and delete it. then install on the disks free space. 
 
be careful during install as linux marks partitions differently.
 
you can use cloning tools for backing up the partition with a bit-by-bit image.
+1
I agree, backup E: using for example ***Clonezilla*** to make a clone or even better (if you get a big enough hard drive for it) make a perfect clone of the whole hard disk drive! That keeps you safe during the partitioning work, which is risky.

If you boot from the Kubuntu install drive and post the output of
```
sudo fdisk -lu
``` we can 'see' your partitions, where they are located on the drive, and that makes it easier to give advice.

---

