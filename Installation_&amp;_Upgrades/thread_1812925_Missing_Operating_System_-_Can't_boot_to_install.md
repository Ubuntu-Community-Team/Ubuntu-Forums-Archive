---
title: "Missing Operating System - Can't boot to install"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by GatorsUF on 2011-07-27
For whatever reason I have tried booting from USB on my Asus EeePC 1000HE quite a few times now and no luck.  I have tried a few different usb installer tools and they all seem to set it up fine.  However when I try to boot via USB it keeps saying "Missing Operating System" very quickly then proceeds to start Windows.

I have had Ubuntu on this computer before, but for some reason its giving me troubles.  Anyone know a fix for this?

BTW I am 100% sure the BIOS boot priority is set correctly, so thats not the issue.

Thanks in advance!

---

### Post by Leonardo74 on 2011-07-27
I think USB is the virtual drive. It will be detecyed by OS only. So you can't boot from USB.

Otherwise Check whether the required file(s) in the root directory of USB and not in the sub -directory.

---

### Post by GatorsUF on 2011-07-27
Negative, you are supposed to be able to boot from the USB...not sure why mine isn't working.

---

### Post by varunendra on 2011-07-28
If it is a USB flash drive, try changing the drive itself? Also, if there's an option in BIOS to delay USB (or 'drive') detection time, try setting it upto 5 sec.

---

