---
title: "Kernel upgrade 2.6.20.15 to 2.6.20.16 borked my SATA drive.  How do I get it back??"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by skyshock21 on 2007-06-03
After I restarted and booted w/ the new kernel, my PATA drive (os stuff is on) came up fine.  However, the SATA drive was missing.  I checked /dev/ and sure enough there are no sd[abc, etc...] drives to be found anywhere. 

Where did my SATA drive go????

---

### Post by neymac on 2007-06-03
There is a bug in the last kernel update (2.6.20-16). You have to wait until they fix it.
See the thread [http://ubuntuforums.org/showthread.php?t=456662&highlight=hde&page=48](http://ubuntuforums.org/showthread.php?t=456662&highlight=hde&page=48)
I had some issues with this update too, but my system still works.
The best solution is to use the previous kernel (2.6.20-15) until the fix arrive.

---

### Post by skyshock21 on 2007-06-03
Greeeeeat.  Why did Canonical include it in the repos then if it hadn't been fully tested???  Seems like having SATA drive functionality should be mandatory?  But what do I know.... :(

Back to 2.6.20-15.  Works like a charm.

---

