---
title: "Desktop bigger than the screen!!"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Pioden on 2010-05-11
I'm setting up Lucid for a friend and I've come across a strange problem - the desktop is bigger than the screen. 

The laptop is a Fujitsu Amilo Pro V2035 with a VIA S3G Unichrome graphics adapter. The desktop resoltion is 1600 ish - but the actual screen size is 1280x800. I've tried changing this in the Display settings but this results in an unreadable screen (refresh settings at a guess).

Can anyone suggest how I solve this? I've never come across the S3G chipset before.

---

### Post by wkulecz on 2010-05-11
I had the same problem initially with the "nouveau" open source Nvidia driver installed by default with a virgin install.  Managed to get the proprietary Nvidia driver installed and all is well now, it was a GeForce 210 card.

Unfortunately I've no experience with the S3G video chipset either.

---

### Post by Pioden on 2010-05-16
I'm slowly making some progress but could do with some assistance from someone who knows their xorg.conf!! I've got Lucid to create an Xorg.conf file which hopefully I can use to correct the screen resolution - problem is I don't know how to do it. I've hacked around a bit but nothing seems to work.

Xorg.conf file is below. At present the system thinks it has a 1600x1200 monitor screen. The reality is an 1280x800 screen. How do I modify xorg.conf to force the system to use the correct resolution?

TIA

Huw


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
    Load  "extmod"
    Load  "dri"
    Load  "dri2"
    Load  "record"
    Load  "dbe"
    Load  "glx"
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

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "PrintVGARegs"           # [<bool>]
        #Option     "PrintTVRegs"            # [<bool>]
        #Option     "I2CScan"                # [<bool>]
        #Option     "VBEModes"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "ExaNoComposite"         # [<bool>]
        #Option     "ExaScratchSize"         # <i>
        #Option     "SWCursor"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "RotationType"           # [<str>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoRAM"               # <i>
        #Option     "ActiveDevice"           # [<str>]
        #Option     "BusWidth"               # [<str>]
        #Option     "Center"                 # [<bool>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForcePanel"             # [<bool>]
        #Option     "TVDotCrawl"             # [<bool>]
        #Option     "TVDeflicker"            # <i>
        #Option     "TVType"                 # [<str>]
        #Option     "TVOutput"               # [<str>]
        #Option     "TVPort"                 # [<str>]
        #Option     "DisableVQ"              # [<bool>]
        #Option     "DisableIRQ"             # [<bool>]
        #Option     "EnableAGPDMA"           # [<bool>]
        #Option     "NoAGPFor2D"             # [<bool>]
        #Option     "NoXVDMA"                # [<bool>]
        #Option     "VbeSaveRestore"         # [<bool>]
        #Option     "DisableXvBWCheck"       # [<bool>]
        #Option     "ModeSwitchMethod"       # [<str>]
        #Option     "MaxDRIMem"              # <i>
        #Option     "AGPMem"                 # <i>
    Identifier  "Card0"
    Driver      "openchrome"
    VendorName  "VIA Technologies, Inc."
    BoardName   "CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]"
    BusID       "PCI:1:0:0"
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


```

---

### Post by Pioden on 2010-05-17
Shamesless bump! I'd like to try and get the laptop back to the owner tonight - with Ubuntu installed!. Would appreciate any help.

---

### Post by cryptotheslow on 2010-05-17
I'm no xorg expert by any means but I did have to manually edit my xorg.conf to get my screen resolution and refresh rates working right.

I think the crucial bits are the HorizSync and VertRefresh options in the "Monitor" section and the Option         "metamodes" "1024x768_75 +0+0"  in the "Screen" section.

Clearly 1024x768_75 is for 1024x768 at 75Hz - so tailor that line to suit your needs.


```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       31.0 - 70.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS250"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768_75 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by hardkorek on 2010-08-25
I also have this problem.

In previous relases following xorg.conf worked:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"openchrome"
	Option	"SWCursor"	"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1024	768
	EndSubSection
EndSection

```

I need help

---

