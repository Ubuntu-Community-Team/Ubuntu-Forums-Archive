---
title: "Installing in mixed IDE/SCSI environment"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by dantm on 2009-12-30
Hi, so I have a mixed HD configuration environment, with both SCSI and IDE drives.
 
As such:
 
(1) 80 Gb SCSI RAID array as a primary Windows drive (and bootable);
 
(2) 150 Gb IDE drive for data
 
(3) 500 Gb IDE drive for backup
 
Before Ubuntu, my Windows 7 was installed on (1) -- the SCSI drive and it would boot up as the single operating system.
 
I installed Ubuntu 9.10 AMD64 and it did not detect the SCSI drive right away but it mentioned that Windows boot was found on the 150 Gb IDE drive, which it saw as a primary drive. I re-sized the drive to make a 50 Gb partition for Ubuntu and left 100 Gb for Windows data.
 
Everything installed ok, and I thought that Ubuntu would modify the boot record to give me the option of selecting either Windows or Linux at powerup.
 
However, Windows 7 boots off the SCSI drive upon reboot (after the install) with no option for Linux.
 
So what I'm thinking is that Ubuntu install modified the boot record of the 2nd drive (the IDE drive) to allow for both Windows 7 and Linux (no idea how it detected Windows boot since it did not see the SCSI drive) but the BIOS is set to look at the SCSI drive first.
 
Any thoughts on how I can modify the boot record to have both? I thought of:
 
(1) manually trying to change boot record info from Windows 7 to have a 2nd pointer to Linux from the first IDE drive;
 
(2) possibly re-shuffling the boot priority in BIOS to see the 2nd drive (IDE) and then it would see Linux and Windows in a double-boot config; but I doubt Windows would point to the SCSI drive since Ubuntu install didn't see it?
 
Thoughts?
 
Thanks!

---

### Post by oldfred on 2009-12-30
I like having an operating system on each drive and that operating system in the MBR of that drive. Grub often or used to always install to the boot drive because it assumed you wanted to boot grub now.

I would switch drive order in BIOS and see if you can boot Ubuntu. I do not know raid but there have been comments about and additional grub raid module since grub2 is modular. The raid module is included in server installs but not in desktop, but can be added. If you can get it to boot then someone can help with raid configuration.

---

### Post by dstew on 2009-12-30
Probably shuffling the boot priority in BIOS will be the easiest fix. By the way, it was probably just the (buggy) partitioner that did not see the SCSI drive. The grub installer likely did, and created an appropriate menu item for it. It is worth at try anyway.

The other fix would be to [re-install grub]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"). The new grub is designed to detect operating systems each time update-grub is run, so re-installing is pretty easy.

---

### Post by dantm on 2009-12-30
Thanks guys -- you were both right...

I switched the boot order in the BIOS and now the boot loader off the IDE drive has Ubuntu as the first option (boots off the 50 Gb IDE partition) and Windows 7 as the last option (boots off the SCSI partition as it should).

Works great...

---

