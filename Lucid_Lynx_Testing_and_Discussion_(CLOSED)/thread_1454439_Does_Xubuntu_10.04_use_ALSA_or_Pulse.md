---
title: "Does Xubuntu 10.04 use ALSA or Pulse?"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Redmage913 on 2010-04-14
Hey,

Does the beta/eventual release of Xubuntu Lucid primarily use ALSA or PulseAudio for its sound management?

I ask because in the Mixer, I have:

[LIST]
[*]HDA Intel (Alsa Mixer)
[*]Realtek ALC268 (OSS Mixer)
[*]Playback: Internal Audio Analog Stereo (PulseAudio Mixer)
[/LIST]
along with two capture options, both Pulse.

How should I correctly interpret this?

--Red

---

### Post by undecim on 2010-04-14
Since you clearly have Pulse installed, it would use Pulse.

---

### Post by Redmage913 on 2010-04-14
Then I should amend the question to Why does it also report ALSA and OSS, and can anybody comment if Pulse is more stable in 10.04 (as far as beta users know)?

---

### Post by philinux on 2010-04-14
Moved to testing forum

---

### Post by kostkon on 2010-04-14
> **Redmage913 said:**
> Hey,

Does the beta/eventual release of Xubuntu Lucid primarily use ALSA or PulseAudio for its sound management?

I ask because in the Mixer, I have:

[LIST]
[*]HDA Intel (Alsa Mixer)
[*]Realtek ALC268 (OSS Mixer)
[*]Playback: Internal Audio Analog Stereo (PulseAudio Mixer)
[/LIST]
along with two capture options, both Pulse.

How should I correctly interpret this?

--Red
Both. ALSA and PulseAudio go together.

If you want to change your hardware volume levels, use the *HDA Intel (Alsa Mixer)* in alsamixer. That is for ALSA.

*PulseAudio Device Chooser* (especially, the pulseaudio volume control that comes with it) would be the tool you'll want to use for PulseAudio.

---

