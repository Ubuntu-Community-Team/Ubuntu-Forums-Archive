---
title: "Mini/Alternate keeps installing on usb stick instead of hdd"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by flammenwurfer on 2010-12-22
Twice now I've tried installing just a base ubuntu system with the mini.iso on a usb drive.  The install goes fine.  I manually partition the 250GB hard drive in the computer thinking that's where I'm installing it to but it keeps getting installed on the usb drive instead of the hard drive.  Or maybe it's just grub that got installed on the usb drive.  

When I boot the computer without the usb drive in, I just get a blinking cursor and nothing happens.  If I reboot with the usb drive in it boots to the terminal like it should.  Is there an option I'm missing somewhere?

---

### Post by lemming465 on 2010-12-26
It's probably just grub that got installed in the wrong place.  This is usually an artefact of the way your BIOS enumerates IDE versus USB devices.  If so, you can probably fix it fairly easily one of two ways:
a) during an install, pick the *advanced* button on the grub page, and pick the correct location by hand
b) boot with the USB drive in, and run grub-install to put grub on the right place.

E.g. if you aren't multibooting different OS's, or if you want Ubuntu to control the master boot record, and if your root file system is on the sda drive, and you didn't make a separate partition and mount point for /boot, then **sudo grub-install /dev/sda**.  If that doesn't match your situation, write back with the output of *sudo parted list* and describe in more detail what you are trying to do.

---

