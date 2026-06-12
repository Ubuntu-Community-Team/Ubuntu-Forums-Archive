---
title: "Can't get surround sound working Dharam 10.10"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by The bagwan on 2011-03-27
Hi,  New to the world of Ubuntu, but learning fast. I've installed Dharma 10.10 on a Gigabyte 880GM-USB3 motherboard using its onboard audio and video so as to use XBMC and MythTV for a HTPC. I can't get surround sound working. Its going via Toslink to my amp. The chipset on the motherboard uses Realtek ALC892. I installed the new Realtek HD drivers (using sudo .install for the auto install). No luck   In sound properties, if I choose 2 channel stereo it works no probs. If I choose 5.1, in XBMC anything encoded using Dolby Digital works, but nothing else does (ac3, dts, mp3, etc).   I've disabled audio via HDMI.  In Alsamixer everything is on high, except my s/pdfi which are both on 00 and can't be altered. (although I can mute them).  I've updated daemon.config and changed ;  ; default-sample-channels = 2    to default-sample channels = 6  I've added; options snd-hda-intel model-auto (and tried a couple of others) to the end of alsa-base.conf  My hardware and output match in sound preferences.  I've downloaded the latest version of alsa (1.2.23)  Running out of things to try. Any help would be greatly appreciated.

---

