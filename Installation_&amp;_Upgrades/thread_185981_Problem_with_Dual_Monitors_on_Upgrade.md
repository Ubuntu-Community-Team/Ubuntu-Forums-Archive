---
title: "Problem with Dual Monitors on Upgrade"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by judas on 2006-06-01
I just upgraded from Breezy to Dapper, and the same xorg.conf file that had been working with Breezy isn't working right now.  Instead of seeing a merged desktop stretched across 2 monitors, the monitors mirror each other, and the desktop on each scrolls - in other words, they each are simulating 2560x1024 on a 1280x1024 screen.

My xorg.conf file...

```
Section "ServerLayout"
        Identifier     "Simple Layout"

        Screen         "Display Merged"

        InputDevice    "Configured Mouse" "CorePointer"
        InputDevice    "Generic Keyboard" "CoreKeyboard"
EndSection



Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
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

Section "Device"
        Identifier      "Matrox Graphics, Inc. MGA G400 AGP"
        Driver          "mga"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor L"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Display Merged"
        Device          "Matrox Graphics, Inc. MGA G400 AGP"
        Monitor         "Generic Monitor L"
        DefaultDepth    24

        Option      "Monitor2Position" "RightOf"
        Option      "MergedFB" "on"
        Option      "MetaModes" "1280x1024-1280x1024"
        #Option      "Monitor2HSync" "30.0 - 133.0"
        #Option      "Monitor2VRefresh" "50.0 - 85.0"

        SubSection "Display"
                Virtual  2560 1024
                Depth    16
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection

        SubSection "Display"
                Virtual  2560 1024
                Depth    24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

If anyone can be of assistance, I'd appreciate it.

---

### Post by FryerFox on 2006-06-01
You need a block that looks like the following:

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen 1" LeftOf "Screen 2"
        Screen          "Screen 2"
        Option          "Xinerama" "on"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

If I remember correctly, Xinerama is responsible for breaking the desktop into two.

---

### Post by autocrosser on 2006-06-01
You should also take a look at the driver support--In a terminal type "man (your driver)" & see the options--I am using FBMerged with a ATI card (PPC system).
 
I'm at work right now--I'll post my xorg this evening----

---

### Post by judas on 2006-06-01
[QUOTE=FryerFox]You need a block that looks like the following:

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen 1" LeftOf "Screen 2"
        Screen          "Screen 2"
        Option          "Xinerama" "on"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection
```

If I remember correctly, Xinerama is responsible for breaking the desktop into two.[/QUOTE]

I will try this, but doing so in Breezy gave me 2 seperate desktops, rather than a merged desktop, and the previous xorg.conf I posted worked fine.

EDIT: This works the same way on Dapper - both monitors are working, but as seperate desktops, not stretched.

EDIT 2: I had forgotten the Xinerama option.  When I add that, it works basically the way I wanted it - the desktop extends onto the second monitor.  It is not stretched, like my previous configuration in Breezy, but it actually works better this way.

Thanks for the help!

---

### Post by Silen on 2006-06-04
I see you have a Matrox G450 - this should fix your problem:
[http://www.tuxx-home.at/archives/2006/06/04/T14_46_29/](http://www.tuxx-home.at/archives/2006/06/04/T14_46_29/)

---

