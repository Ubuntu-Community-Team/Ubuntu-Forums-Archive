---
title: "Not understanding choices for Installation type in 11.10 Ubuntu upgrade"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by lpatti31 on 2011-11-28
I am trying to upgrade from 9.10 to 11.10 on a dual boot system with Vista.  Since I don't want to install 11.10 alongside 9.10, and don't want to overwrite Vista, I have to choose "Something Else" from the "Installation Type" menu.  This is where I get confused.  My partitions are:
sda1 ntfs 75000mb.   This is the Vista partition.
sda6 ext3 212000mb.  This is Ubuntu 9.10
sda7 swap 9000mb.
sda5 swap 9000mb.
sda2 ntfs 12000mb.      This is the Vista recovery partition.

I assume I want to select SDA6 for the overwrite, keeping the partition size.  Do I want to remain with ext3?  I assume I should format the partition.

How do I know which mount point to choose?  I am guessing /home?

My choices for "Device for Boot Loader" are:

dev/sda  ATA Fujitsu 320 GB
      sda1   Vista 
      sda6   Ubuntu 9.10
      sda2   Vista
I am hoping to have the GRUB loader offer me the choice between 11.10 and Vista at boot.

All help appreciated.
Len

---

### Post by Quackers on 2011-11-28
Yes, sda6 would be the correct partition to over-write Ubuntu 9-10
Default partition type is now ext4 really
Mount point is " / " for root (if you are having only one Ubuntu partition)
One of your swap partitions (probably sda7) could go. You won't need 2
Device for bootloader should be /dev/sda ATA Fujitsu 320 GB

Enjoy :-)

---

### Post by lpatti31 on 2011-11-28
> **Quackers said:**
> Yes, sda6 would be the correct partition to over-write Ubuntu 9-10
Default partition type is now ext4 really
Mount point is " / " for root (if you are having only one Ubuntu partition)
One of your swap partitions (probably sda7) could go. You won't need 2
Device for bootloader should be /dev/sda ATA Fujitsu 320 GB

Enjoy :-)
Ah!  I'm glad I asked, I would not have made the right choices.  I'll try it tomorrow night.  Thanks.

---

### Post by Quackers on 2011-11-29
Ok, have fun :-)

---

