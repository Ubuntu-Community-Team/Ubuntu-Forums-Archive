---
title: "Run from USB failures"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by StuartN on 2010-03-25
I just tried booting from a 10.04 USB drive created with 9.10 and came across some bijou bugets:

1) Having booted from the USB drive, it was not possible to burn a CD from the ISO image because Brasero wants to eject the blank CD; earlier distributions will burn the ISO;

2) The Broadcom wireless driver is on the CD and on the USB, but the USB can not be selected as a software source and the CD can not be burned;

3) Booting from the Live CD allows selection of the hardware driver, but it is not possible to enable wireless access. B43 fails to install and wl/STA requires a reboot.

In 9.04 it was straightforward to select a proprietary hardware driver (B43 or wl/STA) and commence wireless access with the Live CD, but all later distributions fail to enable the wireless card. In 9.10 it was necessary to reboot (i.e. also necessary to install) to use the wireless card. In 10.04 it is not yet possible to install the driver, even when booting from the Live CD.

---

