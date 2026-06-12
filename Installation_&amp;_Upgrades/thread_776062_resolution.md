---
title: "resolution"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by iKar310 on 2008-04-30
I'v just installed ubuntu 8.04 and everything is OK..but the restricted driver is activated but it says not in use :confused::confused: and my resolution is small not full screen in settings says its 1024x768 but its not...also my wirelles card doesnt work its Engenius EUB-362 EXT how to activate it 

also when I tried to install some drivers it said u need to be super user to install this  I mean Im the only one who uses pc 

thx guys

---

### Post by dstew on 2008-04-30
> u need to be super user to install thisFrom the command line, use **sudo** to preface your commands to get superuser (administrative) privleges.

To try to get your restricted driver working, press ctrl-F2 and enter the command```
gksudo displayconfig-gtk
```See if you can select the restricted driver there.

---

### Post by iKar310 on 2008-04-30
I tried and now my screen is messed up how to change to previous condition I cant see anything?

---

### Post by dstew on 2008-05-01
Boot in Recovery Mode. On the command line enter ```
sudo dpkg-reconfigure xserver-xorg
```Choose the **vesa** driver when you get to the part about the display. When you are done reconfiguring, enter```
startx
```Hopefully that will get you a working desktop.

---

### Post by beerorkid on 2008-05-01
> **dstew said:**
> From the command line, use **sudo** to preface your commands to get superuser (administrative) privleges.

To try to get your restricted driver working, press ctrl-F2 and enter the command```
gksudo displayconfig-gtk
```See if you can select the restricted driver there.


you saved the day :)  Man there are a lot of threads out there with "resolution" as a keyword ;)

Strange that is not a config area you can get to with the menu options.

Thanks

---

