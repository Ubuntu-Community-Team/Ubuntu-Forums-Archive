---
title: "How to chk whether my video drivers are properly installed"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by durga11 on 2009-12-25
Hi All

I have been using ubuntu 9.10 for the past 1 month,I didnt installed any video drivers explicitly.today while I am trying to run a game, it didnt even started.
Now i want to know if any video drivers needs to be installed.. or how to chk it....

---

### Post by Shazaam on 2009-12-25
Nvidia? ATI?
You can try to run the program "glxgears" to see if the drivers are installed. Go to Applications>Accessories>Terminal and type this in-
```
glxgears
```
A small window with turning gears should open. Or you can enter this-
```
glxinfo | grep direct 
```
Three ways to get drivers with Ubuntu (Karmic)...
1. Go to System>Administration>Hardware Drivers and enable the drivers you want.
2. Go to your video card's website; download and install their linux drivers if they have them.
3. Go to Nvidia or ATI's (or whomever) website and do the same as #2.

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by durga11 on 2009-12-25
Hi , Thanks for the reply,

I am using intel 245 chipset... not NVIDIA..
with glxgears, i am to see the turning gears.

---

