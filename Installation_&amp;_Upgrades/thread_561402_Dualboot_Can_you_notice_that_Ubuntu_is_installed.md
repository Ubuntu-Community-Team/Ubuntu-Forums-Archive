---
title: "Dualboot: Can you notice that Ubuntu is installed"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by Guardian-Mage on 2007-09-27
Ok, I have Windows XP Home installed. If I was to install Ubuntu 7.04 or 7.10 T5, would any of the other users be able to tell that I had it installed. When restarting or anything at all. Is there any possible way they would find out through normal use? And if I unistalled it, would it leave any trace that it was there.

---

### Post by rsambuca on 2007-09-27
If you install Ubuntu after XP in a dual boot situation, the grub bootloader gets loaded to the mbr.  When you boot the computer it gives you a choice of what operating system to use.  The grub menu is highly configurable, so that you can set XP as the default, hide the grub menu (only you would know when to press 'Esc' to enter the grub menu, and you can set the default time down to 1 or 2 seconds, so people won't see it.  If you later remove ubuntu, you will have to use your XP installation disks or super grub disc to reset the mbr to the XP bootloader.

---

### Post by Guardian-Mage on 2007-09-27
Thanks

---

### Post by rsambuca on 2007-09-27
No problem.  

I won't ask *why* you want to hide this, but a savvy computer user may notice that the size of the XP drive has suddenly shrunk!

---

### Post by logos34 on 2007-09-27
> **rsambuca said:**
>  but a savvy computer user may notice that the size of the XP drive has suddenly shrunk!

One way to avoid that would be to use Wubi, which installs ubuntu as a loopmounted filesystem in a folder *within *XP--it doesn't shrink the partition.  So the only giveaway would be be a reduction in available disk space (by ~4 GB).

---

