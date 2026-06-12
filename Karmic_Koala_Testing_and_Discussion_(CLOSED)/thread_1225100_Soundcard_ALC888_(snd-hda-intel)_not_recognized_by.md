---
title: "Soundcard ALC888 (snd-hda-intel) not recognized by pulseaudio"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ernstblaauw on 2009-07-28
[I've already filled a bug report on LaunchPad: [https://bugs.launchpad.net/bugs/405348]](https://bugs.launchpad.net/bugs/405348])

Hi,

My sound card is not recognized correctly. This has been the case for a long time (I always shut down pulseaudio), but I think it is better to report this problem. If you have such a card, can you tell if it works?

The case is, pulseaudio doesn't even see the card; i tonly shows my other sound card. However, my speakers are connected to the ALC888.
Below you see the output of aplay -l, which shows the card. On the attached screenshot it is clear pusleaudio does not see the card at all.

Someone around here with same problems?

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

uname -r
2.6.31-4-generic

lspci|grep audio
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
04:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

lspci|grep Audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
```

---

### Post by ernstblaauw on 2009-07-28
Well, the sound card 'internal audio' is actually my sound card 8-[. I thought it was some internal beep speaker on my motherboard, but it is just the ALC888 which works perfect.

---

