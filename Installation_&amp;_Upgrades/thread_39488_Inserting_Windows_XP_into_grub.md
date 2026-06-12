---
title: "Inserting Windows XP into grub"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by Boopop on 2005-06-05
I know how to edit grub from linux, but how do i find out what it recognizes my windows XP drive ( the C: drive or hda as linux likes to call it) and what do I put into the kernel part and what do i type in for initrd. I'm using gedit by the way to edit it.

Thanks in advance, Boopop

---

### Post by mtron on 2005-06-05
it was not recognized during install and wrote in the grub menu?

to edit grub menu type:

$ sudo gedit /boot/grub/menu.lst

when your wxp is on the first partition of the first drive (hda1 in ubuntu), grub uses the expression (hd0,0). For the second partition (hda2) grub entry: (hd0,1) and so on

a grub entry for windows resident on hda1:

title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Boopop on 2005-06-05
Thanks, my computer illiterate mother shall be able to use windows xp without hassle forever more :razz: .

---

### Post by mtron on 2005-06-05
no problem  ;-)

---

