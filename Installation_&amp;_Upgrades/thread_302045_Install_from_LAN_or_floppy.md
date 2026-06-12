---
title: "Install from LAN or floppy?"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by Genericus on 2006-11-18
I'm trying to install on a Dell smartstep 200n laptop and BIOS won't boot to the CD, but I can read from it in dos/Win.](*,) 

Is there a way I can get the installation started via boot floppy or (cringe) LAN boot??

---

### Post by K.Mandla on 2006-11-18
Yes! I've done this a half-dozen times and it works like a champ.

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Essentially you're booting to a floppy that allows you to pick the boot device, and passes the boot sequence to it. I've used it on Pentium machines that wouldn't boot from CD via the BIOS settings, and it's a godsend.

Let me know if you run into difficulties. Building the boot floppy is confusing for some people. Cheers!

---

### Post by Genericus on 2006-11-18
> **K.Mandla said:**
> Yes! I've done this a half-dozen times and it works like a champ.

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Essentially you're booting to a floppy that allows you to pick the boot device, and passes the boot sequence to it. I've used it on Pentium machines that wouldn't boot from CD via the BIOS settings, and it's a godsend.

Let me know if you run into difficulties. Building the boot floppy is confusing for some people. Cheers!

Worked like a charm but a bit out of date for win users....

rawwrite on win isn't commandline at least not from the link provided, and the image file name doesn't match the  command line params listed. I had to dbl click and browse "All files" to the image.   But still, Thanks!

---

### Post by K.Mandla on 2006-11-19
True, those instructions are slightly off the mark. Still, glad it worked. I keep one of those disks around as a backup plan, or in case I find an oldy moldy to play with. ;)

---

