---
title: "No sound on ASUS P5P55D-E LX with Lucid"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by benlau on 2010-08-29
Hi ,

  I just bought a new computer with ASUS P5P55D-E LX with i7 and Geforce 120 display card. After installed Lucid (64 bits), I found that it's audio interface do not have any sound output.

```

$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf5ff8000 irq 22
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7bfc000 irq 16

```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have installed PulseAudio Volume Control,it show that all of the interface is not muted. And volume bar is changing during audio playback , but can not hear anything from it.. 


I have tried to follow this guide , but do not really help.
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Any suggestions to study and solve the problem? Thanks for any advise.

---

