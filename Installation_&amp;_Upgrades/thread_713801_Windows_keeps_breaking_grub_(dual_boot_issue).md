---
title: "Windows keeps breaking grub (dual boot issue)"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by DMBryant on 2008-03-03
Okay, I've got a laptop with Windows XP installed on the internal drive (work computer so cant replace windows).  In order to install Ubuntu as well I unplugged the internal drive (to keep it safe) and installed to an external USB hard disk.  I partitioned the disk with partition 0 as ext3 (20Gb - for Ubuntu), partition 1 as swap (512mb) and partition 2 as NTFS (230Gb - to be accessed as an external drive in Windows and Ubuntu).

The installation went fine and I can boot normally into windows or use the BIOS boot-from-usb function to boot from the external disk into Ubuntu.  Everything was good.

The trouble came after accessing the NTFS partition from Windows and (I think) writing some data to it.  When I tried to boot back into Ubuntu all I get is 'GRUB' and a flashing cursor (NOT the grub command prompt).  The only way around it I have found is to reinstall grub using the live CD and then it all works fine again.  This is getting really irritating!  I have also noticed that sometimes Windows wont let me safe-remove the drive as well.

What can be causing this?  Why should windows accessing the third (NTFS) partition effect the first partition?

HELP!

Cheers :)

---

### Post by DMBryant on 2008-03-05
I may have fixed the problem by removing the device.map file from /boot/grub (actually I renamed it to device.map.bak).  I think, for some reason, the device ordering kept getting changed by Windows doing something but device.map only pointed to (hd0).

I've only tried booting Ubuntu a couple of times since the change and it's worked each time (even after copying files within windows which broke it before).

---

