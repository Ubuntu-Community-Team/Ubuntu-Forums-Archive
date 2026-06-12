---
title: "Editing GRUB"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by avantgardaclue on 2005-08-03
Hello... I've got a twin hard disk computer; HDA has my win xp on and hdb currently has ubuntu 5.04. If only i could get ubuntu to communicate with my sagem fast 800 adsl thingy then i would swap properly to ubuntu, but i can't so i'm not, well not for now anyway[!]. I have to share the computer with the wife and she insists on using xp. I keep getting it in the neck from her that the boot up sequence allways defaults to ubuntu first and not xp.

Q. How do you edit grub so that xp is the default boot (basically so she can turn it on and forget about it and xp will load)?

---

### Post by Sam on 2005-08-03
```
$ sudo gedit /boot/grub/menu.lst
```
Change the 'default' value to what you want (beware, it's zero-based).

---

### Post by drummer on 2005-08-03
Open the menu.lst file be doing this in a terminal:```
sudo gedit /boot/grub/menu/lst
```
look for this section, near the top:```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0
```Change the number after default as it says (numbering starts at 0) to the place that XP is in the grub menu list. I think I would put 4 here as I have 3 Ubuntu options, 'Other OS' title, then XP. 

EDIT - beat me to it

---

### Post by avantgardaclue on 2005-08-03
>> I think I would put 4 here as I have 3 Ubuntu options, 'Other OS' title, then XP. <<

4 it is then.... and worked first time, thanks!

---

