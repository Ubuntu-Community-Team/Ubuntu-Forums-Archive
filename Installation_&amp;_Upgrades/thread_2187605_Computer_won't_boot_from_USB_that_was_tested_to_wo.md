---
title: "Computer won't boot from USB that was tested to work"
date: 2013-11-12
forum: Installation &amp; Upgrades
---

### Post by tsonnen67 on 2013-11-12
I recently tried to install Ubuntu 13.10 on an old machine of mine (circa 2000). I first tried using a bootable USB that I have tested and it is working. I checked in the BIOS and the only USB listing is USB-FDD, which I understand to be the wrong device, but I tried it anyway and it didn't work. Then after doing some research I learned about PLOP. I downloaded this and burned the plpbt.iso to a CD. I then attempted to use this CD to boot to no avail.

Both when I tried booting with the USB and the CD with PLOP on it I get a message saying to insert a disk and press enter.

Please help, thank you much.

---

### Post by kurt18947 on 2013-11-13
BIOSs from that time did not support the boot options of modern machines.  I have a 2001-2002  notebook and it's pretty finicky.  On my machine,  forget booting from a USB device (with USB 1.0 or 1.1 probably just as well) , even DVD-Rs can be hit & miss. CD-Rs seem fairly reliable.  I've never used PLOP so no experience there.  I do seem to recall that PLOP can boot from a floppy.  I wonder if you'd have better luck with a floppy than with a CD?

---

### Post by mörgæs on 2013-11-13
Agree with Kurt's post, but I would recommend Lubuntu 13.10 from a CD. 
Single-use CD's are often more reliable than reusable ones.

---

### Post by grahammechanical on 2013-11-13
I found on my BIOS that changing the setting from Legacy floppy drive to USB then gave me more options under the Boot section of the BIOS. In fact opening the BIOS with the USB stick in the port saw it reported as a USB hard drive and I could set a boot priority for it. It is worth a try checking if there are other options available in the BIOS.

---

