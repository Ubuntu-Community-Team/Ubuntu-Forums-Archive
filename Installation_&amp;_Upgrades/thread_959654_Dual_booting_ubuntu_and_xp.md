---
title: "Dual booting ubuntu and xp"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by DOMINICANGHOST on 2008-10-26
Everytime ubuntu updates everything goes fine but when i restart the computer and it shows me the os option ubuntu has about6 different versions, i know have of them are recovery mode bu i want to know how to take the old ones out

---

### Post by zvacet on 2008-10-26
In synaptic search box type **linux-image** and you wil see all your kernels.Dalete one with lower number.You can leave two with higher number just in case.

---

### Post by lswb on 2008-10-26
You can search for your kernel version (generic, i686, etc) in synaptic and mark all but the current and perhaps the next most current for removal. Your boot menu will be rewritten as part of the uninstall process. If you need more info on this post back with a copy of your /boot/grub/menu.lst file.

---

### Post by DOMINICANGHOST on 2008-10-26
Thanks worked like a charm

---

