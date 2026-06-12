---
title: "Intel 945 no desktop effects or glx and glxinfo crashes"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MattNuzum on 2008-09-24
Hello, a few weeks ago desktop effects stopped working for me. I believe it was the last week of August that this happened (I noticed it the night I was doing a presentation in front of an audience).

I don't know how to report a bug on this type of problem but I've read through some of the forum posts here and will try to give relevant details. Let me know if I'm missing something, my goal is to either a: fix something I've botched or b: file a bug if it's somethign broken. I'd love to get some help from people with more experience in this.

I'm using the intel 945 based chipset. It's been working fine for a while until recently. When I run glxinfo I get:

> glxinfo 
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
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
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault


My xorg log has these errors:

> grep EE /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(EE) intel(0): underrun on pipe B!
(EE) intel(0): underrun on pipe B!


When I try to enable effects I get this error appended to syslog:

> Sep 24 17:32:08 matts-laptop kernel: [ 2562.697847] glxinfo[16985]: segfault at 0 ip 0804ad46 sp bfc43470 error 4 in glxinfo[8048000+5000]
Sep 24 17:32:08 matts-laptop kernel: [ 2562.728576] glxinfo[16988]: segfault at 0 ip 0804ad46 sp bfe19e30 error 4 in glxinfo[8048000+5000]


copmiz --replace does something, crashes and then leaves me with no window borders and a desktop that is hard to use.

My xorg.conf was customized a little by me in order to get the synaptics touchpad working the way I like it but even when I replace it with the nearly empty xorg.conf file (via dpkg-reconfigure -phigh xserver-xorg) I get the same results.

---

### Post by RAOF on 2008-09-24
```

sudo aptitude remove nvidia-glx-173

```

You've obviously been hit by the packaging bug which accidentally pulled in the nvidia drivers at some time in the past.  Since having the nvidia drivers installed breaks 3d for any other driver, you don't get 3d until you've removed them.

---

