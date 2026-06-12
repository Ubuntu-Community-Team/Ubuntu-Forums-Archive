---
title: "Does the installer make backups . . ?"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by jonsson on 2005-09-30
Background:
hda is an 80GB drive that contained Windows 98, Red Hat Linux 9, an FAT32 partition with lots of data and some free space. My BIOS does not support an 80 GB drive so something called Ontrack Disk Manager was downloaded from IBM/Hitachi when the drive was installed.
hdb was emptied to make room for Ubuntu.
Ubuntu was installed on hdb
Ontrack Disk Manager is gone and hda is thus unaccessible.
I had assumed that Ubuntu would leave hda alone when I installed to hdb?
Anyway, this is the current situation. I have (of course...) lost my Disk Manager install floppy and IBM/Hitachi support have informed me that "Disk Manager is no longer available for download on our site, because
systems with Windows XP and 2000 don't require it." :evil: 
I don't suppose Ubuntu makes a backup before overwriting things like this? I had just assumed it would leave my hda alone... :???:

---

### Post by mlomker on 2005-09-30
> I had assumed that Ubuntu would leave hda alone when I installed to hdb?

No, it installs **grub** (the boot manager that lets you select which operating system to start) to the first disk (your system boots from that).  Disk Manager occupies the same spot on the drive so they will not work together.

> 
I don't suppose Ubuntu makes a backup before overwriting things like this? 

No.  There are commands for backing up the MBR (master boot record) to a file but the installer can't do that (the installer runs from a CD and has nowhere to save it).

---

### Post by jonsson on 2005-10-02
Ah, well. I suppose I'll have to try to reinstall Disk Manager somehow....

Obviously I have myself to blame for not having RTFM properly but I really think that the installer should have asked me before it overwrote my MBR. The Fedora installer, for example, asks you *where* you want to install the boot loader (e.g. on yout /boot or / partition, regardless of where they are located).

---

### Post by mlomker on 2005-10-02
> The Fedora installer, for example, asks you *where* you want to install the boot loader (e.g. on yout /boot or / partition, regardless of where they are located).

And did it boot on your box?  I don't see how that'd be possible without unplugging your first drive.

---

### Post by jonsson on 2005-10-02
Yes, it did. But it required an "exteral" boot loader, such as an existing boot loader that can be configured to boot the new system as well or a boot diskette. And it did mention that the system would otherwise be unbootable.

Having Ubuntu's GRUB instad of Red Hat's GRUB would, of course,  not be a problem if it hadn't been for the Disk Manager program...

---

