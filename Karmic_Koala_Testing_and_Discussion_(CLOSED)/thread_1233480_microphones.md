---
title: "microphones"
date: 2009-08-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kaitwospirit on 2009-08-06
How do I make microphones work? I can't figure out how to get Karmic to detect microphone input.

---

### Post by wayne_cat on 2009-08-06
Do you have a microphone in pavucontrol?


.

---

### Post by cariboo on 2009-08-06
Microphones were autodetected for me.

---

### Post by miegiel on 2009-08-07
I've got this problem too. My mic isn't showning in *pavucontrol* (karmic 64). I've got a feeling it's this new hardware.

```
me@universe:~$ lspci | grep udio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
me@universe:~$ sudo lspci -v -s00:1b.0
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0229
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

---

