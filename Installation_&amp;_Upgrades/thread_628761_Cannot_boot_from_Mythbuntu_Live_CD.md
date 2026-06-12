---
title: "Cannot boot from Mythbuntu Live CD"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by TheAL76 on 2007-12-01
I'm trying to create a MythTV backend using an old Sony machine. 

The internal CD-ROM drive is broken, so I'm using an external USB drive to load the Mythbuntu CD. I changed the boot order in the BIOS to load from the USB FDD. When I boot up the machine, it looks like it tries to boot from the external CD-ROM drive (light is on, activity happening). After a while, it just gives up, moving onto the 2nd choice in the boot order.

I burned the Mythbuntu CD at a low speed (4x). I've even tried to boot from a real Ubuntu CD (one from Canonical) just to check if maybe it's my CD that's the problem. Same thing happened.

Any ideas? 

The specs:

Sony PCV-RX550
Pentium 4 (1.5 GHz)
256 MB RAM
Latest BIOS installed
Internal CD-ROM broken

---

### Post by TheAL76 on 2007-12-02
Bump

---

### Post by marcopolo1981 on 2007-12-02
Hi,
I'm definately not an expert on these things, but I do know that in order to install an OS from an external USB flash device, It has to be formatted and configured as a boot device. Otherwise trying to boot directly from it would be pointless as it only reads benign data rather than an bootable image. Please see [http://www.pendrivelinux.com/2007/01/01/usb-knoppix-510](http://www.pendrivelinux.com/2007/01/01/usb-knoppix-510) as it gives a link to a free hp formatting tool and explains a few things. It is for making Knoppix bootable from a usb key, but it should be kind of similar in making the usb flash drive act as a dvd drive. The main thing to do is make the usb drive bootable, then "burn" the iso image (extract the iso files to the external usb drive) then reboot from the usb drive. Hopefully, this method will prove easier than an external disc drive.
Again, I'm not an expert, but I did follow the instruction from the link to have knoppix boot up from usb on my first attempt.
Hope this point's you in the right direction.
Mark

---

