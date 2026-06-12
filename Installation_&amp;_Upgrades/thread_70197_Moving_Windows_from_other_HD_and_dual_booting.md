---
title: "Moving Windows from other HD and dual booting"
date: 2005-09-29
forum: Installation &amp; Upgrades
---

### Post by ThePyromaniac on 2005-09-29
I'm sure the dual-boot question has been asked a hundred + times here, but this one is slightly different.

I have never really got much luck dual-booting, as something always breaks. I was wondering if I could get some help with that here, as fiddling with grub never works for me.

I wish to move a Win64 installation from my old HD onto the free space of my new HD. How would I go about doing that firstly, then what would be involved with getting Win seen by GRUB?

Thanks,
Phil

---

### Post by drewbie on 2005-09-29
Personally i have no idea how to go about moving a windows partition, maybe search some windows forums?? but once it is moved just run 

sudo update-grub

it should find your windows partition fine, hopefully.

(or you can manually edit the /boot/grub/menu.lst file to point to the new partition

---

