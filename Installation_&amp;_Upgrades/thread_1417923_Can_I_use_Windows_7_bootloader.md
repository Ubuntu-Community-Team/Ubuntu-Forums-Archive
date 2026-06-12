---
title: "Can I use Windows 7 bootloader?"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by ferrazrafael on 2010-02-27
Im having problems with grub in my laptop.. after same reboots, grub gives a "Cannot find Symbol ""  error" making it useless.

There is a way to configure windows 7 bootloader to boot ubuntu instead of grub..?

thanks guys..

---

### Post by Mark Phelps on 2010-02-28
> **ferrazrafael said:**
> ... There is a way to configure windows 7 bootloader to boot ubuntu instead of grub..?
Not directly.

... However ...

The NeoSmart Technology forums provide a free product known as EasyBCD that will install GRUB4DOS and thus allow you to configure the Win7 Loader to allow you to select Ubuntu from the Windows OS menu ... but it's still using a form of GRUB.

From personal experience, it's a lot easier to install GRUB2 and use IT to do multi-OS booting than to use easyBCD.

---

### Post by ferrazrafael on 2010-02-28
how wubi does manage this?

ubuntu 9.10 doesnt use grub2?

because its dificult to randomly lost all operating systems.. I need this laptop to work

thanks

---

