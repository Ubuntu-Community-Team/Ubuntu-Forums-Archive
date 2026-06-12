---
title: "Kernel upgrade causing problems?"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by all13d on 2007-03-30
I installed Ubuntu this morning.  It worked fine until I opted to install the new kernel update.

When attempting to boot the new kernel normally, it hangs about 3 seconds in while running a script.  In rescue mode, it attempts to load drivers for "usbcore" and then hangs.

Kernel *.10 still works, but in recovery mode only.  Is there any method to uninstall a kernel update?

---

### Post by zvacet on 2007-04-01
In synaptic find linux image.Delete one with higher number and that will leaves you with older kernel.

---

