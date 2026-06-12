---
title: "Ubuntu Karmic 2.6.31-15 Upgrade Failed"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by izz.y on 2009-11-27
A few days ago, I upgraded via update manager to 2.6.31-15, and all seemed to go well until I restarted my computer. Ubuntu 9.10 is my only OS on this computer, and it would load the new kernel, and go straight to a flashing command line. After a lot of hassle, I was able to boot into 2.6.31-14, and edit grub2, so it will boot 2.6.31-14 by default, and I deleted all 2.6.31-15 files in /boot. I do not want to try upgrading again, but I would like to replace all the packages(I know they have the headers, firmware, and a few other packages that are installed with the kernel when you upgrade) for 2.6.31-15 to the correct ones for 2.6.31-14.

---

### Post by lidex on 2009-11-27
> and I deleted all 2.6.31-15 files in /boot
Not a good idea. Use synaptic. Type "linux-" (with the dash - minus the quotes) in the search box and mark all the packages relating to that kernel for removal. Apply. The prior kernels are still intact and you can choose the default boot option in system>administration>startup manager.

---

