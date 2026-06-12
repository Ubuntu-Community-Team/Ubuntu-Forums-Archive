---
title: "Poor DVD playback in Ibex"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mordanda on 2008-10-05
Hey all,

In Ibex Beta 1 I'm seeing some odd issues watching DVDs.  Every 5 seconds the screen hitches for a split second and the mouse shows up.  Happens in windowed or full screen mode, in Dragon, Kaffeine, and VLC.  I suspect something is running in the background but I'm unable to spot it.  I'm running this on a Dell D620, 2 GB Ram, 100 GB SATA HD with an intel 945GM graphics card.

Any ideas?  Anyone else seeing this?

Dan

---

### Post by Nullack on 2008-10-05
None of those players are part of the supported packages. Does it happen with Totem on gstreamer?

---

### Post by mordanda on 2008-10-05
I'm not using Totem since it's a Gnome application.  I'm running Kubuntu Ibex Beta 1 with KDE 4.1.2 which comes default with Dragon Player and Xine as the backend.  Previous version of Kubuntu came with Kaffeine as the player with the Xine backend.  This issue is new with Ibex.

Never had an issue with Xine so I'd be curious to see if anyone has a fix.  But I think I can set Kaffeine to use gsteamer as its backend so I'll try it and let you all know.

Dan

---

### Post by mordanda on 2008-10-06
No dice so far.  I switch Kaffeine's backend to gstreamer and it still hitches every 5 seconds.  I suspect it's one of two things:

1. The intel graphics hardware is not accelerated or the drivers are otherwise buggy.
2. There's something going on with the new kwin compositing/Plasma desktop that is refreshing/stealing focus at a set interval.

I suspect it's a minor fix because I had KDE 4.1 loaded on this laptop with 8.04 and DVD playback was not an issue.

Is this jogging anyone memory?  Anyone playing commerical DVDs in Kubuntu 8.10 without problems?

D

---

### Post by mordanda on 2008-10-13
After a couple rounds of updates (kernel, xorg, kwin, and intel drivers) this issue is still around for me.  I formatted and reloaded/updated my laptop to remove the possibility of my changes further harming the OS, but with no luck.  DVD playback is still choppy every 5 seconds and the mouse won't stay hidden.

On a similar note I can duplicate this issue running glxgears.  The animation hitches at the same intervals despite running the demo around ~1000 FPS.

Google pulls up various issues with the intel 945 chipset and Intrepid Ibex, so I think it's a driver/acceleration issue.

Can anyone confirm or have a possible solution?

D

---

### Post by mrboojive on 2008-10-13
I haven't tried playing a DVD but I have the same integrated graphics. Desktop effects seem choppy and sluggish in Kubuntu Ibex but not in Ubuntu. Could just be KWin but I suspect the graphics, too. Is there a way to check whether Kubuntu is actually using graphics acceleration?

---

### Post by joshuajtl on 2008-10-23
I have the same issue whenever I try using Kubuntu 8.10. I installed fluxbox and tried playing a movie through the same applications but in fluxbox, and I don't get the stuttering every 5 seconds! So it appears to be a KDE4 problem!
Joshua

---

### Post by roberine on 2008-10-23
I have the same thing in Ubuntu Ibex. But if I disable compiz all my problems are solved. No more jerky dvd/avi/mkv playback.
Whith compiz enabled Glxgears shows me FPS to be 8000. When compiz
is disabled it increases to 14000 !!!!
Even though you'd think that 8000 would be sufficient to play back
video streams. I've seen this happening ever since the beginning of
compiz in ubuntu.

---

### Post by joshuajtl on 2008-10-23
Interesting, I can have Ubuntu (running gnome) using full compiz and I have no dvd playback issues. But Kubuntu (running kde) I have the sticking playback. Though as I said before Kubuntu running fluxbox I get no problems at all.
J

---

