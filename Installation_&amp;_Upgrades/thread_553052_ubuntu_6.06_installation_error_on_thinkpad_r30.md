---
title: "ubuntu 6.06 installation error on thinkpad r30"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by karsten johansen on 2007-09-17
How do i fix an installation on all my IBM R30  there is an IRQ 15 error, i'm a novice in ubuntu so maybe there is another new  distro arund which can help me?

---

### Post by dixonp on 2007-09-17
If you can, try a more recent version of Ubuntu (6.10, 7.04). Paste the complete error message. "IRQ 15 error" is too vague.

---

### Post by oilchangeguy on 2007-09-17
> **karsten johansen said:**
> How do i fix an installation on all my IBM R30  there is an IRQ 15 error, i'm a novice in ubuntu so maybe there is another new  distro arund which can help me?

this is a bios error. not an os error. irq means, interrupt request. each piece of hardware in the computer is assigned an irq. some hardware can be assigned the same number, this is fine as long as they are not trying to work at the same time. enter the bios, locate your irq list, make sure it's set to auto.

---

