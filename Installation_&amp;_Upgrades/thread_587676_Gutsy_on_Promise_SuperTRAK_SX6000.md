---
title: "Gutsy on Promise SuperTRAK SX6000"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by leptogenesis on 2007-10-22
The install moves normally until I get to the 'detecting discs' phase.  Then it tells me it can't detect any hard discs.  

Does anyone know how to get the install to work?  Does anyone know what the drivers are or how to make ubuntu recognize them? (I can use a floppy drive, CD/DVD drive, or a USB drive to make the drivers available to ubuntu, if anyone can explain how...)

---

### Post by buyerninety on 2007-10-23
maybe this help??

[http://www.linuxquestions.org/questions/linux-hardware-18/fedora-core-7-directly-on-to-supertrak-sx6000-raid-577581/](http://www.linuxquestions.org/questions/linux-hardware-18/fedora-core-7-directly-on-to-supertrak-sx6000-raid-577581/) -->

---

### Post by leptogenesis on 2007-10-25
Finally figured out what it was.  The i2o drivers do indeed work--and they are included in ubuntu--it's just that our raid card (in its own BIOS) was set to be compatible only with Windows NT.  Changing the compatibility setting to 'Other OS' worked perfectly.  

Thanks for the help.

---

