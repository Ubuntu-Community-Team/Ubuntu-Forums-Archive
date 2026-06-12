---
title: "multiple os's one grub"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by keeler1 on 2008-10-30
I want to install multiple linux operating systems on one disk.  Which also means I want exactly one grub to load them.

When I have tried this before kernel updates for the first one installed need to be manually added to grubs list.

Is there any way of configuring a system like this so that both operating systems have access to grub and will share a menu.

---

### Post by caljohnsmith on 2008-10-30
I don't know of a way to actually have all distros share the same menu.lst and update it accordingly, but one trick you can use is:
```
title Linux Distro 1
configfile (hdX,Y)/boot/grub/menu.lst
```
If you put that in the menu.lst of the Grub that gets loaded on start up, then it links to the menu.lst of the other "Linux Distro 1". Thus when Linux Distro 1 updates its menu.lst, you will see the change. The disadvantage of this method is you have to go through two boot menus to get to Linux Distro 1. Let me know if you need more info/details, but that's the general idea.

---

### Post by panda726 on 2008-10-30
What I have done is to make a grub partition and have that point to a menu.lst that has configfile pointers to the menu.lst for each distro.  Then I have installed grub for each distro to the partition I install the OS to.  The advantage of the grub partition for someone who likes playing is that messing with any of your distros is unlikely to mess up booting, whereas if you leave grub with one of your OSs, reinstalling that one will make a mess out of the rest of them.

Tor

---

