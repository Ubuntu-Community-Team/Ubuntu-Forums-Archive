---
title: "USB Startup failure"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by StuartN on 2010-04-14
I created an Ubuntu 10.04 Beta 2 USB Startup Disk

The link /vmlinuz points to a missing file boot/vmlinuz-2.6.32-19-generic which is not installed when the USB Startup Disk is created.

The absence of this file prevents some updates and package installations from completing. **sudo cp /boot/vmlinuz-2.6.32-20-generic /boot/vmlinuz-2.6.32-19-generic** will generate an error on the next reboot, but Ubuntu 10.04 appears to boot correctly afterwards.

(There are a lot of Launchpad bug reports having in common something like *"update-initramfs: deferring update (trigger activated) lzma: Encoder error: -2147467259"* which simply means that there was insufficient space on the device)

---

