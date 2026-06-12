---
title: "Openbox Problems"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by The Real Dave on 2010-03-30
I'm loving Lucid so far, the only thing I've had a problem with is running Openbox on top. It had been working fine, but I updated a few times, and now, when going into "Openbox Session", everything in the autostart.sh runs, but Openbox doesn't. 

Anyone else having the same problem?

autostart.sh

```
#! /bin/bash

###Openbox Startup Script###

#Key ring - Allow nm-applet to connect w/o passwd prompt
gnome-keyring-daemon &

#Tint2 Taskbar
tint2 &

#Network Manager
nm-applet &

#Nitrogen Wallpaper Manger
(sleep 2 && nitrogen --restore) &

#Empathy IM
#empathy &

# Uncomment to enable system updates at boot
#(sleep 180s && system-update) &

#Conky
conky -c .conkyrc

```

If I add "openbox" to the autostart.sh, openbox starts, but nothing else in the autostart.sh runs. Anyone know where I can start looking for the source of the problem? >.<

---

### Post by eriqjaffe on 2010-03-30
I think you need to add an ampersand after the conky command:

```
#Conky
conky -c .conkyrc &
```

---

### Post by The Real Dave on 2010-03-31
Cheers mate :) That solved it. And here was me blaming Lucid :(

---

