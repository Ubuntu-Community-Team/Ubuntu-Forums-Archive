---
title: "nvidia GT 240, HDMI audio not working"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by taxman10m on 2010-04-03
I'm using a Dell Studio Desktop 540 with an NVidia GT 240 video card.  HDMI audio doesn't seem to work.  I searched through the forums but didn't see much to help.  

Running aplay -L gives me this:
```

pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output

```

---

### Post by Naitsirhc Hsem on 2010-04-03
from what I have heard, hdmi audio out is hit or miss depending on the card

---

### Post by jonnan on 2010-04-03
I'm fighting the same issue in the GT240, nothing seems to recognize the nvidia HDMI as a potential output.

As a quick warning, I did try for a time a .asound file I found on a forum with the settings
----
defaults.pcm.!card NVidia
defaults.ctl.!card NVidia
defaults.pcm.!device 3
defaults.ctl.!device 3
----
which did nothing for awhile, then evidently broke everything - I lost sound completely until I figured out it had not only broken my MythTV sound, but was actually preventing recognition of *any* hardware. Just so you are aware that that can evidently cause a delayed reaction if you try it.

On the other hand, if you get it to work, I'm all ears - <G>

Jonnan

---

