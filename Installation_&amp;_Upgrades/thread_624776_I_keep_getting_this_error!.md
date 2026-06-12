---
title: "I keep getting this error!"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Nando-san on 2007-11-27
hi! First of all I am a TOTAL newb in ubuntus, just converted from years of slavery of Windows...

I just instaleed UBUNTU and  the upgdate manager tells me i can donwload 88 upgrades... when i click OK it tells me this in a little box... 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can any1 help me?!?!?!

---

### Post by taurus on 2007-11-27
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

p.s.  Make sure you close down the update manager window first.

---

### Post by Nando-san on 2007-11-27
thanks ! it continued to install the java and whatnot, and this appeared...

Setting up sun-java5-bin (1.5.0-13-0ubuntu1) ...
No theme index file in '/usr/share/icons/sun-java5.png'.
If you really want to create an icon cache here, use --ignore-theme-index.

but then i clicked the manager window and it began downloading the files normally... should i ignore terminal now?

---

### Post by taurus on 2007-11-27
Yes.  You don't have to use terminal anymore if you don't want to.

---

### Post by Nando-san on 2007-11-27
than you for your help!!! very grateful!

also... I want to install the aMSN...any tips on that? i can't install it

---

