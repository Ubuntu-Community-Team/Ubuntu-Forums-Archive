---
title: "panel is flickering"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by davidself1001 on 2011-04-30
Got past a grub/boot problem and now when my desktop comes up the mouse and the panels are flickering and not usable.  i still have the old panel at the bottom flickering but i appear to have a panel at the top flickering.  i don't seem to have unity.  i have my home dir on a separate drive could that have to do with the problem?

---

### Post by Riskexas on 2011-04-30
i have that too i dont understand why they released 11.4 that is bad???:confused::confused::confused:

---

### Post by sikander3786 on 2011-04-30
Which version of Nvidia drivers is installed? We need to see the output of this command please.

```
/usr/lib/nux/unity_support_test -p
```

And I have installed Unity on 5 different machines and all are working just fine. Didn't ever need to tweak any settings. Yes it is not working on some hardware but how can the developers or volunteers test all the hardware on earth?

---

### Post by davidself1001 on 2011-04-30
I don't have a directory called nux in the /usr/lib dir

---

### Post by davidself1001 on 2011-04-30
Do i have a problem with missing files?  Is there another way to verify my graphics?  Where is the Unity program loaded?  Help would be greatly appreciated.  I dead in the water and i hate this damned Windows machine.

---

### Post by sikander3786 on 2011-04-30
Please post the output of this command first.

```
cat /etc/lsb-release
```

---

### Post by jbp006 on 2011-04-30
I'm having the same issue after upgrading from 10.10 to 11.04

This is the result from running /usr/lib/nux/unity_support_test -p


OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2/3DNOW!
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

---

### Post by davidself1001 on 2011-04-30
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

---

### Post by sikander3786 on 2011-04-30
I was just wondering why isn't there the 'nux' directory.

Anyways, press the <super> (window log) key and type 'additional'. Open up 'Additional Drivers' and see which version of drivers is installed. Removal and re-install might also help.

---

### Post by javaholic on 2011-04-30
I'm having a similar problem I think.  It only happens when I try and log into the Ubuntu classic session though.

My Ubuntu session works out fine with unity.  It would be nice to get the Ubuntu classic to work now.

I can report similar results to the debugging tests that have already been requested.

---

