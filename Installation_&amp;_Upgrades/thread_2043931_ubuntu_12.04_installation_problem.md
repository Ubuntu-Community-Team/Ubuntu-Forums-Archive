---
title: "ubuntu 12.04 installation problem"
date: 2012-08-17
forum: Installation &amp; Upgrades
---

### Post by jakelong00 on 2012-08-17
i was installing the ubuntu 12.04 using the mini iso because of the pae problem and during the installation i forgot to install the ubuntu desktop package.now it boots into the command line. i ran the commands
sudo apt-get install unity
sudo apt-get install xinit
and when i try to run startx i get the error
---------------------------------
failed to load session gnome
---------------------------------

and when i run gnome-session i get
---------------------------------
warning:cannot open display
---------------------------------

what to do to start up my gui??

---

### Post by gordintoronto on 2012-08-17
I'm not sure, maybe startx

---

### Post by Marric on 2012-08-18
```
sudo apt-get purge gnome-session
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gnome-session
startx
```
or just reinstall it.

---

### Post by jakelong00 on 2012-08-21
i got it . i ran:
sudo apt-get install ubuntu-desktop

and after rebooting i got the normal login screen.
thnx for helping me out

---

