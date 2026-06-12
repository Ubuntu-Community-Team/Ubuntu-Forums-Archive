---
title: "Changing refresh rate on boot"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Gangus on 2007-10-22
Hi guys, 
   I've just installed Ubuntu 7.10 and even though the live disk worked fine, automatically hit the nv drivers for my card and detected my monitor fine, upon install theis was no longer the case, and it wants to run in VESA mode, at a refresh rate that my old CRT monitor doesn't handle (85 Hz) when i want 60 to 70 on this (it's an ancient 21" ViewSonic G810)

My question is this: what is the file containing the video information, how can i edit it as i'm unable to boot to X, and what should i edit within it?

My apologies if this is a really nubbish question, i'm just needing a gentle prod in the right direction and i'll pick up what i can from there :)

---

### Post by ajgreeny on 2007-10-22
When you get to the console, login with your username and password which you set up when installing this will get you to a terminal with a prompt like this:-
username @computername:~$
At that type in ```
sudo dpkg-reconfigure xserver-xorg
``` and then enter your password when asked.  You will now go through a series of screens where you can chose various configurations for your system.  Accept the defaults until you get to the video/graphics entries and here you can select the ones that fit your system best.  Hopefully at the end you will get a system that on reboot (sudo shutdown -r now) will get you into a gui.  If not come back again and we will try to help.

The file with all the configuration is **/etc/X11/xorg.conf**, but you can only edit it as root, and you should always keep a copy before doing any editing as it is easy to get it all wrong and mess up your graphics in particular, but also your mouse input or keyboard configurations.

Good luck!

---

