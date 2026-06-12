---
title: "im client issues"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by barqers on 2007-09-20
Okay, so i'm trying to find a im client most like msn messenger. So i tried emesene, for some reason i cannot add it to main menu? my command was emesene... possibly just a glitch since it's brand new-ish.

Now there's a problem with mercury...I installed it via, sudo apt-get install mercury and it is installed. but it's not in my applications>internet section... so i tried to add it via main menu, no can do it cannot find this application. so am i forgetting some dependencies? i uninstalled it and reinstalled it via synaptic but it didn't make me install dependencies.

Any ideas? thanks

        Barqers

---

### Post by barqers on 2007-09-20
Bump

---

### Post by barqers on 2007-09-22
bump

---

### Post by UbuWu on 2007-09-24
For emesene:

Add this lines to your /etc/apt/sources.list (or go to system -> administration -> software sources and add this line in the third party sources list):

deb [http://apt.emesene.org/](http://apt.emesene.org/) ./

and then install emesene using synaptic or apt-get install emesene

It will appear in the menus automatically, in the internet submenu.

---

