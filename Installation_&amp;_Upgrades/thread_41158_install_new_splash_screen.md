---
title: "install new splash screen"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by fireedo on 2005-06-12
how to change splash screen?

---

### Post by Error1312 on 2005-06-12
Not sure, but I believe you simply need to download a splash screen from a site (like gnome-look.org) and replace the standard splash screen with it. (make a backup first)

---

### Post by Xian on 2005-06-12
```
$ sudo apt-get install gtweakui
$ gtweakui-session
```

---

### Post by Toddy on 2005-06-12
You can save your splash screen to:

/usr/share/pixmaps/

then using Configuration Editor (Applications - System Tools - Configuration Editor), go to apps - gnome sessions - options.  Double click on splash_image to edit the value to point to your new splash screen.

---

### Post by fireedo on 2005-06-12
[QUOTE=Toddy]You can save your splash screen to:

/usr/share/pixmaps/

then using Configuration Editor (Applications - System Tools - Configuration Editor), go to apps - gnome sessions - options.  Double click on splash_image to edit the value to point to your new splash screen.[/QUOTE]
 that's great!!!...thanx for the information..... :)

---

