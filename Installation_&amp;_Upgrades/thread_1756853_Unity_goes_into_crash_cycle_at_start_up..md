---
title: "Unity goes into crash cycle at start up."
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by Makurosu on 2011-05-12
I'm sure other people must be experiencing this, but I haven't been able to locate another post with these symptoms.  I apologize if someone has.

I've installed Ubuntu 11.04 with Unity on two other machines without a hitch.  A third machine unfortunately requires the nvidia-96 driver and has to use the "experimental" driver, even though it worked fine in Maverick.

My fourth machine was upgraded to 11.04 from Maverick, but when it booted the first time into Unity, it would start to display a window, crash, try again, crash, and continue in that way in an endless cycle.  The left and top bars never appeared.

I happen to like Unity, so I wiped the hard drive and installed 11.04 fresh.  When it booted into Unity, the same thing occurred.

I get the following with the Unity support test:

> sam@Sam:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: Quadro FX 500/FX 600/AGP/SSE/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes


It works fine in Ubuntu classic, but I would prefer to use Unity as I like it.  I tried the live CD, but that comes up in Ubuntu classic.

I tried doing "unity --reset" and a few of the other tips in the sticky note without success, but I don't think any of those options are going to work, because my system passes the support test and it's doing it right off the install.

Is there anything I need to do?

---

