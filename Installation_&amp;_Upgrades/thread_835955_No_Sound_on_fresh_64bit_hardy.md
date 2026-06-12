---
title: "No Sound on fresh 64bit hardy"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by Martel on 2008-06-21
Despite following several guides, I have no sound.

I have a brand new putermachine with an integrated sound card. My mainboard is a msi p6n 680i which has the Creative Soundblaster X-Fi audio Chipset.

alsa did not work, so I am currently using OSS 4-1016amd64
here is my OSS info 

> Version info: OSS 4.0 (b1016/200806162350) (0x00040003) 
Platform: Linux/x86_64 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 (juggernaut)

Number of audio devices:	0
Number of audio engines:	0
Number of mixer devices:	0


Device objects
 0: osscore0 OSS core services
 1: ossusb0 USB audio core services


Mixer devices

Audio devices


and here is my sudo ossdetect -v

> Detected Generic USB audio device (BETA)

I have no idea what to do, all help is appreciated.

Edit: I should add that sound does work on windows.

---

