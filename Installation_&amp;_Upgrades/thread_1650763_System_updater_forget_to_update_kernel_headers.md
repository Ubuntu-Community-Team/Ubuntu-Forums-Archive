---
title: "System updater forget to update kernel headers"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by RussianNeuroMancer on 2010-12-22
Before 2.6.35-23 released this packages is present in the system:
i A linux-headers-2.6.35-22
i A linux-headers-2.6.35-22-generic
i A linux-image-2.6.35-22-generic
But after automatic update to 2.6.35-23 updater install just linux-image-2.6.35-23-generic without headers. In result kernel modules of nVidia driver not compiled and next boot X server can not start.

Now I can install 2.6.35-24 image and headers by hands, but how to explain updater not forget to update headers next time and why this problem occurs?

Bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/693311](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/693311)

---

### Post by RussianNeuroMancer on 2010-12-22
Reason found: while upgrade from 10.04 to 10.10 updater remove linux-headers-generic package, but not reinstall it. In result headers files not updated automatically.

---

### Post by davidmaxwaterman on 2011-03-09
> **RussianNeuroMancer said:**
> Reason found: while upgrade from 10.04 to 10.10 updater remove linux-headers-generic package, but not reinstall it. In result headers files not updated automatically.

I have this same problem, but I never upgraded from 10.04, but instead did a fresh 10.10 install onto a blank laptop.

Can anyone suggest why, after upgrading kernels, it consistently fails to install the corresponding linux-headers and so doesn't recompile the nvidia modules, resulting in no graphics?

How to fix this?

---

