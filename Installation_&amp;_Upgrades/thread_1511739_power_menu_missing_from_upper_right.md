---
title: "power menu missing from upper right"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by unix1adm on 2010-06-17
Im trying to figure out what the latest patch set for ubuntu 10 did to my system.

When I login there USE to be a power off menu on the upper right of my screen. 

Now to get my system to power down I have to login into to a terminal and issue sudo shutdown. 

What happened to the power off menu?

---

### Post by dino99 on 2010-06-17
right click on top panel and add it , 

or into a terminal: metacity --replace

---

### Post by unix1adm on 2010-06-17
> **dino99 said:**
> right click on top panel and add it , 

or into a terminal: metacity --replace

I tried that command but it did funky things to my system and I had to use the pwr button to reset it. 

I can add the button using the right click command you mention but its not the same as the one I use to have. It was a drop down menu that allowed me to switch user or power off the system etc.

---

### Post by unix1adm on 2010-06-21
No one else has run into this?

---

### Post by davidmohammed on 2010-06-21
add to panel and choose "shut down" to install that applet into your panel.

---

### Post by unix1adm on 2010-06-22
OK i see this now and for some reason on bootup today it works like it should odd. but I now see the option should I need to put it back. thank you very much. I was looking at the wrong applet i guess the first time i tried it.

it fixed it self today do i hear twilight zone music playing

---

### Post by unix1adm on 2010-07-29
this still seems to be an issues every time i get a fix or something. I put a separate menu item on my task bar that seems to work

---

### Post by tobart on 2011-07-12
I had the same issue and it was bugging me. It turns out that original menu is part of the applet called "Indicator Applet Session". This applet includes the IM menu and the power menu next to it (all themed very nicely). For me, the IM menu was still showing but the power menu was messed up/gone even between reboots. 

Removing and re-adding the "Indicator Applet Session" applet resolved the issue for me!

---

