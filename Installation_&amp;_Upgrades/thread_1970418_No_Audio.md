---
title: "No Audio"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by daimas on 2012-05-01
Fresh install of 12.04 
Sound card points to HDMI and don't have HDMI
Don't know how to change it - I'm a newbie...

3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
penelope@penelope-RC659AA-ABA-a1632x:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
penelope@penelope-RC659AA-ABA-a1632x:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
penelope@penelope-RC659AA-ABA-a1632x:~$ head -n 1 /proc/asound/card*/codec#*

---

