---
title: "Installing Wine 1.5"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by Kaizoku001 on 2012-05-02
ound a guide That would help to install the new wine 1.5 (i figured this might help with my airvideo problem)
 > wget [http://prdownloads.sourceforge.net/wine/wine-1.5.0.tar.bz2](http://prdownloads.sourceforge.net/wine/wine-1.5.0.tar.bz2) 
tar -xjvf wine-1.5.0.tar.bz2 
cd wine-1.5.0 
sudo apt-get install flex bison qt3-dev-tools qt4-qmake 
./configure 
cd tools 
./wineinstallunfortunately at the last line I got
 
 >  configure: error: Cannot build a 32-bit program, you need to install 32-bit development libraries.

Configure failed, aborting install.I installed a 64 Ubuntu.
Wat are my options?

---

### Post by carl4926 on 2012-05-02
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by zombifier25 on 2012-05-02
You downloaded the 32bit version of Wine. You should download the 64bit one...

...however, you should avoid installing from source as much as possible. Instead, to make your life easier, add Wine's PPA:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.5
```

EDIT: NINJA'D!!!

---

### Post by Kaizoku001 on 2012-05-03
thanks... installation went great.

now just have to figure out how to install AirVideo

---

