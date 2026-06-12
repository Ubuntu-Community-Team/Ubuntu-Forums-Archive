---
title: "Minmal 9.10 Text Install"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by egeezer on 2010-04-28
As an experiment I did a text installation of the Minimal Install CD of 9.10 (Karmic) and wound up with a console only.  I installed Icewm , but have no clue how to boot to graphic (GUI) mode.  Any suggestions for a newbie eager to learn but profoundly confused?  TIA

---

### Post by kbielefe on 2010-04-28
If you want to boot into a graphical login screen, you want to install gdm or xdm (gdm is the ubuntu default, but you probably want xdm if you don't want to pull in gnome dependencies), then choose icewm from the session menu.

If you want to log in to the console, then start the GUI, there are instructions [here]("http://www.icewm.org/FAQ/IceWM-FAQ-3.html").  Basically, you add it to the .xinitrc, then type startx whenever you want to start the GUI.

---

### Post by egeezer on 2010-04-28
Thank you, kbielefe!  I'll give it a try first thing in the morning!

---

### Post by Xyphoid on 2010-04-29
> **egeezer said:**
> As an experiment I did a text installation of the Minimal Install CD of 9.10 (Karmic) and wound up with a console only.  I installed Icewm , but have no clue how to boot to graphic (GUI) mode.  Any suggestions for a newbie eager to learn but profoundly confused?  TIA

A newbie and already doing a text install? You will get far in the Linux world, Ubuntu Grasshopper!! :P
Keep up the good work!

---

### Post by egeezer on 2010-04-29
Well, I tried both (gdm, xdm) and I can now log into either desktop, but neither is functional yet.  The xdm desktop presents a debian menu with options referring only to the screen.  The gdm (which I now have coming up directly on boot) has an ubuntu login panel with the “I'm waiting” watch image and a document-shaped icon with a red X.  If I log in there it brings me to the debian-menu desktop.  Catch-22!
 I've been looking through Sobell's Practical Guide to Ubuntu Linux, but so far you forum guys have been the best source!
 And @ Xyphoid: thanks for the compliment, but at 76 I'm scarcely a grasshopper!

---

### Post by egeezer on 2010-04-29
Solved at last!  Once I had the bare desktop, I finally discovered that all I had to do was a sudo apt-get install synaptic to get going on populating the GUI with something usable.
 A lengthy experience, but well worth the effort to learn a bit more command line navigation!
But I probably would have given up eventually if I hadn't gotten your help and encouragement.  This way, I was too embarrassed to quit!:redface:

---

