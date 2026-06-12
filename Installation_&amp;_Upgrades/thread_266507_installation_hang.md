---
title: "installation hang"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by rexbanner on 2006-09-27
Hi, I'm trying to install ubuntu 6.06.1 and it is hanging when it gets to the "select disk" screen. I've also tried the alternate installation and I get a blank screen at one point which I'm assuming is the disk selection/partition phase.

Currently I am running RedHat enterprise 4 and the filesystem is ext3. I can still happily boot off my hard drive, so it is definitly there and detectable by the bios.

The hardware is a Dell optiplex gx280 and the hard drive is sata, but other people in my office have been able to install ubuntu happily with no detection problems so I'm assuming ubuntu supports this hardware configuration. I'm guessing my issues have to do with what is currently living on my hard drive.

help!

---

### Post by hajk on 2006-09-27
You should give more information, like the current partition table for your HD; and how you want to use or change this for the Ubuntu install. For example, you need a chunk of unallocated space on the disk to install Ubuntu in -- is that already available? If not, which existing partitions (and all contents) do you wish to give up?

---

### Post by rexbanner on 2006-09-27
Ok, so that is probably my issue. My disk is completely allocated to RedHat right now. I'd like to just wipe it and completely reformat for the Ubuntu install. Why isn't the installer smart enough to do that? =\

Do I need to boot off some other iso, reformat my disk and then install ubuntu?

In any case, here is my fdisk info:

Command (m for help): p

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14        9726    78019672+  8e  Linux LVM

---

### Post by hajk on 2006-09-28
The installer is smart enough...;) After it has asked some questions about language and time zone, it should ask about disk partitioning. One of the options is to wipe the whole disk, then install Ubuntu on it -- that's the one you want. It will create /dev/sda1 with an ext3 FS mounted on root, and (in a logical partition) /dev/sda5 for swap; and the install should go forward from there on.

There are several alternatives if this doesn't work:

1. In the installer, choose manual partitioning of the disk, which starts gparted. Delete the existing partitions, leaving unallocated space, then back up a couple of screens and choose installing Ubuntu in the largest unallocated space.

OR

2. Use a program like fdisk (or cfdisk or (g)parted) from any liveCD to create the unallocated space before using the installer. The Ubuntu liveCD can be used for this, but also a Knoppix disk (always handy). Remember that  a liveCd may actually use an existing swap partition, so you must release this first with the swapoff command. You might also already create the new partitions with the FS of choice (like JFS), a choice that the installer does not give you...

---

### Post by rexbanner on 2006-09-28
Yeah, the problem is that the disk partition screen is blank, so option 1 is not possible. :(

I guess I'll have to manually repartition and then do the install. ](*,) 

Thanks for your help hajk

---

### Post by rexbanner on 2006-10-09
Ok, so I found the problem. My bios was set to combination mode for my sata drives. When I switched it to normal and then ran the installation, everything worked as anticipated.

---

