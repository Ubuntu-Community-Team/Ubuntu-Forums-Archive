---
title: "Kernel update to 5.11.0-2019 has killed hdmi output (Hirsuite Raspberry Pi 4)"
date: 2021-10-08
forum: Installation &amp; Upgrades
---

### Post by rogerjames99 on 2021-10-08
This is a workaround for the problem mentioned in the title.

First of all check what is installed.

```
roger@brubeck:~$ dpkg -l | grep linux-image
rc linux-image-5.11.0-1007-raspi 5.11.0-1007.7 arm64 Linux kernel image for version 5.11.0 on ARMv8 SMP
rc linux-image-5.11.0-1009-raspi 5.11.0-1009.10 arm64 Linux kernel image for version 5.11.0 on ARMv8 SMP
rc linux-image-5.11.0-1012-raspi 5.11.0-1012.13 arm64 Linux kernel image for version 5.11.0 on ARMv8 SMP
rc linux-image-5.11.0-1015-raspi 5.11.0-1015.16 arm64 Linux kernel image for version 5.11.0 on ARMv8 SMP
rc linux-image-5.11.0-1016-raspi 5.11.0-1016.17 arm64 Linux kernel image for version 5.11.0 on ARMv8 SMP
ii linux-image-5.11.0-1017-raspi 5.11.0-1017.18 arm64 Linux kernel image for version 5.11.0 on ARMv8 SMP
ii linux-image-5.11.0-1019-raspi 5.11.0-1019.20 arm64 Linux kernel image for version 5.11.0 on ARMv8 SMP
ii linux-image-raspi 5.11.0.1019.17 arm64 Raspberry Pi Linux kernel image

```
Ignore anything marked as rc (residual config).

If 5.11.0-1017-raspi is not installed you need to install it.

```
roger@brubeck:~$ sudo apt-mark hold linux-image-raspi
linux-image-raspi set on hold.
roger@brubeck:~$ sudo apt-mark hold linux-image-5.11.0-1019-raspi
linux-image-5.11.0-1019-raspi set on hold.
roger@brubeck:~$ sudo apt-mark hold linux-image-5.11.0-1017-raspi
linux-image-5.11.0-1017-raspi set on hold

sudo flash-kernel --force 5.11.0-1017-raspi

```
That should do the trick.

Roger

---

### Post by MAFoElffen on 2021-10-09
> **rogerjames99 said:**
> This is a workaround for the problem mentioned in the title.

If this is a thread to share a workaround, shouldn't it be marked as "Solved," so that Users can find it as such?

---

