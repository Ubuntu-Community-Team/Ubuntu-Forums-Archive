---
title: "Is there a way to edit entries in system menus?"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-13
in lubuntu i was able to edit fix and translate entries in system-managment or system preference is there a way to do it gnome?

thanks in advance.

---

### Post by ankspo71 on 2010-03-13
Look in /usr/share/applications/***  Those are the entries in the menus. To edit the one for gparted, use the terminal to launch the shortcut in  gedit.
```
sudo gedit /usr/share/applications/gparted.desktop
```
hope this helps.

---

### Post by aviramof on 2010-03-13
thanks it does only it's not as easy method because you need to know the excact desktop file i think that gnome and nautilus should really check and fix a lot of those things like auto arrange and this option lubuntu have to edit names directly from the right click menu in system.

---

### Post by SevenMachines on 2010-03-13
sorry if i misunderstood the question, but do you mean 
right-click on main-menu icon -> edit menus ?
then you can edit the commands/names of any menu entry

---

