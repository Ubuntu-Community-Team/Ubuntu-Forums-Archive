---
title: "Intel GMA950 and 3945ABG Troubles"
date: 2008-12-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MoridinBG on 2008-12-14
Installation is on HP tc4400 TabletPC.

I update my working Intrepid installation to the current Jaunty, the same way I did with Hardy->Intrepid.

The first thing  I noticed is that my dedicated audio buttons (volume up, down and mute) work again, which they stopped doing when I finally did a clean install of Hardy release.

But my Intel graphics got screwed.
```
fester@fester-tabletpc:~$ glxinfo | grep renderer
OpenGL renderer string: Software Rasterizer

```
In /var/log/Xorg.0.log everything seems normal, the driver is loaded and initialized, the chipset is recognised, DRI is enabled.

I tried reconfigureing xorg.conf, and nothing.

glxgears run at ~150fps, and Compiz is unusable.




The other issue is with the wireless card and the kill switch. The card is Mini PCI-E 3945ABG.
In the release notes  of Intrepid it was stated that currently there are some problems with some configurations, that would be fixed. And yet, with 2.6.28-2-generic the problem is still here. If I boot with kill switch disabled I am unable to enable the wifi card. And if I disable it, while it is running, then most of the time I can't reenable it.

---

### Post by ronacc on 2008-12-14
see this thread for help with your graphics ,
[http://ubuntuforums.org/showthread.php?t=998754](http://ubuntuforums.org/showthread.php?t=998754)

---

### Post by mewithafez on 2008-12-14
> **MoridinBG said:**
> Installation is on HP tc4400 TabletPC.

The other issue is with the wireless card and the kill switch. The card is Mini PCI-E 3945ABG.
In the release notes  of Intrepid it was stated that currently there are some problems with some configurations, that would be fixed. And yet, with 2.6.28-2-generic the problem is still here. If I boot with kill switch disabled I am unable to enable the wifi card. And if I disable it, while it is running, then most of the time I can't reenable it.

Just checking, as I am running the same 3945ABG wifi, it works if enabled under jaunty BUT if you turn it off while it's running or while it's starting then you can't re-enable the wifi? (I'm running intrepid and planning a switch to jaunty after exams :D)

---

### Post by Cloud79 on 2008-12-19
> **MoridinBG said:**
> Installation is on HP tc4400 TabletPC.

But my Intel graphics got screwed.
```
fester@fester-tabletpc:~$ glxinfo | grep renderer
OpenGL renderer string: Software Rasterizer

```


I have exactly the same problem! Worked good in intrepid but compiz is mega slow in jaunty cause of this. Did you find any fix?

---

### Post by klange on 2008-12-19
Intel graphics are wacked out at the moment. 3945 wireless has had problems since Hardy with the switch to iwl3945: everything from what you described to complete system failures...

---

### Post by MoridinBG on 2009-02-07
Bump.
Latest Kubuntu 9.04 Here (alpha 4 + 82 updates)
Switching to UXA fixes the graphics performance (introducing a bit of instability, though). BUT the wireless is still a no-go.
I used Arch for a while with iwl3945 and had no problems turning on and of the WiFi, whenever I want. It runs the same 2.6.28 kernel.

---

