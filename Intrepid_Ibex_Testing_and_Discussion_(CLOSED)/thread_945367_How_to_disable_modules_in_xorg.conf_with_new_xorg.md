---
title: "How to disable modules in xorg.conf with new xorg"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sokopok on 2008-10-12
Anybody know how to disable modules in the new xorg setup?
I'm running Intrepid on a Dell laptop with NVidia 8400M, so no way to get off the console into th gui. I tried lots of stuff to circumvent the NVidia driver problem, but X refuses not to load the glx and related modules.

example xorg.conf section:
```
Section "Module"
  Disable "glx"
EndSection
```results in (nothing really). in /var/log/Xorg.0.log:
```
(WW) "glx"will not be loaded .....
...
(II) "glx" will be loaded even though the default is to disable it.
```This happens for every and any module I try to disable. I wouldn't mind working on a VGA  setup for now, I just don't want to reinstall (which won't help), and certainly not downgrade to 8.04

Any suggestions?


Edit.
One more thing: doesn't matter if I use the nv driver or the nvidia driver they both don't work. nv gives me a black screen, nvidia a funky black and white striped design

---

### Post by sokopok on 2008-10-18
I'm working with the VESA driver now, so not completely broken anymore. But I'm still very curious about this issue. Anybody out there who can shed some light on this issue?

---

