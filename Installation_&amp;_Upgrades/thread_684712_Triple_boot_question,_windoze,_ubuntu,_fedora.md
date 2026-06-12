---
title: "Triple boot question, windoze, ubuntu, fedora"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Michl on 2008-02-01
I can't find guidance on exactly this situation:
On my laptop I am dual-booting W2K and Gutsy.
No problems.
I would like to install a third OS -- Fedora -- that
also uses grub, and during installation there is
an option to leave installed OS partitions and use
free space.  Can I assume that the third installation
will simply add the third OS to the grub menu?

Michl

---

### Post by kellemes on 2008-02-01
> **Michl said:**
> I can't find guidance on exactly this situation:
On my laptop I am dual-booting W2K and Gutsy.
No problems.
I would like to install a third OS -- Fedora -- that
also uses grub, and during installation there is
an option to leave installed OS partitions and use
free space.  Can I assume that the third installation
will simply add the third OS to the grub menu?

Michl


No..
Fedora will overwrite Grub.. Use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to revert back to your previous Grub-install. This will give back your old bootmenu, you can then add a kernelline to your /boot/grub/menu.lst **or** (better way) point to the /boot/grub/menu.lst Fedora created during install..
This way you create a nested bootmenu.

The entry to add to /boot/grub/menu.lst should be something like the following..
```
# Fedora
title Fedora
configfile   (hd2,8)/grub/menu.lst

```(hd0,0) depends on the location of Fedora. It should point to the correct partition and directory of Fedora.

---

