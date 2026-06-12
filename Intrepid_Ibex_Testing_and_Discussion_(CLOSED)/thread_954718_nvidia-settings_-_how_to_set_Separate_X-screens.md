---
title: "nvidia-settings - how to set Separate X-screens?"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kokesh on 2008-10-21
How should I change my Twinview setup (CRT+TV) to separate X-Screens?
nvidia-settings destroys xorg.conf. I have tried to fix it manually, also by copying monitor,device and screen sections from nvidia-settings xorg.conf preview, but without success. Attaching my xorg.conf.

Thanks for help, I hope this bug will be fixed soon :)

---

### Post by adam_kimber on 2008-10-21
> **Kokesh said:**
> 
nvidia-settings destroys xorg.conf. 

It shouldn't! Mine doesn't. What happens? Does X fail to restart? 

If you are tring to get a totally different output per screen i.e. KDE on one screen and Gnome on the other that do not interact, i.e. drag from one to the other, then I think you are after two simultaneous x servers, which I think is not recommended... Check [this]("http://ubuntuforums.org/showthread.php?t=112498") out. 

If you are after an alternative to Twinview. Xinerama is an option. I never got xinerama to work how i wanted but it might be better now. Have a look at [this,]("http://ubuntuforums.org/showthread.php?t=732060") which might help. This might be of [help]("http://ph.ubuntuforums.com/showthread.php?t=844048").....

Twinview can be temperamental. Have a look at [this]("http://ubuntuforums.org/showthread.php?t=782131") for some ideas. Or [this]("http://ph.ubuntuforums.com/showthread.php?t=886938").

---

### Post by jocko on 2008-10-21
Try this. I added your wacom devices, CRT-monitor and keyboard settings into my working xorg.conf (you may need to change some settings, see my comments in red).

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0" [COLOR=Red]#LeftOf, Above, Below[/COLOR]
    InputDevice    "Keyboard" "CoreKeyboard"
    InputDevice    "Mouse" "CorePointer"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "eraser"    "SendCoreEvents"
    InputDevice    "cursor"    "SendCoreEvents"
EndSection

Section "Module"
    Load    "dbe"
    Load    "extmod"
    Load    "type1"
    Load    "freetype"
    Load    "glx"
    Disable    "dri2" [COLOR=Red]#Never tried this. Probably safe to leave here?[/COLOR]
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "yes"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"        "/dev/input/wacom"
    Option        "Type"          "stylus"
    Option        "USB"           "on"
    Option        "ForceDevice"   "ISDV4"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"        "/dev/input/wacom"
    Option        "Type"          "eraser"
    Option        "USB"           "on"
    Option        "ForceDevice"   "ISDV4"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"        "/dev/input/wacom"
    Option        "Type"          "cursor"
    Option        "Mode"          "relative"
    Option        "USB"           "on"
    Option        "ForceDevice"   "ISDV4"
EndSection

Section "InputDevice"
    Identifier "Keyboard"
    Driver "kbd"
    Option "CoreKeyboard"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us,cz,se"
    Option "XkbVariant" ",winkeys"
    Option "XkbOptions" "grp:ctrl_shift_toggle,grp_led:scroll"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AOC Spectrum7F"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: 1152x864_75 +0+0, TV: nvidia-auto-select +1152+0"
    Option "PixmapCacheSize" "2000000" [COLOR=Red]#Probably not required, remove if it doesn't work[/COLOR]
    Option "AllowSHMPixmaps" "0"       [COLOR=Red]#Probably not required, remove if it doesn't work[/COLOR]
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    Option         "TVStandard" "PAL-G"      [COLOR=Red] #Change this to your TV standard[/COLOR]
    Option         "TVOutFormat" "SVIDEO"     [COLOR=Red]#Or Composite[/COLOR]
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by Kokesh on 2008-10-21
This is how it look like after upgrading to Ibex. I read somewhere that nvidia-settings is having some problems with new Xorg, but none of the workarounds helped me. It also screams something about problems with parsing the xorg.conf file (before saving crappy xorg.conf) - whet I restart, X starts in emergency mode saying something about missing screen 0, etc, I probably have to wait for some fix. 

What I want to achieve is to have two separate X screens. Now I have twinview, which is perfectly working, except wallpaper stretched over both screens (I have to make special version of it, first half with the actual image of the CRT's resolution and second with TV's res, which is annoying - no big deal, I was just curious) - before I've just switched Separate Xscreens and Twinview as many times I wanted withou any problems)

---

### Post by kcam01 on 2008-10-21
Im having a problem with twinview and xinerama. I have 1 video card with dual output and 1 with a single out. In 8.04 twinview with xinerama worked fine. Now when I try that configuration Xwindows fails to load.

The motiors come out of sleep mode and it tries to start but it keeps falling like its stuck in a loop. This is the tail end of the log. 

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources


Here is my current conf with xinerama disabled:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL1916W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "JWY"
    HorizSync       31.5 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:3:8:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150 LE"
    BusID          "PCI:0:5:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-au
to-select +1440+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

I would love to get xinerama working again if possible. Any help would be appreciated.

---

