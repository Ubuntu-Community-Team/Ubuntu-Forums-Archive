---
title: "Only detecting dual monitor (HDMI) during boot"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by nosredna on 2012-04-14
This is a very odd problem I've gotten into. When I boot my laptop with a second monitor connected through HDMI, it shows a clone of the image on my laptop (a flashing underscore, that is) but when it arrives at the login screen my TV suddenly says "No Signal" and when I go to *Preferences -> Monitor Settings* there is no second monitor. 

Also, I have another problem. I would love to run XBMC and use the magnificent GUI on my TV (which is why I'm trying to use dual screens in the first place) but when I try to load XBMC it says: **XBMC needs hardware accelerated OpenGL rendering. Install an appropriate graphics driver**. I don't have any driver install as of now that I'm aware of. Choosing ATI/AMD proprietary FGLRX graphics driver in **Preferences -> Additional Drivers** didn't resolve the XBMC problem nor the dual monitor problem.

The laptop has ATI Mobility Radeon HD 4330.

Any suggestions?

---

### Post by nosredna on 2012-04-14
Gah. I must've been tired when I started this thread. Totally wrong forum category.

Mod, please move to correct category.

---

### Post by nosredna on 2012-04-15
Ok, I'll gill you a absolutely awesome guitar solo: :guitar:

Maybe someone who's into speed metal will answer, I don't know. I'm just frustrated. :p

---

### Post by nosredna on 2012-04-15
Not much I can do bot Google around, but I don't find any appropriate guides. I've managed to install xserver-xorg-core at least, and now I can access XBMC. But HDMI is still not being recognized. I downloaded this tool called disper and when I run **disper -l** this is what I get:

display LVDS1: LVDS1
 resolutions: 640x480, 800x600, 1024x768, 1360x768, 1366x768

As you can see only one monitor is in this list, even though I have my TV connected through HDMI and it works for about 10 seconds during startup (showing blinking underscore than returns to "No Signal").

So, how do I active this TV and why isn't it listed under "Monitor Settings" or in disper?

---

### Post by marinara on 2012-04-15
did you check amd catalyst control center?

---

### Post by cortman on 2012-04-15
Hi, please post the output of

```
xrandr
```

And if you want, try a quick fix-

```
xrandr --output HDMI1 --auto
```

---

### Post by nosredna on 2012-05-07
> **cortman said:**
> Hi, please post the output of

```
xrandr
```

And if you want, try a quick fix-

```
xrandr --output HDMI1 --auto
```
I haven't had an internet connection for some time, so here comes my 3 week old answer:

Like I said earlier the computer doesn't detect the TV at all:

[B]nosredna@nosredna-acer:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

nosredna@nosredna-acer:~$ xrandr --output HDMI1 --auto
warning: output HDMI1 not found; ignoring[/B]

---

### Post by cortman on 2012-05-07
> **nosredna said:**
> 
[B]nosredna@nosredna-acer:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


This would point to a graphics driver problem. Are you sure you're using the fglrx proprietary ATI drivers? Are you using the catalyst control center as was advised earlier?
If so, it could be that it simply doesn't work. ATI cards have historically given problems, and [this thread]("http://ubuntuforums.org/archive/index.php/t-1288722.html") doesn't seem very optimistic.

---

