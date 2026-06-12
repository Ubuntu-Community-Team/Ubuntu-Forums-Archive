---
title: "help: cannot boot 64-bit ubuntu 12.04"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by honestann on 2012-05-31
I decided it was time to update (not upgrade) my ubuntu (single boot) computer from 64-bit v10.04 to 64-bit v12.04. Unfortunately, for some reason (or reasons) I just can't make it work.
 
I am attempting a **fresh single-boot install** of 64-bit v12.04 onto a **new 3TB disk drive** (seagate SATA3 @ 7200rpm). My current 64-bit ubuntu v10.04 installation is on a similar but somewhat older 1TB disk drive (seagate SATA3 @ 7200rpm). To perform the attempted install of v12.04 I unplug the SATA cable from the 1TB drive and plug it into the 3TB drive. This assures I do not damage to my working v10.04 installation.
 
I downloaded the ubuntu 64-bit v12.04 install DVD ISO file (~1.6 GB) from the ubuntu releases webpage and burned it onto a DVD. I have downloaded 3 other DVD ISO files and tried them too with identical results (ubuntu DVD, ubuntustudio DVD, ubuntu CD). I run the "check disk" on the DVDs at the beginning of the installation process to assure the DVDs are valid.
 
When installation completes and the system boots the 3TB drive, it reports "unknown filesystem".
 
I also installed on two older 250GB seagate drives, and when they try boot up the first time it reports "grub error 15".
 
During every install I plug the same SATA cable (sda) into only one disk drive (the 3TB or one of the 250GB drives) and leave the other disk drives unconnected (for simplicity and safety).
 
It is my understanding that 64-bit ubuntu (and 64-bit linux in general) has no problem with 3TB disk drives. In the BIOS I have tried having EFI set to both "enabled" and "auto" with no apparent difference (no success and same error).
 
I have tried partitioning the drive in a few ways to see if that makes a difference, but so far it has not mattered. Typically I manually create partitions something like this:
 
```

8GB  /boot  ext4
8GB  swap
3TB  /      ext4

```
 
But I've also tried the following, just in case it matters:
 
```

100MB  boot   efi
  8GB  swap
  8GB  /boot  ext4
  3TB  /      ext4

```
 
Note: In the partition dialog I specify bootup on the same drive I am partitioning and installing ubuntu v12.04 onto. It is a VERY DANGEROUS FACT that the default for this always comes up with the wrong drive (some other drive, generally my 2TB external USB drive). Unless I'm stupid or misunderstanding something, this is very wrong and very dangerous default behavior.
 
Note: If I connect the SATA cable to the 1TB drive that has been my ubuntu 64-bit v10.04 system drive for the past 2 years, it boots up and runs fine.
 
I guess there must be a log file somewhere, and maybe it gives some hints as to what the problem is. I should be able to boot off the 1TB drive with the 3TB drive connected as a secondary (non-boot) drive and get the log file, assuming there is one and someone tells me the name (and where to find it if the name is very generic).
 
After installation on the 3TB drive completes and the system reboots, the following prints out on a black screen:
 
```

Loading Operating System ...
Boot from CD/DVD :
Boot from CD/DVD :
error: unknown filesystem
grub rescue>

```
 
Note: I have two DVD burners in the system, hence the duplicate line above.
The same install and reboot on the 250GB drives generates "grub error 15".
 
I just downloaded the latest daily build of 64-bit ubuntu v12.04 and the error message on reboot changed from "unknown filesystem" to "invalid arch independent ELF magic".
 
Sigh. Any ideas?
 
==========
 
```

motherboard == gigabyte 990FXA-UD7
CPU == AMD FX-8150 8-core bulldozer @ 3.6 GHz
RAM == 8GB of DDR3 in 2 sticks (matched pair)
HDD == seagate 3TB SATA3 @ 7200 rpm (new install 64-bit v12.04)
HDD == seagate 1TB SATA3 @ 7200 rpm (current install 64-bit v10.04)
GPU == nvidia GTX-285
DVD == one DVD burner (SATA)
DVD == one bluray burner (SATA)
USB == external seagate 2TB HDD for making backups
??? == no overclocking or other funky configurations

```
 
Remember, ubuntu 64-bit v10.04 boots and runs fine on the seagate 1TB.

---

### Post by roffisserver on 2012-05-31
What Computer did you burn it with? If you burned the CD wrong that could be a problem. Also have you ever used this drive before?

---

### Post by honestann on 2012-05-31
> **roffisserver said:**
> What Computer did you burn it with? If you burned the CD wrong that could be a problem. Also have you ever used this drive before?
 
