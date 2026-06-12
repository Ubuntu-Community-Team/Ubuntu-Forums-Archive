---
title: "Using lightdm but parts of gdm hang around  -- how to fix"
date: 2018-11-11
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2018-11-11
After upgrading from 16.04 to 18.04 I had immediate dislike for GDM and followed the instructions at [https://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/](https://itsfoss.com/switch-gdm-and-lightdm-in-ubuntu-14-04/) to get to LightDM.  In some cases everything worked as planned.  In other cases, see attached screenshot, parts of GDM remain.  See, for example, square box of 9 yellow dots in bottom left corner of screen and lack of the "Search your computer" at the top of the Launcher.  How does one go about fixing this problem.  It survived the upgrade from 18.04 to 18.10.

Thank you,

John

---

### Post by deadflowr on 2018-11-11
Switching display managers does nothing about switching desktop sessions.
You need to choose which session to run at login.

Currently you're running gnome-shell.
I would assume you want to run unity (which has the tooltip line "Search your Computer")
To switch, at login, click on the icon in the username/password box [in the corner of said box] and select unity from the options listed.
Then enter your password to login.

You need to choose unity and not Ubuntu, as Ubuntu is now gnome-shell.

---

### Post by cigtoxdoc on 2018-11-11
Thank you very much.  I had only done part of the job switching to LightDM.  What I forgot to do was sudo apt-get remove gnome-shell ubuntu-gnome-desktop

John

---

### Post by deadflowr on 2018-11-11
You can remove the ubuntu-desktop meta-package, which is now gnome-shell.
unity has a new meta-package ubuntu-unity-desktop.
But since you have unity already, no need to install it if you don't want to.

---

