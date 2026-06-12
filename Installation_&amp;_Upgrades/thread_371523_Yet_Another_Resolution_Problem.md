---
title: "Yet Another Resolution Problem"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by rabidgnome229 on 2007-02-27
I have used every guide to installing nvidia drivers that exists, checked and rechecked xorg.conf, and scoured 10+ pages of google results looking for a  fix.  I cannot get my Acer AL1917W to display in 1440x900

Here is my xorg.conf (the important bits)

```
Section "Monitor"
    Identifier     "Acer AL1917W"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 7600gt"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 7600gt"
    Monitor        "Acer AL1917W"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection
```

There are many resolutions available to be selected - none of which are correct.  The closest is 1400x1050.  All available res's are 4:3

Why does ubuntu hate me? :(

---

