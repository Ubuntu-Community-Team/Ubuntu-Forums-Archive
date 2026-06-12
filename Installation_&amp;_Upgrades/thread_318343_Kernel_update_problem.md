---
title: "Kernel update problem"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by asab5241 on 2006-12-13
Hello everyone,
I am still new to the Linux and Ubuntu world so please excuse the triviality of this question.  I had recently performed a system update in Ubuntu 6.06 and it updated the kernel image.  Afterwards I noticed that the windows boot section in the Grub menu was gone.  I was able to edit the menu list and get the boot information back in the grub menu, but I was wondering if there is something I must do to prevent this from happening again during future updates.  I do not want to have to put the windows boot information into the grub menu every time I update.  If anyone can provide any assistance, it would be greatly appreciated.  Thanks

-Andrew

---

### Post by fredj on 2006-12-16
It is only when the Kernel is updated that the grub menu.lst gets rewritten. Make
a backup copy of /boot/grub/menu.lst so you can easily cut and paste if you windows
info get wiped again.

---

