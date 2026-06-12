---
title: "stop screen blanking"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by th00ht on 2011-11-17
I'm on a multimedia machine and need to switch off screen blanking. I can issue these commands

xset s blank
xset s 0

But I will have to issue these everytime. the Ubuntu team decide to remove the xorg.conf file so cannot put the there. Where would you recommend to put the proper commands to stop screen blanking?

---

### Post by Toz on 2011-11-17
You could create a file called **.xprofile** in your home directory, make it executable, and place the commands in there.

Or you can place the commands in the /etc/X11/xorg.conf.d. What did the commands look like in your old xorg.conf file?

---

