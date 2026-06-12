---
title: "lubuntu 12.10 wont install"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by Usx8 on 2013-03-28
Alright, when i go to install lubuntu, I get through all of the GUI boxes asking what username i want, timezone, etc. and then i get to the screen with the "see more now!" style message.  After a while theres nothing but a blank screen and my mouse, which lets me click, and when i click with the right button i have all the usual options, but a plain black screen.  on rebooting i find that lubuntu is NOT installed  so i tried again, same deal.  Then i tried to install from inside the live trial, same deal except instead of a black screen, now its the desktop, and i have all the usual desktop options (start menu, etc).  Is there something im doing wrong?  did i miss something?  Im trying to install on a really old HP desktop (2002 I think, 700mhz processor and .5gb ram)  Any help is awesome

---

### Post by ajgreeny on 2013-03-28
You may have the slideshow problem that I have seen in ubiquity (the installation software program).

Boot to the live desktop of Lubuntu from your CD or USB and from that either run synaptic-package-manager and remove **ubiquity-slideshow-lubuntu** package or simply open a terminal and run ```
sudo apt-get remove ubiquity-slideshow-lubuntu
``` to do the same thing.  Now try installing again to see if it goes ahead

---

### Post by Usx8 on 2013-03-28
Should I install from inside the live boot or restart then try installing?

---

### Post by mörgæs on 2013-03-28
Better to try the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO").

---

### Post by Usx8 on 2013-03-28
Deleted the slides how and got it installed!  Thanks a bunch!

---

