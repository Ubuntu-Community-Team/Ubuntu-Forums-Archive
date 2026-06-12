---
title: "Only digital out after latest PulseAudio update"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by isecore on 2009-09-07
Earlier today I installed the latest batch of updates. This brought an updated PulseAudio which solved the problem of crackling/garbled noise that I posted [about earlier]("http://ubuntuforums.org/showthread.php?t=1251091").

I was also happy to see that finally I could use the digial output once again, much appreciated.

However, this also brought with it that since switching the output to Digital, there's no going back. Turn things back to anything analog and my computer becomes a mute. Sound is playing, VU-meters are dancing in the PulseAudio volume control - yet no sound is heard.

Any ideas?

PulseAudio is 0.9.16.-test7-14-g7ca81ubuntu1. Soundcard is a SoundBlaster Audigy2 ZS. Kernel 2.6.31-9-generic provided by Ubuntu.

I've tried logging out/in again, as well as rebooting. No dice.

---

### Post by jocko on 2009-09-07
That happened to me a couple of days ago. I managed to fix it by deleting my ~/.pulse folder.

---

### Post by isecore on 2009-09-07
> **jocko said:**
> That happened to me a couple of days ago. I managed to fix it by deleting my ~/.pulse folder.

Tried that, made no difference. It resets all settings but audio is still dead.

---

### Post by ranch hand on 2009-09-07
That is strange.  I was listening to tunes on mine and I do not use didgetal out.

I do use gnome-alsamixer.  Pulse is still there though.

---

### Post by isecore on 2009-09-07
It's very strange. It's as if someone yanked my cables or something. Believe me, I checked that, even though it would be odd if the cables just came undone.

---

### Post by isecore on 2009-09-07
Well, I fixed it. Started up gnome-alsa-mixer and discovered that the audigy analog/digital had been checked. Uncheck it, I have analog audio once again.

Wow, I'm glad I'm not a complete newbie, I'd still be looking for a control that DOESN'T exist in the default install.

Sorry for the inconvenience, and thanks for taking the time.

---

### Post by isecore on 2009-09-07
And now it works fine switching back and forth between settings, like it should.

---

### Post by ranch hand on 2009-09-07
I really like that mixer.  It seems to "just work".

---

