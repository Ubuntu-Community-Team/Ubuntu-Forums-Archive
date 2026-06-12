---
title: "Reinstalling Grub after Windows XP"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by indobreakz on 2005-06-05
Hi, I had to reinstall Windows XP which has wiped out Grub and now cannot load up Ubuntu 5.04. I have Windows on my primary drive and Ubuntu on the secondary drive. I am a real newbie at this and don't want to admit failure and reinstall Ubuntu. Can someone please tell me the simplist way to reinstall Grub. I have downloaded and made a Live CD (Ubuntu) to help but I am pretty clueless as to what to do next.

Thanks

indobreakz

---

### Post by mingus on 2005-06-05
Boot from install CD

at prompt type :rescue (and kernel arguments that you needed before to boot *if* any)

you will be taken thru a series of setup screens, ending with one that displays the partitions on your system and asks you to indicate which is the / partition.  This is important because without this Ubuntu won't be mounted.

you will then be dropped into a shell prompt, do:

#grub-install /dev/*

where * is the device location you want grub installed to

/dev/hda
is the master boot record - this is the default if /dev/* is omitted

/dev/hd*n
is the partition where /boot resides where * indicates the drive and n the partition number  (for example, hdb1 is first partition on second IDE drive - the "hd" would be "sd" if this were SATA instead) - used when Ubuntu is being chain-loaded from another boot manager, e.g., Windows ntldr (Windows is managing the dual-boot, not grub)

/dev/fd0
puts grub on a boot floppy.  Useful to double-check that grub boot works as desired before writing to the MBR

Before writing grub to the MBR, good idea to make sure you have bootable Windows media for recovery of the MBR if there is a problem.

any device that you want to install grub to must be defined in /boot/grub/device.map - if this is a repeat grub-install, hda is already there.  If you need to edit this file or /boot/grub/menu.lst, you will have to get into another virtual terminal to get to nano.  Alt-F1 and then #nano

---

### Post by indobreakz on 2005-06-06
[QUOTE=mingus]Boot from install CD

at prompt type :rescue (and kernel arguments that you needed before to boot *if* any)

you will be taken thru a series of setup screens, ending with one that displays the partitions on your system and asks you to indicate which is the / partition.  This is important because without this Ubuntu won't be mounted.

you will then be dropped into a shell prompt, do:

#grub-install /dev/*

where * is the device location you want grub installed to

/dev/hda
is the master boot record - this is the default if /dev/* is omitted

/dev/hd*n
is the partition where /boot resides where * indicates the drive and n the partition number  (for example, hdb1 is first partition on second IDE drive - the "hd" would be "sd" if this were SATA instead) - used when Ubuntu is being chain-loaded from another boot manager, e.g., Windows ntldr (Windows is managing the dual-boot, not grub)

/dev/fd0
puts grub on a boot floppy.  Useful to double-check that grub boot works as desired before writing to the MBR

Before writing grub to the MBR, good idea to make sure you have bootable Windows media for recovery of the MBR if there is a problem.

any device that you want to install grub to must be defined in /boot/grub/device.map - if this is a repeat grub-install, hda is already there.  If you need to edit this file or /boot/grub/menu.lst, you will have to get into another virtual terminal to get to nano.  Alt-F1 and then #nano[/QUOTE]
 Thanks for the reply I'll give it a go and let you know how I get on!!!

indobreakz

---

