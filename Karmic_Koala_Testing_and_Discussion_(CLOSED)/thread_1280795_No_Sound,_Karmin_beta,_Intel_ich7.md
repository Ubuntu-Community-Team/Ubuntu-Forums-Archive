---
title: "No Sound, Karmin beta, Intel ich7"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wireless on 2009-10-02
I did a very stupid thing today and after a "partial upgrade" i ended up with no SOUND.

> aplay: device_list:223: no soundcards found...

> lspci -v
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Lenovo Device 2010
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at ee240000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Sound -> Hardware is empty. and Output shows only "Dummy Output Stereo" which i'm not sure if it supposed to be there.
Any advice? I'm lost

Thanks in advance !!! ;)

---

### Post by Tich666 on 2009-10-02
try reloading alsa and restarting pulseaudio while logged in:

```
sudo alsa force-reload
```
```
killall pulseaudio && pulseaudio -vvvv
```

AFAIK there is some kind of race bug where pulseaudio and some other service try to occupy the output and often pulseaudio loses.

---

### Post by wireless on 2009-10-02
Nope :( still exactly the same issue..

---

### Post by wrb302 on 2009-10-02
I have the same trouble here. Just upgrade to karmic beta from jaunty. Dell d630. No sound, no Soujnd->hardware.

---

### Post by wireless on 2009-10-02
> **wrb302 said:**
> I have the same trouble here. Just upgrade to karmic beta from jaunty. Dell d630. No sound, no Soujnd->hardware.

can you please post output of 
```
lspci -v
```
and 
```
aplay -l
```

Thanks

---

### Post by Ayle on 2009-10-03
I have the same exact problem. My laptop is a MSI GX620. Here are my output for:
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

It's quite annoying to have everything working but the sound... :-s

---

### Post by andymorton on 2009-10-21
> **Tich666 said:**
> try reloading alsa and restarting pulseaudio while logged in:

```
sudo alsa force-reload
```
```
killall pulseaudio && pulseaudio -vvvv
```

AFAIK there is some kind of race bug where pulseaudio and some other service try to occupy the output and often pulseaudio loses.

Hi,

I've the same problem for the last day or so. Your suggestion worked. Thank you!!!!!! :)

---

