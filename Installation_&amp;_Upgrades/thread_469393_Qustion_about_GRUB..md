---
title: "Qustion about GRUB."
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by Manji on 2007-06-09
Say, If I were to install X.P. on one of my partition. How I would make an option in GRUB boot menu, so I can boot into X.P.?

---

### Post by jackiecanev2 on 2007-06-09
add your XP installation to /boot/grub/menu.lst

---

### Post by jackiecanev2 on 2007-06-09
sudo gedit /boot/grub/menu.lst

add:

title Windows XP
root (hd?,?) <- your own hd/partition
makeactive
chainloader +1

---

### Post by Manji on 2007-06-09
> **jackiecanev2 said:**
> sudo gedit /boot/grub/menu.lst

add:

title Windows XP
root (hd?,?) <- your own hd/partition
makeactive
chainloader +1

Thanks for the help, this should help me a bunch.

---

