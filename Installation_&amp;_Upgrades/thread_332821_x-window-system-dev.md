---
title: "x-window-system-dev"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by Ubbi on 2007-01-06
while trying to get x-window-system-dev installed with 
sudo apt-get install x-window-system-dev
it says that it can't find it.. How can I do?

---

### Post by taurus on 2007-01-06
You mean

```
sudo aptitude update
sudo aptitude install xorg-dev
```

---

### Post by Ubbi on 2007-01-06
I found this guide to get cedega; this is an extract from it

[I]2. Preparations
Download the script here.

Needed apps, packages, libraries: wget fontconfig freetype2 freetype2-devel bison flex libjpeg libjpeg-devel libpng libpng-devel zlib zlib-devel xorg-x11-devel (resp. XFree86-devel)

Mesa (resp. xorg-x11-Mesa, XFree86-Mesa) Mesa-devel (resp. xorg-x11-Mesa-devel, XFree86-Mesa-devel) freeglut freeglut-devel SDL SDL-devel

Debian users can just use: apt-get install cvs build-essential bison flex-old libasound2-dev **x-window-system-dev** libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev[/I]


The point in bold does not work!:rolleyes:

---

### Post by taurus on 2007-01-06
Have you tried my method from above?  Are you trying to build cedega from source?

---

### Post by Ubbi on 2007-01-06
Thank you for your patience...
And brilliant intuition!!

I'm trying but I'm getting stucked in understanding howto.
I've tried your method but I can't locate WineCVS.sh...
..By the way I don't understand what it is...:-D 
Isn't there a step-by-step guid for cedega (not [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Cedega%20CVS](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Cedega%20CVS) )?

---

