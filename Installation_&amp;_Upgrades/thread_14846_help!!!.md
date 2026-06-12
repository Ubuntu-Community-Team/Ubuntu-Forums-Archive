---
title: "help!!!"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by asani on 2005-02-10
I am new to Linux and just install UBUNTU ON MY COMPUTER. I can login and give my password but what do i do next. I understand ther is a command but I have no clue what to type to get to the GUI. Can someone help me please???

---

### Post by lao_V on 2005-02-10
Normally, you should have been taken to the Graphical display manager (GDM). If you can't then type in startx when you have successfully logged in.

---

### Post by carlc on 2005-02-10
Are you at the command prompt? If so, try typing "startx".

---

### Post by friez on 2005-02-10
[QUOTE=asani]I am new to Linux and just install UBUNTU ON MY COMPUTER. I can login and give my password but what do i do next. I understand ther is a command but I have no clue what to type to get to the GUI. Can someone help me please???[/QUOTE]
 did you install x11/xfree and gnome/kde ? if not then due
```
sudo apt-get update && sudo apt-get install gnome-base gdm
``` x11/xfree should be a depence of gnome

---

