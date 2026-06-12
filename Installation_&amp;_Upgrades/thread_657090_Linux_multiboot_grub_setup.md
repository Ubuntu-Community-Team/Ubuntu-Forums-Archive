---
title: "Linux multiboot grub setup"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by ssam on 2008-01-03
I currently have about 5 distros installed on my system (no windows).

the installers for most distros are pretty good at detecting existing installations, and adding them to their own grub menu. however this seems to mean that only the most recently installed system can update grub. for example if ubuntu gets a kernel update it will add the new kernel to /boot/grub/menu.lst in its own partition, but the grub that starts the computer will be look for menu.lst on another partition.

I think it is possible to chain grubs together, so that a master grub would give a menu option for each partition, and these would load each of the menu.lst for each partition.

Is this a good method. Are their better ways?

Whats the best way to set this up?

How do I stop distros from overwriting it?

---

### Post by meindian523 on 2008-01-03
1]It's possible.
2]A better way,in my opinion would be to add the relevant lines to the Grub of the latest distro.
3]The best way would be to decide whose Grub you want on the MBR and install the other distros' grub on their respective / partitions.
4]If you chainload grub,I would think that whenever a distro updated itself,it would update it's own grub and you wouldn't need to alter the main Grub unless you want to see all your options on one screen.

---

### Post by ssam on 2008-01-03
i did some more searching and found this [http://www.justlinux.com/forum/showthread.php?t=147959](http://www.justlinux.com/forum/showthread.php?t=147959)

---

### Post by meindian523 on 2008-01-03
Well,then I guess your problem is solved.:)Though I had once visited that thread,I didn't remember it till I clicked the link and saw the title bar in my FF.Makes it look so easy.........

---

### Post by mamep on 2008-01-03
Ok with the link it's working..

But suppose that you want to uprgade kernel from one of your different distributions and then grub's menu will be upgraded automatically. 

Is it possible to contain the old entries?

Like other distributions and windows..

---

### Post by meindian523 on 2008-01-04
Run that by me again?

---

