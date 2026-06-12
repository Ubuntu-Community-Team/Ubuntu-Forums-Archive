---
title: "Ubuntu 910 Live CD cant display video mode"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by Joe325 on 2010-03-22
Im trying to run a Live CD of Ubuntu 910 on an 'older machine' which is hooked onto a Dell 19" widescreen monitor.
After the Grey ubuntu logo, I get a:
 removing gdm... command then the monitor displays:
Analogue Input Can not display this video mode Optimum performance 1680x.....  

Ive tried F4 > Safe video mode but I get stuck in the same place.
Any ideas???

---

### Post by Tom.Gee on 2010-03-22
> **Joe325 said:**
>  is hooked onto a Dell 19" widescreen monitor.
  ... Optimum performance 1680x.....
Obviously your video card is trying to send a non-optimal video signal.  The question I have is, how is the monitor connected?  The correct video cable *SHOULD* allow the video card to read the supported video modes.  Perhaps your cable is bad.  Even if you are using the correct cable, if the cable itself has a broken pin or conductor, the video card may not detect what it is connected to.  

If it is a REALLY old PC, you might want to swap out the video card for something a little newer?  It is ultimately my guess that the video card isn't being told the supported video modes available to it.

---

### Post by Joe325 on 2010-03-28
The monitor is brand new (cable too)
The video card is a Gforce 7600GS

I used a vga/DVI converter and swapped from using the VGA on the vid card and used the DVI instead.
This worked

---

