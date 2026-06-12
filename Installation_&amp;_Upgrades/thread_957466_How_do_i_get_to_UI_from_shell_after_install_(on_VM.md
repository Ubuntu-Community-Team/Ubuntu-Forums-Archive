---
title: "How do i get to UI from shell after install (on VMWare)"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by gyro11 on 2008-10-24
Hey, i have just installed the latest Ubuntu server edition via a virtual machine on VMWare.
Installtion went ok and it has now loaded me into a shell.  What do i need to type/do to get to the UI?

thanks,

Rich

---

### Post by ww711 on 2008-10-24
> **gyro11 said:**
> Hey, i have just installed the latest Ubuntu server edition via a virtual machine on VMWare.
Installtion went ok and it has now loaded me into a shell.  What do i need to type/do to get to the UI?

thanks,

Rich

The server edition of ubuntu isn't really aimed for gui/ui...cli all the way.

This will get you the graphical X environment.

```
sudo apt-get install ubuntu-desktop
```
or
```
sudo apt-get install ubuntu-desktop
```

depending on your choice of gnome or kde.

---

