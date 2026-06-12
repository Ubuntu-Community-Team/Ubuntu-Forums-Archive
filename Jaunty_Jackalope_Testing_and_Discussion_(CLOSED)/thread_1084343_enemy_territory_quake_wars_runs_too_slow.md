---
title: "enemy territory quake wars runs too slow"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Cresho on 2009-03-01
Hello!

pc spec
-----------
8800gt
amd 6400 dual core black edition
s-ata drives
2gb ddr800
running jaunty jackelope 32bit alpha 5

Like the title says: it runs too slow.  Im playing the game and in the middle of a firefight, it drops down to like 3 fps.  with maxed or bare minimum graphics.

this is the script I use to launch the thing....its old but it works.
```
#!/bin/bash
#Script Compiz/on/off
#killall awn
# Compiz off;
killall compiz.real &
metacity --replace &


#amixer -q set "Line Capture" 0% mute &
#amixer -q set "Synth Capture" 0% mute &
#amixer -q set "IEC958 Optical Capture" 0% mute &
#amixer -q set "Line2 Capture" 0% mute &
#amixer -q set "PCM Capture" 0% mute &
#amixer -q set "Aux2 Capture" 0% mute &
#amixer -q set "Analog Mix Capture Volume" 0% mute &
#amixer -q set "Audigy CD Capture" 0% mute &
sleep 4 && amixer -q set "Mic Capture" 100% unmute;


#run game;
cd ~/Installed_Programs/etqw
sleep 1 && ./etqw +set sys_VideoRam 512;

#Compiz on;
compiz --replace &
metacity --replace &

#sleep 4 && amixer -q set "Mic Capture" 0% mute;
#killall awn


#sleep 10 && awn
#sleep 3 && killall awn
#sleep 4 && awn

```

btw, it runs flawlessly in hardy heron.

---

### Post by Cresho on 2009-03-08
well, I just figured out that jaunty does not have a kernel for real time yet.  Ill wait and see if the new one has a  Ingo Molnar's full real time preemption patch for etqw gameplay.  I tried the linux-rt but would not boot unless I used the working kernel.

---

