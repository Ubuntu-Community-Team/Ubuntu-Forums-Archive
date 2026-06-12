---
title: "Odd fix for i8xx chipset xorg freeze in 10.04"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by jp40684 on 2010-05-18
Now, this works for me for reasons I'm not going to try and pretend to understand.  I only know that this works (for now) for me without reverting to the vesa driver as detailed in [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes ]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

I'm using the intel 855gm chipset on an old dell inspiron 700m  laptop (really, I just need to buy a new laptop :)).  After updating to 10.04, the laptop froze to a blank black screen on boot (after grub).  Using Workaround A in the link above got me to some boot code or sometime the Ubuntu splash screen before freezing, so I figured Workaround F was the way to go.  Of course I've since then learned that AccelMethod and VideoRam are moot.  BUT I made a typo while editing my xorg.conf file, which gave me the "Linux running on low graphics mode" (or whatever it says).  I chose to boot anyway, and everything works fine.  Videos, 3D graphics, everything I've been able to test so far.  If I take out the text in the xorg.conf file that can't be parsed, I'm back to the freezes.  So, I'm ignorant here, but I thought it might help someone else out for the time being.  OR maybe I'm being a complete idiot! :P 

My xorg.conf file:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "extmod"
    Load  "glx"
    Load  "dri"
    Load  "record"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82852/855GM Integrated Graphics Device"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Option "MonitorLayout" "TV,LFP"
    Option "Clone" "yes"
    Identifier  "Card1"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82852/855GM Integrated Graphics Device"
    BusID       "PCI:0:2:1"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

purperr #my parse error that lets me boot

```Additionally, getting this message every time I boot is kind of an annoyance, so if anyone has any helpful advice, I'll gladly take it.

---

### Post by fanum on 2010-06-30
I have updated [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) with a potential solution for this chipset. I have used it on that exact model of laptop, and now have working intel drivers and compiz

---

