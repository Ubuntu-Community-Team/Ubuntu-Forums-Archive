---
title: "Error during installation: partition not found"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by TnT001 on 2005-09-28
Yesterday i decided to install ubuntu on my PC. I had no problems with the installation, untill the installer wants to reboot. The grub bootmanager is shown in textmode (i suppose there should be a graphical one normally?) and all of the available entries results in an error message "partition not found" (I don't remember the exact message, but it was something like this).

I have 2 HDs, the first one is ATA (/dev/hda) and the second is a SATA (/dev/sda). I have a dualboot with Windows XP and SUSE 9.2 already on the SATA disk and I would like to add ubuntu to it. During installation i choose to install grub on /dev/sda, but from the errormessages i receive, it looks like grub is searching for data on the wrong harddrive (hda instead of sda). How should i install ubuntu?

This are the partitions on both disks:

hda:
hda1: Backup (ntfs)

sda:
sda1: Windows XP (ntfs)
sda5: /boot (ext3)
sda6: / (Suse) (reiserfs)
sda7: / (Ubuntu) (ext3)
sda8: Linux swap
sda9: Documents (ntfs)
sda10: Data (fat32)

I tried installing with and without formatting the /boot partition, but the errors remain. BTW how can i backup my Suse /boot partition, to be able to restore it again after wiping it during the ubuntu install.

---

### Post by Biased turkey on 2005-09-28
If you already installed Suse, it created a /boot/grub/grub.conf
So you should normaly add an extra section to it.
For example:
[http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-custom-kernel-bootloader.html]("http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-custom-kernel-bootloader.html")
I know, redhat is old, very old but Redhat documentation is first class.
Another very good reference about grub:
[http://www.linux-mag.com/2003-11/]("http://www.linux-mag.com/2003-11/")
Their november and december 2003 back-issues has a great topic about grub.

---

### Post by TnT001 on 2005-09-29
I don't think my problem is related to the suse installation. Even if i let the ubuntu installer reformat the boot partition, the problem remains.

---

### Post by TnT001 on 2005-10-03
I could fix the problem by manually editing the entries in the grub configuration file (menu.lst). I had to replace all references to "(hd1,x)" with "(hd0,x)".

---

