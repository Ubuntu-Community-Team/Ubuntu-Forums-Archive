---
title: "nvidia-glx update breaks VMware big-time"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by shirsch on 2007-03-05
BIG FAT WARNING:

After updating with nvidia-glx_1.0.8776+2.6.17.7-11.2, VMware workstation goes down with a core dump 100% of the time.  Problem occurs at or during graphics initialization.

Reverted nvidia-glx, linux-restricted-modules and linux-kernel-devel to 2.6.17.7-11.1 and all is well again.

Surprised that no one else is seeing this.

---

