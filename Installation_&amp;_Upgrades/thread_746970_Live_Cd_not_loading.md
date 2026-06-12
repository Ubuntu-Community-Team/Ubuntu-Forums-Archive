---
title: "Live Cd not loading"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by Switcher05 on 2008-04-06
I have windows xp on a 160gb hard drive and linux on a separate 80gb hard drive. I tried to uninstall linux off my 80gb. I used MbrFix.exe through windows cmd and the operating system select menu when i start my computer was gone. Then i deleted all the partitions on my 80gb using partition magic 8.0. 

Now i want to reinstall Ubuntu. I downloaded the v7 live cd and burned it, inserted it and the ubuntu menu popped up and i selected start or install Ubuntu. When it was done loading the tan background came up with the mouse cursor and then the screen went black and said no connection. There was no login menu or anything like that. 

How can i reinstall ubuntu?

The 80gb is not reconized in windows so im not sure if that has anything to do with it.

---

### Post by Switcher05 on 2008-04-08
anyone?

---

### Post by Pumalite on 2008-04-08
Boot your Ubuntu Live CD and, from the Terminal, post:
sudo fdisk -lu

---

