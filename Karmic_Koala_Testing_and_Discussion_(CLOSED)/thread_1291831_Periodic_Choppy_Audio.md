---
title: "Periodic Choppy Audio"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by aeternitas on 2009-10-15
Since installing Karmic, I've been running into issues where audio (particularly with VLC and embedded video from the web) gets choppy after a while; hard to say what timeframe exactly, it's varied between 5 and 40 minutes of video play.  I've kept open apps to a minimum to rule out excess CPU usage as a root cause, to no avail.  Originally, I found a restart took care of things, but recently killing pulseaudio and restarting it seems to do the trick as well; it seems that's where the problem is, but I'm at a loss as how to stop things from going downhill, and quite frankly it's annoying to kill/restart every once in a while.  

On a side note, totem doesn't seem to run into the same problems; not sure why.

---

### Post by Peter09 on 2009-10-15
I think pulseaudio is still being configured / developed for Karmic - hope it will stabilize soon as I have noisy problems with it (thumps and bangs).

---

### Post by sdowney717 on 2009-10-15
you can try opening up vlc preferences for audio and setting to pulse from default

---

### Post by aethralis on 2009-10-15
I'm suffering from exactly the same problem, with vlc. Totem plays just fine. Tried to find a bug describing this, but could not find any. Maybe it's time to file one?

---

### Post by aeternitas on 2009-10-17
> **sdowney717 said:**
> you can try opening up vlc preferences for audio and setting to pulse from default

If I do that, then even after restarting pulseaudio it goes funky.  I can deal until release, I think, I've refined my method for working around it (I hate to use totem, it doesn't seem to have a stay-on-top option as VLC does), hopefully I'll be fine in 12 days.

---

### Post by 4ekuct25 on 2009-10-17
this bug at launchpad already
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/440921](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/440921)

i have the same bug too
my recipe - turned from stereo to surround and back in sound preferences
for a short time the sound is clean

after do it again.. and again.. and again :-D

---

