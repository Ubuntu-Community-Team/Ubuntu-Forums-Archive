---
title: "Compiz problems (nightmares)"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by kdr on 2008-05-01
Hello community,
I have a problem in running Compiz. Really, this time I do not know how to solve it so I hope to find a way in this forum..

Setup:
OS: Hardy Heron 8.04 desktop ed. upgraded from Gutsy 
HW: lenovo T60 laptop -  ATI MOBILITY FireGL V5200

Problem:
After the login, **in the moment that compiz kicks in my screen goes white (well, actually it is very light gray). No desktop. Pure gray**.

I reinstalled drivers with envy and manually. I also  reinstalled compiz. No help. 

some info:
```

kdr@kdr:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5200
OpenGL version string: 2.1.7415 FireGL Release

```

and

```

kdr@kdr:~$ glxinfo |grep direct
direct rendering: Yes

```

Therefore the ATI drivers are actually working in Xorg.

Now in order to debug this compiz I run a simple Gnome session and then from terminal I run
```

kdr@kdr:~$ /usr/bin/compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c4 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

```

and goes 'gray screen', then I strike CTRL+C and I come back in non-compiz world.

Any idea about how to solve it? It is soooo frustrating :mad:

Cheers

---

### Post by kdr on 2008-05-02
bump

---

