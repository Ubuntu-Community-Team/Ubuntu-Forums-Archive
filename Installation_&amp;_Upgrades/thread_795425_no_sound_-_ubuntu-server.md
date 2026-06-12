---
title: "no sound - ubuntu-server"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by fedesuarez on 2008-05-15
Hi, it may be something stupid but I really can't make it work!!! I installed ubuntu-server and then ubuntu-desktop on it. Unfortunately, I have no sound working... I tried to follow the soundtroubleshooting page but I get stuck since I can't find the driver for my soundcard.

```
I have an Asus P5k-premium motherboard and this is the output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and the output about audio for lspci -v


```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8277
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

typing the following makes nothing:
sudo modprobe snd-hda-intel 


when I go through System->Preferences->Sound I can't here nothing even selecting whichever device...

Hope you can help me, thanks.

fede.

---

