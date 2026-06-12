---
title: "Upgraded to Edgy and lost virtual resolution"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by Pig on 2007-07-15
Hello,

I've just upgraded from Dpper to Edgy today. All was well except that X broke. So I ran ```
dpkg-reconfigure xserver-xorg
```
and it worked. Unfortunately, I am no longer able to cycle through resolutions using ctrl+alt++ and ctrl+alt+-. I can easily change to other resolutions using System->Preferences->Screen Resolution (so all the drivers are working) but, of course its not virtual resolution. I tried many random things to fix this problem today such as editing xorg.conf (adding "virtual 1600 1200"). Also ctrl, alt and the numpad keys all seem to be functioning properly.

Please help. Also, if anyone knows what program captures the keystrokes (ctrl+alt++) and how/if it is logged, that may also be helpful.

Here is the Screen section of my xorg.conf:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "S/M 900NF"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        Virtual    1600 1200
    EndSubSection
EndSection

Section "Extensions" 
        Option  "Composite" "Disable"
EndSection
```

---