I have burned 4 DVDs at this point. I burned 2 of them on my winxp64 system (a separate computer), and 2 of them on the 64-bit ubuntu 10.04 system on the 1TB drive in this system).
 
I have burned dozens of ISO files to DVD in the past, so that's not an issue. Also note that the first step in the installation process asks whether to test the content of the DVD for errors, which I do (the first time I try to install that DVD). Also, I see zero reported errors on the screen during the install process, which runs to completion. Also, I read, write and play files on these DVDs often, so I know they work.
 
As for the 3TB drive, I bought it about 3 months ago and had saved some files on it previously, but it never hosted an operating system.  During my install process I always have the drive newly partitioned as specified above.

---

### Post by darkod on 2012-05-31
Idea number 1. On a 3TB disk the partition table would need to be gpt, not msdos.

I see in your partitions layout you never mentioned the bios_grub partition. On gpt disks, grub2 needs a small 1MB partition, with NO filesystem, nothing, just the bios_grub flag set. This is because grub2 doesn't fit on a MBR of gpt disks, unlike on msdos.

Idea number 2. Not sure if EFI boot is making issues for you, the AUTO option should work like bios boot mode I guess, not using EFI. Otherwise you need a 250-300MB FAT32 EFI system partition on the disk and it needs to be the first partition always.

Try idea number 1. From live mode, make a new gpt table on the disk. Create 1MB partition with no filesystem, with the bios_grub flag.

```
sudo parted /dev/sdX
unit MiB
mklabel gpt
mkpart primary 1 2
set 1 bios_grub on
quit
```That should create the partition. After that create your /boot and all the partitions you want, either in advance or during the install.

Leave the EFI mode on AUTO. See if this works.

---

### Post by honestann on 2012-05-31
> **darkod said:**
> Idea number 1. On a 3TB disk the partition table would need to be gpt, not msdos.
 
I see in your partitions layout you never mentioned the bios_grub partition. On gpt disks, grub2 needs a small 1MB partition, with NO filesystem, nothing, just the bios_grub flag set. This is because grub2 doesn't fit on a MBR of gpt disks, unlike on msdos.
 
Idea number 2. Not sure if EFI boot is making issues for you, the AUTO option should work like bios boot mode I guess, not using EFI. Otherwise you need a 250-300MB FAT32 EFI system partition on the disk and it needs to be the first partition always.
 
Try idea number 1. From live mode, make a new gpt table on the disk. Create 1MB partition with no filesystem, with the bios_grub flag.
 
```
sudo parted /dev/sdX
unit MiB
mklabel gpt
mkpart primary 1 2
set 1 bios_grub on
quit
```
 
That should create the partition. After that create your /boot and all the partitions you want, either in advance or during the install.
 
Leave the EFI mode on AUTO. See if this works.
 
Okay, I tried your approach #1. This is what happened.
 
I got some warning dialogs when I executed some of the lines above, but I told parted to go ahead and perform the operation anyway. Typically the warnings were that it could not tell the kernel what was happening for some reason (maybe because the kernel was booted off the DVD, not this or any hard disk).
 
When I got to the partition portion of the install process, it showed me a 1MB free space at the beginning, followed by 1MB with a type called "biosgrub" in the dialog. I added an 8GB swap partition, an 8GB /boot partition, and a 3TB / partition after the "biosgrub" partition.
 
When I clicked "install now", it displayed a dialog with the following two paragraphs of text:
 
-----
The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as an "EFI boot partition" and should be at least 35MB in size. Note that this is not the same as a partition mounted on /boot.
 
If you do not go back to the partitioning menu and correct this error, boot loader installation may fail later, although it may still be possible to install the boot loader to a partition.
-----
 
I clicked the "go back" button on this dialog, deleted all partitions, then created the following partitions:
 
```

/dev/sda1   biosgrub        68 MB
/dev/sda2   swap          8590 MB
/dev/sda3   /boot         8590 MB
/dev/sda4   /          2983344 MB (rest of disk)

```
 
Interestingly, the biosgrub partition can be made with the install program, which is what I did. In the list of partition types it is called "reserved BIOS boot area" (nothing about grub, but once created the filesystem type is called "biosgrub" in the partition dialog).
 
Okay, I figured 68MB is plenty large enough (larger than 35MB they requested). But when I selected "continue", it gave me the same warning dialog again. Not sure why. But this time I just kept going and clicked "install" to see what happens. It is going through the install process now. When it finishes and tries to reboot, I'll add more text to this message to report the results.
 
Yikes! Bad news! Now when the system tries to boot, nothing appears after:
 
```

Loading Operating System ...
Boot from CD/DVD :
Boot from CD/DVD :

```
 
Okay, now what?

---

