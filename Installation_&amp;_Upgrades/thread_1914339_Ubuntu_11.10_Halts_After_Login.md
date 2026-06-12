---
title: "Ubuntu 11.10 Halts After Login"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by twiistedkaos on 2012-01-24
I've been quite puzzled as 11.04 worked perfectly fine. I've seen a lot of people having "slow" issues with 11.10. Here's what's going on.

Login -> Unity pops up -> CPU Halts for 10 mins

After this 10min halt, everything works fine(Unity runs perfectly smooth). Logs aren't showing any errors. 

I tweaked Compiz by switching of sync to vb, switched off sync refresh rate, change textures to fast. Still does the same thing.  I really don't think it's a compiz / unity issue. It seems that something is just taking 100% CPU for those 10mins and after that everything is cool.

**/usr/lib/nux/unity_support_test -p**
```
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GME x86/MMX/SSE2
OpenGL version string:  1.4 Mesa 7.11

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

Unity 3D supported:       yes

```

System Specs:
HP Netbook
1GB Ram
Intel® 945GME x86/MMX/SSE2

---

### Post by twiistedkaos on 2012-01-24
Seems like the updated kernels(3.0) fixed this. updates ftw!

---

