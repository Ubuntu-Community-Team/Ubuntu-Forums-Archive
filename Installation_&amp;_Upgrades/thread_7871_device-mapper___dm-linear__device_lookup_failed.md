---
title: "device-mapper : : dm-linear : device lookup failed"
date: 2004-12-12
forum: Installation &amp; Upgrades
---

### Post by taygan on 2004-12-12
Currentlky running 2.6.8.1, I'm trying to downgrade to 2.6.7 in warty.  When I reinstall 2.6.7 I get a series of 'device-mapper : : dm-linear : device lookup failed' on boot, then I get the terminal and a blue screen of 'cannot start x server' I'm using a nvidia5200 card.

Do I need to reinstall the restricted modules from 2.6.7 and if so, where are they?  I also tried kernel 2.6.9 and get the same errors (yes, I know the nvidia support isn't 100% with 2.6.9 yet)

I'm using a SATA drive, a google search leads me to believe something isn't mapping right with the SATA drive, but I can't figure out what to do with it.  Chipset is VIA VT8237 Southbridge on an ASUS A7V600-X motherboard.

what's going on?

---

### Post by jdong on 2004-12-12
dm-linear is some kind of kernel patch in Ubuntu's default kernel -- has something to do with RAID...


That's not the cause of your video issues -- you have to install NVidia's 3d Linux drivers, from their website.

---

### Post by jdong on 2004-12-12
and why are you trying to downgrade to 2.6.7? It has a known IPTables vulnerability.

---

### Post by taygan on 2004-12-12
Hmmm, yep it is a RAID issue in the kernel, although I'm not using RAID, I am using a SATA drive..  2.6.9 and 2.6.8 work so I'll *assume* that the device-mapper issue is RAID support in 2.6.7 and earlier kernels.

The more pertinent question is are nvidia modules backwards compatible?  DO 2.6.8.1 drivers work with 2.6.7?

And more importantly do the 2.6.9 modules work with 2.6.8.1?

---

