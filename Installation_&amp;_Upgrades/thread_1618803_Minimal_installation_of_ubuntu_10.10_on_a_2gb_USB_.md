---
title: "Minimal installation of ubuntu 10.10 on a 2gb USB stick"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by Creativepro on 2010-11-11
I am a beginner to linux and have no idea how to do the text installation of the minimal iso. I want ubuntu 10.10 to be installed with just a few software. Can you tell me how to go about it. I am using an eeepc 1000h.

Things i need:
1) Ubuntu core
2) Wireless and ethernet drivers
3) printer drivers
4) basic stuff like sound drivers, touchpad etc.
5) Gimp
6) Open office
7) Firefox with flash
8) Docky
9) Update manager
10) Ubuntu software center
11) pdf reader
12) update manager

So how do I go about doing it. Thanks for your time, long live ubuntu :)

---

### Post by Creativepro on 2010-11-11
oh come on

---

### Post by roddersg on 2010-11-11
Well, if you want a minimal installation, what you could do is to look for a copy of the server edition.  Install that, and don't select any packages at the end. Reboot and you have a copy of minimal ubuntu.
Next manually install the other parts using apt-get install
for example, the Gnome Desktop can be installed using apt-get install gnome-desktop
and then work on each application, one by one.

Bear in mind you would need to do some work by creating a tempfs in ram and then transfering the /proc, /tmp and other directories into this area.

---

