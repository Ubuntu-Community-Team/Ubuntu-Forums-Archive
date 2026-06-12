---
title: "&quot;Desktop Effects Could not be Enabled&quot; Help!"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mr, Bean on 2009-10-22
Hello,

I have been using Ubuntu for a couple of months and I haven't really had any major problems until today, 

Im using Ubuntu 9.10 Beta release and its great. I've been using it a while with desktop effects working fine .Today I noticed that they had been disabled I tried to turn them on again and I see the screen flickering and then the error message appears "Desktop effects could not be enabled".

I do not know what to do, Please post any ideas that you think might help.

I'll put in the Output when i type "compiz" in the terminal (it might be useful to someone)

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```Thanks In Advance :)

---

### Post by Woody1987 on 2009-10-22
What graphics card do you have?

---

### Post by Mr, Bean on 2009-10-23
My Laptop has "UMA integrated graphics card" (I am using an [Advent 5431]("http://www.dealgiant.co.uk/advent-5431-laptop-review-performance-specifications/"))

---

