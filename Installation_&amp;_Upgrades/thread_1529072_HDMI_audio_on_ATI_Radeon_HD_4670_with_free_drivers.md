---
title: "HDMI audio on ATI Radeon HD 4670 with free drivers?"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by OmegaWarrior on 2010-07-11
So I just installed 10.4 on my system with my new ATI Radeon HD 4670 card to use as an HTPC.  one big reason that I got this card was that it can do audio over HDMI, which the nVidia cards seemed unable to do.  I was able to get the sound working only by installing the proprietary ATI drivers for the card, but once I did that I noticed a remarkable drop in the video quality and performance (strange, I know).

Is there a way to get sound over the HDMI port using free/open drivers?

All the tutorials I've checked are either out of date or don't have relevant info on this matter.  I've searched for days (was up 'till 8:00 am this morning googling this stuff) and am back at square one.  does anyone have a tutorial for setting this card up in ubuntu 10.4?

My CPU is an Athlon64 x2 3800+
The video card is an ATI Radeon HD 4670 with 1GB of DDR3, output to a 42" Toshiba Regza TV over HDMI (1080p) and is in a PCIe 2.0 slot.
The system has 2GB of DDR2 RAM

Thanks.

(P.S. I'm a tad noobish to linux; you have been warned)

---

### Post by markbuntu on 2010-07-12
I know the radeonhd and radeon open source drivers added hdmi support some time ago. HDMi is part of the gpu and is a separate device from the sound card. You can see if the HDMI device and its driver are available with

aplay -l

which will list all available playback hardware devices. Open a terminal and type

aplay -l

and post the results.

---

### Post by OmegaWarrior on 2010-07-17
the results are:
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I can see the device and select it in the Sound Preferences menu in the Hardware tab, but when I close the window, it reverts back to the internal Audio setting.  even when I launch it with 

```
sudo gnome-volume-control
```

---

### Post by OmegaWarrior on 2010-07-18
I found  [this guide]("https://help.ubuntu.com/community/RadeonHD") but when I set Driver "radeonhd" i get a not-found error.  I tried installing the radeonhd package in synaptic but it didn't help.

---

### Post by runesvend on 2010-08-31
As far as I can tell, it shouldn't be necessary to use the RadeonHD driver. So try not changing the "Driver"-line in your xorg.conf, and see if it works.

---

