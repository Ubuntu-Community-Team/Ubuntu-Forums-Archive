---
title: "Installation stops at 23%"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by Skoopman on 2010-10-15
Hey guys, I am running Ubuntu 10.04 without problems via Wubi. Told a friend of mine about it, but his installation stops after the boot in Ubuntu at 23%. I think the installations freezes, because he can't move the mouse.

It looks like [this](http://s1.directupload.net/file/d/2313/5ibf5lgm_jpg.htm)

His PC:

CPU #0 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+, 2210 MHz
2 GB RAM
Geforce 8800gts

He tried both the amd 64 bit ubuntu iso and the normal 32 bit, both stopped at 23%. Any suggestions?

---

### Post by bcbc on 2010-10-15
> **Skoopman said:**
> Hey guys, I am running Ubuntu 10.04 without problems via Wubi. Told a friend of mine about it, but his installation stops after the boot in Ubuntu at 23%. I think the installations freezes, because he can't move the mouse.

It looks like [this](http://s1.directupload.net/file/d/2313/5ibf5lgm_jpg.htm)

His PC:

CPU #0 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+, 2210 MHz
2 GB RAM
Geforce 8800gts

He tried both the amd 64 bit ubuntu iso and the normal 32 bit, both stopped at 23%. Any suggestions?
First get it booting from a live CD (boot from the Ubuntu cd and select "try without installing"). It's quicker to figure out what the problem is (and workaround) if you're not installing each time. In general with nvidia I'd try adding 'nomodeset' to the boot options. You can do this on both a live CD and a wubi install (slightly different method).

---

