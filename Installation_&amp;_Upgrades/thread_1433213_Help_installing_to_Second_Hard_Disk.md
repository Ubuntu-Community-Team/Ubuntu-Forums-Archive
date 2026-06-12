---
title: "Help installing to Second Hard Disk"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by samstreet101 on 2010-03-18
If anyone could help me out with this I'd be very greatful. Been using Karmic for a while now under Wubi and wanted to install it properly.

I burned the disk and booted fine. My issue is with partitioning.

I have 2 Hard disks; one with WIndows XP on it, the other is just a large disk that i use for storage.

I want to install on the 2nd hard disk but when I went to manually partition the drive (in the ubuntu set up) i can't create any partition on it without formating the entire disk (which I don't want to do as i have a lot of important data on there). I've noticed that this disk only has 1 partition on it which accounts for all the data, whereas the other disk not only has the Windows partition on it but also has 'Free Space', the second hard disk has no option of 'free space' and before anyone asks, yes there is plenty of space left on it.

Any thoughts??

---

### Post by Ben_neB on 2010-03-18
You have to use the Windows Disk Manager, since your second HDD is formatted to NTFS. 

This link should explain how to create free space from an NTFS partition, using Windows Disk Manager:

[http://www.tips4pc.com/Format%20your%20computer/how_to_shrink_a_partition_on_you.htm](http://www.tips4pc.com/Format%20your%20computer/how_to_shrink_a_partition_on_you.htm)

---

### Post by samstreet101 on 2010-03-19
Thanks very much, all done now, you were right just needed to partition the disk with Gparted (actually needed to do a checkdisk on it first). Many thanks again

---

