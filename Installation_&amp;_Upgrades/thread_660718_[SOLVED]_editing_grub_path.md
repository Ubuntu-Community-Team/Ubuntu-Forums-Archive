---
title: "[SOLVED] editing grub path"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by dasan on 2008-01-07
I am having two harddisk drive and in one there is Ubuntu and in other there is XP
is there any way to enter in to Xp by giving it's path in Grub ?
The thing is tat my motherboard is old and doesn't support fast boot so every time i have to enter to BIOS and edit boot device priority..

---

### Post by forestpixie on 2008-01-07
can you post the following to start

sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by dasan on 2008-01-12
It is Solved 
Only Thing i have done is
i hav edited /boot/grub/menu.list
which was lik this

[COLOR="YellowGreen"]title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/COLOR]

To[COLOR="SeaGreen"]
title		XP
root		(hd1,0)
map           (hd0) (hd1)
map           (hd1) (hd0)
savedefault
makeactive
chainloader	+1
[/COLOR]

This Works If You have Added a new hard drive with xp and U need to give path to it from Your Hard disk

---

### Post by dasan on 2008-01-12
Thank U ...... **forestpixie**

---

