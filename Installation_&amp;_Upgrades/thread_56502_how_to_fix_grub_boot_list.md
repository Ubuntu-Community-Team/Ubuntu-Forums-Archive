---
title: "how to fix grub boot list?"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by guardianx on 2005-08-12
right now if i dont press anything grub will boot into ubuntu..


i would like to change it so that if i dont select any thing i would like grub to select winxp by default. 

how do i do that?

---

### Post by PeP on 2005-08-12
[QUOTE=guardianx]right now if i dont press anything grub will boot into ubuntu..


i would like to change it so that if i dont select any thing i would like grub to select winxp by default. 

how do i do that?[/QUOTE]
sudo gedit /boot/grub/menu.lst
search 'default'
change it to the line for win XP, stating from 0, 
(i mean the position of the winxp boot section amongst the other ones (linux ...), not the lines in the file.)
0 should be ok

---

