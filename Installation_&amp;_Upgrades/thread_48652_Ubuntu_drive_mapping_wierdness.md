---
title: "Ubuntu drive mapping wierdness"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by Donmiller on 2005-07-13
Hi:

I'm definately a newbee here, so please be kind...

I have two IDE drives, with my XP installation on the first (both drives use ntfs).  I just added an SATA drive so that I could install Ubuntu without messing with my current XP installation.  (The current XP installation is not game for any potentially destructive experiments).

Ubuntu installs on the SATA drive without too much trouble, but Grub showed some quirks.  I installed Grub on the SATA drive and modified my BIOS boot order to boot off of it.  I had to modify my menu.lst to get Ubuntu going, but so far my XP installion is not bootable from Grub.  I'm not in big trouble though, because I can change the BIOS boot order to get back to XP.

My device.map shows the mapping that I expected:

(hdo)    /dev/hda
(hd1)    /dev/hdb
(hd2)    /dev/sda   (the SATA drive somehow "looks" like a SCSI device to Ubuntu)

The Grub installation generated a menu.lst that points root at (hd2,0) for the Ubuntu installation, but Ubuntu will not boot unless I edit this to (hd0,0).  Whatsupwidat?  Shouldn't both (hd0) and (hd1) be my ntfs volumes?  How do I get XP to boot via menu.lst?  

Right now, hd0 is detected as a ext2 file system, and both hd1 and hd2 are detected, but Grub cannot identify their file systems.

Does grub consider the drive that you booted from to be (hd0) no matter what device.map says?

Any ideas on how to make this setup boot both operating systems?

I know that it is likely that the real problem is between my ears...

Thanks in advance,
Don

---

### Post by al7kz on 2005-07-14
HI, When you changed the boot order you changed the drive mapping. After you changed it, hd0 is the sata, and hd1 is the xp. device.map shows the mapping before you switched. Windows has to boot from the first hard drive. See 

[http://www.ubuntuforums.org/showthread.php?t=47451&page=4&pp=10](http://www.ubuntuforums.org/showthread.php?t=47451&page=4&pp=10)

First you could try re-mapping the drives in the grub menu, so edit the menu.lst windows entry:

title Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
makeactive
chainloader +1

This will work if bios is controlling the drives, not the OS. Otherwise I would recommend you make a grub boot floppy, edit menu.lst, change the first boot drive in bios to the xp drive, boot with the grub floppy, and install grub on the mbr of the xp drive.

---

### Post by Donmiller on 2005-07-14
Well,

I tried the re-mapping, and now I get:

Error 13: Invalid or unsupported executable format :(

I'll push on a while longer.  I'll use bios boot options before I use a floppy to boot, and I want to stay away from writing to the MBR of my stable XP disk for now...

Thanks,
Don

---

### Post by Donmiller on 2005-07-14
FIXED,  FIXED, FIXED!!!

Your advice was *almost* right on.

The modification below worked:

rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

Basically, I had to delete the "rootnoverify (hd0,0)" after the map statements and replace it with a "rootnoverify (hd1,0)" before the map statements.  It seems like maybe the mapping is what Windoze sees, but maybe Grub still sees the disk as hd1?

Thanks for your help,
Don

---

