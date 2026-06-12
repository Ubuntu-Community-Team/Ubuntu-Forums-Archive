---
title: "Dual screen problem"
date: 2005-03-10
forum: Installation &amp; Upgrades
---

### Post by doc_holiday on 2005-03-10
I'm trying to get a two screens working on a Compaq nc8000 ati video controler.
My config is the following:

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/Speedo"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
        Load    "xtt"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "be"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Driver          "ati"
        Screen          0
        BusID           "PCI:1:0:0"
EndSection


Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Driver          "ati"
        Screen          0
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Monitor1"
        HorizSync       30-67
        VertRefresh     50-75
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Monitor2"
        HorizSync       30-67
        VertRefresh     50-75
        Option          "DPMS"
EndSection


Section "Screen"
        Identifier      "Screen1"
        Device          "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Monitor         "Monitor1"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen2"
        Device          "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Monitor         "Monitor2"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Option          "Xinerama" "On"
        Option          "Twinview" "On"
        Screen          "Screen1"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        Screen          "Screen2" RightOf "Screen1"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by rsay on 2005-03-10
I had a problem with dual screen on Xorg 6.8.* where I could only see a mirror of screen 1 on screen 2 with the radeon driver. I have a radeon mobility M6 which isn't supported by fglrx. My problem went away with a switch back to XFree instead of Xorg.

---

### Post by doc_holiday on 2005-03-10
That's the problem I have, can you tell me how to change? I'm rather new to linux.

---

### Post by Leif on 2005-03-10
Try putting 

        Option          "Clone" "off"

in the ServerLayout section. Also, I'm not sure you need both Xinerama and Twinview on. If you've got a dualhead card, Twinview on its own should do it.

---

### Post by doc_holiday on 2005-03-10
[QUOTE=Leif]Try putting 

        Option          "Clone" "off"

in the ServerLayout section. Also, I'm not sure you need both Xinerama and Twinview on. If you've got a dualhead card, Twinview on its own should do it.[/QUOTE]

tried the clone off before, didn't work. Also tried Xinerama en twinview sepperate. None of it worked.

---

### Post by Leif on 2005-03-11
Does setting both screens to the same resolution change anything ?

---

