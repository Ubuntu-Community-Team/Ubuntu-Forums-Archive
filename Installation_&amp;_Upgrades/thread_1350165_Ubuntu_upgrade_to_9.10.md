---
title: "Ubuntu upgrade to 9.10"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by ymf on 2009-12-09
Hi,

I have recently upgraded to ubuntu 9.10. Also, I've got grub bootloader 1.5 which displays ubuntu 9.04 (although I have upgraded to 9.10) and windows vista.

After logging in as the administrator the screen goes blank and random coloured spots light up on the screen. Is there anything I should adjust on my system?

Any help would be appreciated,

Thanks :)

---

### Post by lemming465 on 2009-12-12
Garbage video in this situation typically means that there are regression bugs in either the kernel or Xorg drivers for your video chip.  Re-installing with the previous version (there is no easy downgrade) is often your best option.\

I like to test with live CD's before doing upgrades to help avoid this scenario.

---

