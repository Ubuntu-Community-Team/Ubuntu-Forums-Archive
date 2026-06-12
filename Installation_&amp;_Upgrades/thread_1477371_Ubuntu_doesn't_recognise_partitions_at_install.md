---
title: "Ubuntu doesn't recognise partitions at install"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Kleine miserie on 2010-05-08
Hi all,
I have a Dell Inpsiron 1564 core i5 with windows 7 installed and I would like to have a dual boot with ubuntu 10.04, but when I try to install from cd, the installer doesn't recognise the partitions on my hard drive. It just shows 1 big bar of 320gig (my entire disk) and no OS.

So I read other threads from people with the same problems and this is what I did:
- At the beginning my hdd was divided in a small C: partition with windows and a big empty D: (and also a small FAT and Recovery). Ubuntu could recognise these partitions, but then I did something I shouldn't have done: I made the C bigger and the D smaller with partition wizard in windows and since then Ubuntu doesn't recognise my partitions (but in windows I can see them)
- In an attempt to fix this, I tried to change the D part from ntfs to ext3, it didn't work.
- I used Testdisk (in windows) to rewrite my partitiontable. It ****ed up my windoze but didn't fix the problem
- I have also added all_generic_ide at the end of the bootcommand when booting from install cd, but I didn't see any change

Can anyone help me? I'm still a big linux noob, but I'm planning to learn how to use it and eventually stop using windows.

Thanks

---

