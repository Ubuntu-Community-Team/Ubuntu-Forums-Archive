---
title: "Broken Busybox Mount in Server initrd?"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by drachs on 2008-03-07
I'm trying to install busybox on a new server platform, but I don't have access to a SATA CDROM and linux doesn't support the IDE chain that's on board this unit.

To that end, I've made a compaq flash chip with the contents of the CD and used lilo to boot up the server intall over usb.

It boots fine but it cant "Detect a cdrom drive".   I drop to the shell and try to mount /dev/sdc1 to the /cdrom directory and busy box responds with "Invalid argument".  sdc1 shows up in the syslog every time I plug and unplug it, and shows up in /sys fine.

If I try and pass -t for a filesystem type it responds with "No such device".   I can't mount any other filesystems with this mount either.

Am I doing something wrong? Is there some reason the initrd can't mount my filesystem?  Maybe there is no ext2 support in the stock kernel or something crazy like that?

The workstation version booted just fine this way and was able to manipulate the flash chip over usb.

Here is some actual output (retyped by hand):

mount /dev/sdc1 /cdrom
mount: Mounting /dev/sdc1 on /cdrom failed: Invalid argument

mount -t ext2  /dev/sdc1 /cdrom
mount: Mounting /dev/sdc1 on /cdrom failed: No such device

---

### Post by cjwatson on 2008-04-08
The ext2/ext3 modules may not be available at that point, since they're normally expected to be loaded from the CD.

Try 'mount -t iso9660'. However, there's probably a reason the installer didn't manage to do that either. Please file a bug on cdrom-detect.

---

