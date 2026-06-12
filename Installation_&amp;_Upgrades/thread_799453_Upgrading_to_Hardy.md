---
title: "Upgrading to Hardy"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by theredpolak on 2008-05-19
I've been pushing it off too long, and I realize that I need to upgrade to a new version of Ubuntu.

I realize that there is no real reason to uninstall the old version before the upgrade, but is there any way to remove some of the old version kernels from my boot menu?

I dual boot XP/Ubuntu, but having more than one Linux kernel installed means I have to scroll down to find XP, which seems unnecessary, help?

Also, there isn't any pressing difference in running Ubuntu through Wubi rather than through it's own partition, is there?

---

### Post by housam on 2008-05-19
You can edit the grub menu.lst to make the unwanted kernels from appearing in the grub menu by adding # in front of the lines of these kernels then save and reboot.
installing through wubi only save the partitioning process.

---

