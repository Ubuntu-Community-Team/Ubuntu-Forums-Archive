---
title: "Xrandr detects resolution on monitor wrong"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olavjunior on 2008-10-12
Xrandr (screen resolution applet) always suggest wrong resolution when connecting an external monitor over hdmi. It thinks all widescreen monitor and tvs are 4:3 or 5:4. 

Is there a way to override/force a resolution in xrandr??

---

### Post by wgrant on 2008-10-12
You can use 'xrandr --newmode', using 'cvt' to generate the apropriate mode. I've not got time to walk through this now.

---

### Post by olavjunior on 2008-10-13
Thanks! I'll try google how to fix this with the hints you've given. 

Would appreciate if someone who knows how to do this would spare me some time though :)

EDIT: Thanks for pointing me in that direction. I had previously tried with --addmode, but now I've figured it out. First create newmode, and then add it with addmode. THANKS! It took me 15 min to figure out, and that's nothing compared to the hours I've spent struggling with the screens and resolution applet cause it hasn't given me the right modes on hdmi.

---

### Post by nanog on 2008-10-13
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

If your hardware is not supported by xrandr you are back to manually hacking xorg.conf.

---

### Post by olavjunior on 2008-10-15
I've seen that article. I'll have to look further into it when I get time. I see that the modes doesn't get remembered between boots, so I'll probably have to put something into my xorg.conf yes. 

Any ideas on how to just put more modes into ex TMDS-1 so that every time I connect it these modes will get listed?

---

### Post by Istonian on 2008-10-17
Anyone care to guide me through newmode? I am having problems

---

### Post by olavjunior on 2008-10-19
> **Istonian said:**
> Anyone care to guide me through newmode? I am having problems

use cvt to find the thing to put into new mode, ex cvt 1920 1080
Youll get a output like ```
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

you@ll be interested in this ```
 173.00  1920 2048 2248 2576  1080 1083 1088 1120
```

Youll do ```
xrandr --newmode name  173.00  1920 2048 2248 2576  1080 1083 1088 1120

```

then youll have to do ```
xrandr --addmode TMDS-1 name
``` (if it is to TMDS-1 youll add this mode...

Now youll have this new mode "name" for TMDS-1. Hope this points you in the right direction!

---

### Post by Istonian on 2008-10-19
It says it cant find output TMDS-1 when I try to addmode. What do I do?

---

### Post by olavjunior on 2008-10-19
Is TMDS-1 a output at yours? You have to use the output name of your monitor, so do ```
xrandr
``` to see what it is

---

### Post by Istonian on 2008-10-19
Ok, I have got it done. I did everything right so now how do I change my resolution? Ack, it won't let me change the resolution. Its there but I cant apply. I restarted and the option is gone.

---

### Post by olavjunior on 2008-10-21
It doesn't get saved between reboots no. There might be some way of providing it in xorg.conf, but I don't know this. It's odd you couldn't apply it. Try starting the screen resolution applet after you've added the mode. It's all really done in two simple steps once you know what to do. 

But lately I haven't had problems with xrandr not noticing the monitor with right resolution (maybe an update, or maybe pure luck)

---

