---
title: "Wine sound - call for testers"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aldursys on 2009-10-13
Hi all,

A new version of the wine1.2 beta package (1.1.31) has been uploaded to the archives with fixes to the sound drivers.

Additionally I have on my PPA ([https://launchpad.net/~neil-aldur/+archive/ppa](https://launchpad.net/~neil-aldur/+archive/ppa)) a version of wine1.2 with a new release of the Winepulse driver incorporated (0.32).

If you're working with karmic, can you test out the vanilla release in the archives and my PPA version and see whether the sound is improved by either versions.

Please post your results on the bug ticket ([https://bugs.launchpad.net/bugs/371897](https://bugs.launchpad.net/bugs/371897)).

TIA

---

### Post by emarkay on 2009-10-13
Can you give examples of what to use to test?  Do you mean things like Windows Media Palyer11 or MS Flight Sim 9?  ;)  Seriously, what apps are you thinking are applicable?

---

### Post by viniosity on 2009-10-13
works great, thank you!

---

### Post by eric71 on 2009-10-14
I have been using Reaper with wineasio in Karmic for a few weeks, and it has been running great. Wine was upgraded yesterday (and a new rt kernel as well) and now things are not working well. Not sure if it is Wine or the new rt-kernel that have caused my problems. I'll try your PPA Wine tonight and see if that helps.

---

### Post by eric71 on 2009-10-14
Never mind my previous post. It does not seem to be Wine related. Definitely something to do with the latest RT-kernel.

---

### Post by viniosity on 2009-10-25
Well, spoke to soon. This *was* working but after the latest upgrade I get no sound whatsoever.  Launching winecfg I see "Found driver in registry that is not available! Remove 'pulse' from registry?"

Not sure if it's coincidence or what.. reverting back to wine from the official repo does not seem to solve my issue even when trying ALSA or OSS

Edit: Looks like the issue is that Universe has a different/newer Wine1.2 package which overwrites the one from PPA.  Pinning might be the solution but I hate to do it..

---

### Post by thatsPipe on 2009-10-28
I also installed Neil's version of Wine with the pulseaudio plugin and it was working fine until a few days ago. I'm getting the exact same problem as viniosity ("Found driver in registry that is not available! Remove 'pulse' from registry?")

I'm suspecting it must have been something updated recently that is causing wine to no longer find pulseaudio. I'd really like to get this working again; passing the audio through OSS is painful (snap, crackle and pop all the time!)

EDIT: Didn't read far enough into viniosity's message. I went into Synaptic and found that there was a newer version of wine1.2 that had overwritten Neil's. Forced Neil's version and I'm back to using pulseaudio!

P.S. Awesome job on the pulseaudio plugin, Neil ;)

---

