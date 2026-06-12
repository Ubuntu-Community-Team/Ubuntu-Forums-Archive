---
title: "How do I change video cards without reinstalling?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by aeh on 2009-11-25
I have a system running Ubuntu 9.10 as well as U studio 9.10. My motherboard Asrock p4i65gv has a built in video adapter which is pretty crappy. I also have a separate video adapter that I'd like to install instead. How do I configure Ubuntu for this?  TIA

Alex

---

### Post by TenPlus1 on 2009-11-25
Install and enable the new graphics adaptor in the bios and boot into Ubuntu...  The kernel should automatically detect the driver needed for the new card otherwise it will use vesa/vga standard modes...  If this is the case then running Hardware Drivers will detect the propriatory driver and install it for you (nvidia/ati)...

---

### Post by aeh on 2009-11-26
Well I have tried that, I get past GRUB, then lots of text scrolling on the screen, then an error message....  I certainly cannot boot into Ubuntu

---

