---
title: "Headphones worked in 18.04, but not in 20.04"
date: 2021-04-12
forum: Installation &amp; Upgrades
---

### Post by DavidS on 2021-04-12
I recently installed Ubuntu 20.04 in a separate partition from my previous 18.04 install.  They both use the same /home folder, which is on another partition.

My headphones work fine when I run 18.04, but in 20.04 they do not even show up in System Settings - Sound.

If I run '[COLOR="#0000CD"]aplay -l[/COLOR]' I get this output, whichever OS version I am using:

[COLOR="#0000CD"]**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Speaker [USB Speaker], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR]

If I run '[COLOR="#0000CD"]aplay -D plughw:0,0 /usr/share/sounds/alsa/Front_Center.wav[/COLOR]' under 18.04 the file plays through my headphones, but in 20.04 I just get an error message:

[COLOR="#0000CD"]aplay: main:830: audio open error: Device or resource busy[/COLOR]

I have run alsamixer, and all the volume settings seem to be OK.

I have also run the PulseAudio Volume Control, and the headphones don't appear there at all.

What might be causing this problem in 20.02?

David

---

