---
title: "Kernel Panic"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by impman89 on 2005-04-30
when i boot into ubuntu i get the following error:

exec: 428: chroot not found
Kernel Panic: not syncing - attempted to kill init!

does anyone know why this is so and how to solve it?

---

### Post by defkewl on 2005-04-30
Check your /boot/grub/menu.lst and /etc/fstab
Make sure that your Ubuntu load from the correct HD

Please inform us as much information as possible :)

---

### Post by Nob on 2005-05-01
reconfigure grub, that seem to be the problem..

---

