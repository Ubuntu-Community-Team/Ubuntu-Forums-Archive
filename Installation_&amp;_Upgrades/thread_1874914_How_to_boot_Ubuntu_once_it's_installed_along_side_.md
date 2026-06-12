---
title: "How to boot Ubuntu once it's installed along side Windows 7?"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by White Canary on 2011-11-04
I installed Ubuntu 11.10 on a separate partition on my laptop, but when I turn it on, I never see an option to choose between Windows 7 or Ubuntu- it simply loads up Windows 7. I didn't have this problem when I had last installed 9.10, so I'm curious to know what the problem is now, and how I could fix it. Any help would be appreciated, thank you!

---

### Post by pavi_elex on 2011-11-04
Try to install ubuntu with WUBI.It will give select option before booting.

---

### Post by Hedgehog1 on 2011-11-04
Please follow this link below to generate a RESULTS.txt file - the contents of the text file will tell us about your current installion:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

After downloading and running the boot info script by following the instructions in the link, please post the contents of the RESULTS.txt file between [noparse]```
 and [/noparse]
``` tags in your next post.

Once we can see your current install situation, we can the better advise you.

***The Hedge***

:KS

---

### Post by Jack Brown on 2011-11-04
grub bootloader.

might have gotten installed somewhere else.

or an incomplete install.  good thing your laptop still boots up.

edit: make sure you install ubuntu AFTER windows.

---

### Post by Mark Phelps on 2011-11-04
Messing around with partitions to fix dual-boot problems runs the risk of corrupting the Win7 OS filesystem, rendering it unbootable.  So, before that happens, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

