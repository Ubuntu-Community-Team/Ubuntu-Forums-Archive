---
title: "pcidata module problems after upgrading to Fiesty"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by suso on 2007-04-27
Hi.  I upgraded from Edgy to Fiesty yesterday and now when i try to start gdm with my old xorg.conf file, it errors out saying

```
(II) Loader running on linux
(II) LoadModule: "pcidata"
(WW) Warning, couldn't open module pcidata
(II) UnloadModule: "pcidata"
(EE) Failed to load module "pcidata" (module does not exist, 0)

Fatal server error:
Unable to load required base modules, Exiting...

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
```

I am running the nvidia module and using twinview if that makes any difference.  The weird thing is that I can load a single monitor xorg.conf just fine with the nvidia module.  So it sounds like something with twinview, but I can't see what.   There are practically no other posts about this problem.

Here is my xorg.conf:

```

Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        RgbPath      "/usr/lib64/X11/rgb"
        ModulePath   "/usr/lib64/modules"
        FontPath     "/usr/share/fonts/misc/"
        FontPath     "/usr/share/fonts/TTF/"
        FontPath     "/usr/share/fonts/Type1/"
        FontPath     "/usr/share/fonts/CID/"
        FontPath     "/usr/share/fonts/75dpi/"
        FontPath     "/usr/share/fonts/100dpi/"
EndSection

Section "Module"
        Load  "record"
        Load  "extmod"
        Load  "dbe"
        Load  "dri"
        Load  "glx"
        Load  "xtrap"
        Load  "freetype"
        Load  "type1"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "IMPS/2"
        Option      "Device" "/dev/psaux"
    Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
         Option     "AllowGLXWithComposite"      "1"
         Option     "LoadKernelModule"           "0"
         Identifier  "Card0"
        Driver      "nvidia"
        VendorName  "nVidia Corporation"
        BoardName   "Quadro FX 1400 128MB"
        BusID       "PCI:5:0:0"
EndSection


Section "Screen"
       Identifier   "Screen0"
       Device       "Card0"
       Monitor      "Monitor0"
       DefaultDepth    24
       Option "TwinView " "on"
       Option "TwinViewOrientation" "LeftOf"
       Option "MetaModes" "1600x1200,1600x1200;1280x1024,1280x1024;1280x1024,1024x768;1280x1024,NULL;1280x1024,1280x1024+1200+0"
       #Option "SecondMonitorHorizSync" "30 - 96.0"
       #Option "SecondMonitorVertRefresh" "50 - 120"
       Subsection "Display"
               Depth       24
               Modes       "1600x1200" "1280x1024" "1152x864" "1024x768"
       EndSubsection
EndSection

```

I'd REALLY appreciate some help on this as this is my primary work computer and I need to get it working today if possible.  In the worst case, i can use the single monitor config, but it will make me feel dirty. :frown:

---

### Post by suso on 2007-04-27
Actually, I managed to get my twinview configuration working again by pseudo merging the the working one monitor config with the device and screen section of the twinview config.  I would still like to know why it was giving me the pcidata error as it might cause problems later.

---

