---
title: "[kubuntu] lost sound"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wizard10000 on 2009-09-26
Had this problem with Jaunty and had to fix it myself with policykit.  It worked fine until last night's updates were applied.

policykit in kubuntu doesn't have much of a user interface yet - but check this out:

```
wizard@wizard-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...
wizard@wizard-desktop:~$ **sudo** aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wizard@wizard-desktop:~$
```

Wonder if I can fix it without installing ubuntu-desktop?  I did just download policykit-doc so I guess we'll find out.

---

### Post by wizard10000 on 2009-09-27
Solved with last night's updates.

---

