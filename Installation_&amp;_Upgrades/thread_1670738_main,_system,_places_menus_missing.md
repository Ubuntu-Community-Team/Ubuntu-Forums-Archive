---
title: "main, system, places menus missing"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by geo316 on 2011-01-19
I have 11.04 installed, Gnome 2.32.0 - life has been good until I responded as normal to the update manager this morning. Upon reboot noticed my main menu, system menu and places menu are gone. Other icons and stuff like power button remain on the top toolbar but again, no menus.

Googling around I found solutions that were years old and/or did not work for me (like installing XFCE - which did nothing).

Is there any help for this?

G

---

### Post by plucky on 2011-01-19
> **geo316 said:**
> I have 11.04 installed, Gnome 2.32.0 - life has been good until I responded as normal to the update manager this morning. Upon reboot noticed my main menu, system menu and places menu are gone. Other icons and stuff like power button remain on the top toolbar but again, no menus.

Googling around I found solutions that were years old and/or did not work for me (like installing XFCE - which did nothing).

Is there any help for this?

G

There is Natty Narwhal Testing and Discussion Forum where you should ask any questions related 11.04.That is where all the testers hang out.

See [Here](http://ubuntuforums.org/forumdisplay.php?f=394)

As for your problem,Right click on the top panel and select **Add to Panel**.

In the window that opens,find and select **Menu Bar** and ADD.

Good Luck

---

### Post by azmand01 on 2011-01-19
Hey, i have been having similar problems.This is what I did.

I reinstalled all apps-menus by:

sudo apt-get install gnome-panel
gnome-panel

Also creating another user will recover for that user the original panels, but i find out that the app switch-user or something like that crashes all the time. I never reinstalled and it seems my problems went away.

Good luck.

---

### Post by azmand01 on 2011-01-19
Hey, i have been having similar problems.This is what I did.

I reinstalled all apps-menus by:

sudo apt-get install gnome-panel
gnome-panel

Also creating another user will recover for that user the original panels, but i find out that the app switch-user or something like that crashes all the time. I never reinstalled and it seems my problems went away.

Good luck.

---

### Post by azmand01 on 2011-01-19
Hey, i have been having similar problems.This is what I did.

I reinstalled all apps-menus by:

sudo apt-get install gnome-panel
gnome-panel

Also creating another user will recover for that user the original panels, but i find out that the app switch-user or something like that crashes all the time. I never reinstalled and it seems my problems went away.

Good luck.

---

### Post by azmand01 on 2011-01-19
Hey, i have been having similar problems.This is what I did.

I reinstalled all apps-menus by:

sudo apt-get install gnome-panel
gnome-panel

Also creating another user will recover for that user the original panels, but i find out that the app switch-user or something like that crashes all the time. I never reinstalled and it seems my problems went away.

Good luck.

---

### Post by geo316 on 2011-01-19
Plucky - that did it... interesting how I'm always braced for something long and technical to solve my issue... what a refreshing experience! Thx

---

