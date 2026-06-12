---
title: "upgrade to oneiric from natty crashed system"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by rubing on 2011-12-26
I am using a netbook version of ubuntu on my asus computer.  Recently I attempted to upgrade from Natty to Oneiric, but it crashed while installing packages.  After that I was only able to boot into recovery mode.  I tried fixing by finishing the apt-get update, but first had to dpkg -a configure.  

Now, when I try to boot the menu option still says Ubuntu 11.04 and when I select it, it'll start to boot, but then gets hung up at either battery state [ok], or runlevel v [ok] 


My hunch is that it's an issue with the oneiric installation not finishing.  Anyway I can enter the recovery mode and get it to finish properly?

---

### Post by Frogs Hair on 2011-12-26
Upgrades can be a problem without bringing Wubi into the picture . You could try Crtl+Alt+F1 enter tty . From there enter your user / name and see what options you have there . If there is nothing important in Ubuntu I would suggest removing and installing a new version of Wubi if you are not ready to do a traditional dual boot yet .

---