### Post by srs5694 on 2010-05-08
Please start a Linux emergency disc (such as [PartedMagic](http://partedmagic.com/) or [System Rescue CD](http://www.sysresccd.org/)), launch a text-mode command prompt (often called "Terminal", "Konsole", or "xterm"), and type "fdisk -lu". Post the results of typing that command (post the output within a [noparse]```

```[/noparse] block for legibility). You can cut-and-paste it into a file that you save to a USB flash drive or the like. This command will show us precisely how your hard disk is laid out. Chances are there's a subtle error that Windows is ignoring but that's confusing the Ubuntu installation partitioner.

---

### Post by Kleine miserie on 2010-05-09
Ok thank you for your response!
I will try that later today and post the results in here

---

### Post by Kleine miserie on 2010-05-09
I used parted magic and this is what I got:

```
Welcome - Parted Magic (Linux 2.6.32.11-pmagic)
Most of the filesystem tools and partition programs featured by Parted Magic
include man pages.  To read a manual page,  simply type man and
the name of the tool. (Examples: 'man ntfsprogs' or 'man fdisk')

root@PartedMagic:~# fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3038db8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206844      102398+   6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848    20686847    10240000    7  HPFS/NTFS
/dev/sda3        20686848   497870408   238591780+   7  HPFS/NTFS
/dev/sda4       497870415   625153409    63641497+   f  W95 Ext'd (LBA)
/dev/sda5       497870478   625137341    63633432   83  Linux

Disk /dev/sdc: 4040 MB, 4040724480 bytes
125 heads, 62 sectors/track, 1018 cylinders, total 7892040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3223366781  3470046704   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(415918, 36, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(447747, 120, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   432871117  1208554935   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(55854, 42, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(155942, 71, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?  1869562563  3788792630   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(241233, 109, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(488876, 58, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?  3189243904  3197566977     4161537    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(411515, 42, 51)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(412589, 35, 58)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
root@PartedMagic:~# 

```

---

### Post by srs5694 on 2010-05-09
First, /dev/sdc is a 4GB disk with either a corrupt partition table or no partition table. If you've got a 4GB USB flash drive or something like that, this is probably fine; but if you've got a second hard disk that *should* be partitioned, something is wrong. I'll assume this is just a USB flash drive. For safety, you should remove it when you install Linux.

Your problem is caused by your extended partition (/dev/sda4), which ends at sector 625153409, which is after the end of your disk (625142448 sectors). Fortunately, none of your real partitions is malformed, so the fix is just a matter of correcting the end point of that extended partition. To do so, follow these steps:


[list=1]
[*]Boot your PartedMagic CD-R.
[*]In a command prompt window, type "sfdisk -d /dev/sda > sda-parts.txt". This should create a file called sda-parts.txt.
[*]For safety, back up sda-parts.txt to a USB flash drive, a floppy disk, or some other medium other than your hard disk. You'll be able to use this backup to restore your current partitions in case of problems.
[*]Edit sda-parts.txt. (I'm not sure what editors are available in PartedMagic, offhand. Try the gedit and emacs commands, or browse for an editor in the menus. If necessary, reboot to Windows and edit the file there.) Locate the line for the extended partition (/dev/sda4) and change the "Length" value so that the partition fits within the disk. (127271970 should do the trick, but please check my arithmetic, using the disk size and partition start point from the "fdisk -lu" output to compute the maximum length. Any value that brings the end point to between the /dev/sda5 end point and the final disk sector should work.)
[*]Type "sfdisk --force /dev/sda < sda-parts.txt" to write the changed sda-parts.txt partitions to disk.
[*]Type "gparted" or otherwise launch GParted to edit your partition table. You should now be able to do so. Go ahead and set up your partitions for Linux.
[*]Reboot into the Ubuntu installer. It should now work. Use the "manual" or "advanced" partitioning option (I don't recall precisely what it's called) to select which partition(s) to use for Ubuntu.
[/list]


You can skip the next-to-the-last step and use the Ubuntu installer's partitioner if you like; however, doing the partitioning in PartedMagic enables you to verify that the changes worked without rebooting. If problems persist, you can type "fdisk -lu" again and check the partition start and end points for overlapping partitions and to be sure that no partitions end after the disk's end. (Note that the extended partition, /dev/sda4 in your case, is a placeholder for logical partitions, just /dev/sda5 in your case. Thus, /dev/sda5 resides entirely within /dev/sda4.)

---

### Post by simonrodan on 2010-05-09
I have whiat my be a similar issue. I am reinstalling 9.10 (10.04 seems to have issues with VMware player so I'm going back 9.10) using the amd64 alternate installer.

The installer partition step is only seeing 3 of the 4 disks on the system: /dev/sda is not recognized, /dev/sd[b-d] are. It's there in the bios and if I drop into a shell from the installer, I can see using fdisk /dev/sda: the partitions from the old system are there. 

It's also part of a 2 RAID arrays (one is raid0, the other raid10) both of which span all four discs. The installer reassembles correctly them and I can mount the arrays from the shell - the file system on the arrays are intact. 

Since the raid arrays use sda, the OS knows they're there but the installer doesn't. Since I want to include sda in the installation (the installed OS will go on the raid0 array with my data on a raid10 partition) I can't move forward with the install unless the installer lets me identify a partition for the /boot which I wanted to put on /dev/sda

Sorry for asking what is probably a simple question.

---

### Post by Kleine miserie on 2010-05-09
Thank you srs5694 for the easy and detailed solution. I'll try it as soon as possible.
That 4GB drive is (indeed) the usb I used to boot parted magic. I think I understand everything, I just don't see how you calculated 127271970. I multiplied and substracted almost every number, yet I didn't get near it :s

One last question: When I rewrite my partition table will it cause windows to stop booting? Because I rewrote it with testdisk and I couldn't boot windows; I executed every fixmbr command I could find without solving it and eventually I had to format and re-install.

I'll let you know if it worked.

Thanks

---

### Post by simonrodan on 2010-05-09
Problem overcome if not solved. From the installer's shell I used fdisk to delete all the raid0 partitions, restarted the installation and then recreated the array in the disk partitioner in the install process. 

It's probably just me but the detection of disk and partitions in the installer seems rather idiosyncratic. For example, if you don't create all the raid partition during the install it won't recognize existing ones.

---

### Post by srs5694 on 2010-05-09
> **Kleine miserie said:**
> Thank you srs5694 for the easy and detailed solution. I'll try it as soon as possible.
That 4GB drive is (indeed) the usb I used to boot parted magic. I think I understand everything, I just don't see how you calculated 127271970. I multiplied and substracted almost every number, yet I didn't get near it :s

That may be because I erred. It should be:

(Number of sectors on disk) - (Start of partition) = Maximum partition size

625142448 - 497870415 = 127272033

It looks like I used the start of the logical partition rather than the start of the extended partition. Still, my initial value would have worked; anything that ends the extended partition between the end of the last (and only) logical partition and the end of the disk will be OK.

> One last question: When I rewrite my partition table will it cause windows to stop booting? Because I rewrote it with testdisk and I couldn't boot windows; I executed every fixmbr command I could find without solving it and eventually I had to format and re-install.

It *should* still work; however, I think they've got one or two voodoo witch doctors working on the Windows booting code, so I can't make any promises.

simonrodan: Your problem is almost certainly unrelated to Kleine's. I recommend you start a new thread if you still need help.

---

### Post by Kleine miserie on 2010-05-10
Ok, since I'm working on some projects and can't afford to lose my pc right now, I'm going to stay on the safe side and wait a bit before I do these things.

Thank you for all the help and I'll post the results in here.

---

