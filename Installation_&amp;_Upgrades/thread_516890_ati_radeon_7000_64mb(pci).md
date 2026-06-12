---
title: "ati radeon 7000 64mb(pci)"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by omishd on 2007-08-03
wen i installed the card.. i turned the comp on.. it started fine but once it got to the part were is shows ubuntu loading before u log in... it doesent show it.. all i c is a bunch of vertical coloured lines.. like my card is garbage or theirs on error with it.. (it works good on windows, so i think the cards good its just an error)... is it my comp, driver related or doesnt work with ubuntu

---

### Post by eggdeng on 2007-08-03
It doesn't work with the proprietary fglrx driver. Check your /etc/X11/xorg.conf to see that you have ```
Driver "ati"
``` in the device section. You should be able to get Beryl up and running using the bundled ati driver + aiglx, I got it to run this way on Edgy.

---

