---
title: "Boot options to tame video drivers"
date: 2005-11-21
forum: Installation &amp; Upgrades
---

### Post by Frank-Hamersley on 2005-11-21
Nubi to Breezy - looking to install on a SiS760GX chipset - Gnome is fine but the character mode driver gets way confused on the way there.

It shows some chars but is out of shape (wierd panels splashed around) and doesn't look like it can find a simple VGA mode to get started on.

Are there any initial boot time options to force a real simple driver to load or coach the hardware scan to make it more useful?

Cheers, F.

---

### Post by Frank-Hamersley on 2005-11-21
Woot - I seem to have found the answer in the Hardware support section....

To boot the Live CD cleanly ...

   boot: live debian-installer/framebuffer=false

I presume to install the OS it will be something like ....

   boot: linux debian-installer/framebuffer=false

Breezy now works nicely on the Acer 3002WLC (uses SiS M760GX or 760GX ? chipset).

Will let y'all know when its bedded it.  Cheers F.

---

