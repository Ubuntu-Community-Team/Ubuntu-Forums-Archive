---
title: "xorg-driver-fglrx update problem"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by dojo on 2007-03-05
hey when i try to update xorg-driver-fglrx which are ati drivers for ubuntu i get the following error:
xorg-driver-fglrx:
  Depends: libc6 (>=2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
  Depends: libfreetype6 (>=2.2) but 2.1.10-1ubuntu2.2 is to be installed
  Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed

I used Synaptic Pakeage Manager to try and upgrade but it didnt work so if anyone has a soloution please say:D.

---

### Post by egoldtech on 2007-03-16
im having same same problem .....

---

### Post by dejitarob on 2007-03-17
If you are trying to install the fglrx drivers I recommend using this guide [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) since there are some additional things you need to do. If you still get that error try 'sudo aptitude' rather than 'sudo apt-get.'

---

