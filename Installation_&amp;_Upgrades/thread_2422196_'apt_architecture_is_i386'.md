---
title: "'apt architecture is i386'"
date: 2019-07-03
forum: Installation &amp; Upgrades
---

### Post by nautiman on 2019-07-03
Computer is Lenovo B560 with i3 processor, i686 architecture, op-modes 32 and 64bit.  I want to run fully 64bit 19.04 system,  but it will not load 18.10 , giving message 'apt architecture is i386'. 

How do I get around this ?

---

### Post by CatKiller on 2019-07-03
If you've initially installed from a 32-bit image, as both i386 and i686 are, then you can't change that to 64-bit in-place nor as an upgrade. You'd need to install from a fresh AMD64 image.

---

