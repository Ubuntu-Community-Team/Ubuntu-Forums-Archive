---
title: "Xserver not found ?"
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by ulefr01 on 2004-10-21
done install of warty-release-install-amd64 of 20 okt 2004
X is not starting, there is no X in /usr/X11R6/bin
the log in /var/log/gdm is showing me :
GDM: Xserver not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or edit /etc/gdm/gdm.conf to point to the right place.
Can you help ?

---

### Post by daniels on 2004-10-22
Do you have /usr/X11R6/bin/XFree86?  What does dpkg -l xserver-xfree86 say?  What went wrong during the install?

---

### Post by ulefr01 on 2004-10-22
dpkg -L xserver-xfree86
says that xserver-xfree86 was not yet installed
----
after setting the sources.list
i have done now :
apt-get update
apt-get install xserver-xfree86
apt-get install xserver-common     --  (maybe together with xserver-xfree86)
apt-get install xfonts-base
-----
startx is working now; 
redone reboot ; gdm is ok now
Free86.log is giving me an error on 'v4l' and 'synaptics' not found
this seems to be a bug in the installation
-----
there is still no sound,  and no wireless connection with router

---

