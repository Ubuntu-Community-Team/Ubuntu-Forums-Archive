---
title: "Monitor Resolution - Need Help"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by chisox on 2010-01-19
I upgraded from 9.04 to 9.10 and my display is not being properly recognized.  It is showing a maximum resolution of 800x600.  I would like to use at least 1024x768.  The monitor worked correctly on the same PC on 9.04.

I have searched the forum and tried many potential solutions.  I have worked on this for many hours and have not been able to resolve the issue.

I am a only a very casual linux user and could use some help.  Is anybody willing to review my information below and provide a suggestion?

My monitor is a Dell P780 and the specs can be found at this URL:

 body {height: 100%; color:#000000; font-size:12pt; font-family:Arial;}[http://support.dell.com/support/edocs/monitors/p780/En/spec.htm](http://support.dell.com/support/edocs/monitors/p780/En/spec.htm)

My xorg.conf file is pasted below.

I appreciate any support that anybody is willing to provide.


 body {height: 100%; color:#000000; font-size:12pt; font-family:Arial;}Section "ServerLayout"
    Identifier     "X.org Configured"
     Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf  "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice     "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
     ModulePath   "/usr/lib/xorg/modules"
    FontPath      "/usr/share/fonts/X11/misc"
    FontPath      "/usr/share/fonts/X11/cyrillic"
    FontPath      "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath      "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath      "/usr/share/fonts/X11/Type1"
    FontPath      "/usr/share/fonts/X11/100dpi"
    FontPath      "/usr/share/fonts/X11/75dpi"
    FontPath      "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath      "built-ins"
EndSection

Section "Module"
    Load  "dbe"
     Load  "dri2"
    Load  "extmod"
    Load  "glx"
    Load  "dri"
     Load  "record"
EndSection

Section "InputDevice"
    Identifier   "Keyboard0"
    Driver      "kbd"
EndSection

Section  "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
     Option        "Protocol" "auto"
    Option        "Device"  "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6  7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
     HorizSync    30 - 85
        VertRefresh  48 - 120
    VendorName    "Monitor Vendor"
    ModelName    "Monitor  Model"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor  Model"
EndSection

Section "Device"
        ### Available Driver  options are:-
        ### Values: <i>: integer, <f>: float,  <bool>: "True"/"False",
        ### <string>: "String",  <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg  optional
        #Option     "NoAccel"                #  [<bool>]
        #Option     "SWcursor"               #  [<bool>]
        #Option     "ColorKey"               #  <i>
        #Option     "CacheLines"             # <i>
         #Option     "Dac6Bit"                # [<bool>]
        #Option      "DRI"                    # [<bool>]
        #Option      "NoDDC"                  # [<bool>]
        #Option      "ShowCache"              # [<bool>]
        #Option      "XvMCSurfaces"           # <i>
        #Option     "PageFlip"                # [<bool>]
    Identifier  "Card0"
    Driver       "intel"
    VendorName  "Intel Corporation"
    BoardName   "82830 CGC  [Chipset Graphics Controller]"
    BusID        "PCI:0:2:0"
EndSection

Section "Device"
        ### Available  Driver options are:-
        ### Values: <i>: integer, <f>:  float, <bool>: "True"/"False",
        ### <string>: "String",  <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg  optional
        #Option     "NoAccel"                #  [<bool>]
        #Option     "SWcursor"               #  [<bool>]
        #Option     "ColorKey"               #  <i>
        #Option     "CacheLines"             # <i>
         #Option     "Dac6Bit"                # [<bool>]
        #Option      "DRI"                    # [<bool>]
        #Option      "NoDDC"                  # [<bool>]
        #Option      "ShowCache"              # [<bool>]
        #Option      "XvMCSurfaces"           # <i>
        #Option     "PageFlip"                # [<bool>]
    Identifier  "Card1"
    Driver       "intel"
    VendorName  "Intel Corporation"
    BoardName   "82830 CGC  [Chipset Graphics Controller]"
    BusID        "PCI:0:2:1"
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
     SubSection "Display"
        Viewport   0 0
        Depth     1         
    EndSubSection
    SubSection "Display"
        Viewport   0  0
        Depth     4
    EndSubSection
    SubSection "Display"
         Viewport   0 0
        Depth     8
    EndSubSection
    SubSection  "Display"
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

Section "Screen"
    Identifier  "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
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
    SubSection  "Display"
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

---

### Post by SusieSA on 2010-01-23
HI

Did you find a solution to this problem?  I have exactly the same problem.  Thanks

---

