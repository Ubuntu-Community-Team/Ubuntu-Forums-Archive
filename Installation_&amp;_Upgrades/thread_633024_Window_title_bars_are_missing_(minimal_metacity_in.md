---
title: "Window title bars are missing (minimal metacity installation)"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by nn4l on 2007-12-06
I am trying to create a small Ubuntu installation for use in a VMWare image. The plan is to start with the minimal command line installation and then add X, gnome and metacity. I found these instructions: [http://wiki.makethemove.net/index.php?title=CustomUbuntu](http://wiki.makethemove.net/index.php?title=CustomUbuntu) but they are for Ubuntu 7.06 and don't seem to work for Ubuntu 7.10

I have installed these packages on top of the minimal installation:
```
apt-get install xorg gdm gnome-session gnome-menus gnome-panel gnome-terminal metacity
```
When opening the terminal program, it does not have the usual window title bar. After starting "metacity" from inside the terminal everything is ok.

So it seems that I have missed to install a package or missed a configuration step which causes metacity to run after the user logs in.

Please advise.

---

