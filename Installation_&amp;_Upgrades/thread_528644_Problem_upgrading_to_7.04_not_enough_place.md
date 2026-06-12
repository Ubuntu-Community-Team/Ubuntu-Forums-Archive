---
title: "Problem upgrading to 7.04 not enough place"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by josefcarel on 2007-08-18
**Im trying to update from 6.10 to 7.04** through adept manager but after a few steps i get a message like this: [COLOR=Red]there is not enough place at /boot[/COLOR]
Before that I was asked to make apt-get clean but seems to be not enough! What can I do?
By the way /boot is not to big only the Grub and oher little file.
Thanks in advance:confused:

---

### Post by ruibernardo on 2007-08-18
There are some files you can remove.

You could try to remove old kernel images that you don't use anymore. They are installed by the packages "linux-image-2.6.20-15-generic" for example. It can end with "-386" or "-k7" depending on your processor.

Don't remove the main package "linux-image-generic"

To remove kernel 2.6.20-15:

```
sudo apt-get remove linux-image-2.6.20-15-generic
```

That should free the space needed in /boot for any new kernel you install.

---

### Post by josefcarel on 2007-08-19
> **epimeteo said:**
> There are some files you can remove.

You could try to remove old kernel images that you don't use anymore. They are installed by the packages "linux-image-2.6.20-15-generic" for example. It can end with "-386" or "-k7" depending on your processor.

Don't remove the main package "linux-image-generic"

To remove kernel 2.6.20-15:

```
sudo apt-get remove linux-image-2.6.20-15-generic
```

That should free the space needed in /boot for any new kernel you install.

Yes I have deleted an old kernel the 2.6.15-10 generic directly from the /boot archive that was there but i dont think i have the 2.6.20-15 generic. This the new kernel for ubuntu 7.04, yes? 
In any case i will try now to made the upgrading

**Muito Obrigado!! **
Josef Carel  :lolflag:

---

### Post by josefcarel on 2007-08-19
**No way! The same problem after cleanning the older kernel**! I get the same message telling that It's needed 26 Mb sapce in /boot :(
What can I do? Making a clean upgrading with the CD?
Thanks and Muito Obrigado

---

### Post by ruibernardo on 2007-08-19
If you make a fresh install with the same size on /boot, you will have the same problem on the next kernel upgrade/update. Probably a fresh install with a new partition mapping is advised.

If you have only 1 kernel image installed and you can't install any new kernel, then the only way would be to enlarge the /boot partition.

Give /boot partition at least 100MB or 200MB to be sure. You can boot with a "Desktop CD" and use its "Gnome partition editor" (gparted). Be careful with this operation, if you enlarge «to the left» (using free space before /boot partition) you might make your Ubuntu unbootable.

Again, if all this fails, make a new install and this time give some more space to /boot partition.

---

### Post by josefcarel on 2007-08-19
It seems to be very hard to do and I dont feel sure enough to do that my self. I will look for some other help.
Thanks any way
Josef

---

