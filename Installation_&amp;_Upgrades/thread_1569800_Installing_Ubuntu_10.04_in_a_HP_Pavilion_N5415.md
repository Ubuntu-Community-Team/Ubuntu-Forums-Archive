---
title: "Installing Ubuntu 10.04 in a HP Pavilion N5415"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by Claudio Bogado Pompa on 2010-09-07
I manage to install Ubuntu 10.04 in a HP Pavilion N5415 without cdrom with the PLOP boot manager floppy and a USB stick (this notebook bios does not support usb boot).
I can't have the 1024x768 resolution of the screen, I only have 800x600.
I created a xorg.conf.new to test posible solutions with sudo Xorg -configure with the gdm service stopped (sudo service gdm stop).
I edited the xorg.conf.new file with sudo pico xorg.conf.new.
I added in the screen section:
```
SubSection "Display"
Depth 24
Virtual 1024 768
Modes "1024x768"
EndSubSection
```
When trying the xorg.conf.new with sudo X -config xorg.conf.new I get error setting MTRR (base = 0xec000000, size = 0x00800000, type = 1) Inappropiate ioctl for device (25).
What can I do to fix this?
The video card is a Trident CyberbladeXP.
Greetings from Paraguay

---

### Post by Claudio Bogado Pompa on 2010-09-14
I saved this code on /etc/X11/xorg.conf and it solved my problem:
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
    Load  "dri2"
    Load  "glx"
    Load  "dri"
    Load  "record"
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
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    Horizsync 31.5-48.0
    VertRefresh 56.0-65.0
    modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma 1.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "SetMClk"                # <freq>
        #Option     "MUXThreshold"           # <i>
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "NoMMIO"                 # [<bool>]
        #Option     "NoPciBurst"             # [<bool>]
        #Option     "MMIOonly"               # [<bool>]
        #Option     "CyberShadow"            # [<bool>]
        #Option     "CyberStretch"           # [<bool>]
        #Option     "XvHsync"                # <i>
        #Option     "XvVsync"                # <i>
        #Option     "XvBskew"                # <i>
        #Option     "XvRskew"                # <i>
        #Option     "FpDelay"                # <i>
        #Option     "Display1400"            # [<bool>]
        #Option     "Display"                # [<str>]
        #Option     "GammaBrightness"        # [<str>]
        #Option     "TVChipset"              # [<str>]
        #Option     "TVSignal"               # <i>
    Identifier  "Card0"
    Driver      "trident"
    VendorName  "Trident Microsystems"
    BoardName   "CyberBlade/XP"
    BusID       "PCI:1:0:0"
    Screen 0
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
        Modes "1024x768@60"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
        Modes "1024x768@60"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
        Modes "1024x768@60"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
        Modes "1024x768@60"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes "1024x768@60"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes "1024x768@60"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth 32
        Modes "1024x768@60"
    EndSubSection
EndSection
```

---

