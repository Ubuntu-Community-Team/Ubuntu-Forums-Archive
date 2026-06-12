---
title: "how to delete xp without harming the ubuntu install"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by bash7869 on 2009-12-30
HI guys

I am currently dual booting with xp and Ubuntu 9.04. I would like to delete xp and have a dedicated Ubuntu install only.
Anyone have any ideas on how to do this without messing up the ubuntu install.

Thanks

---

### Post by zey on 2009-12-30
> **bash7869 said:**
> HI guys

I am currently dual booting with xp and Ubuntu 9.04. I would like to delete xp and have a dedicated Ubuntu install only.
Anyone have any ideas on how to do this without messing up the ubuntu install.

Thanks

format the xp partition, then you can use it for ubuntu partiton...
use ext3 or ext4

---

### Post by dandnsmith on 2009-12-30
If you have a 'proper' install, rather than the easy one which installs in the XP filespace, then you need to get acquainted with the content of grub.conf/menu.lst in /boot/grub.
There you'll be able to see how to lose the boot entry for XP, and all that remains is to clear out the XP partition - easy with gparted (just re-format it to whatever type you want).
Provided you've a reasonably modern system I don't foresee any snags - but, you necver know for sure until you do it!

---

### Post by bash7869 on 2009-12-30
thanks for the reply's guys....could i modify the grub menu by removing the xp title and then formatting as i had xp installed first before i added Ubuntu?
would this cause any problems?

---

### Post by presence1960 on 2009-12-30
> **bash7869 said:**
> thanks for the reply's guys....could i modify the grub menu by removing the xp title and then formatting as i had xp installed first before i added Ubuntu?
would this cause any problems?

You can use gparted to format the xp partition and either create a new partition as ext3 or ext4 (only use ext4 if your 9.04 / is ext4. If it is not you will not be able to access it because ext3 can not access ext4. But ext4 can access ext3) or add the unallocated space to your Ubuntu / partition. Your choice. I prefer a separate partition for all my data that way when I reinstall at the next release all data on that partition remains in place untouched.

Then from Ubuntu open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst

Scroll down to the windows entry and remove it. 
Click Save on top toolbar. Close file. When you reboot your windows OS and the windows entry in GRUB will be gone!

---

