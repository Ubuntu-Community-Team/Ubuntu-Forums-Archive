---
title: "Pulseaudio - No audio after upgrade"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Dr. Feltersnatch on 2010-05-01
Recent upgrade from 9.10->10.04

Sound preferences does not detect a device to configure.

lspci | grep -i multimedia
 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER  (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

cat /proc/asound/cards
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with ALC850 at irq 17

cat /proc/asound/modules  
 0 snd_intel8x0

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

arecord -l
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I have removed pulseaudio and installed again, but still no audio. :(

any ideas?

---

