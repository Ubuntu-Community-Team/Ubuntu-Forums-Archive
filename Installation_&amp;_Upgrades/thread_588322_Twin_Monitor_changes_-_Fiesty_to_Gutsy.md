---
title: "Twin Monitor changes - Fiesty to Gutsy"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by thewump on 2007-10-23
Can someone advise.

Bottom line, I've gone from 2 x 1600x1200 monitors in fiestly to effectively 1 x 3200x1200 in Gutsy.

In Fiesty I used nvidia-settings to get things setup and spit out the right xorg.conf settings for me, and I'm still using the same xorg.conf, but here's my Gutsy experience:

In Adminstration > Screens & Graphics

If I configure screens 1 and 2 as 1600x1200, and configure screen 2 to be an extended RIGHT of screen 1, it instead is just a mirror.

It's driving me nuts, because of course, AWN and new windows are right there in middle split between both screens and spinning the cube seems like I'm spinning a monstor..

NVIDIA 7600 GT ( and an onboard nvidia card not being used )

xorg.conf:

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Screen0" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        Fontpath        "/usr/share/X11/fonts/misc"
        Fontpath        "/usr/share/X11/fonts/cyrillic"
        Fontpath        "/usr/share/X11/fonts/100dpi/:unscaled"
        Fontpath        "/usr/share/X11/fonts/75dpi/:unscaled"
        Fontpath        "/usr/share/X11/fonts/Type1"
        Fontpath        "/usr/share/X11/fonts/100dpi"
        Fontpath        "/usr/share/X11/fonts/75dpi"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dbe"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "type1"
        Load            "vbe"
EndSection

Section "ServerFlags"

        # Removed Option "Xinerama" "1"
        Option          "Xinerama"      "0"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"

        # /dev/input/event
        # for USB
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/wacom"# Change to 
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

        # /dev/input/event
        # for USB
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/wacom"# Change to 
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

        # /dev/input/event
        # for USB
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/wacom"# Change to 
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "HP w19b/w19e"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        Vendorname      "Unknown"
        Modelname       "DELL 2000FP"
        Horizsync       31.0    -       80.0
        Vertrefresh     56.0    -       76.0
EndSection

Section "Monitor"
        Identifier      "Monitor1"
        Vendorname      "Unknown"
        Modelname       "DELL 2000FP"
        Horizsync       31.0    -       80.0
        Vertrefresh     56.0    -       76.0
EndSection

Section "Device"

        # I think this is the onboard
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "nvidia"
        Vendorname      "NVIDIA Corporation"
        Boardname       "GeForce 7600 GT"
EndSection

Section "Device"
        Identifier      "Videocard1"
        Driver          "nvidia"
        Vendorname      "NVIDIA Corporation"
        Boardname       "GeForce 7600 GT"
        Busid           "PCI:2:0:0"
        Screen  1
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "HP w19b/w19e"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Depth   1
                Modes           "1440x1440"     "1280x1024"     "1280x960"     "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1440x1440"     "1280x1024"     "1280x960"     "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1440x1440"     "1280x1024"     "1280x960"     "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1440x1440"     "1280x1024"     "1280x960"     "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1440x1440"     "1280x1024"     "1280x960"     "1152x864"       "1024x768"      "832x624"       "800x600"       "720x400"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1600x1200"     "1440x1440"     "1280x1024"    "1280x960"       "1152x864"      "1024x768"      "832x624"       "800x600"      "720x400"        "640x480"
        EndSubSection
EndSection

Section "Screen"

        # Removed Option "TwinView" "0"
        # Removed Option "metamodes" "DFP-0: 1600x1200 +0+0; DFP-0: 1280x1024 +0+0; DFP-0: 1280x960 +0+0; DFP-0: 1152x864 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 832x624 +0+0; DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0"
        Identifier      "Screen0"
        Device          "Videocard0"
        Monitor         "Monitor0"
        Defaultdepth    24
        Option          "TwinView"      "1"
        Option          "metamodes"     "DFP-0: 1600x1200 +0+0, DFP-1: nvidia-auto-select +1600+0; DFP-0: 1280x1024 +0+0; DFP-0: 1280x960 +0+0; DFP-0: 1152x864 +0+0; DFP-0: 1024x768 +0+0; DFP-0: 832x624 +0+0; DFP-0: 800x600 +0+0; DFP-0: 640x480 +0+0"
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Videocard1"
        Monitor         "Monitor1"
        Defaultdepth    24
        Option          "TwinView"      "0"
        Option          "metamodes"     "DFP-1: nvidia-auto-select +0+0"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

THANKS IN ADVANCE!

Keith

---

