---
title: "Boot USB from internal HD?"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by arron on 2006-12-15
Ok i have followed the USB drive install, and it works very well on my laptop.  I can get it to boot from the usb with no problem, but every time i want to i have to go threw the bios and set it to boot from the usb, each and every time i want to boot linux.

I have another ubuntu version on the laptop hard drive (i want to remove it, and get back the space for windows, because the usb drive works very well as a os i can secure form the kids and have stuff for dads eyes only :cool: ).

On the usb drive, grub boots well using either /dev/sda1, or the root=device name and serial number in case sd* changes.  I have trid to add the same entries to the grub menu on the internal hard drive, and it gives me a error.

How can i add the usb drive to the grub boot menu on the internal hard drive so it would work with usb drive in and wouldnt matter if not.  

Then with that working, what is my best option to remove the ubuntu install on the hard drive, and how would i resize the ntfs partition to get back the room?  (200 gig usb drive gives me many more options than stealing 20 gigs of the laptop drive).

Thanks

Arron :mrgreen:

---

### Post by Wall86 on 2006-12-15
don't know about your ubuntu problem, but if ya want to recover that un used partition in windows go start>control panel>administrative tools>computer management>disk management then locate the partition, then just reformat it in like ntfs or fat 32, u decide :)

---

