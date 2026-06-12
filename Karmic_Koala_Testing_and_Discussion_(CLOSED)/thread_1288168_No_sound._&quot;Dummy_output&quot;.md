---
title: "No sound. &quot;Dummy output&quot;"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Ayle on 2009-10-11
My laptop is a MSI GX620. Here are my terminal output for:
_lspci-v:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 6510
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f8ef8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

_aplay -l;
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

and alsamixer list this:
```
Card:HDA Intel
Chip: Nvidia MCP78 HDMI 
```

It's quite annoying to have everything working but the sound... :-s.  I also have a problem with my WLAN card(bcm4328) since the lastest software update I did, I'm unable to join any network. Even when they are unprotected. The joining keeps failing. I ordered an Intel 5300 n card and hopefully this will solve my connection problem but if anyone have a solution in the mean time, my ears are open.

---

### Post by nitinab on 2009-10-11
i have something similar on my Lenovo R60 ... but the cause there is missing codec in the alsa system ... check if u have the codec ... [here's the howto]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

