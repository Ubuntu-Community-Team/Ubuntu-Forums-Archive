---
title: "Problem with Intel 965 mainboard"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by rleon on 2006-12-18
Hi, 
Live CD's do not work with my DG965ss mainboard and I cannot install Ubuntu on my HD. I think that this is because as Linux loads drivers and PATA is not supported by Intel 965 chipset, my DVD drive is not found. Now, if I used an SATA to IDE adapter between one SATA interface on the board and the drive, would Edgy boot?

---

### Post by pay on 2006-12-18
I think that you need kernel 2.6.18 or newer for that chipset. 6.10 is 2.6.17.

---

### Post by Sef on 2006-12-18
> I think that you need kernel 2.6.18

That is correct.  Read this on[ KernelTrap]("http://kerneltrap.org/node/7020").

---

