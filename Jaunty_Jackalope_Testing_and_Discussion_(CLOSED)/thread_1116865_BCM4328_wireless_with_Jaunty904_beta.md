---
title: "BCM4328 wireless with Jaunty904 beta"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pxwpxw on 2009-04-05
I find the only way I can get wireless up for the BCM4328 802.11a/b/g/n on iMac81 with ubuntu904beta is to update-initramfs after removing the ssb.ko module from /lib/modules/. Blacklist wont do it, ssb keeps loading.

I am using the Broadcom STA driver from the System/Hardware-drivers.
The same applies on MBP41 and for 904beta x86 or x86_64, or for the separate package from Broadcom STA (compiled).

---

