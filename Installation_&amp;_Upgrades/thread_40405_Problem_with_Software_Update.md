---
title: "Problem with Software Update"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by mobile.army on 2005-06-08
I've been trying to install the linux-image-2.6.10-5-386 update, but I get the following error:

E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.2_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386

How do I fix this?

---

### Post by zAo on 2005-06-09
[QUOTE=mobile.army]I've been trying to install the linux-image-2.6.10-5-386 update, but I get the following error:

E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.2_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386

How do I fix this?[/QUOTE]
What do you mean with "inux-image-2.6.10-5-386 update" ? You current kernel uses the ndiswrapper-modules, so you need to update your kernel and ndiswrapper, or remove ndiswrapper first.

---

