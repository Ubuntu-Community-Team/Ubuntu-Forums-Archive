---
title: "recover ubuntu after windows reinstall"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Siddharth Yadav on 2007-11-27
i had ubuntu and windows XP installed on  my dell inspiron..
the windows crashed due to some virus or something....when i reinstalled windows i dont get the grub any more...i cant login to ubuntu anymore....wats the problem...i have data on the ubuntu desktop that i would like to recover...what should i do??:confused:

---

### Post by nzadLithium on 2007-11-27
If you can then stick a live cd in to get all your files off. (just in case).

Then open a terminal (Applications >> accessories >> terminal)
type sudo grub
root (hd0,0)
setup (hd0)
exit

assuming you only have one hard disk then this should work (unless you have some reallly weird setup) if you have more though then post back and we'll find out which harddisk you should be booting from.

---

### Post by pete.dawgg on 2007-11-27
"in the software eco-system there's only one os allowed: windoze" (acc. to billg)

you need to reinstall grub, because windoze just kicks out all other boot-loaders on installation. just boot with a live or rescue-cd; i think some live-cds have the option of booting installed os. if you do it from inside yout installed ubuntu it's probably easiest.

---

### Post by nzadLithium on 2007-11-27
pete thats what those commands i jsut wrote out do :)

---

