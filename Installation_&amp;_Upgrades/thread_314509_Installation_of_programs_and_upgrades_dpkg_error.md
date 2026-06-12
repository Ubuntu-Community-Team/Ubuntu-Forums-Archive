---
title: "Installation of programs and upgrades dpkg error"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by dan_seguin90 on 2006-12-07
Hi when i try to install using the add/remove sofftware device or just the standard upgrade device i am always gettin this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

then when i open a terminal and type what it says to type then it errors and says:

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

Can anyone help because i currently cant install anything.

Dan

---

### Post by meng on 2006-12-07
Make sure that Add/Remove software isn't running at the time you enter the command dpkg --configure -a. That means you shouldn't be running Synaptic package manager either.

And I would recommend you type
sudo dpkg --configure -a
instead, and enter your user password when prompted. Then tell us what happens.

---

### Post by dan_seguin90 on 2006-12-07
thx a bunch turns out i wasnt running teh dpkg long enough... now it works

---

