---
title: "Grub menu.lst problem"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by gros0350 on 2005-07-19
Hello,

I've got a dual-boot set-up and I'm trying to change the grub boot order.  I know that I should do sudo gedit boot/grub/menu.lst BUT the menu.lst seems to be a read only file.  I should be able to change whatever I want in ubuntu but is there something that I must do before I'm allowed to change this file? 

Is this unheard of?  Should I post more info?  Any help would be appreciated,
Gregg

---

### Post by codejunkie on 2005-07-19
[QUOTE=gros0350]Hello,

I've got a dual-boot set-up and I'm trying to change the grub boot order.  I know that I should do sudo gedit boot/grub/menu.lst BUT the menu.lst seems to be a read only file.  I should be able to change whatever I want in ubuntu but is there something that I must do before I'm allowed to change this file? 

Is this unheard of?  Should I post more info?  Any help would be appreciated,
Gregg[/QUOTE]
try
```

sudo gedit /boot/grub/menu.lst

```
insted of 
> 
sudo gedit boot/grub/menu.lst

if that doesnt work try 
```
sudo su
```
then cd /boot/grub then nano menu.lst or gedit menu.lst

---

