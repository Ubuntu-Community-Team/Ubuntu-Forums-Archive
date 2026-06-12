---
title: "problems after ati installation"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by kboy on 2008-02-14
hi, a few days ago i've installed the ati driver using this guide:
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

after the reboot the gnome desktop had some problems:
1) the borders of the windows are gone.
2)all of the windows open in the upper left corner, that means i cant open more then one window at a time.
3)some of the icons on the desktop disappeared.
4)becouse there's no border i can't move the windows.

i've tried to reconfigure the xserver-xorg, but it didn't work.
in short, i don't know what to do and i need some help!
(i am getting tired of using windows!!!)

thanks

---

### Post by ajgreeny on 2008-02-14
Sounds as if it is a problem related to compiz.  Try with compiz disabled and it may all come good.

---

### Post by erginemr on 2008-02-14
If disabling compiz as suggested above does not work, you can always go back you your open source "ati" drive by running:
```
sudo dpkg-configure xserver-xorg
```
and selecting the "ati" driver when prompted.

---

### Post by kboy on 2008-02-14
nothing works!!!!!!!!!!
i removed compiz completely and the ati drive, but nothing works!
i'm starting to think that the only solution is to reinstall ubuntu. :confused::(

---

### Post by erginemr on 2008-02-14
Just one more trick before a complete reinstall: You can try booting with the Live CD and use its xorg.conf file to replace the one installed in your system with it.

---

