---
title: "dist-upgrade hosed eth0"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by jimmyj on 2006-06-08
I updated my repos and ran sudo apt-get dist-upgrade. Upon rebooting my mouse wheel stopped working, but more importantly there was no internet device.

lspci returns the onboard chipset perfectly, it just isn't being loaded.  I don't really know where to start looking to solve this problem. I rebooted into the 2.6.12-9 kernel and everything loaded up fine, so I think it may have something to do with the kernel modules included in the update of the newer kernel. This is pretty far beyond my limited knowledge of linux and any help getting started fixing it would be appreciated.

---

### Post by jimmyj on 2006-06-08
I got it. It had to do with GRUB not running the new kernel.

---

