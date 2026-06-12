---
title: "Any one else experiencing poor 2D peformance integrated intel gma965"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bigbrovar on 2009-10-24
My laptop performs very poorly for 2d graphics. For example,  Kwin effects are very choppy. and the whole desktop experience feels slow. In Jaunty, I was able to fix this by adding the following line under the "Device" section in my xorg.conf:

Option "MigrationHeuristic" "greedy"
In Karmic, there is no xorg.conf by default, so I copied my old one (from Jaunty). However, everything is still slow. Here is my xorg.conf:

Section "Device"
    Identifier  "Configured Video Device"
    Option      "MigrationHeuristic" "greedy"
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor             "Configured Monitor"
    Device              "Configured Video Device"
EndSection
From googling about, it sounds like "MigrationHeuristic" is only an option for the "EXA" mode, while Karmic has switched the intel driver to "UXA". So I tried adding this line under the "Device" section:

Option "AccelMethod" "exa"
But this didn't help.

anyone else experiencing this on karmic? and is there a way to tweak UXA to be faster?

---

### Post by bigbrovar on 2009-10-24
I found a bug report has already been filed concerning the issue If you are affected you can sub it here [https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/416073](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/416073)

---

### Post by PatrikG on 2009-10-25
Same thing on the intel 945 graphics. Good 2D performance in Jaunty and now just terrible in Karmic. 

I sure hope they fix it otherwise I'm moving back to Jaunty...

---

