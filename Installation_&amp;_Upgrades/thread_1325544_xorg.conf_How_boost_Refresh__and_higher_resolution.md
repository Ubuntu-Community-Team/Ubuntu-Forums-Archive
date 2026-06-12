---
title: "xorg.conf How boost Refresh?  and higher resolution?"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by pwrcul on 2009-11-13
I installed Kubuntu 9.10 (32 bit) as a dual boot on an Athlon 64 X2 box.  I am hoping to migrate to Linux from Windows.

I managed to get 75 Hz at 1280x1024 so far in a stable way, but it precludes 1600x1200 at any refresh rate.
(On Win XP I get 85 Hz at 1280x1024 and 75 Hz at 1600x1200.)

I use a KVM switch also so I avoid EDID.

The monitor section of my current xorg.conf is below.

Section "Monitor"
#    Identifier     "Configured Monitor"
    Identifier	"Nokia 445Xi" 
    Option      "VenderName"     "Nokia"
    Option      "ModelName"      "445Xi"
#   Option      "DisplaySize"    395 298
    Option      "ModeValidation" "NoEdidModes"
    Option      "UseEDIDFreqs"   "False"
#   Option      "UseEDIDDpi"     "False"
    Option		"DPMS"
    Horizsync	30-102
    Vertrefresh	50-150
    Modeline "1280x1024" 188.40 1280 1312 2024 2056 1024 1043 1057 1076
    Modeline "1600x1200" 245.66 1600 1632 2560 2592 1200 1223 1238 1261
EndSection

The corresponding section of Xorg.0.log is below.

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEdidFreqs" "False"
(**) NVIDIA(0): Option "ModeValidation" "NoEdidModes"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.16.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:5:0:0:
(--) NVIDIA(0):     Nokia (CRT-0)
(--) NVIDIA(0): Nokia (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Mode Validation Overrides for Nokia (CRT-0):
(II) NVIDIA(0):     NoEdidModes
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (83, 89); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

You can see my video controller in the above.

If you can advice on how to insert a scroll box in a forum post like some I have seen I would appreciate it. I would have included the full text if I had a way to make it practical.

---

### Post by pwrcul on 2009-11-13
Progress, but related issue:  I can get 85 Hz for 1280x1024 and 75 Hz for 1600x1200.  That's the good news.

But I can't have both available without having a virtual screensize of 1600x1200.

If I add virtual 1280 1024, it eliminates the 1600x1200 option from the Nvidia X Server Settings choices.

Does anyone know how to limit 1280x1024 to the physical screen size and still be able to boost resolution higher without having to edit xorg.conf each time?

Here's the section of xorg.conf that almost does all that I want.

Section "Monitor"
#    Identifier     "Configured Monitor"
    Identifier  "Nokia 445Xi"
    Option      "UseEDID"   "False"
    Option              "DPMS"
    Option      "DPI"            "83 x 89"
    Horizsync   30-102
    Vertrefresh 50-150
    DisplaySize 395 298
# 1280x1024 84.84 Hz (CVT 1.31M4) hsync: 91.46 kHz; pclk: 159.50 MHz
    Modeline "1280x1024_85.00"  159.50  1280 1376 1512 1744  1024 1027 1034 1078 -hsync +vsync
# 1600x1200 74.98 Hz (CVT 1.92M3) hsync: 94.09 kHz; pclk: 204.75 MHz
    Modeline "1600x1200_75.00"  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device      "NVIDIA GeForce 6600"
    Monitor             "Nokia 445Xi"
    Defaultdepth        24
    SubSection "Display"
        Depth   24
        Modes   "1280x1024" "1600x1200" "1024x768" "800x600" "640x480"
        virtual     1280 1024
    EndSubSection

---

