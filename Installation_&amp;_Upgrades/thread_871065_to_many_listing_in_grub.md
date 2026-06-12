---
title: "to many listing in grub"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by 565Customz on 2008-07-26
hey guys every time i get an update it list a new version in the grub along with the old one. anyone know how to get it back to one ubuntu listing and one windows listing? someone told me how to do it before but i cant find the thread.  i know there is a way to comment them out but last time i was told how to completly remove them. thanks alot

---

### Post by oldos2er on 2008-07-26
Use Synaptic Package Manager to uninstall unneeded kernels; this will also remove them from the grub menu.

---

### Post by northern lights on 2008-07-26
I'd say leave at least 2 though.

Plus, kernels do not necessarily need to be uninstalled to leave the GRUB menu.

Edit your menu.lst by running```
gksu gedit /boot/grub/menu.lst
```
find where it reads ```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=ALL

```
and set it to '# howmany=2' (leave the comment). Only the latest two will appear in the bootmenu.

---

### Post by zvacet on 2008-07-26
@ **northern lights**

> kernels do not necessarily need to be uninstalled to leave the GRUB menu.

You are right,but what is a point to have kernels which you don´t use?By deleting them you are geting some (not much but still) free space.

---

### Post by 565Customz on 2008-07-29
what am i supposed to look for in synaptic?

---

### Post by zvacet on 2008-07-30
In synaptic search box type **linux-image** and then delete ones with lower number.You can keep last two (higher numbers).

---

### Post by 565Customz on 2008-08-11
thanks alot guys!

---

### Post by Oldsoldier2003 on 2008-08-11
Dont forget to mark the images for "complete removal" for best results.

---

### Post by Hunter M. on 2008-08-11
And once you uninstall the unneeded kernals, if it is still there (the old listings) try a program called: QGrubEditor, it's an interface to editing the grub list by hand

---

