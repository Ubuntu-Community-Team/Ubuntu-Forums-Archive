---
title: "Install on Computer with Multiple Harddisks"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by yBfj3nbmn7 on 2007-09-04
I have three hard disks on my computer:

C, physical, NTSC, 60 Gig, with WinXP
F, physical, NTSC, 30 Gig, empty
G, external, FAT32, 250 Gig, with lots of big files

I'm running a Live CD with Ubuntu, and I want to install it to F. But I'm unsure what to do when the installation reaches the "partition hard disk phase." Can anybody help me?

---

### Post by vanadium on 2007-09-04
What are your options when you reach that point? I do not have the installation manual with me.

---

### Post by svtfmook on 2007-09-04
> **RedChili said:**
> I have three hard disks on my computer:

C, physical, NTSC, 60 Gig, with WinXP
F, physical, NTSC, 30 Gig, empty
G, external, FAT32, 250 Gig, with lots of big files

I'm running a Live CD with Ubuntu, and I want to install it to F. But I'm unsure what to do when the installation reaches the "partition hard disk phase." Can anybody help me?
first off, unplug the other drives.  if not, the grub will load the boot loader on all of the drive, even if they are not designated in BIOS as boot devices.

just leave the 1 hard disk in, boot with cd, install.
plug the other drives in, and select with OS to boot from by changing the boot device priority in BIOS.

---

### Post by logos34 on 2007-09-04
> **svtfmook said:**
> first off, unplug the other drives.  if not, the grub will load the boot loader on all of the drive, even if they are not designated in BIOS as boot devices.

just leave the 1 hard disk in, boot with cd, install.
plug the other drives in, and select with OS to boot from by changing the boot device priority in BIOS.

Actually what will most likely happen is that Grub will install on the first Bios drive--in this case the bootable  windows C: drive.

You really don't need to unplug the other drives.  You'll be able to easily distinguish the target install drive (F: ) based on size, and the whole point of Grub is to allow you to dual boot without having to go through the Bios.  Plus if you unplug the other drives they will not be detected, requiring you to manually edit your files so you can boot windows and mount your ntfs partitions in linux.

---

