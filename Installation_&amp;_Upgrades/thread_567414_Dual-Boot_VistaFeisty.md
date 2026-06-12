---
title: "Dual-Boot Vista/Feisty"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by sparcxl on 2007-10-04
I have been beating my head on my desk for the last couple of days. I run Ubuntu in a VMWare session but really want to see what it can do with full use of the hardware but I am running into some troubles. I am hoping someone here can help. I hate that my first post is a question but....

A little background: I have a machine with Vista install currently. 3 SATA drives and a PATA DVD Writer. When I try to boot 7.04 LiveCD I get a BusyBox /bin/sh/cannot access tty; job control stopped etc..etc. I have "resolved" this by using the addition parameters all_generic_ide in order to get the LiveCD to boot.  When I get to the partitioner the drives are listed as

SCSI1(0,1,0) (sda) - (this is the drive with Vista installed, NTFS) (SATA)
SCSI2(0,1,0) (sdb) - (this is the drive I have/want to install Ubuntu to) (SATA)
SCSI4(0,0,0) (sdc) - This is a storage drive (SATA)

First question that comes to mind is why they are being detected as SCSI.

The install seems to go through fine on SCSI2 - Grub installs and shows that it will setup the Vista/Longhorn boot entry.

When the install has completed GRUB boots with Error 17. I removed grub and reinstalled the Vista bootloader and attempted to use EasyBCD. Grub will fully load and show the entries for the Kernel that I instralled with Ubuntu however when selected they are not found. My understanding bootloaders is very minimal and I do not understand how the drives are labeled in Ubuntu. Any help getting this straightened out would be appreciated. I have done a lot of searching but get either outdated articles and posts and am very confused on what is doing what. If someone could link me to a definitive howto I would appreciate it.

TIA.

---

### Post by sparcxl on 2007-10-04
Anyone? 

Update** I am back to the grub error 17 -- I have tried super grub disk but it did not help. I have matched the drives in menu.lst to what I show in fdisk -l but still get the error. Not sure where to go now.

---

### Post by Gremlinzzz on 2007-10-05
sounds like a mess.i would install ubuntu on the same drive as vista and use the other drive as a slave for vista.
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

