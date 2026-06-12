---
title: "ALSA Sound Problems"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by jso2897 on 2008-10-31
I just upgraded from Hardy to Intrepid on my HP Pavillion a1520n. It has an AMD CPU and the nVidia chipset. At first, I had no sound, and attempts to make it work failed. Then i just went into the sound settings and changed everything to the OSS sound shceme. Now, video& audio files play with sound, but Flash still doesn't. Has anybody who has one of the H/P proprietary sound chips found the real solution to this?:confused:

---

### Post by MikaelHolber on 2008-11-02
Same here, I have a HP Pavillion 2115ea. Intel chip with core duo. Only OSS works for both my built in card and my usb-sound card.

---

### Post by Drew_[SCED] on 2008-11-02
Same here, Toshiba Satellite M115.

Perhaps Flash 10 is the default in Ibex?

---

### Post by tuxxy on 2008-11-02
Try the sound troubleshooting guide

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Drew_[SCED] on 2008-11-02
> **tuxxy said:**
> Try the sound troubleshooting guide

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

That's not helpful, because we're getting sound fine, just not in Flash applications.

---

### Post by jso2897 on 2008-11-04
Yeah. Alsa is broken in some way - the system sees my soundcard fine - in fact, I have sound (at least in the movie player). I just changed the sound scheme from alsa to OSS in Sound Preferences. But ALSA hangs on the shutdown for two minutes, and flash sound doesn't work, and I want ALSA to work properly. I've tried a couple of edits to alsa-utils, but no love.
A lot of people are having this problem. What the heck did they do, and what's the fix for it?:confused:

---

### Post by forest.r on 2008-11-04
I am having the same problem. Whenever I try and use flash objects in FireFox, it freezes, usually along with the whole computer. My computer hangs on ASLA durring shutdown as well.

---

### Post by jso2897 on 2008-11-04
Well, I've made some progress - I set all the sound channels to the OSS sound preference, and now I get sound in everything, including Wine Games. But the quality is crappy. Lots of noise, no real presence with music. I wish I could get ALSA working.:(

---

### Post by Drew_[SCED] on 2008-11-05
Seems to me that this is enough of a bug to have some sort of attention...

I guess I'll change to OSS and check to see if there's a bugfix later on.

UPDATE: That didn't work... I can't get sound in flash no matter what I do.

---

### Post by Drew_[SCED] on 2008-11-05
> **'Drew_[SCED] said:**
> Seems to me that this is enough of a bug to have some sort of attention...

I guess I'll change to OSS and check to see if there's a bugfix later on.

UPDATE: That didn't work... I can't get sound in flash no matter what I do.

Update!  I installed the .deb of Adobe's latest Flash version and now sound works fine in Flash.

I guess the built-in Ibex Flash is broken or out of date or something.

---

### Post by woolyninja on 2008-11-05
Try installing libflashsupport:

sudo apt-get install libflashsupport

---

### Post by forest.r on 2008-11-06
Remember, although this may fix the flash problem, this thread is about the ALSA problem, please dont label as fixed if this temporarily solves the problem.

---

