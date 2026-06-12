---
title: "AMD graphics card and ubuntu"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by Fouf on 2012-03-25
When I install the amd drivers thorugh the additional hardware under system, administration, the graphics card seems to work.. (I can run some graphical applications that didn't work before) the only problem is that the resolution is stuck at 640x480 and I tried playing with xrandr as some websites suggested, there is no amd unsupported water mark in the bottom right and when I go to the amd CCC it identifies the graphics card correctly (HD 6550D)
If anyone has any hints, it'd be greatly appreciated.

Thanks,
Fouf.

---

### Post by Fouf on 2012-03-28
I don't know how it takes to bump something, but I do have some more information.
When I try to get to recovery mode.. I can use failsafex graphics, but for some reason 14 out of 15 attempts to get into recovery mode always hang at inital ram disk.. or something like that. Not sure why :/ but yeah I can get into failsafex graphics, and when I try doing startx it says failed to load fglrx module. So I googled that and I purged and tried most of the suggestions but I still get that error, is it because I was doing it through the recovery mode when I could get into it?

---

### Post by darkod on 2012-03-28
Have you tried downloading a driver directly from ATI (AMD)?

If you decide to do that, can you boot recovery mode to try to install it or that doesn't work too?

---

### Post by Fouf on 2012-03-28
I did try, but the resolution was stuck at something very small so I gave up on them, but when I tried to uninstall back to the original open source drivers, or whatever comes with it normally (without using the additional drivers under system administration) I get this now.

Is there a way to force failsafex graphics on boot up and not worry about it? I'm not going to be doing any graphical intensive stuff on it, just holding data, I just thought I'd give install the drivers a shot (unfortunately).

---

