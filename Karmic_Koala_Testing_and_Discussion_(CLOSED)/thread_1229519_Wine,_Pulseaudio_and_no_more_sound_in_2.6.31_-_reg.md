---
title: "Wine, Pulseaudio and no more sound in 2.6.31 - regression?"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Christian Juner on 2009-08-02
Running system: karmic amd64 with all updates as of today
Wine version: wine1.2 1.1.26-0ubuntu1

I have both the generic (2.6.31-4-generic) and rt (2.6.29.6-1-rt) kernels installed.

For a long time running karmic (almost since day 1), running applications in Wine with sound worked fine. They used Wine's ALSA interface which in turn was run through the ALSA pulseaudio plugin.

Some time ago that stopped working for me.

However, when I boot with the rt kernel (which is still 2.6.29) - it's back working.

Running winecfg with 2.6.29 I see the following outputs/inputs listed under ALSA (from my memory, so might look a little different):
- waveout
- midi out 1
- midi out 2
- mixer

With 2.6.31, waveout disappears and only two midi outs and mixer remain.

So I suspect there has been a regression somewhere. It may very well be connected to my hardware and not be a general regression.

I'll be glad to provide any information requested and hope this can be fixed.

Has anybody experienced something similar or is even able to help me on this issue?

I have filed a bug report (same text): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407970](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407970)

---

### Post by kostkon on 2009-08-02
Yeah, it seems there is a regression. But, try this:
run *winecfg*, select the audio tab and in the *DirectSound* section set the *Hardware Acceleration* to *Emulated*.

---

### Post by Christian Juner on 2009-08-02
> **kostkon said:**
> But, try this:
run *winecfg*, select the audio tab and in the *DirectSound* section set the *Hardware Acceleration* to *Emulated*.
Tried that. It didn't seem to have any effect for me - that is I still have no sound in the applications.

---

