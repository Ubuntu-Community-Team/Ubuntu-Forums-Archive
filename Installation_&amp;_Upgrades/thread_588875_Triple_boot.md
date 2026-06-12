---
title: "Triple boot?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by andhar on 2007-10-23
I was thinking about about booting 3 OSs (ubuntu, FreeBSD, XP 32bit) on one of my rigs, now the question I have is if i partition a 500gb hd 3 ways and formart each partition using the installers would a tripple boot in grub be possible if i installed ubuntu last?

---

### Post by Pumalite on 2007-10-23
No problem. XP first, FreeBSD 2nd, Ubuntu last. You'll have a Grub to boot any of the three OS's.

---

### Post by andhar on 2007-10-23
so as long as I manually make all the Partitions and tell the installers which to use I should be ok?  Am I going to have to manually edit grub or should it pick up that there are 2 other OSs installed?

---

### Post by rsambuca on 2007-10-23
Yes, the manual partitioning to direct each OS where to install is best.  I don't know about the BSD, but the Ubuntu grub should detect XP.

---

### Post by andhar on 2007-10-23
thankyou guys. I will post my progress when I do it tomorrow night.

---

### Post by Pumalite on 2007-10-23
You are welcome. Good luck.

---

### Post by jinx099 on 2007-10-24
Ubuntu will find XP, but will not find FreeBSD.  Just chainload FreeBSD the same way Ubuntu does it for Windows and it should work fine.

---

