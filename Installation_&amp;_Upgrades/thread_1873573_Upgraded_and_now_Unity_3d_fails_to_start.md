---
title: "Upgraded and now Unity 3d fails to start"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by ibussieres on 2011-11-01
So, I log in with unity (3d) and :

```
echo $DESKTOP_SESSION
```

prints : 
ubuntu-2d

I've followed these steps very carefully : 
[http://ubuntuforums.org/showthread.php?t=1856053](http://ubuntuforums.org/showthread.php?t=1856053)

```
/usr/lib/nux/unity_support_test -p 
```

prints :
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context

```
DISPLAY=:0.0 /usr/bin/glxgears
```

prints:
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

It might be important to note that before updating, I was indeed running unity3d. 

Oh, also, I am running Ubuntu 11.10 -> Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Cheers.

**Edit: **
It really looks as if my driver is messed up. When I run jockey-gtk, I get absolutely no drivers listed. Other than this dialog, how can I reinstall the drivers ?

---

