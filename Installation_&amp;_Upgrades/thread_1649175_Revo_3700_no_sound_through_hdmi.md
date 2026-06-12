---
title: "Revo 3700 no sound through hdmi"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by UptownRiot on 2010-12-19
I've just installed ubuntu 11.04 on my recently purchased acer aspire revo 3700. After competing the initial install of ubuntu, running all available critical and recommended updates, and installing and activating the 3rd party driver for the nvidia card I'm having trouble. I am getting good video through the hdmi cable to my sony bravia 32" tv, but no sound (sound works fine through regular tv or xbox use). Whenever the acer reboots I hear a pop from the speakers, though i know that is mostly irrelevant. 

I'm relatively inexperienced with linux so I'm not entirely sure what information would be relevant and helpful to assisting me with deciphering this issue, but I will do my best. 

I've found no proprietary driver for sound through the nvidia ion processor, only one for the graphics arm. I would assume they are sharing a driver, but as its not stated I cannot be sure. The 'additional drivers' control panel calls it the 'NVIDIA accelerated graphics driver (version current)' The chip is the nvidia GT218-ION.

Settings in sound preferences are high definition audio controller digital stereo (hdmi) selected for output.

results from aplay are:

UR@UR-Acer:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Through various reading of forum posts around i've edited a few files, i haven't changed them back as of yet

1) gksudo gedit /etc/modprobe.d/sound.conf

then added the following to what was a blank file

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2

2) sudo nano ~/.asoundrc

and added to what was also a blank file

defaults.pcm.device 3


Ultimately nothing so far has worked. I'm not getting any sound from any application or the sound tests in the preferences hardware tab. If there is any other information I can provide that would help I will provide it. 

Any thoughts on what could be causing this strange issue?

---

### Post by UptownRiot on 2010-12-20
I've now tried swapping cables just in case, but still getting nothing.

---

