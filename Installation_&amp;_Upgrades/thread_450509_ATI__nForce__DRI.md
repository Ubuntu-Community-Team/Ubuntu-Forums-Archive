---
title: "ATI / nForce / DRI"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by philzli on 2007-05-21
And now, Ladies and Gentlemen, another thread by a despaired guy, trying to get his DRI/3D Accl. to work.

To keep it short:
Feisty Kubuntu,
AMD/ATI X800 XT (Asus)
nForce4 (Asus A8N)

Nice stuff from my Xorg.0.log:
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

I am sure this is the correct BusID, I am sure that I use the current fglrx driver.

[B]What did you guys out there do to get it to work?

Do I need to install an older driver?
Do I need to install some nForce specific drivers?[/B]

```
Section "device" #
        Identifier      "ATI Graphics Adapter1"
        Driver  "fglrx"
        Option  "VideoOverlay" "on"
        Option  "OpenGLOverlay" "off"
        BoardName       "ATI Radeon X800XT"
        Option          "no_accel"              "no"
        Option          "no_dri"                "no"
        Option          "mtrr"                  "no"  # disable DRI mtrr mapper, driver has its own code for mtrr
        Option          "DesktopLayout"         "LVDS, AUTO" #"LVDS, NONE" #"AUTO, NONE" MonitorLayout
        Option          "IgnoreEDID"            "off"
        Option          "HSync2"                "unspecified" #"31.5 - 90.0"
        Option          "VRefresh2"             "unspecified" #"75"
        Option          "ScreenOverlap"         "0"
        Option          "NoTV"                  "yes"
        Option          "TVStandard"            "NTSC-M"
        Option          "TVHSizeAdj"            "0"
        Option          "TVVSizeAdj"            "0"
        Option          "TVHPosAdj"             "0"
        Option          "TVVPosAdj"             "0"
        Option          "TVHStartAdj"           "0"
        Option          "TVColorAdj"            "0"
        Option          "GammaCorrectionI"      "0x00000000"
        Option          "GammaCorrectionII"     "0x00000000"
        Option          "Capabilities"          "0x00000000"
        Option          "CenterMode"            "off"
        Option          "PseudoColorVisuals"    "off"
        Option          "Stereo"                "off"
        Option          "StereoSyncEnable"      "1"
        Option          "FSAAEnable"            "no"
        Option          "FSAAScale"             "1"
        Option          "FSAADisableGamma"      "no"
        Option          "FSAACustomizeMSPos"    "no"
        Option          "FSAAMSPosX0"           "0.000000"
        Option          "FSAAMSPosY0"           "0.000000"
        Option          "FSAAMSPosX1"           "0.000000"
        Option          "FSAAMSPosY1"           "0.000000"
        Option          "FSAAMSPosX2"           "0.000000"
        Option          "FSAAMSPosY2"           "0.000000"
        Option          "FSAAMSPosX3"           "0.000000"
        Option          "FSAAMSPosY3"           "0.000000"
        Option          "FSAAMSPosX4"           "0.000000"
        Option          "FSAAMSPosY4"           "0.000000"
        Option          "FSAAMSPosX5"           "0.000000"
        Option          "FSAAMSPosY5"           "0.000000"
        Option          "UseFastTLS"            "0"
        Option          "BlockSignalsOnLock"    "on"
        Option          "UseInternalAGPGART"    "yes"
        Option          "ForceGenericCPU"       "no"
        Option          "DesktopSetup"          "clone" #clone or horizontal to stretch
        BusID           "PCI:1:0:0"    # vendor=1002, device=5460
        #ChipID 0x5D57
EndSection

```

---

