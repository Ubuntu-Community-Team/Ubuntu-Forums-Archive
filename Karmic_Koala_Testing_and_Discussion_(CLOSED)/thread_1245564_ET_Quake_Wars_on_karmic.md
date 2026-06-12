---
title: "ET: Quake Wars on karmic"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-08-20
I just got Quake Wars. It doesn't play well with PulseAudio.

In jaunty (and older) you can easily use pasuspender to release /dev/dsp but that doesn't appear to work in jaunty.

Anyone playing it under karmic with sound (and with PA still installed)?

---

### Post by durand on 2009-08-20
pasuspender worked fine 3 weeks ago with qw but not now :S

---

### Post by BwackNinja on 2009-08-20
[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

method 4. works for me.

---

### Post by rajeev1204 on 2009-08-21
> **OliW said:**
> I just got Quake Wars. It doesn't play well with PulseAudio.

In jaunty (and older) you can easily use pasuspender to release /dev/dsp but that doesn't appear to work in jaunty.

Anyone playing it under karmic with sound (and with PA still installed)?


Iam using quake 4 with oss,withe the line quake4 +set s_driver oss.

Doesnt work with pulseaudio over alsa.

---

### Post by OliW on 2009-08-21
> **rajeev1204 said:**
> Iam using quake 4 with oss,withe the line quake4 +set s_driver oss.

w00t! Works well.

---

### Post by durand on 2009-08-21
> **OliW said:**
> w00t! Works well.

Doesn't work for me :S

I start etqw with this command:
```
padsp /usr/local/games/etqw/etqw-rthread +set s_driver oss
```

and I get this error:
> ------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OpenSound.com's OSS implementation. If you run Linux kernel OSS or Alsa OSS, don't bother.
WARNING: ioctl OSS_GETVERSION failed
close sound device
WARNING: sound subsystem disabled


I tried using pasuspender and that works however I have two soundcards (recently got a usb one) so I'm wondering if I can play music and other things through one and etqw through the other.

EDIT: Managed to do that by running pasuspender with etqw, then killing pulseaudio (so that it restarts) and then playing music as normal. Everything is routed through my usb card except for etqw :D

---

### Post by rajeev1204 on 2009-08-21
> **durand said:**
> Doesn't work for me :S

I start etqw with this command:
```
padsp /usr/local/games/etqw/etqw-rthread +set s_driver oss
```

and I get this error:


I tried using pasuspender and that works however I have two soundcards (recently got a usb one) so I'm wondering if I can play music and other things through one and etqw through the other.

EDIT: Managed to do that by running pasuspender with etqw, then killing pulseaudio (so that it restarts) and then playing music as normal. Everything is routed through my usb card except for etqw :D


install the package alsa-oss, then try from terminal etqw +set s_driver oss

---

### Post by durand on 2009-08-21
Thanks, that seems to half work. It seems  to be going through PA now but I can't control the volume of the stream, just of the whole device. The stream doesn't even show up in PA volume control.

---

### Post by rajeev1204 on 2009-08-21
> **durand said:**
> Thanks, that seems to half work. It seems  to be going through PA now but I can't control the volume of the stream, just of the whole device. The stream doesn't even show up in PA volume control.

If that is the case,you could allways kill pulseaudio.There are a lot of pulseaudio fixes coming through, so iam gonna try and use alsa again with this to see if it gives errors again.

Alsa sounds a little nicer to me.

---

### Post by durand on 2009-08-21
Yeah, it might work properly at some point.

---

