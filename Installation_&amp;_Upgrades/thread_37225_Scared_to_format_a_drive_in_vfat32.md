---
title: "Scared to format a drive in vfat32"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by HJB on 2005-05-26
Hi all. Yes I am scared. I'v looked at the the **fdisk,** **mkfs.msdos** and **mkfs.vfat** commands and am now more confused that ever.
I have a 120gig hard drive, currently formatted (via Window$) as NTFS. It ahs my backup data on. I have backed it all up to two different media and now want to format that drive and use it between Ubuntu and XP in a dual  boot setup.

Is there not an easy to use GUI interface to format this drive in vfat32?. Even Windows says nothing bigger that (i think) 32gig can be done from within XP...

What command line should I use with which settings?

mkfs.msdos mentions >> 32 bit FAT  (FAT32  format)  must  (still)  be selected explicitly if you want it. This is fine but then they state the following which baffels me >> Select the number of reserved sectos. With FAT32 format at least 2 reserved sectors are needed, the default is 32. Otherwise  the default is 1 (only the boot sector).... Do I need to set this? Is it now 2, 32 or 1?

What about sectors per cluster and sector size? Will the application set this (read from somewhere on the drive) automatically?

_This drive is /dev/hdb1_

> **$ sudo fdisk /dev/hdb1**

The number of cylinders for this disk is set to 14592.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

**Command (m for help): p**

Disk /dev/hdb1: 120.0 GB, 120031478784 bytes
255 heads, 63 sectors/track, 14592 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/hdb1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hdb1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdb1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hdb1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Can I use this info?
Should I use it?
**Will this work - mkfs.msdos /dev/hdb1 -F 32**
Is this the write command or are there something much better?
Remember, I need XP to see and use this also (basically for the occasional gameing ): )

Thanks in advance
HJB

---

### Post by bored2k on 2005-05-26
> Is there not an easy to use GUI interface to format this drive in vfat32?. Even Windows says nothing bigger that (i think) 32gig can be done from within XP...

I would recommend getting one of the powerful recovery discs like [Ultimate Boot CD](http://ubcd.sourceforge.net/) wich has the following partition tools:
--
Ranish Partition Manager  	2.44
XFDISK (Extended FDISK) 	0.9.3beta
SPFDISK (Special FDISK) 	2000-03q
TestDisk 	5.7
Partition Resizer 	1.3.4
Partition Saving 	3.00
Free FDISK 	1.3.0
MBRtool 	2.2.100
MBRWork 	1.07b
FIPS 	2.0
Active Partition Recovery
--

There are better like Hiren's Boot CD v6, but they're a little "shady". You could also get gparted or qparted and work with the GUI.

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=HJB]Hi all. Yes I am scared. I'v looked at the the **fdisk,** **mkfs.msdos** and **mkfs.vfat** commands and am now more confused that ever.
I have a 120gig hard drive, currently formatted (via Window$) as NTFS. It ahs my backup data on. I have backed it all up to two different media and now want to format that drive and use it between Ubuntu and XP in a dual  boot setup.

Is there not an easy to use GUI interface to format this drive in vfat32?. Even Windows says nothing bigger that (i think) 32gig can be done from within XP...

What command line should I use with which settings?

HJB[/QUOTE]

My rule of thumb is: use native platform for formatting drives. That is, Windows for formatting drives in FAT32, and Linux for linux filesystems. 
But if you want to use Linux, I suggest installing and using gparted - nice graphical tool. 
 

I must admit that I would feel uneasy about partitioning it as a single FAT32 volume, given the 32 GB limit of windows. Even though official MS documentation states that XP can use larger volumes created by other OS, I'd test this before putting anything valuable on it. Another option is to partition it into 4 partitions of 30 MB each and format each under WIndows.

---

