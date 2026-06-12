---
title: "How to restore grub?!"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by cwmaxson on 2007-04-24
Hola,

I've installed Feisty with the intention of dual booting it with dapper.  However, when I installed Feisty, I installed it over not only a 10 GB empty partition, but also my original /boot partition.  When I installed Feisty, my dapper partition was not in Grub, and I would like to know how to restore my /boot/grub/menu.lst and all /boot files so that I can dual boot both OS's.

Thank You.

---

### Post by zorkerz on 2007-04-25
'sudo dpkg-reconfigure grub' in a terminal that will reconfigure grub i believe. I do not think backups are saved of menu.lst. Your old one would not have the the new installation on it would it?

Can you mount the partition of your original install. You might be able to fine the original menu.lst there. Is it possible the dapper install got wiped out?

I don't think any other boot files are necessary for this though im by no means an expert.

Just for curiosities sake; why dual boot feisty and dapper?

---

### Post by zvacet on 2007-04-25
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")

---

