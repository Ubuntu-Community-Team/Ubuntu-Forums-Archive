---
title: "instaling ubunto after 2 win xp installations - grub error"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by slingman on 2006-09-07
i have 2 win xp installs (1 clean one on c: i use rarely, & another on d: which is my working drive  (2 partition master) - i have 3 other hard drives on a raid card and a small 20gig as a secondary master that has about 6gb of data

i used the bootable cd to load ubuntu and then install

i used the 20gb drive as the base and used the simple sugestions rather than any manual configurations so that it created a 10gb partition and installed ubuntu on that - everything went fine until i rebooted and i got the grub error 22  - did a google and did the xp recovery console, fixmbr and i got my win xp boot menu back

i really want to try ubuntu but dont want to spend another hour, reinstalling ubuntu only to have an error 22 and have to go back to the xp recovery console

are there any pointers on the installation that will avoid this ?

thanks

---

### Post by HeLiS on 2006-09-13
Your not the only one with this problem. maybe if ubuntu actually allowed us to change to using LILO we could avoid this problem.

---

### Post by confused57 on 2006-09-13
> **HeLiS said:**
> Your not the only one with this problem. maybe if ubuntu actually allowed us to change to using LILO we could avoid this problem.

You can use Lilo:
[http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal](http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal)

---

### Post by K.Mandla on 2006-09-14
LILO is also an option on the alternate/install CD. If you escape out of the install process at any time (or choose the expert install option ... if I recall correctly), you can select LILO over Grub.

LILO also becomes the default if you pick a boot partition with a non-Grub-friendly file system (like xfs).

---

