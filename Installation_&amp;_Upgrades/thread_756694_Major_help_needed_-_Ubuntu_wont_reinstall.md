---
title: "Major help needed - Ubuntu wont reinstall"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by heiowge on 2008-04-16
Had to do a complete reinstall, and can't get Ububtu working.

Spec:

Dell Desktop PC
2.8Ghz P4
1.25 Gb DDR RAM
80Gb hd was running XP on 40Gb and Ubuntu 7.04 - upgraded to 7.10 on the other 40
**PNY Nvidia 256Mb (GeForce 6, 6200) Graphics card** (which was the straw that broke the camels back)

Ok.  Put the card in and configured XP.  Tried to load Ubuntu and it failed to start the GUI, going instead to a text prompt.  Several attempts to fix resulted in breaking the Grub file, so decided to do a full install.  Got XP on, but Ubuntu just won't fix.  I think it can't get the monitor to work.

Also tried Linux Mint, no joy.

What I really need is an install that supports my Nvidia card (and Ethernet - drivers vanished for XP, had to install them with a wireless USB card!) right out of the box.

Would prefer Ubuntu or any dirivative and Gnome desktop.  Any Help?

---

### Post by Partyboi2 on 2008-04-16
what is the actually error message or where is the boot process stopping?

---

### Post by kellemes on 2008-04-16
Assuming this is a videocard issue you should try (as root)..
```
dpkg-reconfigure xserver-xorg
```

---

### Post by zvacet on 2008-04-16
If you can install Ubuntu but you don´ have GUI boot in recovery mode and type 

```
dpkg-reconfigure -phigh xserver-xorg
```

and select vesa driver.After restart you will have basic graphic.For wireless I don´t know.Maybe you should look in [here](http://ubuntuforums.org/forumdisplay.php?f=136) for faster answer.

---

### Post by heiowge on 2008-04-19
Full reinstall solved problems.  Ta all!

---

