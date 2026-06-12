---
title: "use cdromupgrade without GUI"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by naruvimama on 2008-04-03
my graphic driver isn't supported by 7.04 (G965) need to update from iso (7.10) on hard disk... but how do i do 'cdromupgrade' without graphical interface(exception while starting pyGtk).

thanks in advance

---

### Post by zvacet on 2008-04-03
```
sudo dpkg-reconfigure xserver-xorg
```

when you come to the drivers select** vesa** and continue.After reboot you will have basic graphic ans after upgrade find driver for your card.

---

