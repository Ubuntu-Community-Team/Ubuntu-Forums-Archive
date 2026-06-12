---
title: "fake raid empty /dev/mapper (9.10, intel Skulltrail)"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by pinan on 2010-02-26
I trying to install ubuntu on a intel skull trail system using the fake raid software.

I have the board set up for raid 1.

Installing ubuntu goes well enough until the intial reboot is tried.

The system hangs in the ash shell with a refference to a missing file in /dev/mapper.  The name of this file is the character special file for the /boot filesystem.

If you look in /dev/mapper there is character special file called cotrol, but no other files.

I assume that part of the boot process dynamic populates the /dev/mapper with the character devices that refer to the different raid partations.

looking /etc/modules
lists
usbhid
e1000e
ohic1394
ieee1394

I assume that e1000 is the ehternet,usbhid is the usb system, 1394 is for the ieee1394 interface, should this file also include a reference to the fake raid software?

If thats not the case can anybody suggest any fixes or any thing that I should do?

---

