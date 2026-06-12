---
title: "High-pitched audio after updating to Jaunty"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cajunaggie on 2009-04-05
I've searched this thread and found a lot "no audio" or "scratch/stutter audio" threads, but none that pertain to this particular issue. Apologies if I missed it somewhere.

Before I updated to Jaunty, my audio worked fine. However, after updating, my audio sounds "tinny" and higher-pitched. It's a little hard to describe in text, but it's like a cassette tape being played back at higher speeds, or listening to a person who's just inhaled some helium. 

It's not a hardware issue (I used XP for comparison and used both speakers & headphone), and it affects all audio/video files, even ones created or downloaded after the update.

Any ideas?

---

### Post by cajunaggie on 2009-04-05
Browsing through Synaptic, I also noticed that I have ALSA installed. Could ALSA and PulseAudio be fighting with each other?

---

### Post by psyke83 on 2009-04-06
> **cajunaggie said:**
> Browsing through Synaptic, I also noticed that I have ALSA installed. Could ALSA and PulseAudio be fighting with each other?

No, PulseAudio requires ALSA to function properly, so don't remove either of them.

Are you using IEC958 output? If so, see this bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/172654](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/172654)

---

### Post by cajunaggie on 2009-04-06
Thanks psyke83, that's the closest description of the problem I've found so far.

---

