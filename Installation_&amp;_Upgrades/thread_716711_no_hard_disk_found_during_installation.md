---
title: "no hard disk found during installation"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by fouadk on 2008-03-06
hi everyone...

im trying to install ubuntu 7.10 on a newly formated hard disk....

i have installed winXP successfully first and then booted from the ubuntu CD and launched the installer, when i reach the step that i have to select the hard disk where i want to install ubuntu, it doesnt find an hard disk...

please help....

thanks in advance

---

### Post by taurus on 2008-03-06
From Ubuntu LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L, not number 1.

---

### Post by fouadk on 2008-03-06
i got this one solved...i just removed the master/slave jumper from the back of the hard disk and started the installer and everything went smooth...

thank u for ur time

---

