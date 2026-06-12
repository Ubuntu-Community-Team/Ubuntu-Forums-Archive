---
title: "Graphics issues"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by heise on 2011-05-23
I just installed Ubuntu on this machine and I'm having some issues with the graphics. The computer has 3 GTX580 graphics cards with each of them driving three HDTVs using a TripleHead2Go. The resolution of each display simulated by the Matrox box is 4080x768. I have to log on using Ubuntu Classic (no effects) to avoid the issue I having where display and active area do not match up (see attached image). But now I'm getting Xlib:  extension "RANDR" missing on display ":0.0".

Any help would be greatly appreciated.

Steffen

---

### Post by MAFoElffen on 2011-05-24
> **heise said:**
> I just installed Ubuntu on this machine and I'm having some issues with the graphics. The computer has 3 GTX580 graphics cards with each of them driving three HDTVs using a TripleHead2Go. The resolution of each display simulated by the Matrox box is 4080x768. I have to log on using Ubuntu Classic (no effects) to avoid the issue I having where display and active area do not match up (see attached image). But now I'm getting Xlib:  extension "RANDR" missing on display ":0.0".

Any help would be greatly appreciated.

Steffen

This is a snippet of your xorg.conf:
```

Section "ServerLayout"
       Identifier     "Layout0"
       [COLOR=Green]Screen      0  "Screen0" 0 0[/COLOR]
      [COLOR=Red] Screen      1  "Screen1" Below "Screen0[/COLOR]"
       [COLOR=Blue]Screen      2  "Screen2" Below "Screen1"[/COLOR]
       InputDevice    "Keyboard0" "CoreKeyboard"
       InputDevice    "Mouse0" "CorePointer"
       Option         "Xinerama" "1"
EndSection

Section "Monitor"
       [COLOR=Green]# HorizSync source: edid, VertRefresh source: edid
       Identifier     "Monitor0"[/COLOR]
       VendorName     "Unknown"
   ModelName      "Matrox"
      [COLOR=Green] HorizSync       31.5 - 80.0
       VertRefresh     60.0 - 75.0[/COLOR]
       Option         "DPMS"
EndSection

Section "Monitor"
       [COLOR=Red]# HorizSync source: unknown, VertRefresh source: unknown
       Identifier     "Monitor1"[/COLOR]
       VendorName     "Unknown"
   ModelName      "Matrox"
      [COLOR=Red] HorizSync       0.0 - 0.0
       VertRefresh     0.0[/COLOR]
       Option         "DPMS"
EndSection

Section "Monitor"
       [COLOR=Blue]# HorizSync source: unknown, VertRefresh source: unknown
       Identifier     "Monitor2"[/COLOR]
       VendorName     "Unknown"
   ModelName      "Matrox"
      [COLOR=Blue] HorizSync       0.0 - 0.0
       VertRefresh     0.0[/COLOR]
       Option         "DPMS"
EndSection

Section "Screen"
       Identifier     "Screen0"
       Device         "Device0"
  Monitor        "Monitor0"
  DefaultDepth    24
  Option         "TwinView" "0"
       Option         "metamodes" "nvidia-auto-select +0+0"
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
       Option         "metamodes" "nvidia-auto-select +0+0"
       SubSection     "Display"
             Depth       24
       EndSubSection
EndSection

Section "Screen"
       Identifier     "Screen2"
       Device         "Device2"
       Monitor        "Monitor2"
       DefaultDepth    24
       Option         "TwinView" "0"
       Option         "metamodes" "nvidia-auto-select +0+0"
       SubSection     "Display"
             Depth       24
       EndSubSection
EndSection

```Now look at these two other snippets:
```

Section "Monitor"     
        Identifier      "External DVi-0"     
          Modeline        [COLOR=Red][COLOR=Black]"1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync    [/COLOR] [/COLOR]
          Option          "PreferredMode" [COLOR=Black]"1280x1024_60.00" [/COLOR]
EndSection 

Section "Screen"     
        Identifier      "Primary Screen"     
        Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"     
        DefaultDepth    24     
        SubSection "Display"         
             Depth           24         
             Modes [COLOR=Red]  [COLOR=Black]"1280x1024[/COLOR][/COLOR][COLOR=Black]" "102[/COLOR]4x768" "640x480"     
        EndSubSection 
EndSection  


```And this one
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSP LM02"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 Ultra"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
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
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```What you should notice is that the horizontal and verticle sync is showing up for your first monitor but not for your other 2...

Does
```

xrandr -q

```See all 3 monitors? (post results)

As for your error on RANDR-  from what I read, You are using
```

Option         "Xinerama" "1"

```There are incompatibilities between the two but everyone says just to ignore the error message.  (That it's just an annoyance.)

---

### Post by heise on 2011-05-25
If I have Xinerama enabled I and log in using Ubuntu I get the two black rows I showed in the original picture and I can't seem to get a terminal into the lower row. Logging In with Ubuntu Classic (no effects) I see the whole desktop, but I get

```
RandR extension missing
```

without Xinerama logging in using Ubuntu I get the following result:

```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 4080 x 768, maximum 4080 x 768
default connected 4080x768+0+0 0mm x 0mm
   4080x768       50.0* 
   1360x768       51.0     52.0  
   1024x768       53.0     54.0     55.0     56.0     57.0     58.0     59.0     60.0  
   960x720        61.0     62.0     63.0  
   960x600        64.0  
   960x540        65.0  
   928x696        66.0     67.0  
   896x672        68.0     69.0  
   840x525        70.0     71.0     72.0     73.0     74.0  
   832x624        75.0  
   800x600        76.0     77.0     78.0     79.0     80.0     81.0     82.0     83.0     84.0     85.0  
   800x512        86.0  
   720x450        87.0  
   720x400        88.0  
   700x525        89.0     90.0     91.0     92.0  
   680x384        93.0     94.0  
   640x512        95.0     96.0     97.0  
   640x480        98.0     99.0    100.0    101.0    102.0    103.0    104.0  
   640x400       105.0  
   640x350       106.0  
   576x432       107.0    108.0    109.0    110.0    111.0    112.0    113.0  
   512x384       114.0    115.0    116.0    117.0    118.0  
   416x312       119.0  
   400x300       120.0    121.0    122.0    123.0    124.0  
   360x200       125.0  
   320x240       126.0    127.0    128.0    129.0  
   320x200       130.0  
   320x175       131.0  

```

Steffen

---

