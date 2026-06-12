---
title: "startup problem"
date: 2015-12-12
forum: Installation &amp; Upgrades
---

### Post by jeffjohn2 on 2015-12-12
Hoping someone recognises this problem.

Ubuntu 15.04 kernel 3.19.0-39

On startup I have to choose ^D default option.

The logged fault is: "Device sys-subsystem-net-devices  -eth1.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0"

This has only happened recently, after kernel and security updates.

Any solutions or suggestions gratefully received, thanks.

---

### Post by mörgæs on 2015-12-12
15.04 is running out of support in a months time. One solution, though not elegant, is a fresh install of 15.10 to which you have to switch anyway, sooner or later.

---

### Post by jeffjohn2 on 2015-12-17
Many thanks for reply.  I have since run "**Boot Builder**" and all the problems have disappeared; presumably the Grub installation went awry somewhere.

---

