---
title: "Ubuntu dual boot option modification,Please help me?"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by wengkhin on 2008-06-05
--------------------------------

---

### Post by Pumalite on 2008-06-05
Edit /boot/grub/menu.lst and change 'default=0' to 'default=?'
? depending on what position your Windows entry is in the menu.lst, keeping in mind that Grub starts counting fron 0

---

### Post by wengkhin on 2008-06-05
-----------------------------

---

### Post by Pumalite on 2008-06-05
Post:
cat /boot/grub/menu.lst

---

