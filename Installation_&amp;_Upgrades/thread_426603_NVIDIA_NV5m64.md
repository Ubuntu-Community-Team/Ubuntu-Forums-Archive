---
title: "NVIDIA NV5m64"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Woody@N87 on 2007-04-28
Hope this is the correct place for this, I have upgraded to 7.04 and since then have had problems with the display.  Tough to explain but the contrast sucks and there is this weird horizontal ghosting of anything on the screen.  Version 6.10 seemed fine.  I have an nVidia Corporation NV5M64 and here is the output of my xorg.conf

```
Section "Device"
    Identifier  "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64
Pro]"
    Driver      "nv"
    BusID       "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier  "DELL 1702FP"
    Option      "DPMS"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Device      "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    Monitor     "DELL 1702FP"
    DefaultDepth    24
    SubSection "Display"
        Depth       1
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       4
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       8
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       15
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       16
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       24
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

Anything jump out at anyone here?
 Thanks in advance,
           Mike

---

