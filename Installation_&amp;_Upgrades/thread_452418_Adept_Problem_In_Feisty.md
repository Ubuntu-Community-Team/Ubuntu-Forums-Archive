---
title: "Adept Problem In Feisty"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by morpheus55 on 2007-05-23
Hello All.

I just installed Feisty and she is just that!!!  When I tried to install and open ADEPT I got the window 'Must open in root" . I did that but all the control things and edit and etc are grayed out. Not able to do anything whether as root or as a nobody! Is there a bug in the distro, cos it seems like it. ( by the way I installed automatix2 and that was fine)....  the morf   ;)

---

### Post by bmartin on 2007-05-23
Are you clicking on an icon to open it or using the terminal?
[LIST]
[*]If you're using a terminal, try using **sudo adept**, which will run it as root.
[*]If you're using a launcher, it should use the launch command **gksudo adept**. If the item is in a menu, you'll have to edit the menu.
[/LIST]

---

### Post by morpheus55 on 2007-05-23
Thanx, I tried both of those avenues when I first encountered the problem, but they had no effect. Nothing works. Is it just possible that the distro has a few bits or a file missing, and would it be possible to re -install  [over the top, as they say in m$ circles?] :p

---

