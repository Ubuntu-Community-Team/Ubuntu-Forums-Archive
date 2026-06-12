---
title: "Audio issues on 10.04"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by TaxAlien on 2010-05-11
Hi, I have an Intel HDA based system and upgraded to 10.04.

Before the upgrade no audio issues, after that nothing but trouble.

Previously I was using Alsa but the upgrade appears to have totally wrecked it.

I use Amarok and it seems it chose AD198x Analog as the preferred device. Intermittently on startup I would get a message saying "AD198x Analog" doesn't work. It might play one song and then die.

Looking at things, if I open alsamixergui it says pulseaudio, even though I thought I had got rid of it again during debugging of this problem.

I then used pulseaudio mixer and decided to change the output device to digital stereo duplex iec958 and then amarok is happy. However flash on firefox stops working.

Is there any simple reinstall the whole sound system guide or idea that someone could pass me? It seems to me to be the only way out.

---

