---
title: "install on G4 ppc, hangs when copying files"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by verdandi on 2006-10-10
hi,

I'm new to ubuntu (prospective fedora/OS X convert), and thoroughly impressed. so far. I tried to install dapper drake from livecd (is there any other way?) onto a Mac G4 with 512MB ram and an 80 GB hard drive. It boots, the install utility starts, formats the drives, starts copying files, and at 47% of the way, it slows down ... waits a few minutes ... then tells me instead of 3:37 left in the install, there is anywhere from 3038:24 left to 4892:39 left in the install, and then the machine hangs.

I thought it might have been a RAM issue, so I connected a USB drive and added an additional swap partition of about 200MB (dd'd a file with bs=1M and count=200, then sudo mkswap and sudo swapon), and there is completely no change in behavior. I figured that if it was a RAM issue, even if 200M wasn't enough, it might still at least get a little farther, but no dice.

Any ideas? :-k ](*,) 

Thanks so much,

Fred

---

### Post by verdandi on 2006-10-10
btw, will d/l and try the server edition and the alternate install, but in the meantime, any ideas?

thx,
F

---

### Post by linear on 2006-10-11
Alternate install disk may be the solution. If that fails, try a Breezy install. If Breezy installs, dist-upgrade to Dapper.

---

