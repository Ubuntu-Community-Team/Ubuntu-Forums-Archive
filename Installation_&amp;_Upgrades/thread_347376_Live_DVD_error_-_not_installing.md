---
title: "Live DVD error - not installing"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by fremeer on 2007-01-27
Ive already set up a ext2 partition with gparted and i have the live dvd but everytime i try to install it with either normal or safe graphics mode GUI it freezes. If i try text mode i get the error
PCI:Cannot Allocate region 2 of device 0000:05:00.0
PCI:Cannot Allocate region 0 of device 0000:05:00.1

after that it goes 

Buffer I/0 error on device hdc1, something about sector (some number)
and this buffer thing goes on forever till i restart

My system specs are
amd 3200+
dfi ultra-d
1gb ram
ati x800 
pioneer dvd-rw

---

### Post by Pobega on 2007-01-27
Sounds like a bad burn to me; Reburn the CD at the lowest speed possible (2x or 4x, depending on your burning program). If you get the same error your CDs are possibly scratched, or your ISO image might be bad, so redownload and reburn.

---

### Post by terrapin28 on 2007-01-28
I notice your configuration includes an ATI x800 graphics card. There are several known issues with the X server and the default ati drivers. You have two options as far as I can tell. 1. Is to use vesa drivers by editing your xorg config file then installing ATI's restricted propietary drivers.
2. [http://www.ubuntuforums.org/showthread.php?t=347216&highlight=ati+x800](http://www.ubuntuforums.org/showthread.php?t=347216&highlight=ati+x800)

Hope that helps.

---

