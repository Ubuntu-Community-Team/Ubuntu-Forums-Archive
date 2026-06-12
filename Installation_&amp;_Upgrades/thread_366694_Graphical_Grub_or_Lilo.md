---
title: "Graphical Grub or Lilo"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by eppoh on 2007-02-21
Can't remember for sure- I think it was Mandrake.. anyway there was a really neat graphical program for manuplating Grub and Lilo. It would let you choose which kernel to place where, which was default and change the timer for auto loading.

I cannot find it in Kubuntu.

I tried to install Lilo-config. The install went fine but it does not show up in the menu anywhere and will not run from the command line.

---

### Post by ffxr on 2007-02-21
i dont know of any such utility & i dont think lilo-config will work in ubuntu.

cant you just edit the grub menu manually...? (back up first in case you screw it up)

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by eppoh on 2007-02-21
Maybe it was lilo-config

---

