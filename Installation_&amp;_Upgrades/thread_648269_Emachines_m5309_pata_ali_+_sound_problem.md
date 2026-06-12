---
title: "Emachines m5309 pata_ali + sound problem"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by dhaupin on 2007-12-23
Hey all, a friend of mine is just starting to get into linux.  Unfortunately most distros aren't taking kindly to his machine.  I know Emachines are junk, but this is surprisingly junki-er.  It seems there is a problem with the pata_ali module, or the hardware itself.  I am able to load up and install opensuse using the brokenmodules=pata_ali, but I really wanna put a debian derivative on there.  Ubuntu freezes at hardware detection.  How do I tell grub/ubuntu to not load this module at boot?

This would probably fix the sound card issue too (the onboard is broken, forcing us to use a usb style one) if i can figure out how to not load the modules from grub.

---

