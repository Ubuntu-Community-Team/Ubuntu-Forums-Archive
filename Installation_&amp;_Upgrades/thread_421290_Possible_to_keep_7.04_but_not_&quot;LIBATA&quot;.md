---
title: "Possible to keep 7.04 but not &quot;LIBATA&quot;"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by jhaefner on 2007-04-24
I was one of the lucky ones: my ISO did a clean install from Edgy without too many hitches, AND I can boot from the resulting system (including to WinXP).  My problem (and that of many others) is that the kernel 2.6.20 is flawed especially concerning the use of "ibata" in place of the earlier "ide-generic" and related modules so that my CDROM and ZIP drives are not recognized.  I don't mind if linux thinks my EIDE drives are SCSI, but I would like to use my external drives.

My question is: does anyone have a recipe or link showing how to force 2.6.20 to use the earlier ide modules, or have too many other changes been made for this to work?  Simply putting the appropriate module names in /etc/modules does not do it.

Thanks.
Jim H.

---

