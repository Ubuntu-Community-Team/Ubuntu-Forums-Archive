---
title: "Upgrade from 13.10 to 14.04 no sound"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by corey10 on 2014-04-21
I updated ubuntu today from 13.10 to 14, now I have no sound, I tried what was suggested by poster #20 ([http://ubuntuforums.org/showthread.php?t=2211608&page=2](http://ubuntuforums.org/showthread.php?t=2211608&page=2)) and had to reinstall sound indicator. still nothing. should I just do a fresh install? when I go to sound settings it goes to system settings. when I type aplay -l this is what I get 

```
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

---

### Post by Mark Phelps on 2014-04-21
According to Ubuntu Engineering Foundations team manager Steve Langasek:

Upgrades between LTS releases are not enabled by default until the first point release, 12.04.1/14.04.1, scheduled for July/August. It is recommended that most LTS users wait until then before upgrading to 12.04/14.04.

They don't say this this applies to 13.10 --> 14.04, but it might be the same situation. Sorry.

---

### Post by corey10 on 2014-04-23
Thanks... Good to know...now...

---

### Post by coffeecat on 2014-04-23
@corey10, I don't think the upgrade policy for 12.04 -> 14.04 matters here. I upgraded my 13.10 system to 14.04 a few days ago and my sound is still working just fine, but of course I have different hardware from you. As a first step, click on the sound icon in the top bar, and then click on Sound Settings and see if any of those settings help you. Perhaps the wrong output device is selected.

By the way, I've restored the url tags to your first post to make your link clickable and added code tags to make your terminal output readable. I also removed all the redundant color tags. There's no point in setting your post text colour to #000000. It already is! :)

---

### Post by FreeBrrd on 2014-04-23
I have the same problem with upgrade from 13.10 to 14.04. No sound. No devices in sound settings. Removing and reinstalling restricted extras fixed it for a little while. Not sure if for a reboot or not. Than it went away. Now sound is back. I also have a grayed out unlock icon in user account and am getting a password request on shutdown. They all come and go together. Right now, everything works. It didn't in the middle of the night. Did nothing except shutdown. But if doesn't fix on every restart. Love intermittant stuff.

---

### Post by andrewfbailey on 2014-04-23
I have the same (?) problem as well. I do have sound, however, but only through analog output (motherboard), not through HDMI (NVIDIA GTX 660)
aplay -l gives:
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've tried removing and adding restricted extras, but that doesn't seem to have helped much.. :confused:

---

### Post by gstanden on 2014-05-01
Thanks for starting this thread.  I'm having same/similar problem.  Upgraded from 13.10 --> 14.04 and all HDMI sound output options were lost.  I've tried all the usual 13.10 stuff: reinstalling pulse audio, etc. and nothing is working.  I also see many other threads out there about this and very few/no replies.  We do appreciate Ubuntu gurus who help out the masses.  If any Ubuntu gurus can figure this out, much appreciated.  Right now it looks like 13.10 --> 14.04 upgrade is stepping on HDMI sound functionality completely.  TIA.

---

### Post by gstanden on 2014-08-10
I reinstalled 14.04.1 (not upgrade) and all these audio problems went away and everything works great right out of the box exactly as designed.  The problem seems to be with upgrading, not with 14.04.1 itself.

---

