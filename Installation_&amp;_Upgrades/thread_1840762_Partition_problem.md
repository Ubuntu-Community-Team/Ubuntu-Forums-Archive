---
title: "Partition problem"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by ahsan08 on 2011-09-08
[IMG]http://imageshack.us/photo/my-images/819/selection015.png/[/IMG][IMG]http://img819.imageshack.us/img819/5215/selection015.png[/IMG]

This is the current condition of the partition of my pc. But I want to add the 1, 2, 3 no. unallocated space to the no. 4 drive. But i couldn't do this. I tried with my ubuntu disk. Actually I don't know the system.

Could anyone please help me???

---

### Post by Quackers on 2011-09-08
If you want to add no 1 to no 4 you will have to move partitions /dev/sda11 and /dev/sda14 to the left, so that the unallocated space joins up with no 2.
This move will take time - quite a lot!.

You can then add no 2 to no 4 by resizing the ext4 partition and moving its start point to the left. It will take some time and there is sometimes a risk when moving a bootable partition but I have done it. 
You would be safer to backup what you need first!

All these changes should be made using gparted from the live cd/usb desktop - not your Ubuntu desktop. That way the file system will not be mounted as it is in your screenshot (see the little keys to the left of /dev/sda12 and /dev/sda13).

To add no 3 to no 4 you would first need to extend the extended partition (dev/sda2) to include that space, as currently it lies outside.
You could then move the swap partition to the right, then extend the ext4 partition to the right. Not sure it's worth it for 584 MB, but that's up to you.

All in all it's quite a bit of work and will take several hours to do.

---

### Post by nipunshakya on 2011-09-08
Mate, i guess you have a dual boot(seeing your /dev/sda5 onwards partitions i guess)......if that is the problem, then first thing you need to know is that windows 7 allows only 4 primary partitions...
if you have windows, you can always log in back to it and shrink volumes and then divide it accordingly so that you form a single unallocated space and don't have more than 4 primary partitions...
You can then use Gparted after a restart of your machine and then merge the unallocated space to your root partition (/) . . .if you do this, you can have an advantage of moving the ext4's start point to left.....but be careful doing this...might cause trouble as you tend to work with your bootable drive.goodluck....

One advantage of using windows' disk management utility is that you don't see your Linux partitions. And if you are unfamiliar with such sdaX partitions, then windows' Disk Management Utility might help you right...Won't take much of your time...


Regards,WinuxUser

---

### Post by Quackers on 2011-09-08
It's not a Windows limit of 4 primary partitions, it's a mbr partitioning limit.

The OP only has 2 primary partitions at the moment (sda1 and sda2).

---

### Post by ajgreeny on 2011-09-08
> **WinuxUser said:**
> Mate, i guess you have a dual boot(seeing your /dev/sda5 onwards partitions i guess)......if that is the problem, then first thing you need to know is that windows 7 allows only 4 primary partitions...
if you have windows, you can always log in back to it and shrink volumes and then divide it accordingly so that you form a single unallocated space and don't have more than 4 primary partitions...
You can then use Gparted after a restart of your machine and then merge the unallocated space to your root partition (/) . . .if you do this, you can have an advantage of moving the ext4's start point to left.....but be careful doing this...might cause trouble as you tend to work with your bootable drive.goodluck....

One advantage of using windows' disk management utility is that you don't see your Linux partitions. And if you are unfamiliar with such sdaX partitions, then windows' Disk Management Utility might help you right...Won't take much of your time...


Regards,WinuxUser
@ WinuxUser:  It is not windows 7 that limits partition numbers to 4, but the hard disk formating and mbr setup.  However the OP has overcome that limit by making sda2 as an extended partition in which for practical purposes, an almost unlimited number of partitions can be made.

@ OP:  By all means use windows disk management to work on windows partitions, though with newer versions of gparted the old problems have gone and new partitions start at the correct point on the disk.

Rather than move all those ntfs partitions, I think it may be easier to either amalgamate them into a larger one, by backing up all files and then restoring them to better arranged partitions and get rid of the unallocated space that way.  Incidentally, why so many partitions?

  To do any of that, even using gparted on the live CD, you will still need to set swapoff by right clicking on it and choosing that option.  The empty space at the end of the disk would be best used by enlarging your current swap fully to the right, giving you ~2GB.

The ext4 sda12 can be moved backwards to use any space freed by better management of the ntfs partitions, but that will take a long time and it is important to backup all your /home files first, and to make sure that you do not interrupt the partition moving operation or you will cause a total loss of your current setup.

---

### Post by ahsan08 on 2011-09-08
Many thanx to you all. gonna try to fix it.

---

### Post by coffeecat on 2011-09-08
> **WinuxUser said:**
> 
One advantage of using windows' disk management utility is that you don't see your Linux partitions. And if you are unfamiliar with such sdaX partitions, then windows' Disk Management Utility might help you right...Won't take much of your time...

I guess you might not have used Windows Disk Management in the presence of Linux partitions. Windows Disk Management does indeed see Linux partitions (why shouldn't it? - it's reading the partition table) but gets confused when the Linux partitions are logical ones. It then calls them primary with the bizarre result that it can report more than 4 "primary" partitions on a hard drive.

With Disk Utility displaying such confusion it is very inadvisable to use it in the presence of Linux partitions. It could do something very odd, such as what the Windows installer sometimes does in the presence of Linux logical partitions. (You don't want to know!)

---

### Post by nipunshakya on 2011-09-08
> **coffeecat said:**
> I guess you might not have used Windows Disk Management in the presence of Linux partitions. Windows Disk Management does indeed see Linux partitions (why shouldn't it? - it's reading the partition table) but gets confused when the Linux partitions are logical ones. It then calls them primary with the bizarre result that it can report more than 4 "primary" partitions on a hard drive.

With Disk Utility displaying such confusion it is very inadvisable to use it in the presence of Linux partitions. It could do something very odd, such as what the Windows installer sometimes does in the presence of Linux logical partitions. (You don't want to know!)

I had mentioned earlier in my comment that windows disk management doesn't see Linux partitions as well :)
To avoid reporting more than 4 primary partitions on HDD, i suggested him to be aware of that...and i guess you were right coffeecat....i knew a bunch of things about this and u expanded it..thanks...

---

