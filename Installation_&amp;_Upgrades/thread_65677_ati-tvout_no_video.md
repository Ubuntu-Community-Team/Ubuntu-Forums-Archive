---
title: "ati-tvout no video"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by jesperf on 2005-09-14
After alot of trouble i finally got my tv-out on ATI Radeon 6900 to work

Just one catch, it does'nt show film.
My fglrxinfo:

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.4893 (X4.3.0-8.10.19)

Plus now i can't change screen resolution.
The error message says it does'nt support the XrandR -extension

Any ideas?

Thanks alot

oh, maby I should say i'm new to linux

---

### Post by mlomker on 2005-09-14
[QUOTE=jesperf]Just one catch, it does'nt show film.
[/QUOTE]

I've read that max resolution is 1024x768 when you have video output enabled.  What player are you using for films?  Do you mean all DVD's?

You are running an older driver as well.  You can consider [upgrading](http://www.ubuntuforums.org/showthread.php?p=348911) to the latest version.

---

### Post by jesperf on 2005-09-15
yepp, all films. svid divx dvds everyting.
will try to upgrade driver and see if that helps

---

### Post by joebanana on 2007-10-28
You probably have to choose your TV as primary display in order for video to work. I have never managed to stream video on both screens at the same time, only on one. I dont know where to set this though.

---

### Post by jonij on 2008-02-25
i have an ati 9250 , and cannot make the tvout work

How did you install the graphic card?

Regards.

---

### Post by martin_swain on 2008-07-01
> **jesperf said:**
> yepp, all films. svid divx dvds everyting.
will try to upgrade driver and see if that helps

Hi,
  I have a similar setup, & encountered the same problem. I managed to get it working by using the mplayer program and setting the driver to "gl2". A couple other drivers also produced video output, but fullscreen only seems to work with the gl2 driver.

Cheers,

Martin

---

