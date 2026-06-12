---
title: "[SOLVED] Display not working once graphic card driver is installed"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by djbsteart1 on 2008-01-11
when i finished installing kubuntu, a message saying that i could install restricted drivers appeared, the install for the modem went fine but the graphics card, which is a nvidea go420 32mb card, seemed to be fine untill reboot, the resolution had a max of 640 by 480 and i couldnt ajust it. i tried to reconfigure the xorg file using:

hpkg-reconfigure xserver-xorg 

but after that xorg wouldnt start and the system goes to command line. any help will be greatly appreciated, thanks i advance.

donald

---

### Post by taurus on 2008-01-11
What driver did you pick for your graphic card when you ran that command?

```
sudo dpk-reconfigure -phigh xserver-xorg
```
Try the **nv** driver to see if it works.

```
startx
```

---

### Post by djbsteart1 on 2008-01-11
i dont know, i wasnt given the option to pick one. it was a automated setup i think. thnks for the codes ill just run them.

---

### Post by CalvertaBeck on 2008-01-11
* I have the same issue and a smaller screen is a REAL pain. HELP!*

---

### Post by djbsteart1 on 2008-01-12
i ran the scripts you gave and the external monitor is a mess bt my laptops one is ok. my problem now is that i need to get the external one working as my laptops one is temperamental. any suggestions?

---

### Post by djbsteart1 on 2008-01-12
> **CalvertaBeck said:**
> * I have the same issue and a smaller screen is a REAL pain. HELP!*
try these:
[http://ubuntuforums.org/showthread.php?t=626513](http://ubuntuforums.org/showthread.php?t=626513)
[http://ubuntuforums.org/showthread.php?t=661842](http://ubuntuforums.org/showthread.php?t=661842)

there was another one about switching xorg to xvesa but i cant find it, will look and put it up.

---

