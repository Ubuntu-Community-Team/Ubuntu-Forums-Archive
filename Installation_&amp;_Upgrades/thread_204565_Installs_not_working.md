---
title: "Installs not working"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by .Maleficus. on 2006-06-27
For some reason, none of the programs I just installed will run.  I installed Blender, Stellarium and Warsow, and none of them will run.  Other programs that I installed at the same time work, like Kino, Audacity and digiKam, but the others don't.  Thanks for any help!

---

### Post by taurus on 2006-06-27
I assume you click on them and nothing happens!  Try to run them from a terminal to see what the error message is.  Open a terminal by clicking Applications -> Accessories -> Terminal and type
```

blender <-- for blender
stellariun <-- for stellarium

```
Then, paste the error messages here if you choose...

---

### Post by .Maleficus. on 2006-06-27
This is what I get.

andy@andy-desktop:~$ blender
Using Python version 2.4
[COLOR="Red"]Xlib:  extension "GLX" missing on display ":0.0".[/COLOR]
[COLOR="Red"]ERROR: Unable to open Blender window[/COLOR]
andy@andy-desktop:~$ stellarium

    -----------------------------------------
    | ## ### ### #   #   ### ###  #  # # # #|
    | #   #  ##  #   #   ### ##   #  # # ###|
    |##   #  ### ### ### # # # #  #  ### # #|
    |                       Stellarium 0.7.1|
    -----------------------------------------

Copyright (C) 2000-2005 Fabien Chereau et al.

Please check last version and send bug report & comments
on stellarium web page : [http://www.stellarium.org](http://www.stellarium.org)

Loading configuration file /home/andy/.stellarium/config.ini ...
[COLOR="Red"]Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
sdl: Couldn't set 1024x768 video mode (Couldn't find matching GLX visual), retrying with stencil size 0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
sdl: Couldn't set 1024x768 video mode: Couldn't find matching GLX visual![/COLOR]
andy@andy-desktop:~$

It seems that this GLX thing is what is keeping me from opening both of those programs.  So now my question is, what is GLX, and how do I install that?

---

### Post by taurus on 2006-06-27
What video card do you have and did you install a driver for it?

---

### Post by .Maleficus. on 2006-06-27
Never mind, I did some searching, found out how to install the XGL drivers, and everything is up and running.

---

