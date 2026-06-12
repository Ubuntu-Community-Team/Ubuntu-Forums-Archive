---
title: "Recompiling the kernel."
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by kazik1616 on 2005-07-20
Could you tell me how to do it under Ubuntu? I need to add some modules.

---

### Post by codejunkie on 2005-07-20
[QUOTE=kazik1616]Could you tell me how to do it under Ubuntu? I need to add some modules.[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel) this might help.

---

### Post by kazik1616 on 2005-07-22
Thanks very much :)

---

### Post by az on 2005-07-22
If you just need to compile modules, use the linux-headers package.  Do not forget to install build-essential, too.

That's what the headers are for - building extra modules for your stock kernel (2.6.10-5-386)  Check you kernel version...  Headers are available for all versions.

---

