---
title: "Use Wubi to overwrite old Ubuntu installation?"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by gsk320 on 2012-11-17
Hi,

I tried upgrading from 12.04 for 12.10, however, my computer crashed during the upgrade process, and as such, ubuntu is completely corrupted. Is there a way to use wubi to overwrite the old ubuntu installation? When I open wubi, the only option I get is to install it on the C: drive. I want it to overwrite my old Ubuntu partition. Is there any way to do this?

Thanks!

---

### Post by whatthefunk on 2012-11-17
Do you have a Live CD/DVD or a USB startup disk?  That would be the easiest way.

---

### Post by darkod on 2012-11-17
If your old installation is a proper install on its own partition (not wubi), you can't.

Wubi installs inside windows, on ntfs partitions, and won't touch the existing linux partitions.

If you want to delete the existing linux partitions, or install over them, you can always do that with the ubuntu cd in live mode.

---

