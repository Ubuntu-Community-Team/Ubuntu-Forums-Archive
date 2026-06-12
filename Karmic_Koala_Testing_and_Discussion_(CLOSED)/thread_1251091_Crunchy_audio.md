---
title: "Crunchy audio"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by isecore on 2009-08-27
I've had the problem recently that whenever two sound-sources try to play audio at the same time, the audio becomes garbled and "crunchy".

For example, listening to Rhythmbox and then Pidgin makes a noise causes the audio to become severely distorted as long as the secondary source is playing audio.

Same with watching flash-videos, or doing anything where two apps play audio. Badly garpled, crunchy audio whenever that happens. As long as just one app is playing audio everything is peachy.

Is there a fix for this or should I just stick it out and wait for it to go away by itself?

---

### Post by isecore on 2009-09-04
Would be nice with a reply... or any information, since this is _extremely_ annoying.

Update: I'm primarily using my Soundblaster Audigy2 ZS for audio. This worked perfectly in every previous Ubuntu release (starting with Edgy back in early 2007 when I switched to Ubuntu) and worked fine early in Alpha 4 of Karmic but then somewhere along the way this started.

---

### Post by taavikko on 2009-09-04
> **isecore said:**
> Would be nice with a reply... or any information, since this is _extremely_ annoying.

Is this upgrade from Jaunty or a clean install?
What chip do you have? "aplay -l ; grep Codec /proc/asound/card0/codec#0"

Have you tried "rm ~/.pulse*" (while gdm closed, and restarting session)

---

### Post by isecore on 2009-09-04
> **taavikko said:**
> Is this upgrade from Jaunty or a clean install?
What chip do you have? "aplay -l ; grep Codec /proc/asound/card0/codec#0"

Have you tried "rm ~/.pulse*" (while gdm closed, and restarting session)

Duh, I'm such a retard - I should've thought of removing the pulse-files myself. Works perfectly now, thanks for the help!

---

### Post by isecore on 2009-09-04
For what it's worth, I discovered the cause. I prefer to have my soundcard output analog 5.1 (since I have such a setup) and if I change the output profile in Sound (our the PulseAudio Volume Manager) to it then presto, two sound sources garble audio.

Set it to analog stereo, no such problem.

Very annoying, since I really prefer DVD's and such to have multichannel audio since I have such a speaker-setup. Oh well.

---

### Post by isecore on 2009-09-04
Still talking to myself, but I'm considering filing a bug-report - if I knew what to file it about. Is it PulseAudio, the kernel?

I tried an earlier kernel, same experience. I'm guessing it's PulseAudio.

---

