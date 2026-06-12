---
title: "A Fresh Install, then brown screen (nothing works)"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by tmcw on 2005-06-05
I have a USB external drive, 120 gigs, already formatted FAT32 with 4 partitions. Nautilus recognizes this drive as usb0 and doesn't allow it to be browsed, giving the error "mount: I could not determine the filesystem type, and none was specified." It shows up in /dev/ as sdc1, 2 ,3, 5. How do I mount this? i don't think the mount command is working.

---

### Post by mingus on 2005-06-05
Have you tried to mount it from the command line?

---

### Post by az on 2005-06-05
It is an external drive with four partitions.  It is bizarre that it is not automatically mounted.  Are you running kubuntu or Ubuntu?  Did you remove any packages or install anything from a wierd repository (non-ubuntu)?

If not, this merrits a bug report (bugzilla.ubuntu.com.  If you do not report it, no one will fix it)

To see if you can mount them, do (from a consol in your home drive)

mkdir disk
sudo mount /dev/sdc1 /home/(youruser)/disk  #change the name appropriately!

try to browse that.  You would need to make four mount point to mount all foud partitions.  This is supposed to be done by the volume-manager...

---

