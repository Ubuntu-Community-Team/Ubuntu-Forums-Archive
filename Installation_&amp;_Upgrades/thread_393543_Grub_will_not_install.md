---
title: "Grub will not install"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by eppoh on 2007-03-25
I am trying to install xubuntu on a PC with win xp and Mepis already on it.

Got Xubuntu to install okay, but when I start up, it boots directly to Xubuntu- bypassing Grub.
The Xubuntu installer said it was installing grub on the mbr. I actually went through the complete install twice.

I tried using super grub to reinstall Grub. That reinstalled it in the previous configuration only- without any Xubuntu

---

### Post by zvacet on 2007-03-26
```
sudo gedit boot/grub/menu.lst
```
You will find line named timeout.Select number(10 maybe)and that is time in seconds your grub will be on the screen.Save the file.next time you login you  should see grub and with arrow key pick wich OS you want boot to.

---

