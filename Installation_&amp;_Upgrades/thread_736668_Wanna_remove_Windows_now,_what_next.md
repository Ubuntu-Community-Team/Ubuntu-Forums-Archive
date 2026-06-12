---
title: "Wanna remove Windows now, what next?"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by njenkins on 2008-03-26
Hey all, 

I've made myself at ease with the latest version of Ubuntu and don't want to look back. My question is how do I now remove Windows and free up that partition and change it so Ubuntu can use it?
I am running Xubuntu on an old Thinkpad A30.. Its Windows XP in case that matters.

Thanks

---

### Post by chewearn on 2008-03-27
1. Reformat the XP partition, using gparted.
2. Edit /boot/grub/menu.lst; remove XP boot entry.

---

