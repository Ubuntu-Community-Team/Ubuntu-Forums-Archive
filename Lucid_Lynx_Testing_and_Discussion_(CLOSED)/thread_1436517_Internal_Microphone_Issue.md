---
title: "Internal Microphone Issue"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kestal on 2010-03-22
Since Lucid, I've been getting a decent amount of static and/or beeping (depending on my settings via accessing alsamixer from the terminal - it could even end up muffled) from my internal microphone when recording. It's not that I cannot hear myself, though I cannot hear myself relatively well for me to use it at all (whether skype, or recording voice/video).

I was wondering if someone here could quickly guide me a bit so I can troubleshoot the issue and potentially fix. I'd still run Lucid regardless, but it would be nice to have a functioning mic as I tend to use it often.

Some hardware info:

Currently using a fully updated Ubuntu 10.04 Beta 1 (up until this very posted with all backports/proposed from Sources). 

I am using a Laptop (Dell Studio 14z) and card shown on the alsermixer window is HDA Nvidia with the chip Nvidia MCP7A HDMI. There is one built-in internal mic and also a jack for a second mic.

aplay -l returns:
```
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```



amixer returns:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',1
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Front Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 2 [67%] [20.00dB]
  Front Right: Capture 2 [67%] [20.00dB]
Simple mixer control 'Front Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Line In'
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 1 [33%] [10.00dB]
  Front Right: Capture 1 [33%] [10.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]

```

---

