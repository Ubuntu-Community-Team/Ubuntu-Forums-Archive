---
title: "manual compiling of alsa drivers"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by icegood on 2012-12-01
Have next issues:
1) fw_device_get and fw_device_put are not valid in headers anymore. Where they should be spotted?
2) alsa-kernel/pci/asihpi/hpios.h:33:24: fatal error: asm/system.h: No such file or directory

Via apt-file found that they was in previous linux headers:
linux-headers-3.5.0-17: /usr/src/linux-headers-3.5.0-17/arch/arm/include/asm/system.h
linux-headers-3.5.0-18: /usr/src/linux-headers-3.5.0-18/arch/arm/include/asm/system.h

but not in my current linux-headers-3.5.0-19. Is it bug?

---

### Post by dino99 on 2012-12-01
i have it with the 3.7.0-4 kernel (ubuntu RR i386)
so you might have it too on your system if the kernel is well installed ( 2 headers + 1 or 2 images in case of big image splitted in 2 (with extra)

---

