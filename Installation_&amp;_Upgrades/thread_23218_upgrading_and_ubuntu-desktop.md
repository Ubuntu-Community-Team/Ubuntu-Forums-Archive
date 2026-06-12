---
title: "upgrading and ubuntu-desktop"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by audax321 on 2005-03-31
When I installed Warty I removed Firefox, Evolution, and OpenOffice and all of them required me to remove ubuntu-desktop.

So, should I reinstall ubuntu-desktop before I do the upgrade to Hoary? Also, why does Ubuntu have Firefox, Evolution, and OpenOffice as dependencies... why not just leave them as installed packages that don't depend on ubuntu-desktop???

---

### Post by humanity_to_others on 2005-04-08
Ubuntu 4.10 (ubuntu-desktop)= Gnome2.8+Openoffice1.1.2+Firefox0.97+Evolution2
Ubuntu 5.04 (ubuntu-desktop)= Gnome2.10+Openoffice1.1.3+Firefox1+Evolution2.2

---

### Post by az on 2005-04-08
Because that is what a meta package it.  The ubuntu desktop is what it is.

I do not know if you can do this in synaptic, but in dselect, you can update your packages, pick ubuntu-desktop and all the dependancies will come up.  From them, you can remove the ones you do not want.  It will then show you what is left out of what was selected taking into considerstion all the dependancies and the whatnot.

You make it go and you get all that you want.  I would recommend aptitude, but it is harder to do with the dependancy handling settings.  It is much more straightforward with dselect.

As soon as I am in front of an ubuntu box, I will try it out in synaptic and let you know...

---

### Post by az on 2005-04-08
OK.  Change your repo settings to point to hoary in synaptic.  Update and find the Ubuntu-desktop package.
Mark it for installation.
Scroll through the list of packages marked for installation and unmark the ones you do not want (Firefox, Evolution, and OpenOffice)
Then make it go.  You should be happy.

---

