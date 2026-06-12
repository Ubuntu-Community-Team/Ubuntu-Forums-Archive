---
title: "Ati x1950+Ubuntu+3D, cant get to work"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by fresch1 on 2007-02-23
Hi..

I just got Ubuntu to work with the new ATI driver.
But when i installed Beryl xgl (i followed this guide [http://lhansen.blogspot.com/2006/10/...untu-edgy.html](http://lhansen.blogspot.com/2006/10/...untu-edgy.html))
Then i reboot, and select the session "Xgl".

The background becomes black and white with full of small dots and a white cross instead of the cursor, for 1 second, and then the normal desktop appears, and i cant see any xgl or beryl stuff, plus its suddently extremelyt slow (Resizeing windows ect. is extremely slow)...

I have ATI Radeon x1950pro, and the 34.8 Ati Driver installed.

Afterwards i tried this guide:

[http://wiki.beryl-project.org/wiki/I...dgy_with_AIGLX](http://wiki.beryl-project.org/wiki/I...dgy_with_AIGLX)

to the point where i have to write:

 sudo /etc/init.d/gdm restart

Then this screen appears and freezes, and the colour becomes all wierd (i have the wallpaper with the bush and fireflies as wallpaper)


[IMG]http://www.muwo.dk/up/upload/DSC00238.jpg[/IMG]


I Tried to reset my pc, and Ubuntu booted fine, but without any 3D effects.
Aftewards i tried to enter fglrxinfo in the terminal.
This is what i got:


```
frederik@Frederik:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

I tried ALL day to get this to work, but i still cant get i to work. :(

---

### Post by r4ik on 2007-02-23
Here's someone who found a solution,

[http://www.ubuntuforums.org/showthread.php?t=368728](http://www.ubuntuforums.org/showthread.php?t=368728)

Good luck !

---

### Post by fresch1 on 2007-02-23
> **r4ik said:**
> Here's someone who found a solution,

[http://www.ubuntuforums.org/showthread.php?t=368728](http://www.ubuntuforums.org/showthread.php?t=368728)

Good luck !

Thanks.
I Used envy at got so far:

Now it seems to work on the paper, 

```
frederik@Frederik:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

But i still cant get the 3D to work :(
I tried the glxgears command and it works fine.
But still cant get xgl, or beryl to work with 3d.

---

