---
title: "Two questions: Changing mac address, and installing Kile."
date: 2005-08-05
forum: Installation &amp; Upgrades
---

### Post by JohnRus on 2005-08-05
Hello!

First my question:
How i can automatically change mac adress of my ethernet card in Ubuntu configuration? (i.e. hw ether).   I am using package "macchanger" for changing mac on my Gentoo linux installation.  What can i do with Ubuntu?

Second question:
How i can install Kile application to original Ubuntu 5.04 installation? (i.e. with only Gnome on my computer)


Thanks.

---

### Post by dave9191 on 2005-08-05
Hey, 

You can install both of the programs using apt-get

apt-get install macchanger
apt-get intsall kile

If you get an error that the packages are not found, you need to add extra repositories. You can find how to do that at ubuntuguide.org

Dave

---

### Post by Reb on 2005-08-05
For the second question, sudo apt-get install kile will work.
That will download a lot of KDE and QT libraries, which you might already have.

---

### Post by dave9191 on 2005-08-05
[QUOTE=Reb]For the second question, sudo apt-get install kile will work.
That will download a lot of KDE and QT libraries, which you might already have.[/QUOTE]

The standard ubuntu install shouldnt have any kde libs. But apt-get will install what it thinks is needed to run something. If you have what it needs installed already, it wont install it agian. 

Dave

---

