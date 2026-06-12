---
title: "new ubuntu user error problem"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by orkis xela on 2008-07-10
hello everyone of the Ubuntu community.

i just installed Ubuntu on an external usb hard drive and it worked fine but when i tried to get back to the windows side i got GRUB error  21 and when i tried to get back to the Ubuntu side it gave me error 22 and so far i have not been able to use windows or Ubuntu. i have only been able to use my system with the live disk .  and when i tried what was posted in the forum by typing find /boot/grub/menu.lst   and it sais no file exists so i cannot do any of the grub fixes posted

---

### Post by Pumalite on 2008-07-10
Boot your Live CD, connect your USB and run from the Terminal:
sudo fdisk -lu

---

