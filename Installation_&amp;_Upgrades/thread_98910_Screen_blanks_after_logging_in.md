---
title: "Screen blanks after logging in"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by pucbaldwin on 2005-12-04
[Posted this in the newbie forum a few days ago but have had no response so am reposting here]

Hi there,

Just downloaded and installed Ubuntu for the first time. All seemed to go well until I went to log in after rebooting at the end of the install. Type in username and password and then the screen goes brown and nothing happens. Still have mouse movement but that's it. Num lock on keyboard is unresponsive.

I was using Fedora 3 until yesterday, tried to upgrade to Fedora 4 but had a similar problem (screen went blank when accessing the graphical installer program when upgrading).

I think Fedora 3 didn't recognise my Geforce FX 9800 (used generic driver), whereas Fedora 4 did (it said so). Presumably Ubuntu does as its more uptodate.

Is this a video card problem? Thanks very much in advance.

Pete

---

### Post by bwog on 2005-12-04
You could try this: [http://ubuntuforums.org/showthread.php?t=98700&highlight=vesa+console](http://ubuntuforums.org/showthread.php?t=98700&highlight=vesa+console)

do sudo dpkg-reconfigure xserver-xorg press ctrl-alt-f1 to get into console if you need to

and chose vesa driver

If this works, search the howtos in 'customization tips' to install your nvidia driver. If it is possible for your video card, choose one that is available via synaptic.

---

### Post by pucbaldwin on 2005-12-04
Thanks for this. Unfortunately I can't get into the console, Alt Cntrl F1 doesnt do anything. Is there any other way to get into the console?

Cheers,

Pete

---

### Post by bwog on 2005-12-04
Your keyboard seems to work before login. Perhaps you can try to get into a console before login.

---

### Post by pucbaldwin on 2005-12-05
This worked. Thanks for the advice.

Pete

---

