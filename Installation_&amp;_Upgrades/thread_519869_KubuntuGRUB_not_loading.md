---
title: "Kubuntu/GRUB not loading"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by inflamous on 2007-08-07
I just installed Kubuntu 7.04 with an alternate CD and I set my /boot (/dev/sda7) with the boot flag when I partitioned my drives.  When I restarted, I get:

Broadcom UNDI PXE-2.1 v2.10
Copyright (C) 2000-2006 Broadcom Corporation
Copyright (C) 1997-2000 Intel Corporation
All Rights Reserved
PXE-E61: Media Test Failure, check cable
PXE_M0F: Exiting Broadcom PXE ROM

And then my computer stops.

I reloaded into the alternate cd and I set the boot flag to the root directory / (/dev/sda8 ), and when I restart I get the same error message.

I have a Dell Inspiron 1501 with Windows XP Home installed on a primary partition 15 GB (Although Ubuntu reads it as 16 for some reason), on the extended partition I have a storage drive thats 40 GB, Kubuntu is 15 GB, I have 1 GB swap, 0.5 GB for /boot and Dell had 2 primary partitions already used for other things (a FAT16 and FAT32 which I didn't mount in Kubuntu).

The Broadcom is my Ethernet connection and I have absolutely no clue why its popping up when GRUB should.  I disabled it in windows because I use the wireless connection.

But when I set the boot flag to Windows, everything loads up perfectly fine.  Can anybody tell me why GRUB/linux isn't loading up?

---

### Post by dougfractal on 2007-08-07
PXE is the network device, check the bios boot order as it looks as if it set to:
CDROM
NETWORK
HARD DISK

---

### Post by inflamous on 2007-08-07
I set my BIOS before installing ubuntu, its:

cdrom
hard disk
...

---

### Post by confused57 on 2007-08-07
I would recommend burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

SGD can boot Windows or Linux and install grub or  Windows IPL to the mbr.  It's only a 5-7 Mb download & is a useful boot utility to have.

It's necessary to set the boot flag on a Window's partition, but Linux doesn't require this.

---

### Post by inflamous on 2007-08-08
Thanks, I'll try it out

---

