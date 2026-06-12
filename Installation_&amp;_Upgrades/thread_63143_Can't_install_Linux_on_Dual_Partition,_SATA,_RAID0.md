---
title: "Can't install Linux on Dual Partition, SATA, RAID0"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by ~J~ on 2005-09-07
Hiya,

Kinda like the title says really, although I'll explain a little more...

My PC has 3 drives.  One 120Gb IDE (my backup drive), and 2 160Gb SATA2 drives.

My motherboard has an nVidia chipset and because of this I can, and have, set up my SATA2 drives as a RAID0 stripe.

I've installed Windows XP from the CD, and sure enough in my Windows Setup I can see my RAID0 stripe as having 300Gb of space.  I've then partitioned this with a 250Gb split for XP and a 50Gb split for Ubuntu.

Windows XP installs no problems, I then go into the disk management tools of XP, create a logical drive of the 50Gb partition and reboot with Ubuntu in the drive.

The first 'worry' I have is that the installer for Ubuntu doesn't recognise the RAID0 and thus shows 3 drives (ok, so it doesn't recognise it, but well done Ubuntu for see 3 seperate peripherals in the PC).

I can't remember the EXACT details (sorry), but basically it shows the 3 drives as...

IDE 120Gb
SCSI1,0,0 160Gb
SCSI2,0,0 160Gb

The second SCSI shows 2 partitions, a 90Gb and a 60Gb.

I select the 60Gb partition to install, set it as the /root, it's bootable and format it and install away.

Everything seems to go well until I come to the GRUB installation which simply says it's trying to install on HD0 but then stops at 50% with an error.

IDEALLY, what I'd like, is to NOT use RAID0 at all, but have the following...

120Gb IDE BACKUP only
160Gb SATA2 WindowsXP
160Gb SATA2 [100Gb | 60Gb]

And install on the 60Gb of one of SATA2 drives.

If anyone can help I'd really appreciate it.

---

