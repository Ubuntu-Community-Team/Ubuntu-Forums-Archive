---
title: "Install Problem"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by phoenixdown on 2008-01-23
I'm trying to install Ubuntu onto my pc. It's definately good enough. i got the amd 64 version of 7.10, did the checksum check, burnt it, booted with it, did the check there, the logo with the status bar appear, then i start to see a graphical interface loading, i can see the logo but its distorted and on the top of the screen like 5 times, then i see a cursor that looks like an X for about 4 seconds, then it goes away and i get this screen:



[B] * Starting deferred execution scheduler atd          [ OK ]
 * Starting periodic command scheduler crond          [ OK ] 
 * Checking battery state...                                       [ OK ]
 * Running local boot scripts (/etc/rc.local)                 [ OK ][/B]


At this point i can type stuff, but it doesn't really respond to anything... and when i hit ctrl alt del i get ome more lines of it saying it's stopping things and then it reboots and nothing's been installed. What can i do??




Dave

Any help with this would be much appreaciated, i hope there isn't another thread on this, i already have looked for about an hour and i'm still getting to responses on IRC.

---

### Post by Partyboi2 on 2008-01-23
What are your system spec?

---

### Post by phoenixdown on 2008-01-23
AMD Athlon X2 64 2400+
2gb RAM
ATI Radeon X3500 or something, 

i'd check but it's hanging with a curser just flashing now.

---

### Post by someonestolemyname on 2008-01-23
I had this problem for a bit. Most likely there is something wrong with your graphical setup (xorg.conf...).

Did you ever get it running? And mess with something to do with graphics?

Especially ince you have an ATI video card (unbelievable pain...).

Good luck.

---

### Post by Partyboi2 on 2008-01-23
Have you tried choosing option 2 at the main menu to start it in safe graphics mode. If that does not work try:
pressing Ctrl+Alt+F2 when you get to the place it gets stuck (Hopefully that will bring you to a terminal where you can type). Then type
```
 sudo dpkg-reconfigure xserver-xorg
```choose vesa for the driver and finish answering all the questions. If unsure just use the default ones that are displayed on screen. When you have finshed type:
```
startx
``` If that does not work try the alternate cd from [here]("http://releases.ubuntu.com/releases/7.10/")

---

