---
title: "Installing multi boot Windows XP from within Ubuntu"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by steadybear on 2007-07-13
I'm trying to install dual boot Windows XP alongside my Ubuntu install and am having trouble.

I have my linux partition setup with around 60 gig unformatted, so when I run my Windows XP install it gives me an error that the partition isn't a Windows compatible one.

I have no floppy drive so am unable to run FDISK.

Does anyone know how I can install Windows XP as my primary OS, using GRUB to select my ubuntu install when I need to.

---

### Post by jmaryinchina on 2007-07-13
To proceed a safe install, you can create a vfat partition at using fdisk from ubuntu :

sudo fdisk /dev/hda

Then you create a primary vfat partition with the size you want.
It's useless to format it at this stage.

Once this is done you reboot with the XP cd and proceed your install. Once your windows install will be finished, XP will have erased the mbr calling grub.

You don't have to worry about that because you can reboot on the ubuntu cd and lauch a console to proceed a chroot in your system and reinstall grub on the mbr. If you have the alternate it will be simple to use the repair a broken system area, it will mount everything and then you can run grub-install hd0 is your system is on hda.

---

### Post by steadybear on 2007-07-14
When I enter:
sudo fdisk /dev/hda

I get the error:
Unable to open /dev/hda

Any help is appreciated

---

### Post by confused57 on 2007-07-14
You should be able to boot the Ubuntu live cd and use Gnome Partition Editor to format the unallocated space to FAT32...You may have to look for it, but I think it's System---Administration---Gnome Partition Editor...I could be wrong on it's location.

---

