---
title: "Dumb question: Gparuntu is installdted, where'd it go"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Balinsky on 2007-02-09
Ok gparted is installed on the live cd but i cant for the life of me find it to install now that ubuntu is installed

---

### Post by tbroderick on 2007-02-09
/usr/bin/gparted

Try editing your menu. Maybe the gparted entry is turned off.

---

### Post by Balinsky on 2007-02-10
wow i was a little more out of it when i posted this than i thought. that title looks retarded. this one is better.

but there is no usr/bin/gparted nor is there an entry for the menu. it just doesnt seem to be installed. and it also isnt in the add/remove programs

Is there any other way i could install it (like the yum command in fedora)

---

### Post by tbroderick on 2007-02-10
Open a terminal, Alt-F2 type gnome-terminal, and enter;
```
sudo apt-get install gparted
```

---

