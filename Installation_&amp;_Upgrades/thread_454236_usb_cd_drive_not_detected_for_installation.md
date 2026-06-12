---
title: "usb cd drive not detected for installation"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by box2 on 2007-05-25
I have a laptop with usb cd drive.  It currently has FreeBSD 5.4 installed, and when it's booted into that umass0 detects the drive and uses it just fine.

My problem is that I cannot boot from this drive, nor does smart bootmanager from floppy detect the drive (in fact the drive locks and won't even eject during the whole boot process until an OS is loaded).

Is there a way to get the Ubuntu installation to start from FreeBSD, or other ideas for booting from the CD?

---

### Post by Paperclips4u on 2007-05-25
What you'll probably have to do is enable USB booting. Not all BIOS support USB booting though. You can try to update your BIOS, if an update is provided by the manufacturer. 

Some BIOS models will not be able to boot from a USB device unless they are USB bootable.

---

### Post by box2 on 2007-05-25
the thing about smart bootmanager is that it's supposed to be able to detect and use usb cd drives even if your bios doesn't support it.

i tried a bios update but it will not run unless there is a battery installed... which has long since been missing.

maybe i should try a boot system with more driver support?

---

### Post by Paperclips4u on 2007-05-25
Ah... Either new battery or different boot system. Not sure which is best for you. Good luck!

---

