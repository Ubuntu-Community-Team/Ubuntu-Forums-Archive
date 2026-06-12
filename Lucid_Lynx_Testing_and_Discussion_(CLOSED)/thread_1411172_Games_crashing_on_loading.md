---
title: "Games crashing on loading"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2010-02-19
Hi guys,

I've been having this problem for a few days now (more like a week actually): I can't play any games - whether it's with Wine or native ones like Supertuxkart or Openarena. (64bit Lucid, Radeon 2600 RV630)

The error messages are along the lines of this:

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  179 ()
  Serial number of failed request:  20375
  Current serial number in output stream:  26121


This is due to DRI being disabled (see below). I have disabled KMS and Plymouth due to stability problems (system freezes) but temporarily enabling KMS upon boot doesn't bring the games back.

> glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
[...]


Any ideas (and if it's only what package to file the bug against...)

cheers,
mm

---

### Post by moviemaniac on 2010-02-20
Okay, I finally found the culprit: Some darn update installed the NVidia drivers some days ago which messed with the ATI drivers and effectively killing DRI. Ditching all the NVidia-related packages in Synaptic and reinstalling all ATI-related ones brought back DRI support.

---

