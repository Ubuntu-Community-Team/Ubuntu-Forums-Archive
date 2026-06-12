---
title: "Ubuntu Karmic vs. ATI Radeon Mobility 9600"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-10-04
Okay, out of the box, Jaunty performance was crap until I modified the xorg.conf file as below:

Section "Device"
Identifier     "Configured Video Device"
Option         "AccelDFS"                            "on"
Option         "AccelMethod"                         "XAA"
Option         "MigrationHeuristic"                  "smart"
Option         "EnablePageFlip"                      "on"
Option         "EnableDepthMoves"                    "on"
Option         "ColorTiling"                         "on"
Option         "FBTexPercent"                        "0"
Option         "RenderAccel"                         "on"
EndSection


With Karmic, I see no xorg.conf

How do I get my 2D performance back?

---

### Post by bacardiandwatermelon on 2009-10-04
```
Xorg -configure
```
Should create a new xorg.conf in your home directory... edit it and move it to /etc/X11/

---

### Post by crjackson on 2009-10-04
> **bacardiandwatermelon said:**
> ```
Xorg -configure
```
Should create a new xorg.conf in your home directory... edit it and move it to /etc/X11/

Okay, and if it doesn't work or messes something up, can a safely delete it and just reboot to return to the previous settings?

Also, I'm wondering how come there isn't one.  Does Ubuntu not use this by default anymore?

---

### Post by autocrosser on 2009-10-04
Everything is done "on the fly" by xorg--If it looks in /etc/X11 & finds a xorg.conf, it will use it--if there isn't one it creates one with probed values--so if you change things it will "adapt" to the changes....... Sounds Borg-like :)

I created one for my system--I use a nvidia-SLI system & xorg can't work with that yet....

Just plug-in your values into mine....

```
#Custom Xorg

Section "Monitor"
    Identifier    "Monitor0"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth    24
        Modes    "1920x1200" "1680x1050"    "1600x1200" "1440x900" "1280x1024" "1024x768"
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "ServerLayout"
    Identifier      "Single-Monitor"
    Screen         "Screen0"
EndSection

Section "Device"
    Identifier       "Videocard0"
    Vendorname  "NVIDIA Corporation"
    Boardname    "GeForce 9800 GT"
    Driver            "nvidia"
    BusID            "2:0:0"
    Option           "Coolbits"     "1"
    Option           "SLI"             "Auto"
    Option           "ModeValidation" "AllowInterlacedModes"
    Option           "ModeValidation" "NoVesaModes"
    Option           "FlatPanelProperties" "Scaling = Native"
    Option           "IncludeImplicitMetaModes" "False"
    Option           "UseEvents"      "True"
    Option           "NoLogo"     "True"
EndSection

Section "ServerFlags"
    Option            "DontZap"    "False"
EndSection

```As you can see, it's a real basic xorg with only the values that I don't want auto-configured defined in.......If you b0rk the xorg--just reboot & pop in a LiveCD & remove the xorg.conf you made--then reboot again--no mess, no fuss

---

### Post by crjackson on 2009-10-11
Well, I created my xorg.conf finally.  I put in my previously tweaked ATI settings and my system is back to normal (as compared to Jaunty).  It's much snappier and I'm feeling much better about thing.

I just wish it would perform like this out of the box.  It's still not up to par as compared to Hardy with proprietary drivers.

Oh well, maybe 10.04 will bring better ATI community drivers.

---

### Post by peakshysteria on 2009-10-11
Like last time my upgrade to Karmic worked smooth out of the box. Even with Compiz everything runs very smooth. Forwarding movies in VLC doesn't tear or hang VLC. Like with Jaunty I'm extremely happy with Ubuntu out of the box :)

---

