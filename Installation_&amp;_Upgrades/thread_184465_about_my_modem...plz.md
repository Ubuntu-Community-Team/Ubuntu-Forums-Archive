---
title: "about my modem...plz"
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by Iron_550 on 2006-05-29
how do i find out what com prot my modem is in. and what command do i use to find in in ubuntu?

---

### Post by Ptero-4 on 2006-05-30
use sudo pppconfig. The password is the one for the user you created during the installation. The pppconfig utility creates a dialup conection and even tries to find which port the modem is connected to (if it's a hardware modem).

---

### Post by Iron_550 on 2006-05-30
thank you i well try this and get back to you.

---

### Post by Iron_550 on 2006-05-30
now thats thats all done how do i connect to the internet?

---

### Post by Ptero-4 on 2006-05-30
from the command line use pon to connect, plog to see how it's going, and poff to disconnect. In KDE download kmodemlights from [www.kde-apps.org](www.kde-apps.org) and use it to conect to the internet. In gnome get gnome-ppp from synaptic and use it.

---

