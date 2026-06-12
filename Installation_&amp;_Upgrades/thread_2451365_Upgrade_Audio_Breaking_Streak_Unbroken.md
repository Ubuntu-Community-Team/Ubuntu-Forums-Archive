---
title: "Upgrade Audio Breaking Streak Unbroken"
date: 2020-10-02
forum: Installation &amp; Upgrades
---

### Post by AR_Kozz on 2020-10-02
I don't know how many times in a row it's been. Upgrades always break the audio. This time 18.04 to 20.04 caused ALSA to ignore the headphone jack (what I normally use) on boot up. 

Among the more common suggested fixes was doing this (which works)

> $ sudo alsa force-reload
[sudo] password for (me): 
Unloading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-hdmi snd-hrtimer snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer (failed: modules still loaded: snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-hdmi snd-hrtimer snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-intel-dspcfg snd-hda-codec snd-hda-core snd-hwdep snd-pcm snd-timer.

Then pulse detects and switches to the headphones. None of the hardware is configured any differently when booting up than when doing this reload. What could it be getting wrong at bootup?

---

