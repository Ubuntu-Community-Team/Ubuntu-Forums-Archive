---
title: "[SOLVED] Videos playing ?"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2008-09-01
Suddenly, today my videos have stopped playing on intrepid. 

Totem plays them real slow, like 4-5 frames/s

Mplayer, just pauses at the position I reach to, using seekbar.

Anyone else having same issues ?

Mplayer logs:

```

VDec: vo config request - 624 x 336 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.86:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.8571
[swscaler @ 0x89357b0]SwScaler: using unscaled yuv420p -> bgr24 special converter
VO: [xv] 624x336 => 624x336 Planar YV12  [zoom]
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguri
```ng)

This happens with compiz on/off, smplayer, mplayer, totem.

:confused:

---

### Post by vikrant82 on 2008-09-01
It was because, Skype was configured with a sound device which was not letting other applications use the sound device.

Letting skype use default device, made everyone happy.

---

