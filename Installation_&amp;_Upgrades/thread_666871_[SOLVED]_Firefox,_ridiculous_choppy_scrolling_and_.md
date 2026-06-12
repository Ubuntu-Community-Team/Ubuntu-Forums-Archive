---
title: "[SOLVED] Firefox, ridiculous choppy scrolling and flickering video...."
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by Gredge on 2008-01-13
I've recently installed Gutsy on my system.  I am having a problem with firefox having really chopping scrolling, and full screen videos (of any format) are choppy and flickering as well.

I am running a Pentium D 2.6, 2gb Ram, and Ati Radeon X1950.

At first I installed XGL, and then used Envy to get my drivers.  Later on I realized this was a little messed up so I removed XGL and re-installed all drivers using Envy. Compiz runs great with Emerald etc, but I still have choppy scrolling on firefox and on full screen vid's.

Here are some of my outputs:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7170 Release

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

The weird thing is that if I were to default back to the Vesa driver, all firefox scrolling and vid's run smooth. Any ideas????

---

### Post by Ozor Mox on 2008-01-18
Using the same driver with an ATI Radeon X800, I get choppy scrolling in Firefox and flickering on things like screensavers and games if I have Compiz enabled. Disabling it fixes the problems for me. Have you tried that?

---

### Post by Gredge on 2008-01-18
Yes actually I've figured out that when compiz is not running, everything is perfectly smooth.  However now I will be loosing all of my eye-candy like cube, emerald, and awn. It's not a big deal except for awn (I reallllllly like it).

Is there any way to run awn (or any other eye candy) without running compiz?

Thanks for the response btw.

---

### Post by Gredge on 2008-01-18
Okay I got it. Keep the driver, keep awn, ditch Compiz. I followed the instructions [here]("http://www.cypherbios.org/blog/?p=43&language=en") to use a different window manager. Sure I'm losing the cube but I'm getting back my smooth environment....

SOLVED.

---

