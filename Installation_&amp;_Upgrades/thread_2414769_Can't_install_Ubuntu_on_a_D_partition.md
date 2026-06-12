---
title: "Can't install Ubuntu on a D: partition"
date: 2019-03-14
forum: Installation &amp; Upgrades
---

### Post by siejo-stillboys on 2019-03-14
hey, 


I have windows installed on my C drive and im trying to install ubuntu on my D drive. I don't want to format it tho so i made it 100 gb smaller in order to make a new partition. 
I'm booting it from a usb key and I'm clicking the "something else" option to partition the drives manualy. Here comes the problem because I can turn the whole partition that I made(the 100gb one) into a SWAP partition but I can't change the volume of it so I would be left with a 100gb SWAP. Changing the volume only works on the whole D or C drive. What could be the cause.

Thanks

---

### Post by TheFu on 2019-03-14
Depending on the version of Ubuntu being installed, you might need 2, free, unformatted, partitions. If you choose LVM during the install, the installer really wants to wipe an entire disk.

Drive letters mean nothing to Unix systems.  To be certain the correct drive is used, it is best to know the vendor and how partitions are named AND double-check that the size you want is actually the selected partition. At least 10,000 new users have accidentally wiped their Windows and other OS installed by not completely understanding the naming conventions.

There are exceptions, but 80% of the time, /dev/sda is the first drive in the computer. The entire drive.  
/dev/sda1 is the first primary partition, which most Windows people would see as their "C:" drive.  Under UEFI, I don't know if that is still true. I've never used Windows with a UEFI computer.

The "D:" drive would almost certainly be the 1st partition on the 2nd physical HDD inside the computer.  That would be /dev/sdb1 in Linux.

None of this is guaranteed.  If the SATA cables are moved around, then the drive that was sda could become sdb or sdc or ... sdz. The partition numbers would remain.  Linux systems almost always use UUIDs to deal with this issue AFTER the OS is installed.  This decouples the specific SATA port connection from the way that Linux mounts the partition.  There are other methods for mounting too - by the bus-path and card and label.  Those aren't important.

Anyways, to get the most useful help, we need some facts to be provided.  There is a tool called **boot-repair** that can be installed under a live-boot flash drive, then run.  I think near the bottom is a gather information button.  Push that and post the URL back here.  It will answer all the questions we'd ask.

---

### Post by yancek on 2019-03-14
> /dev/sda1 is the first primary partition, which most Windows people would see as their "C:" drive.  Under UEFI, I don't know if that is still true. I've never used Windows with a UEFI computer.

On a windows UEFI system, sda1 is "usually" the vfat EFI partition but not necessarily so. 

Windows does not give drive letters (C, D, etc.) to non-windows filesystem partitions.  Also, the D name doesn't really tell us anything as it could be a partition on the same hard drive or a partition on another hard drive.  That has been my experience with windows.  Installing Ubuntu on a windows formatted partition is pointless, it won't work.   I think you need to do as suggested above and learn a little more about Linux drive/partition naming conventions.  Part of the problems windows users have coming to Linux is that windows uses the terms "drive, partition, volume" interchangeably.  If you can get and run boot repair, that will provide enough information so that someone can at least point you in the right direction.

---

