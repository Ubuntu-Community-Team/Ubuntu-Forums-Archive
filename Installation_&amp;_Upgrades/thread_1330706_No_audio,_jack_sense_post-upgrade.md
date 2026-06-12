---
title: "No audio, jack sense post-upgrade"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by letired on 2009-11-18
Upgraded 9.04 &#8594; 9.10 today and it's been easier than the last couple of times around. However, as with previous upgrades, the audio is not working properly.
What doesn't work:
[list][*] No audio on boot
[*] Jack sense, neither for headphones nor sound system
[*] In-browser audio, specifically flash
[/list]
I can get audio to work by doing the following steps:
1. Sound preferences from volume icon
2. Output tab
3. Switch to Internal Analog Audio Stereo (from Simultaneous output to IAAS)
4. Switch connector to Analog Headphones
5. Switch connector back to Analog Output

This gives me audio on the laptop speakers. However, there's no detection of headphones or external sound system being inserted into the headphone jack. My sound card make/model is Realtek ALC268.

Pastebin from bash alsa-info.sh:
[http://pastebin.ca/1676962](http://pastebin.ca/1676962)

I'm guessing the problem, as always, is pulseaudio. I haven't done anything to disable it during install, although I might have had something changed in my 9.04 install. I do recall pulseaudio being used there too, however.
pulseaudio +vv yields nothing at all (it's running, but no output is printed). I guess this might mean pulseaudio isn't being used?

---

### Post by letired on 2009-11-19
Bumped I guess. I've been trying a bunch of things from searches both before and after starting the thread, to no avail.

---

### Post by rolandixor on 2009-11-25
I have a similar issue, but only with the jack sense. Does you jack get sensed if you turn up or down your volume on the volume control?

---

