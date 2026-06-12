---
title: "Install won't see partitions"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by Aspiegeek on 2012-02-24
I have two machines I have been trying to install Ubuntu on dual boot with Win XP.  Both have Seagate drives, each has 3 primary NTFS partitions and free space (~30gb) between sda1 and sda2 (or C: & D: in Windowspeak).  Install refuses to recognize the NTFS partitions.  I've tried every Ubuntu version form 9.04 to 11.10, a couple of Kubuntus and Linux Mint 9, 10, 11 & 12.  Always ends the same: It shows my physical disk as unallocated and wants to overwrite the whole thing.

I've read every post I can find on similar problems and not found a solution.

Here is what I have done:
I have checked partition boundaries and determined that there are none out of bounds,  none overlap and none go beyond the last sector.

I've run:
sudo fdisk -l
sudo parted -l print 
sudo parted /dev/sda print
Testdisk in DOS
Various hard disk diagnostic tools to rule out disk problems
Everything looks good, no errors, out of boundaries, etc.

AND, I've never attempted a Hackintosh install or used anything resembling GUID that would bugger up things.

I tried creating an EXT4 partiton in the unused space, install doesn't see that either.

HOWEVER, Gparted DOES see the NTFS partitions, free space and/or EXT4 partitions correctly.   If Gparted can see it, howcum not install?

There is some old stuff in the forums suggesting this problem being somewhat peculiar to Seagate drives, which both of these are.  One of these drives was a member of a RAID mirror quite a while ago. It has been running as a standalone for quite a while.  The other was never RAIDed as far as I know.  If leftover RAID data were responsible for the problem, how would I remove it?

Any thoughts appreciated.

Aspiegeek

---

### Post by oldfred on 2012-02-24
RAID leaves meta data on drives that prevent installs. If you are sure you are not running RAID:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by Aspiegeek on 2012-03-03
Got it solved.  Old RAID metadata was only one problem.  Windows dynamic disk partitioning was other.  Used 
sudo dmraid -E -r /dev/sda for the RAID problem.

A Windows partitioning utility (Easeus) converted the /sda partitions to Basic.  Everything worked as it should then.

Grazie,

Aspiegeek

---

