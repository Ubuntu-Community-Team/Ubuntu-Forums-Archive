---
title: "where do i find xorg.conf????"
date: 2005-07-07
forum: Installation &amp; Upgrades
---

### Post by korny666 on 2005-07-07
can someone tell me where i would find the xorg.conf file?

---

### Post by tonym on 2005-07-07
/etc/X11

---

### Post by frodon on 2005-07-07
xorg.conf is locared in /etc/X11/
to open it ```
gedit /etc/X11/xorg.conf
```to edit it ```
sudo gedit /etc/X11/xorg.conf
```To locate a file in your system : ```
sudo updatedb
```it will make a database of all path then to locate a file in this database : ```
locate xorg.conf
```if you add some software think to update the database with sudo updatedb before use locate, if you just type "locate xor" it will also work because you don't need to write the whole name of the file.

---

