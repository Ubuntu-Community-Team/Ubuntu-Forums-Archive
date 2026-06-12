---
title: "Installing to external HDD?"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by mdipi on 2005-05-23
Hey all, I want to install Ubuntu onto my external HDD with a 40 gig parition for it, but I'm not sure how i go about selecting this drive to install to?

Any help would be great!

Thanks-
-Mike

---

### Post by gerrit74 on 2005-05-24
Hello,

First of all you need to know if your computer supports usb start up. 
Know your bios.
Disable the first ide port in bios if there's an internal hard disk on that port.
Boot order should be cd-rom(on the second ide drive),hard disk drive. Install ubuntu.
Ready? Change the boot order in usb hard drive+cd rom.
If you want to boot up the internal hard drive change the boot order again. Enable it first.

---

