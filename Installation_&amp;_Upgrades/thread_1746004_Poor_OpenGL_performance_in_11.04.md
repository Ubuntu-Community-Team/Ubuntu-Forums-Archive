---
title: "Poor OpenGL performance in 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Chris on 2011-05-01
I'm using a clean new install of 11.04.  Basically: install Ubuntu Desktop, install nVidia restricted drivers (current), then testing.

If I do this in 10.10 glxgears runs at 21000+ FPS and other OpenGL apps run at full speed.

Doing the exact same thing with the same setup in 11.04 results in glxgears running at 3000 FPS and other OpenGL app similarly slowed down.

Unity actually screws up everything if I try to run other OpenGL apps (the whole screen freezes) so I'm only testing with Ubuntu Desktop Classic (no effects).  So there should be no conflicts since the desktop should not be using OpenGL at all with this setting.

Something seems broken here.  Any ideas?  Could the console framebuffer be the culprit?  I have tried booting with various combinations of "nofb fb=false vga=normal nosetmode" and it made no difference.  I do notice that even when disabling all of that the console fonts change right when X.org starts so something seems fishy there.  I know in the past there have been problems with the console framebuffer and nVidia.  10.10 does not change the console at all when running nVidia drivers.

---

### Post by khelben1979 on 2011-05-01
Are you using the same version of the nVidia drivers as you did with the previous version of Ubuntu?

---

### Post by Chris on 2011-05-01
10.10 uses the 260.xxx series while 11.04 uses 270.xxx.

However, installing the 270.xxx series makes no difference in 10.10, it is still much higher performance.  Anything is possible but I don't think it's a driver issue.

Besides, in the last 10+ years I have been running nVidia drivers I have never seen a newer version perform worse than the old version.

---

### Post by salvosq on 2011-05-04
me too, my opengl software is performing bad under unity, while under the classic desktop with no effects all is good

---

### Post by khelben1979 on 2011-05-06
What nVidia card are you using for this?

---

### Post by Chris on 2011-05-07
I'm using an EVGA 8800 GTS 512 (the G92 card).  I have tried with and without an xorg.conf, it makes no difference (I'm testing the same config in 10.10 and 11.04 anyway).

I played with it some this morning and found that it's metacity that's causing most of the slowdown.  If I run openbox or other window manager I get almost normal performance.  It's still about 10% slower than 10.10, but not an order of magnitude like when running metacity.

I have no idea what metacity could be doing.  Something is very wrong here.

---

### Post by linuxftw3 on 2011-05-07
> **chris said:**
> i'm using a clean new install of 11.04.  Basically: Install ubuntu desktop, install nvidia restricted drivers (current), then testing.

If i do this in 10.10 glxgears runs at 21000+ fps and other opengl apps run at full speed.

Doing the exact same thing with the same setup in 11.04 results in glxgears running at 3000 fps and other opengl app similarly slowed down.

Unity actually screws up everything if i try to run other opengl apps (the whole screen freezes) so i'm only testing with ubuntu desktop classic (no effects).  So there should be no conflicts since the desktop should not be using opengl at all with this setting.

Something seems broken here.  Any ideas?  Could the console framebuffer be the culprit?  I have tried booting with various combinations of "nofb fb=false vga=normal nosetmode" and it made no difference.  I do notice that even when disabling all of that the console fonts change right when x.org starts so something seems fishy there.  I know in the past there have been problems with the console framebuffer and nvidia.  10.10 does not change the console at all when running nvidia drivers.


use maverick ! Natty sucks!

---

### Post by khelben1979 on 2011-05-08
If metacity is the problem, avoid it, problem solved. And if wanting to know more about how it works: ```
man metacity
```

---

### Post by nerdy_kid on 2011-05-08
Maybe this will help:

install and open up ccsm, go to the "composite" section and hit "unredirect fullscreen windows"  then try a full screen opengl app and see if the fps is better.

---

### Post by Chris on 2011-05-09
> **khelben1979 said:**
> If metacity is the problem, avoid it, problem solved.

Sure, ignoring bugs is probably the best way to fix them.  ;)  Besides, getting rid of metacity means getting rid of all the default Ubuntu theme stuff so you end up with a mismatched looking and confusing to use system.

> **nerdy_kid said:**
> Maybe this will help:

install and open up ccsm, go to the "composite" section and hit "unredirect fullscreen windows"  then try a full screen opengl app and see if the fps is better.

I'm not running compiz.  If I were then I wouldn't be running metacity.

---

### Post by khelben1979 on 2011-05-09
> **Chris said:**
> Sure, ignoring bugs is probably the best way to fix them.  ;)  Besides, getting rid of metacity means getting rid of all the default Ubuntu theme stuff so you end up with a mismatched looking and confusing to use system.

Good point! I didn't realize it worked that way. :)

---

### Post by nerdy_kid on 2011-05-09
> **Chris said:**
> Sure, ignoring bugs is probably the best way to fix them.  ;)  Besides, getting rid of metacity means getting rid of all the default Ubuntu theme stuff so you end up with a mismatched looking and confusing to use system.



I'm not running compiz.  If I were then I wouldn't be running metacity.

Sorry, I thought you meant the metacity decorator, which does run with compiz.

---

### Post by erandd on 2011-05-14
me too
i am using an on board screen card
some hardware info
Asus board
**Computer**
Processor	4x Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
Memory	1943MB (1084MB used)
Operating System	Ubuntu 11.04

**Display**
Resolution	1024x768 pixels
OpenGL Renderer	Mesa DRI Intel(R) Sandybridge Desktop GEM 20100330 DEVELOPMENT x86/MMX/SSE2
X11 Vendor	The X.Org Foundation

**Display**
Resolution	1024x768 pixels
Vendor	The X.Org Foundation
Version	1.10.1

**OpenGL**
Vendor	Tungsten Graphics, Inc
Renderer	Mesa DRI Intel(R) Sandybridge Desktop GEM 20100330 DEVELOPMENT x86/MMX/SSE2
Version	2.1 Mesa 7.10.2
Direct Rendering	Yes

---

### Post by Geoff Wilson on 2011-07-10
I significantly improved my performance by going into compiz settings manager, and unchecking "Sync to VBlank" in the OpenGL settings.

If you have an ATI card you can turn V-Sync back on in the Catalyst Control Centre and performance stays about the same, there's an option called "Tear Free Desktop"

---

