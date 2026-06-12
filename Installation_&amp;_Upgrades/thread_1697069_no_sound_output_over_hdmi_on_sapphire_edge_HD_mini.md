---
title: "no sound output over hdmi on sapphire edge HD mini-pc  on 10.10( ion 2 )"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by clovis86 on 2011-02-28
Hi all ! ):P
just a noob here ;) 
I just bought a powerful Sapphire nettop HD Mini-pc as shown here : 
[http://www.sapphiretech.com/presentation/product/?psn=0001&pid=1088](http://www.sapphiretech.com/presentation/product/?psn=0001&pid=1088)

Installed a 32 bits version of ubuntu 10.10
everything is working smoothly 
So basically : 
- installed 10.10 with usb key on HDD 
- launch all update of the OS 
- installed Nvidia closed driver 
- update alsamixer to 1.0.23

So for now, i have in alsamixer 4 SPDIF out but no sound output from hdmi :( 
HDMI output is well configured in the sound settings of ubuntu. 

I think this is linked to the ION 2 chipset and D510 proc.

Anybody got an idea regarding this issue pleeasssse ? :p


Here is the aplay -l return : 

> 
 aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: NVidia [HDA NVidia], périphérique 3 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: NVidia [HDA NVidia], périphérique 7 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: NVidia [HDA NVidia], périphérique 8 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: NVidia [HDA NVidia], périphérique 9 : NVIDIA HDMI [NVIDIA HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

dmesg|grep -i nvidia return : 

> 
[   11.653064] nvidia: module license 'NVIDIA' taints kernel.
[   11.909936] hda_intel: Disable MSI for Nvidia chipset
[   15.119287] nvidia 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.119304] nvidia 0000:04:00.0: setting latency timer to 64
[   15.119847] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.29  Wed Feb 23 1                                                       6:16:53 PST 2011 

---

### Post by clovis86 on 2011-02-28
BTW I didn't even tried the SPDIF output ...

---

### Post by bedege on 2011-02-28
Hi
You should read the following topic in here [http://ubuntuforums.org/showthread.php?t=1668737]("http://ubuntuforums.org/showthread.php?t=1668737").

That explains in details how to set up sound over hdmi, and that more or less worked for me on a Jetway NC98 mobo.
I must admit the mod_probe solution did not solve everything for me, and I had to edit the alsa.conf file, as explained in this thread.

Bon courage :P

---

### Post by clovis86 on 2011-03-03
Hey thanks to Bedege, 
here is the tips to get the sound working : 
On this specific configuration hardware , you got to modify  /usr/share/alsa/alsa.conf and change this original part :

defaults.ctl.card 0 
defaults.pcm.card 0 
defaults.pcm.device 0 

into this one and put this one instead : 

defaults.ctl.card NVidia 
defaults.pcm.card NVidia 
defaults.pcm.device 9

---

### Post by clovis86 on 2011-03-03
so problem is solved !

---

### Post by bedege on 2011-03-15
Glad this helped and worked on your system!

---

