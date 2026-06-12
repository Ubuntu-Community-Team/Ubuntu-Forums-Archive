---
title: "USB drive concerns"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by donvan on 2007-12-22
I have just purchased a 4 gigabyte USB drive from Micro Center (marked on its case).  I would like to install UBUNTU 7.10 on it, to be used in persistant mode.  When I "fdisk -l" it shows the following for the USB sb1 drive:

Disk /dev/sdb: 4043 MB, 4043308544 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         492     3948512    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 37)

gparted says my first sector for the drive begins on 63 and last  cylinder is 7897086.

If I want to use the installation process explained on http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/, Would I set the sdb1 partition size larger than +750?

I'm also a little concerned about the present partition starting on sector 63 instead of sector 1.  Will repartitioning this drive blow away something in the first 62 sectors that the drive needs to function correctly in say XP (to allow file exchange between UBUNTU and XP)?

I had a little bad luck with a generic 16 gigabyte USB flash drive I tried to install UBUNTU 7.10 on. UBUNTU failed to get passed the startup screen and I reformatted it with gparted to fat32.  It looked ok for a while under Linux and Windows but later failed  (It wasn't accessable by gparted or by fdisk -l, and XP suggested that It needed a "disk in the drive" when I tried to open it.  I don't know if I messed it up or the drive just failed.

---

### Post by Pumalite on 2007-12-22
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

