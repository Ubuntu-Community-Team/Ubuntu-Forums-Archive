---
title: "fglxr not working"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bo Rosén on 2008-10-29
I upgraded from Hardy yesterday and most things went very smoothly, however like a few others I can't get fglrx to work.
I have a Radeon 9500 Pro and am less intersted in fancy 3d effects than tv-out to work properly.

X won't use the proprietary driver, which is installed but does not show up in jockey, and falls back to failsafe graphics mode.

My old xorg.conf looks like this
```


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    Screen         "aticonfig-Screen[0]-1" RightOf "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    Option        "" "DDX"
    Option        "DesktopSetup" "horizontal"
    Option        "Mode2" "1024x768"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```/var/log/Xorg.0.log.old has this to say
```

(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.54.3
    Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.54.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.543.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 10 2008 21:37:39
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

```Is this something to do with AGP?

I tried installing the drivers manually and run aticonfig --initial -f which produces this unhappy response:

Uninitialised file found, configuring.
Segmentation fault

Any ideas?

---

### Post by sdowney717 on 2008-10-29
yes, it does not work for many people with a 9000 series card.
it did not work for my 9600 either.
I get no devices detected and ubuntu runs in low graphics mode.

The good news is an x1300 works just fine.
could it be fixed, who knows but so far for weeks it has not and we are at release time.

this is likely an issue with the fglrx driver? And perhaps AMD forgot to remember about all the old card people out there.
so what do people with laptops and 9000 series card do?

We should start a poll and see who has what card working with fglrx

---

### Post by Bo Rosén on 2008-10-29
Maybe I should try the open source driver. Is it possible to get different resolutions on my monitor and tv with that?

---

### Post by jfelts on 2008-10-29
open source driver works fine, but your not going to get any 3d acceleration.

---

### Post by Bo Rosén on 2008-10-29
> **jfelts said:**
> open source driver works fine, but your not going to get any 3d acceleration.

Thanks. Just need to figure out how to get tv-out to work.  ;)

---

