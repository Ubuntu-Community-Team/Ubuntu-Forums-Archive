---
title: "boot from a partion like a cd"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by freemanen on 2006-07-31
I have a partion on hda6 that is a copy of a cd,(dd if=edgy-desktop-i386.iso of=/dev/hda6) but how do i boot from it in. that should i write in grub?

---

### Post by OpsVentus on 2006-07-31
I think it should be:
grub> rootnoverify (hd0,5)
grub> makeactive
grub> chainloader +1
grub> boot

Maybe leave out the "grub> makeactive".

Cheers,
Bart.

---

