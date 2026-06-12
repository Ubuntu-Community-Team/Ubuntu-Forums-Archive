---
title: "UBuntu 9.10 can't work with my sound card"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by LordOrange on 2010-01-24
As many others, I have a problem with my sound since upgrading to Ubuntu 9.10. It appears that Ubuntu can't see my card. I've tried reinstaliing the alsa drivers butit still lists no devices under the hardware tab in sound properties. Here are some of the listings I got from other tutorials.

[SIZE=2]benjamin@benjamin-desktop:/$ aplay -l
aplay: device_list:223: no soundcards found...

benjamin@benjamin-desktop:/$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 829f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f7ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


[/SIZE]for the lspci -v I just coppied the relevant sound card section. This was the only 1. I'm running on an Asus P5K ( and am using the onboard sound) and also have a Windows RC and another installation of 9.10 that i used as trial, both of which have perfectly working sound but not the apps and environment i want to use. PLEASE can some one help... having to hop between operating systems is getting 2 be a real pain

---

