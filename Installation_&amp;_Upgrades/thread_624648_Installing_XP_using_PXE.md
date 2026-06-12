---
title: "Installing XP using PXE"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by psycho5 on 2007-11-27
Hi everyone.

I recently installed ubuntu 7.10 32bit on a laptop using PXE lan boot, and used my computer as the host. This laptop's CDROM is spoilt, and it has no floppy drive, and no USB boot support (due to old version of BIOS). Only option was LAN boot.

Anyway, after successful installation, I want to install XP, using the same PXE setup, on another partition on the same hard disk on the laptop. I would like to mount the winxp.iso and load the appropriate bootstrap files. Does anyone know how to do that? 

mount -o loop /location/winxp.iso /mount/point <--- is that correct? 

I have no idea about the bootstrap files needed for windows. 

Another thing, I read a couple of threads saying that XP setup messes up your GRUB loader and you can't boot into Ubuntu. The solution suggested was to use the livecd to boot and recover your data and then reinstall. 

However, I can't use a live-cd on this laptop if that were to happen since its CDROM is spoiled. Is there an alternate way around this predicament? Is there a way to update BIOS through Ubuntu? That way I wouldn't have to go through all that crap. 

This laptop is an Acer Aspire 1680 with Bios Pheonix 3A03 (7 versions old). Latest version available is 3A10. 

Much help appreciated.

---

### Post by Cochise on 2007-11-27
maybe the supergrub live cd can be booted using pxe i dont know may be worth looking in to before you do anything tough. As for the bootstrap files, i think i saw something about needing the 6 bootdisk for xp and get the files from that. There a few download for M$ anyway

---

