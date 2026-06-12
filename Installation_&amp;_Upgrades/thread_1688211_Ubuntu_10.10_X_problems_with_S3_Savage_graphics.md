---
title: "Ubuntu 10.10 X problems with S3 Savage graphics"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by IBM_T21 on 2011-02-15
Hello,

this is my first post, because the solutions didn't help me in my problem.
I'm using an IBM Thinkpad T21 with S3 Savage graphic card. Using Ubuntu 8.x
works fine, but now I installed Ubuntu 10.10 and I get problems with X.
After a fresh, clean installation I tried to start the hardware tests from menue.
When the video is testet, the screen became warped and misplaced and some seconds later I have to re-login. All open programms are closed. This behaviour is also when I try to switch in text-mode with CTRL+ALT+F1 with the difference the the complete system hangs.
One solution for the S3 graphics could be to start in recovery mode and to configure X new (X -configure). I restartet the system, but nothing changed. Then I modfied the conf-file with known T21 S3 savage setting, but still the same behaviour. 
Can anyone help me to find out whats the problem? At the moment I'm thinking about an installation of an older working version of ubunut.

Thanks and best regards,

IBM_T21

---

### Post by IBM_T21 on 2011-02-15
Ok, I testet my system a little bit more. After creating the xorg.conf, I could select different display resolutions. Regular is 1024x768 working. After changing to another resolution, the display became black and I have to re-login. Here is my xorg.conf - has some a hint for me?
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
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
    Load  "record"
    Load  "dri2"
    Load  "dri"
    Load  "glx"
    Load  "extmod"
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
    VendorName   "IBM"
    ModelName    "Thinkpad T21 LCD"
        HorizSync    31.5-48.5
        VertRefresh  50-70
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "HWCursor"               # [<bool>]
        #Option     "SWCursor"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "UseBIOS"                # [<bool>]
        #Option     "LCDClock"               # <freq>
        #Option     "ShadowStatus"           # [<bool>]
        #Option     "CrtOnly"                # [<bool>]
        #Option     "TvOn"                   # [<bool>]
        #Option     "PAL"                    # [<bool>]
        #Option     "ForceInit"              # [<bool>]
        #Option     "Overlay"                # [<str>]
        #Option     "TransparencyKey"        # [<str>]
        #Option     "ForceInit"              # [<bool>]
        #Option     "DisableXVMC"            # [<bool>]
        #Option     "DisableTile"            # [<bool>]
        #Option     "DisableCOB"             # [<bool>]
        #Option     "BCIforXv"               # [<bool>]
        #Option     "DVI"                    # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "DmaType"                # [<str>]
        #Option     "DmaMode"                # [<str>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DRI"                    # [<bool>]
        #Option     "AGPforXv"               # [<bool>]
    Identifier  "Card0"
    Driver      "savage"
        Vendorname  "S3 Inc."
        Option      "Use Bios" "true"
        Option      "ShadowStatus"
    BusID       "PCI:1:0:0"
        Boardname   "SuperSavage IX/C SDR"
        Option      "BusType" "PCI"
        Option      "DmaMode" "None"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
        DefaultDepth 24
    SubSection "Display"
        Viewport   0 0
        Depth     24
                Modes     "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
                Modes     "800x600"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
                Modes     "640x480"
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

```Thanks, IBM_T21

---

### Post by IBM_T21 on 2011-02-17
Hi, I solved the problem. Here is the working xorg.conf with used "vesa" driver:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
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
    Load  "record"
    Load  "dri2"
    Load  "dri"
    Load  "glx"
    Load  "extmod"
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
    VendorName   "IBM"
    ModelName    "Thinkpad T21 LCD"
#        HorizSync    31.5-48.5
#        VertRefresh  50-70
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "HWCursor"               # [<bool>]
        #Option     "SWCursor"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "UseBIOS"                # [<bool>]
        #Option     "LCDClock"               # <freq>
        #Option     "ShadowStatus"           # [<bool>]
        #Option     "CrtOnly"                # [<bool>]
        #Option     "TvOn"                   # [<bool>]
        #Option     "PAL"                    # [<bool>]
        #Option     "ForceInit"              # [<bool>]
        #Option     "Overlay"                # [<str>]
        #Option     "TransparencyKey"        # [<str>]
        #Option     "ForceInit"              # [<bool>]
        #Option     "DisableXVMC"            # [<bool>]
        #Option     "DisableTile"            # [<bool>]
        #Option     "DisableCOB"             # [<bool>]
        #Option     "BCIforXv"               # [<bool>]
        #Option     "DVI"                    # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "DmaType"                # [<str>]
        #Option     "DmaMode"                # [<str>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DRI"                    # [<bool>]
        #Option     "AGPforXv"               # [<bool>]
      Identifier  "Card0"
#    Driver      "savage"
      Driver      "vesa"
#    Vendorname  "S3 Inc."
      Vendorname    "Vesa"
      Option      "Use Bios" "true"
      Option      "ShadowStatus"
      BusID       "PCI:1:0:0"
      Boardname   "SuperSavage IX/C SDR"
      Option      "BusType" "PCI"
      Option      "DmaMode" "None"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
        DefaultDepth 24
    SubSection "Display"
        Viewport   0 0
        Depth     24
                Modes     "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
                Modes     "1024x768" "800x600" "640x480" "320x240"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
                Modes     "800x600" "640x480" "320x240"
    EndSubSection
EndSection


```

---

### Post by tormod on 2011-05-04
Little bit of a late reply, but I guess this issue is now fixed with the xserver-xorg-video-savage in maverick-updates.

---

