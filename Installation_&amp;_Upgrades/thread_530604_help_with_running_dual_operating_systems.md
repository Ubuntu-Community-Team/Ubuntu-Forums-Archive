---
title: "help with running dual operating systems"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by tmelliott88 on 2007-08-20
I just installed ubuntu and love it. it seems to work great and everything. The only problem i have is I do not know how to boot up windows again. When it tells you to press the "esc"button on the start-up to run a different OS, windows is not a choice and i don't know how i can boot windows. any help would be greatly appreciated. Thanks.

---

### Post by Pumalite on 2007-08-20
Explain what you did. Especially where did you install Grub? Do you have access to a system now?

---

### Post by tmelliott88 on 2007-08-20
i installed ubuntu off my a live cd. my only problem is I can't figure out how to boot windows XP up again.

---

### Post by Pumalite on 2007-08-20
Did you install Ubuntu 2nd? and Where did you install grub? What system do you have access to now?

---

### Post by Pumalite on 2007-08-20
Sorry, apparently you have access to Ubuntu, you installed Grub to MBR and the problem is probably your menu.list. So, post:
cat /boot/grub/menu.list (from terminal)

---

### Post by tmelliott88 on 2007-08-20
> **Pumalite said:**
> Sorry, apparently you have access to Ubuntu, you installed Grub to MBR and the problem is probably your menu.list. So, post:
cat /boot/grub/menu.list (from terminal)

sorry, you'll have to get excuse me. I'm not very familiar with ubuntu yet and don't know what this means or where to post this

---

### Post by confused57 on 2007-08-20
Since Pumalite isn't logged in right now, I'll try to help...open a terminal(Applications---Accessories---Terminal), post the output of:
```
gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list

also, post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

---

