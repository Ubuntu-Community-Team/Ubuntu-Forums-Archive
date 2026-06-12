---
title: "NVidia and Sync to VBlank - screen tearing at the top of the screen"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2009-04-13
I am noticing a possible problem when I have Sync to VBlank enabled for applications which I think involve OpenGL, particularly when in fullscreen. If there is fast scrolling action at the very top of the screen, then screen tearing occurs, which shouldn't happen. 

I knew this problem occured intermittently using the 180 drivers from the official repositories but using the 185 drivers from thefirstm PPA, it seems the problem now happens all the time, regardless of whatever settings are made in nvidia-settings or whether Sync to VBlank is enabled or disabled for either the OpenGL or XVideo Setting options.

It's an annoyance but the problem is that I get the problem with Wine and some native Linux applications, but not with Firefox or Totem. Anyone else notice this?

---

### Post by tghe-retford on 2009-04-19
Just to add two things to my previous post that I have spotted tonight:

[LIST]
[*]The same problem also occurs with Mednafen.
[*]My LCD monitor is currently set at a refresh rate of 75.02Hz according to NVidia settings, and I am wondering whether the .02Hz is the possible problem, though I must stress that the refresh rate has always been as such (to make the Compiz effects smoother) and the problem didn't occur in the past. Same occurs if the monitor is set at 60Hz (which shows as 60.02Hz).
[/LIST]

---

