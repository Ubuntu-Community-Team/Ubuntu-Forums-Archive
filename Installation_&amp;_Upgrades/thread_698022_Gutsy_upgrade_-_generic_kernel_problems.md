---
title: "Gutsy upgrade - generic kernel problems"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by Skeorx13 on 2008-02-15
I know there are several threads that relate to this but it seems that mine may be unique. I upgraded to gutsy from feisty and everything went relatively smooth (aside from needing to disconnect both my lcd monitors and plug in a crappy 13" crt just to get the livecd to show on screen... ). When it booted up into the 386 kernel the graphics went into low graphics mode. I updated all synaptic updates and rebooted. Everything went back to normal layout (except no sound. I found a thread on this and fixed alsa so that's working fine). However I noticed that the system monitor was only showing one core of my processor and forgot I had to be in the generic kernel to get smp to work. So I boot into it and I get low graphics mode again. Sound seemed to work but my extra mouse buttons don't work anymore. I had edited them in feisty and they work in the 386 kernel but not now. Nothing I do to the graphics settings will change the layout. I tried the open source nvidia drivers (for my 7600 gt) as well as the proprietary (which I'm using in 386 with no issues) and nothing will change the layout. The monitor selection won't go above 600x800 and won't let me select a secondary monitor. Both of my monitors are mirrored when they should be twinview. I tried to dpkg-reconfigure but it borked my xserver for both kernels and I had to reload the backup manually in recovery mode. Does anyone know why merely using the smp kernel would completely screw my xserver? Whenever I boot back into 386 kernel I have no problems. What the crap is going on???

---

