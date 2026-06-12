---
title: "Live CD: Error messages. Please Help."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Master_Z on 2007-10-19
Okay. I rebooted with the CD being in my drive and the Ubuntu logo appeared and asked me what to do. I selected "start or install ubuntu". It began loading, and soon my screen filled with various errors, a few main ones being:

-buffer i/o error on device hdb
-hdb:error code 0x70 sense_key:0x03
-sb_bread failed reading block
-FAIL

I have no clue what this means. I used Feisty to burn the ISO image to the CD-RW (does it need to be a CD-R instead?) at 4.7x speed. My PC specs are below.


Specs:
-Intel Pentium Dual Core @ 1.6ghz (laptop)
-1.5gb of ram
-Dual Boot w/Vista and Feisty
-ATI Radeon Xpess 200m video card.

---

### Post by Master_Z on 2007-10-20
Bump.

---

### Post by Jermski on 2007-10-20
It looks like a problem reading one of your drives ... 

Although 1/2 the times I have had problems with booting a live CD on a laptop have been related to the acpi. Try the "noacpi" boot option to see what happens.

---

### Post by Jermski on 2007-10-20
Also, you might try using boot option "irqpoll"

If niether of those work - try reburning the live CD at 2x. There may be a problem reading that CD.

---

