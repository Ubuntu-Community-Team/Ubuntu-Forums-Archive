---
title: "Switching from HDB to HDA"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by someusernoob on 2006-09-12
Downstairs i got another PC, and its config is this:

HDA = Windows
HDB = Ubuntu

I want to rip out HDA, so HDB becomes HDA then.

But... of course this give me troubles, because Grub is configured on HDA and my fstab contains HDB entries, so it cant find HDB once HDB is HDA (still get it?)

So im wondering. If i do sudo grub-install /dev/hdb while in Ubuntu, and change the menu list to HD0,0 i think, instead of HD1,0, and i edit the entries in the fstab file from HDB to HDA, will it boot again then without any problems? Or is there more to look out for?

It aint a problem if it doesnt work, because i can install Ubuntu again in under 40 minutes, but in that 40 minutes i could also let the dog out. :grin:

---

### Post by someusernoob on 2006-09-13
Im typing this from Ubuntu on HDA. It seems that my way worked fine. 

I installed grub to /dev/hdb before i ripped out hda. In menu.lst changed hd1,0 to hd0,0 and hdb1 to hda1. And in fstab i also changed everything that was hdb to hda (root, home and swap). And it runs fine. Great work.

---

### Post by someusernoob on 2006-09-16
Oh, when i updated some kernel stuff today, grub renamed everything back to the old situation again in the menu.lst file. Not a big problem at all, but if anyone has done the same thing as me, and you update your kernel, check if menu.lst has changed, other wise you can edit the settings while grub is loading, but doing it before you reboot is easier imo.

Im planning on installing edgy from scratch once it is released, so then the problems will be totally gone, altough it isnt really a big problem i cant live with...

---

