---
title: "grub loader on linux partition"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by Titomarques on 2008-09-20
Hi, I want to do a dual boot with xp and ubuntu 7.10, and i want to place the grub loader on the ubuntu partiton, i don't wanna mess up with windows, the problem is that i can't. I already change the loader position that by default is (hda0) and change it to sda6 my linux partition, i already change it to other things but when instalation cames to end it gives me an error "loader position error" or something else. Any help??

---

### Post by Pumalite on 2008-09-20
In 'Advanced Tab' you have to change (hd0) for /dev/sda6(if sda6 is where 'root' is)

---

### Post by Titomarques on 2008-09-20
I already solved that, but now my ubuntu takes a eternity to start.

---

### Post by Titomarques on 2008-09-21
I think the ubuntu partition must be adjacent to the windows partition, is my guess, the only problem that may be

---

