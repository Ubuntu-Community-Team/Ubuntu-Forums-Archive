---
title: "Lubuntu 18.04.1 and wine"
date: 2019-02-01
forum: Installation &amp; Upgrades
---

### Post by wjbmd48 on 2019-02-01
Hi all:

I've found installing wine on Lubuntu 18.04.1 problematic. On a new system, after doing the 

sudo apt install wine32

and then getting to

$ wine --version
wine-3.0
 
then

Winecfg

Everything's fine to that point. Then I enter

sudo ln -s /usr/share/doc/wine-stable/examples/wine.desktop /usr/share/applications/

to put the wine desktop/context menu in the usr/share/applications directory,

the Terminal tells me there's no such program as "ln"

I've never run into this before. Any ideas?

Thanks,

Bill

---

### Post by wjbmd48 on 2019-02-02
OK, finally figured it out myself. Had to manually find another copy of wine.desktop, put it in /usr/share/applications, then on first run of an .exe install, associate that .exe with that file in properties.

Bill

---

