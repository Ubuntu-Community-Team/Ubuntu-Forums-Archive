---
title: "Cannot detect any Output Sound hardware"
date: 2014-11-05
forum: Installation &amp; Upgrades
---

### Post by shikhar38 on 2014-11-05
I am running ubuntu 14.04 64-bit with the latest updates. I am unable to see any Output sound hardware. My board has an onboard soundcard but it is not detected. 

```
aplay -l
``` gives the output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia_1 [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

No HDA Intel device is shown. Can anyone help?

---

