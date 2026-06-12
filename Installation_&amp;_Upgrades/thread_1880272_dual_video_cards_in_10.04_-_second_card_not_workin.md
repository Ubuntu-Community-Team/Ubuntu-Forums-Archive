---
title: "dual video cards in 10.04 - second card not working"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by v_dragon on 2011-11-13
I have a dual card setup that worked fine in 9.10. One is an Nvidia 9800gtx, the other an 8800gts. Either a fresh install or an upgrade from 9.10 the second card is not working. I have tried the current nvidia drivers, the older 173 drivers and ones installed from nivida's site (256 i think).

i can see this in the Xorg.0.log

(EE) Nov 13 03:54:31 NVIDIA(1): Failed to initialize the NVIDIA graphics device PCI:3:0:0. 
(EE) Nov 13 03:54:31 NVIDIA(1):     Please check your system's kernel log for additional error
(EE) Nov 13 03:54:31 NVIDIA(1):     messages and refer to Chapter 8: Common Problems in the
(EE) Nov 13 03:54:31 NVIDIA(1):     README for additional information.
(EE) Nov 13 03:54:31 NVIDIA(1): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) Nov 13 03:54:31 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(EE) Nov 13 03:54:31 NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device PCI:3:0:0. 
(EE) Nov 13 03:54:31 NVIDIA(GPU-1):     Please check your system's kernel log for additional error
(EE) Nov 13 03:54:31 NVIDIA(GPU-1):     messages and refer to Chapter 8: Common Problems in the
(EE) Nov 13 03:54:31 NVIDIA(GPU-1):     README for additional information.
(EE) Nov 13 03:54:31 NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device!


The card shows up in lspci...
been trying for days to get my workstation running right again, frustrated ><:

---

### Post by v_dragon on 2011-11-14
Okay so if i add vmalloc=256M to the end of a relevant line in /boot/grub/menu.lst it works...or do a temporary edit...but...

how do i set grub defaults?
/etc/default/grub is a blank file, i added grub_cmdline_linux="vmalloc=256M" then did a update-grub but nothing changed.

Also i upgraded to 10.10

---

