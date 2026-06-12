---
title: "Ubuntu not recognizing my disk / controller"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by thoughts on 2006-11-01
I was running Edgy on a Tyan motherboard with a VIA chipset.  I just upgraded to a new motherboard, an Intel DG965WH.  This new board has 6 SATA ports but I'm only using the single IDE port because my HD and CDROM are IDE.

When I start the system, it boots fine, but on the Ubuntu splash screen, the progress bar never moves.  After a few minutes it dumps me to a text console with a message that /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx does not exist.  The console has a watered-down shell prompt and I can run an ls on the /dev directory; it has no "disk" subdirectory at all.

I'm thinking this means that Ubuntu does not support the IDE controller on my motherboard?  If so, what are my options?  Can I tell Ubuntu to use some kind of generic driver for the disk controller?

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

