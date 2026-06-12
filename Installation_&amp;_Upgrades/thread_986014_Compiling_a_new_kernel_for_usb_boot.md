---
title: "Compiling a new kernel for usb boot"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by haal on 2008-11-18
Hi, i just installed ubuntu 8.10 into my usb stick, but i need a different kernel version so after compiling a new kernel from scratch, i copied the new vmlinuz and modified initrd.gz with the new modules.
But after loading vmlinuz and initrd.gz from the usb stick, it just drops to a busybox shell, i don't remember the exact error but it seems it cannot access sda.
Which parameters do i need to compile into the new kernel to boot from the usb stick, apart from the obvisous usb_storage and squashfs?

---

