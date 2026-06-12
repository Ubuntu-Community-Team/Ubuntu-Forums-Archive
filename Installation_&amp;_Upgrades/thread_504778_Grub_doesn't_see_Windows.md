---
title: "Grub doesn't see Windows"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Jored on 2007-07-19
I have recently installed Xubuntu 7.04 Feisty with Xfce desktop on a Dell Latitude LS400, 400Mhz, 256MB, 40GB HDD which also runs Windows 2000.

The Grub menu doesn't include Windows. Yet I can boot Windows with no problem with Super Grub.

I tried :

sudo update-grub    and    sudo /sbin/update-grub  and every time got back the same menu list with just the Xubunto O.S line, the Xubuntu Recovery OS line and the Memory Test line, but not Windows.

I picked up in one the threads the recommendation to type into the terminal:

sudo gedit /boot/grub/menu.lst

and edit the menu list by adding:

title Windows 2000
rootnoverify (hd0,0)
chainloader +1
boot

But I can never get to the menu list as I always get  back :

sudo: gedit: command not found

Any clues? 

Does "sudo gedit /boot/grub/menu.lst" work with Gnome and not with Xfce?

---

### Post by confused57 on 2007-07-19
Xubuntu doesn't have gedit, you'll have to use nano:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo nano menu.lst
```
or just:
```
sudo nano /boot/grub/menu.lst
```

add your Window's entry, then...ctrl+x, y, enter..to save your changes.

---

### Post by Jored on 2007-07-19
Thank you. Worked first time. I'm new to Linux and I'd spent hours on this one ....

Xubuntu has given a new lease of life to my old laptop which struggled with W2000 and couldn't install straight Ubuntu from the LiveCD. Xububtu installed first time, only problem being the missing Windows entry in the Grub menu for dual boot, now solved.

---

