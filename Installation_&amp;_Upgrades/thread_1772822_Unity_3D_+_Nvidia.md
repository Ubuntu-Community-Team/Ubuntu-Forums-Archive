---
title: "Unity 3D + Nvidia"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2011-06-01
Here is a summary of my status with Unity:

Ubuntu 10.04: glxgears = 25K frames per second
Ubuntu 10.10: glxgears = 27K 
Ubuntu 11.04 classic: glxgears = 8K
Ubuntu 11.04 Unity 2D: glxgears = 8K
Ubuntu 11.04 Unity 3D: glxgears locks the desktop. Only recovery is to power off.

My GPU: nVidia Corporation GF106 [GeForce 450 GTS] (rev a1)

From the forums here I see millions of problems with compiz and Nvidia. There does not seem to be a clear solution. I can use Unity 2D well enough for now, and I hope someone is working on this.

---

### Post by kornelix on 2011-06-09
Not that anyone is listening, but I found a partial solution after reading a few thousand launchpad bug reports about Nvidia, Compiz, and Unity.

Using the Nvidia settings tool, set "Sync to VBlank" = ON in two different places: 
   XServer XVideo Settings
   Open GL Settings

After doing this, glxgears no longer freezes my desktop. Another graphic intensive application also no longer freezes the desktop, but it runs very jerky and when killed needs a long, long time to die. It runs fine on Ubuntu 10.10.

---

