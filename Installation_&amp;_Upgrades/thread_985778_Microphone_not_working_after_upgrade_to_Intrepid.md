---
title: "Microphone not working after upgrade to Intrepid"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by vishnumrao on 2008-11-17
We did an upgrade to Intrepid Ibex from Hardy Heron on a friends desktop. Now the microphone does not work. When I use the microphone in Skype, there is some output but very little and is very noisy. Also there is some noise through the speaker at all times.  I did some searching on the forum but not quite what the problem is.

```
jp@jp-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jp@jp-desktop:~$ 

```

Relevant output of ```
lspci -v
``` 


```

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Intel Corporation Device 0102
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at e400 [size=256]
	I/O ports at e080 [size=64]
	Memory at ffa7f800 (32-bit, non-prefetchable) [size=512]
	Memory at ffa7f400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

```

The microphone was working great in Hardy. My friend use Skype quite a bit. I do not know if its a issue with Skype or with the Sound driver. 

Thanks,
Vishnu Rao.

---

