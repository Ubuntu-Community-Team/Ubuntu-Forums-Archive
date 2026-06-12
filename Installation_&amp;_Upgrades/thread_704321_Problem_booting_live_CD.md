---
title: "Problem booting live CD"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by mightypeo on 2008-02-22
I'm trying to boot the 7.10 live CD (32 or 64 bit). Very quickly after the boot, there's a kernel panic message and a reboot. Unfortunately this is a very fast motherboard and there's no way to stop it, so it's almost impossible to read the message

This is on a ASUS P5K-V motherboard with an Intel Q6600 QuadCore (2.40 GHZ). The motherboard has an Intel G33 chipset.

Any ideas on how I can capture that message ? I tried verbose and other switches (noapm, noacpi) but that doesn't seem to make a difference

---

### Post by Pumalite on 2008-02-22
If you want to install, try the Alternate CD.

---

### Post by mightypeo on 2008-02-22
Pumalite

Thanks I will try that, in the mean time, is there a way to stop the display and keep the machine from rebooting (a single step mode maybe) ?

---

### Post by Pumalite on 2008-02-22
I would do 2 things:
1.-Check for hardware incompatibilities in the Ubuntu site
2.-Do md5sum on iso, burn at 4x as image in good quality CD-R media and check for CD integrity before install.

---

### Post by mightypeo on 2008-02-22
some more information.

if I specify nosmp, I get to ash...

---

### Post by mightypeo on 2008-02-22
more information, with nosmp and acpi=off I was able to boot the 7.10 64 bit Live CD.

Does this then mean, that one of the cores of my CPU is bad ?

---

