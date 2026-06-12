---
title: "Installing on Intel Quad Core Xeon 53xx"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by hauge on 2007-10-12
The kernel on the x64 distros for 6.10 and 7.04 (+7.10 beta) does not support the Quad core Xeon (possibly also problems with Dual core 50xx/51xx but not tested). You will encounter problems with an unexpected CPU state (CPU's being offline) and the system freezes (reset necessary).

In order to install you have to:
[LIST=1]
[*]Switch off the the multicore functionality in the bios
[*]Install the os
[*]Make and install a new kernel when the system has been installed that supports the Xeon
[*]Turn on the multicore functionality in bios again and boot the system
[/LIST]

/Jan

---

