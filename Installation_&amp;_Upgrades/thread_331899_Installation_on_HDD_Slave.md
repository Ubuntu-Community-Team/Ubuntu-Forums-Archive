---
title: "Installation on HDD Slave"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by mr_manson on 2007-01-05
Hi to all

I've a pc composed byt 2 HD

1 Master HD Maxtor with XP 

2 Slave on removable mobile   HD Maxtor with installed just now a ubuntu 6.10

Then....

When i start the boot with the second slave hd inserted all is ok the grub menu is ok and make me the possibility to choice what O.S. use but...

If i put out the removable Hd i think wgere is thre grub write the boot make an error.... error 21 

So i i would start XP when the HD removable is off what can i do ?

Maybe i must rewrite the MBR ox XP ?

Thanks a Lot  :-k

---

### Post by scrooge_74 on 2007-01-05
I don't think i understand you to well, but I think you should check if Grub is installed on the master boot of the first disk

---

### Post by rejser on 2007-01-05
Even if grub is installed on mbr it will still need files in /boot/grub folder, such as menu.lst
Maybe U can use win xp bootloader to dual, a little bit tricky, but works. Search the forum

---

### Post by mr_manson on 2007-01-05
Really... i try to backup the mbr on first disk and i see there is something about grub 
but when i remove the second hd slave the grub will not load ,,,,, grub loading error 21 so i think the grub is write on second slave and the mbr of first is modify by conseguence of grub....

I just want recover the old situation ...with no slave hdd and just first  with xp what way ?

---

### Post by scrooge_74 on 2007-01-05
use your Xp Cd to recover your MBR and then start over

---

### Post by mr_manson on 2007-01-06
Thanks to all  I resolve ....i used xp cd to recover mbr with emergency console 8)

---

