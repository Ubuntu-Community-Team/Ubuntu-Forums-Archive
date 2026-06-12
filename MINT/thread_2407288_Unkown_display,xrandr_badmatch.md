---
title: "Unkown display,xrandr badmatch"
date: 2018-12-02
forum: MINT
---

### Post by mxhyj on 2018-12-02
Hi,

I am new to Linux, my monitor couldn't be recognized, tried couple ways to add resolution, it doesn't work, hope someone could help me out here :).

```

cvt 1680 1050
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync


xrandr --newmode "1680x1050_60.00" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync
xrandr --addmode DVI-D-0 "1680x1050_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  35
  Current serial number in output stream:  36


```

```

xrandr
Screen 0: minimum 8 x 8, current 1984 x 768, maximum 16384 x 16384
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1024x768      60.00*+  75.03    70.07  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.95    59.94  
DVI-D-0 connected 960x540+1024+101 (normal left inverted right x axis y axis) 0mm x 0mm
   960x540       59.82*+
   864x486       59.92    59.57  
   640x480       59.94  
   480x270       59.82  
   432x243       59.92    59.57  
   320x240       60.05  
HDMI-0 disconnected (normal left inverted right x axis y axis)
  Mode 0 (0x2c0) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  Mode 1680 (0x2ce) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz

```

```

lspci -vk | grep -iA15 vga
01:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 710B] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] GK208B [GeForce GT 710]
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=128M]
    Memory at ee000000 (64-bit, prefetchable) [size=32M]
    I/O ports at bf00 [size=128]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia


01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] GK208 HDMI/DP Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at faffc000 (32-bit, non-prefetchable) [size=16K]

```

```

sudo get-edid | parse-edid

This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 5
No EDID on bus 6
No EDID on bus 7
No EDID on bus 10
2 potential busses found: 8 9
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
256-byte EDID successfully retrieved from i2c bus 8
Looks like i2c was successful. Have a good day.
WARNING: Checksum failed
Trying to continue...
Section "Monitor"
    Identifier "VX2235wm"
    ModelName "VX2235wm"
    VendorName "VSC"
    # Monitor Manufactured week 5 of 2007
    # EDID version 1.3
    # Digital Display
    DisplaySize 470 300
    Gamma 2.20
    Option "DPMS" "true"
    Horizsync 30-82
    VertRefresh 50-75
    # Maximum pixel clock is 150MHz
    #Not giving standard mode: 1680x1050, 60Hz
    #Not giving standard mode: 1600x1200, 60Hz
    #Not giving standard mode: 1440x900, 60Hz
    #Not giving standard mode: 1400x1050, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz
    #Not giving standard mode: 1280x960, 60Hz
    #Not giving standard mode: 1152x864, 75Hz
    #Not giving standard mode: 640x400, 70Hz
    Modeline     "Mode 0" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync

```

---

### Post by 4techguns on 2018-12-02
What distro/flavor or version of Ubuntu are you running?

---

### Post by mxhyj on 2018-12-04
I am running [COLOR=#333333][FONT=&quot]Linux Mint 19, codename "Tara"[/FONT][/COLOR]

---

### Post by deadflowr on 2018-12-04
*Thread moved to **MINT***

---

