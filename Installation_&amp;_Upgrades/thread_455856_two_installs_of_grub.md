---
title: "two installs of grub"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by faminator on 2007-05-27
I have 3 drives on my system with 2 installs of feisty.
First Install is on hda1 using all default installation options.
Second install is on hdc1 using all default installation options except the disk to use.
The 2nd Install was to fix X after I put a different video card in. I used it to get a working xorg.conf file.
(mission accomplished)

The problem now is that I am finished with the 2nd install and would like to get rid of it, but...

When the system boots it is using the grub on hdc1 which includes entries for both installs. I want it to revert to using the grub on hda1 which just has entries for the first install.

Before I mkfs hdc1 what do I need to do to make sure it will use the grub on hda1?

I hope this wasn't too confusing.

Faminator

---

### Post by confused57 on 2007-05-27
You can use the live cd to reinstall whicheve install'sr grub you want on the mbr:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

---

### Post by faminator on 2007-05-27
Many Thanks

That worked flawlessly.

---

