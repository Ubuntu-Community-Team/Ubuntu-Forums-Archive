---
title: "formatting usb key before creating bootable (usb key)"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by poldie on 2009-12-21
I'm trying to produce a bootable usb with Ubuntu 9.10 on it.  I've clicked on `usb startup disk creator`, and I'm at the `make startup disk` window, I have the cd in the drive (which has been detected) - all I have to do now is click Format on the USB stick (which has been detected - correct name and size) and it'll format and then install to it, right?

Wrong.  I've tried 2 usb keys now in all my ports and I get the same error each time:


---
Unable to mount 1.1 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found
---

I just want to wipe out whatever is on there, and format it (so it's definately in whatever format Ubuntu wants to make it bootable), because I've tried creating a bootable USB key before without doing format and my PC wouldn't boot from it.  These keys work fine in both windows and ubuntu on this PC, and I'm sure I've booted from a usb key on this box before.   Even if my PC can't boot from these keys presumably it should still be possible to format them?!

---

### Post by darkod on 2009-12-21
Split the process. First open Gparted (in System-Administration) and format the stick as FAT32.
Then use the USB Startup disc creator.
I've never actually tried to do the format with it.

---

### Post by bynge on 2009-12-21
If you have Windows it would be very easy and hassle free. Linux systems have reported different errors as usual.
 
Follow what ever is given here:
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Good Luck!!

---

### Post by Frdbrkl on 2010-01-05
> **darkod said:**
> Split the process. First open Gparted (in System-Administration) and format the stick as FAT32.
Then use the USB Startup disc creator.
I've never actually tried to do the format with it.


Awesome (and simple-the best kind) Advice!!!!

Thanks for the tip!

Frd
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

