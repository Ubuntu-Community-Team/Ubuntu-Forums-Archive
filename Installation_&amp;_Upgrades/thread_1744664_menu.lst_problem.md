---
title: "menu.lst problem"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by davidself1001 on 2011-04-30
I did an upgrade from 10.10 to 11.04 and when it rebooted it still shows 10.10 as my primary option in the menu.lst file.  Also, it just freezes at a splash screen or something but never gets to the login prompt.  I was asked during the install about debconfig and i said to use the exist one.  Is that the problem and if so how do i get it corrected?

---

### Post by dino99 on 2011-04-30
actual distro use grub2 (grub-pc) and it conflict with old grub-legacy and its menu.lst

so remove it and update-grub again

you can also, from synaptic, remove/purge then reinstall: grub-pc & grub-common

---

### Post by davidself1001 on 2011-04-30
i'm a novice. how do i do the grub update?  I can only get in via recovery mode.  What do i do then?

---

