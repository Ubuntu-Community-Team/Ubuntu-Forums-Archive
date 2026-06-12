---
title: "Live CD not displaying Ubuntu Desktop! Experts needed on Vid card setup"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by deezy on 2007-03-19
So basically I've got two cards I've been playing around with trying to install Ubuntu + beryl.  I had installed my ATI all in wonder x800xt then installed Ubuntu successfully.  After some reading, I decided it was best to use my nvidia card to get beryl to play nice with Ubuntu.  Turns out I can't see a damn thing with my nvidia GF4 5600FX card, once I'm booted into the desktop.  I hear the startup sound but then my screen displays horrible, It appears to be a video driver problem as everything is green/red/white etc  and all I can see is the mouse cursor.  What do I need to do in order to get this Nvidia card to:  Install Ubuntu and get it to display right so I can move onto beryl.

Thanks,

-D

---

### Post by Kateikyoushi on 2007-03-19
This should help. [LINK]("http://ubuntuforums.org/showthread.php?t=379807")

---

### Post by deezy on 2007-03-20
I tried the suggested link, and after changing to the "Vesa" driver and exiting, my screen goes into a loop.  That's turning black/then saying no video source, over, and over, etc...

thoughts?

---

### Post by Pru on 2007-03-20
I fixed this problem this morning in a rather unorthodox way...

I had openSuse 10.2 install on my computer and I hadn't install my nVidia drivers yet but when loading openSuse 10.2 it worked fine so I basically copied the contents of xorg.conf to my ubuntu one and it worked!

only bit of code I actually needed was this
```
sudo nano /etc/X11/xorg.conf
```
to open and edit the xorg file for ubuntu

I know this will probably be a last resort kinda thing but I thought I'd put it out there

---

