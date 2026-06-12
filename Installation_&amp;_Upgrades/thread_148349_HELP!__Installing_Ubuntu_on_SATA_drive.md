---
title: "HELP!  Installing Ubuntu on SATA drive?"
date: 2006-03-21
forum: Installation &amp; Upgrades
---

### Post by rainbowjoshua on 2006-03-21
Please.  I posted an earlier post, but I want to unmuddle the situation.  No matter what installation options I've tried, I cannot get ubuntu to boot on my SATA drive.  Mostly, I just get

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

Although the installation recognizes my hard drive (although it sees my 320 GB drive as a 250 GB), and I've tried installing it with and without LVM and with all different sizes of boot partitions.  I've tried with grub and without it.  I haven't tried lilo yet, but that's about all I can think of now.  The installer sees my SATA drive as SCSI1

Your help is so appreciated!
Joshua

---

### Post by drummer on 2006-03-22
I'd check your bios settings and make sure that the hard drive is in the boot order. I'm pretty sure "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER" is a bios error and not a grub error. If the bios setup is all good, perhaps in the install fi you manually edited the partition table, didn't set the bootable flag on the correct partition/drive.

---

### Post by rainbowjoshua on 2006-03-22
Indeed, it's a BIOS error.  The only mention that the BIOS has of the SATA controller is, it seems to assign it to the IDE interface.  The only other option is RAID controller.  ARGH!

---

### Post by Deepsyx on 2006-03-22
It is definately a Bios generated error - However I believe that if you set your boot disk as a SCSI it will read. As Sata drives are read as SCSI drives by the BIOS. 

If you have already tried that. Then the SATA drivers might not be recognized by that Distro!!! Just a couple of thoughts.

---

### Post by dicecca112 on 2006-03-22
if the driver (and the drive for that matter) aren't recognized by the distro he wouldn't have been able to install the distro.  Yes its a BIOS error, you system is still set to boot from CD-ROM when you set it to boot the cd.

---

