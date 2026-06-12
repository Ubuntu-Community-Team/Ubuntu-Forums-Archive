---
title: "Looking to install XP and Ubuntu in Dual Boot Setup w/ Mult Hard Drives"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by gregin_az on 2009-12-30
Okay, so I've decided to tread into the Linux pool, mainly to eventually establish a media server using MythTV.
 
Research led me to Ubuntu and several examples made the install of a dual-boot situation look painless and easy.
 
I've created the CD and booted successfully from the same.  I choose the install and everything looks good.  The machine is running with three physical IDE drives with XP being the only thing installed in C:  I use the other two drives as data drives.
 
When Ubuntu reaches the point of install / partitioning, it says "No other operating systems on this computer" and goes on to suggest that it create "side by side" partitions, but no mention of XP.   I suspect it's referring to one of my data drives, but am not sure.
 
Oddly, below there's a message / option that says something like "erase everything" along with a grayed out message that says "Warning, this will erase Windows XP Home Edition".  
 
I'm concerned about proceeding, as one message says "no opearting system", while the other warns me about deleting XP.  Also concerning is that it will wipe out all the information on one of my data drives to install Ubuntu.
 
I've looked on the web for examples, but can't find any.  Suggestions / insight would be very much appreciated.

---

### Post by dstew on 2009-12-30
The message "no operating system on this computer" is not optimal, since this is referring only to the disk you have selected for installation. It really should say "There is no operating system on the selected disk". You can proceed safely (if this is in fact the disk you want to install to). You can erase everything on the disk, or create side-by-side partitions.

If you select the Windows disk, the partitioner will warn you that using the whole disk will wipe out Windows XP. It is greyed out because you have not selected the XP disk to install to.

Even though the partitioner says "No operating system on this computer", when you get down to the last step, when it installs grub, it will find the Windows OS and create a menu entry for it.

As a precaution, if you have any irreplaceable data on any of your partitions, you should back that data up. The process is generally safe, but any time you repartition a disk, you can have problems.

One other thing: the installer partitioner for 9.10 has a bug that prevents it from seeing all the disks in some systems with RAID BIOS extensions. If you can see all your disks in the partitioner drop-down list, then you don't have this problem. If you can't see your other disks, it might be wise to do the workaround before partitioning. The workaround is to remove the dmraid program from the Live CD system, with the command```
sudo apt-get remove dmraid
```.

---

