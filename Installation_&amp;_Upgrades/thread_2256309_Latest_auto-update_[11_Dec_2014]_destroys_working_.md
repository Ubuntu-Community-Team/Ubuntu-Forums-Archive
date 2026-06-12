---
title: "Latest auto-update [11 Dec 2014] destroys working nouveau configuration"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by NHclimber on 2014-12-11
This morning's auto update installed nvidia-331-updates _and_ switches the configuration from nouveau to nvidia, even though I don't run the binary driver.

Plus, since I run custom kernels, dkms failed to even build the kernel driver, but yet the install blithely continues on anyway, leaving a broken boot.
Had to restore xorg.conf from backup.

---

