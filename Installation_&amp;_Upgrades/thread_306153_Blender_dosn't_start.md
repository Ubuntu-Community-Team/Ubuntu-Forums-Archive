---
title: "Blender dosn't start"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by robytex on 2006-11-24
I've installed succesfully Blender3D from the repository.
I try to start it from terminal:

robytex@robytex-desktop:~$ blender-bin
Compiled with Python version 2.4.
Checking for installed Python... got it!
libGL warning: 3D driver claims to not support visual 0x4b

and nothing happen!
Why? what can I do?
TIA
Roby

---

### Post by burwaco on 2006-11-25
I installed blender with apt-get a while ago, mean time I upgraded from dapper to edgy and fooled around with kernel packages from ubuntu and kernel.org.

I have a  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]" card and I just noticed that I have the same libGL warning: 3D driver claims to not support visual 0x4b problem.

Blender works fine...

```

burwaco@box:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.4.
Checking for installed Python... got it!
**[COLOR="Red"]libGL warning: 3D driver claims to not support visual 0x4b[/COLOR]**
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 412
Software fallback:ctx->Line.SmoothFlag
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 409
Software fallback:ctx->Line.StippleFlag
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_vertexprog.c function t_dst_index line 184
Unknown output 13
***************************************************************************

Blender quit

```

---

