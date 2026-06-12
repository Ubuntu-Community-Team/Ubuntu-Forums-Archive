---
title: "Installer can't find CD it booted from in the DVD drive"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by tomwhipple on 2006-10-10
I am having a problem where I can boot the install CD (6.06.1 alternate AMD64), but when the installer goes to read from it for the install data, it asks me to give the /dev location for the CDROM. 

I have looked in /dev and cannot find anything that makes sense.

System:
CPU - Intel Core2 Duo 6600
Mainboard - Intel DP965LT 
DVD/CD drive - IDE Sony DVD-RW
Hard disks are SATA

Thanks!

---

### Post by Kateikyoushi on 2006-10-10
Maybe because of the chipset ?
I saw similar problems on other forums.
You could try network install or the edgy beta, maybe that supports that mainboard.

---

### Post by tomwhipple on 2006-10-11
This is a problem with the 6.10 beta image also.

According to [http://kerneltrap.org/node/7020](http://kerneltrap.org/node/7020), you are right and it is a chipset issue which is addressed in kernel 2.6.18.

So, the trick would seem to be finding an install image with a current enough kernel ...

---

### Post by tomwhipple on 2006-12-17
UPDATE: I have had a running system for a while now, (currently running kernel 2.6.19.1) but still no luck with the CD/DVD drive.

Any one discover a solution?

---

