---
title: "From primary to logical"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by blazemore on 2010-01-20
Here's my problem.
I have all 4 possible primary partitions, but I want to install another Linux distribution alongside.
Is there any way of doing this?
Easiest way to show you is with screenshot [attached]

---

### Post by mikewhatever on 2010-01-20
Yes, there is. You'd have to delete one of the primary partitions, which will make it possible to create lots of logical ones.

---

### Post by oldfred on 2010-01-20
Where are you going to get the space from? Moving partitions can be a long process.

It would be relatively easy to remove your swap which will break you boot. then you can shrink your /home partition if you have space. then create the extended partition, add new partition and swap. To repair your boot you will have to edit fstab with the new UUID for swap. If any other partitions get renumbered or new UUID's you may also have to edit those in fstab and in grub. 
to see new UUID
sudo blkid

On second thought it may be easier just to back up /home and reinstall with the new partitions defined first.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

You cannot share /home with other distributions but can mount and share data partitions. If you want the same data you should create a data partition also. I have all my data several data partitions and now my /home is only 1GB. Some data is in NTFS for windows sharing and some in ext3 for linux sharing.

---

### Post by Leppie on 2010-01-20
you could unmount your swap, remove the partition then shrink your windows partition and create a logical partition in the free space.

---

### Post by blazemore on 2010-01-21
I have HUNDREDS of free gigabytes on /home
I'm going to:

[LIST=1]
[*]Remove swap
[*]Shrink /home
[*]Make logical partitions in free space
[*]Remake swap and new OS partition as logical
[/LIST]

---

### Post by Leppie on 2010-01-21
> **blazemore said:**
> I have HUNDREDS of free gigabytes on /home
I'm going to:

[LIST=1]
[*]Remove swap
[*]Shrink /home
[*]Make logical partitions in free space
[*]Remake swap and new OS partition as logical
[/LIST]

that's basically the same thing.
just remember, if you want to install another windows os, it most probably doesn't like being in a logical parition.

---

