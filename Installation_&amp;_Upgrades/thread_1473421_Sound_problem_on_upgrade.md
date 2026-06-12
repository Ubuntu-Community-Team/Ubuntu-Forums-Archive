---
title: "Sound problem on upgrade"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2010-05-05
I was using v 8.10. It came to its end of life and I felt compelled to upgrade. I upgraded to v 9.04. All seemed well, but then I discovered that I had no sound.

As a test, I booted up with the v 9.04 CD, using it as a live CD. I had sound, so it seems as though it should be possible for me to have sound from my upgraded v 9.04 too, provided I can make the necessary changes to it.

When using the live CD and opening the volume control, I get as the listed device "HDA ATI SB (Alsa mixer)". That doesn't appear when I open the volume control using my upgraded v 9.04. Instead, it says "Playback: Null Output (PulseAudio mixer)".

Also, when I check for loaded modules when using the live CD, I get many with snd in their name, but nary a one when using the upgraded 9.04.

Is there some simple way for me to load the same modules in the upgraded 9.04 as are loaded by the live CD?

I tried to figure out the answer to this by reading other threads, but was simply overwhelmed by the volume of material and often wasn't sure to which version of Ubuntu it applied.

Thanks for reading this,

Leslie

---

### Post by lesliek on 2010-05-06
Running the ALSA upgrade script here: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
got me sound on the computer I asked about.

I also upgraded another computer at the same time and also had no sound on it. Unfortunately, running the upgrade script wasn't enough to get that one going. Obviously, more searching is required.

Leslie

---

