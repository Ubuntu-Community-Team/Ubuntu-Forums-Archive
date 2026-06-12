---
title: "Upgrade-from-grub-legacy: command not found"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2009-10-28
Hi,
I need help with upgrading grub to grub2.  Followed instructions in wiki.ubuntu.com/grub2.

$ sudo apt-get install grub2

grub-pc configuration screen appears with a general warning message but nothing happens when I tried to click on OK. Then:

$ sudo upgrade-from-grub-legacy
Error: sudo: upgrade-from-grub-legacy: command not found

$ grub-install -v
grub (GNU 0.97)

I would very much appreciate your help.

---

### Post by dino99 on 2009-10-28
better to stay with grub; too much troubles with grub2  :D

if you want grub2, read sticky on top of page first, install grub-pc (not grub2) & os-prober

---

### Post by ranch hand on 2009-10-28
Read the thread linked in my sig along with some of the links.

The links are great.

Grub2 is a lot of fun as yo can build a menu that will never need editing if you are on a static system.  If you ad to the system it is easy to pick up the new install in a few seconds.

---

