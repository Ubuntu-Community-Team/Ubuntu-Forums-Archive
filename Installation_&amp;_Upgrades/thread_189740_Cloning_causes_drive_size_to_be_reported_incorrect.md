---
title: "Cloning causes drive size to be reported incorrectly?"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by TwistedLincoln on 2006-06-05
I've recently created an image of a system using Partimage and dd (for the MBR).  The size of this original drive is 4gb.  I reinstalled Ubuntu on a 30gb hard drive, and copied the MBR.  I then blanked the drive, and restored the MBR.  I then proceeded to copy the data from the /dev/hda1 partition on the 4gb drive to the corresponding partition on the 30gb drive.  

The copy worked fine, and Ubuntu booted and performed exactly as it did on the old drive.  However Ubuntu reports the drive size as 30gb, but the partition as 4gb (with only 1.5gb free).  Running cfdisk and QTParted, I see that the partition is in reality ~28gb, as it should be.  

I tried repeating the situation again, but this time I created the partitions manually (rather than making a copy of the MBR).  I got the same results -- the system works fine, but won't see the entire partition.  

This leads me to believe that there is something within Ubuntu itself that tells the OS what size partition it lives on, regardless of what the MBR/partition table reports.  If this file needs to be modified accordingly, then that is to be my goal.

Does anyone have and idea if such a file exists?  If so, where is it?  Any help would be greatly appreciated.  

--TwistedLincoln

EDIT: I'm using the OEM install of Ubuntu 6.06, if it matters

---

