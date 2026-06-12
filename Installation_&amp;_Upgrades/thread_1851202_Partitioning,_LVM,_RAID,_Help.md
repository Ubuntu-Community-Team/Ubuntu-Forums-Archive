---
title: "Partitioning, LVM, RAID, Help"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by drhiii on 2011-09-27
Help... with creating logical volumes and RAID on a 5 hard drive server.

I've been studying HOWTOS but admit to being wrapped around the axle on making the right choice so am turning to this saged group for I hope is good opinion on how to go at this.

I have a server with 5 750gb hard drives.  Can anyone point me to a good way to partition it?  What I think I want to do is create sda and sdb as a single partition ( root or / ), create sdc and sdd as a RAID1, and sde as another mount point as in say, /media/extradrive  or something like that.

Basically, want to tie the 1st and 2nd drives together, use the 3rd and 4th drives as a software RAID1, and the 5th drive as an extra drive.   Is the way to do this to create an LVM for 1 and 2, RAID 3 and 4, and then partition 5 and set a mount point for it?

Is there a better way to come at tying 1 and 2, 3 and 4, and having 5 available?  What I am struggling with also is how to use the Ubuntu server install partition manager to create this scenario.   

Anyone have pointers, advice, admonishments, anything?

---

