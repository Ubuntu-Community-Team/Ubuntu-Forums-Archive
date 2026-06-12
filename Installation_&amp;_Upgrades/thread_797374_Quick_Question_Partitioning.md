---
title: "Quick Question Partitioning"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by CompactDestruction on 2008-05-17
[img]http://img372.imageshack.us/img372/4109/diskpy0.png[/img]

The Ubuntu installer shows the free space as unususable and I can't proceed. What gives?

---

### Post by uidb4056 on 2008-05-17
> **CompactDestruction said:**
> [IMG]http://img372.imageshack.us/img372/4109/diskpy0.png[/IMG]

The Ubuntu installer shows the free space as unususable and I can't proceed. What gives?

Here is showed that you have 4 primary partitions that is the maximum your disk can have. The way that you can have more partitions is to delete one of the primaries and create then an extended partition, inside the new extended partition you can create more logical partitions.

I don't know what you have in the last partition showed of 3,24 GB, but in the case that you are SURE! you don't really need, you can delete it and assign all unpartitioned space to an new extend partition, then inside it you can create your root and swap partitions for Linux. You can do it from the Live CD starting gparted or from the install process choosing manual partitioning of disk.

But be SURE first that you really don't need the last partition (may have utilities for your PC)

---

### Post by CompactDestruction on 2008-05-17
Oh its probably system recovery utilities. Oh dear... lol

---

### Post by teaker1s on 2008-05-17
defrag windows and also run
```
chkdsk /f
``` this will get the file system into a good state that you can then resize

---

### Post by undecidable on 2008-05-17
Apologies, but uidb4056's reply is absolutely correct - you cannot have more than 4 primary partitions.  While defragging can make repartitioning faster, and while you should always do chkdsk before defragging or repartitioning, defragging and chkdsk are not your problem.  Suggest you follow uidb4056's advice.  

Though a bit of detail on the procedure:
1.  backup the data on the 3.24gb partition.
2.  delete the 3.24 gb partition.
     you should now have about 21.4gb of unallocated space.
3.  Make the whole 21.4gb an extended partition.
4.  Within that extended partition create some logical partitions for Ubuntu
and maybe one 3.24gb for whatever you had on there before.

The easiest way to do all this might be to download the gparted live CD, burn it and run that first to repartition then install later. 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Hope this helps.
MC

---

