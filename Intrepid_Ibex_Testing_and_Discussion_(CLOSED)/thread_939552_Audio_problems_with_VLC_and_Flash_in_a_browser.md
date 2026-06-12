---
title: "Audio problems with VLC and Flash in a browser"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2008-10-06
I've noticed lately that my audio quits working properly in the following cases.

1. If I open a browser and watch a flash video (say YouTube) after starting up in Ubuntu 8.10 then audio no logner works in VLC. If I try to watch a dvd or anything at all in VLC after first watching a flash video then sound in VLC will not work again until I restart.

2. If I play a movie in VLC first after startup and then try to watch a flash video in a browser then the audio for the flash video will not work.

If I want to watch a video in the one that isn't working then I have to completely restart my computer and log back into Ubuntu. Luckily the shut down and startup time is much faster for Ubuntu than my Windows install, so it just takes a minute or two before the movie is playing again, but it shouldn't be this way.

This is a very frustrating problem. Does anyone else ever see this happening or know of a solution? I'm not sure if this makes a difference, but I use Opera and Firefox for watching flash videos. I'm also running Ubuntu 8.10 64-bit.

---

### Post by bionnaki on 2008-10-06
see if you notice any levels dropping to 0 in alsamixer.

---

### Post by kyleabaker on 2008-10-06
> **bionnaki said:**
> see if you notice any levels dropping to 0 in alsamixer.

I'm not noticing anything dropping to zero. Is there anything particular that I can watch to change in the alsamixer?

It's still doing this.

---

### Post by jfernyhough on 2008-10-06
Which version of Flash plugin are you running? Also check whether vlc-plugin-pulse (or whatever it's called) is installed (it should be), and if you're using Flash 10 remove libflashsupport.

Double-check Pulseaudio is working (one way is to open Sound preferences, set the output device to Pulseaudio and test).

---

### Post by psyke83 on 2008-10-06
You really need to use PulseAudio Volume Control to see which applications list themselves as PulseAudio clients.

If an application plays sound but isn't listed in the PA Volume Control playback tab, it's bypassing PulseAudio. When such a scenario occurs, PulseAudio can no longer access the sound card, causing a mixing conflict.

At the moment, 64bit autodetection support for PulseAudio is a little flaky (which will cause problems with Flash, Skype, and other 32 bit applications). You can wait for the fix, or apply the workaround listed near the end of the PulseAudio thread. See: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

