---
title: "Error 18"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by xtrabyte on 2005-10-01
Hi
I had sucess on my P4 3.2 works perfect.  I am trying to install on an old AMD 1000 mhz. I get this error after booting, after doing an install of hoary 5.04 
"Grub loading stage 1.5
Grub loading, please wait
Error 18"
By the way Breezy 5.1 would not work past the install package stage, so I tried 5.04
Any comments welcome

---

### Post by xtrabyte on 2005-10-01
Hi
I did a search of the forums (I should have done this first!!) and found the following:
[COLOR="Blue"]Error 18: Selected cylinder exceeds max supported by BIOS
Solution
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).
Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range).[/COLOR]

My new HDD is too big for the BIOS in this old PC to handle.

---

