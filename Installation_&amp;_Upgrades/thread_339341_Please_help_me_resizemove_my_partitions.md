---
title: "Please help me resize/move my partitions"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by Goldspink on 2007-01-15
My current partition table is like this:

NTFS *boot <---want to increase
Linux <--- want to reduce
Extended
Swap

My NTFS partition has Windows XP and is 12 Gb and the Linux partition is about 97 Gb. I think this is a difficult situation though as I have no unallocated space to the right of my NTFS partition. GParted doesn't seem to let me move anything.

I want to swap them round by shrinking the Linux part to 12 Gb and the rest for Windows. I thought as they are next to one another they could be grown/shrunk together in one process but the NTFS partition has a 'Max size' allocated to it so I cannot increase it.

Could anyone experienced give me some help please?

Thank you

---

### Post by Richard Kut on 2007-01-16
Hello Goldspink!  To reduce the size of your Linux partition, use gparted from a bootable CD. Otherwise, if the Linux partition is in use because you booted from it, then it is locked, and gparted cannot resize it.

Bootable gparted images can be found here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Pick the highest version number and download it. Then burn it onto a CD, and use that CD to boot your computer.

Once rebooted from the CD, gparted should allow you to shrink the Linux partition. 

Once that is done, and you have some free space on your disk again, reboot into Linux. You should be able to resize your NTFS partition using gparted from within Linux now.

Good luck!

---

### Post by louieb on 2007-01-17
Messing with partitions has turned more computers into expensive door stops than any other cause I know. Before you start backup everything you want to keep and have your installation disks handy. 
On the Linux side you can use tar for backup. There are good backup and restore threads in the how to section of the forum.
On the XP side I know XP pro has a backup and restore tool also. You may want to get some windows tools like partition magic and ghost.
For complete safety you want an external hard drive large enough to hold everything needed to backup and restore.  

GParted is a fine tool for Linux only computers, but Linux NTFS support is iffy and GParted is a Linux application, you are taking a chance there.   

After the backups have been taken then you can use your tool of choice to resize the partitions on fly.  Richard explains how to do it with GParted well.

---

