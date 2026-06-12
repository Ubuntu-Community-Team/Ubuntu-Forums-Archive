---
title: "Couldn't get native resolution after 13.04 upgrade"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by mysticalzero on 2013-04-30
My monitor's native resolution of 1920x1080 is not being listed as one of the display options. Not even on **xrandr**.
NOTE: I should have mentioned that I have set the **nomodeset** kernel parameter. Otherwise, I couldn't even boot passed the bootup splash screen. For example, the kubuntu splash screen will be shown momentarily before displaying visual artifacts. I had to perform a magic sysrq key sequence to reboot.

_Hardware and setup:_
GPU: AMD/ATi Radeon 4670M
Driver: open-source radeon

_What I have done:_
Seeing that **nomodeset** allows me to boot without issues, I took it upon myself to check the display modes that are reported by xrandr:
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1400 x 1050, maximum 1400 x 1050
default connected 1400x1050+0+0 0mm x 0mm
   1400x1050      60.0* 
   1280x1024      61.0  
   1280x960       61.0  
   1152x864       60.0  
   1024x768       61.0  
   800x600        61.0  

```

An online search on the issue of missing resolution tells me that I have to add a new mode using xrandr and set it as the new display mode. However, doing so has no effect (apart from the short flicker before being brought back to 1400x1050 with the message **xrandr: Configure crtc 0 failed**)
```

ricky@ci5-Studio-XPS-1647:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
ricky@ci5-Studio-XPS-1647:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default
ricky@ci5-Studio-XPS-1647:~$ xrandr --addmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
ricky@ci5-Studio-XPS-1647:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1400 x 1050, maximum 1920 x 1080
default connected 1400x1050+0+0 0mm x 0mm
   1400x1050      60.0* 
   1280x1024      61.0  
   1280x960       61.0  
   1152x864       60.0  
   1024x768       61.0  
   800x600        61.0  
   1920x1080_60.00   60.0
ricky@ci5-Studio-XPS-1647:~$ xrandr --output default --mode 1920x1080_60.00
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```

I don't remember seeing **xrandr: Failed to get size of gamma for output default** last time. I wonder if that's an issue. 

Anyone can shed some light on this problem?

Any suggestions will be greatly appreciated. :)

_Logs:_
[Xorg log](http://paste.ubuntu.com/5618088/)

hwinfo --framebuffer
```

ricky@ci5-Studio-XPS-1647:~$ sudo hwinfo --framebuffer
> hal.1: read hal dataprocess 5384: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.UKXxIqIgY83
  Hardware Class: framebuffer
  Model: "(C) 1988-2005, ATI Technologies Inc.  M96"
  Vendor: "(C) 1988-2005, ATI Technologies Inc. "
  Device: "M96"
  SubVendor: "ATI ATOMBIOS"
  SubDevice: 
  Revision: "01.00"
  Memory Size: 16 MB
  Memory Range: 0xd0000000-0xd0ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0319: 1280x1024 (+2560), 15 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0320: 320x200 (+1280), 24 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 24 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 24 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 24 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 24 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 24 bits
  Mode 0x0363: 1280x960 (+1280), 8 bits
  Mode 0x0365: 1280x960 (+2560), 16 bits
  Mode 0x0366: 1280x960 (+5120), 24 bits
  Mode 0x0321: 640x480 (+2560), 24 bits
  Mode 0x0322: 800x600 (+3200), 24 bits
  Mode 0x0323: 1024x768 (+4096), 24 bits
  Mode 0x0324: 1280x1024 (+5120), 24 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

hwinfo --monitor
```

ricky@ci5-Studio-XPS-1647:~$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 7699: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
37: None 00.0: 10002 LCD Monitor                                
  [Created at monitor.95]
  Unique ID: rdCR.g4DerC9yFH1
  Hardware Class: monitor
  Model: "C088T 156WF1 LCD Monitor"
  Vendor: LGD "C088T 156WF1"
  Device: eisa 0x0215 
  Resolution: 1920x1080@60Hz
  Size: 345x194 mm
  Detailed Timings #0:
     Resolution: 1920x1080
     Horizontal: 1920 1968 2000 2080 (+48 +80 +160) -hsync
       Vertical: 1080 1083 1088 1111 (+3 +8 +31) +vsync
    Frequencies: 138.50 MHz, 66.59 kHz, 59.93 Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

38: None 00.1: 10002 LCD Monitor
  [Created at monitor.95]
  Unique ID: jyhG.g4DerC9yFH1
  Hardware Class: monitor
  Model: "C088T 156WF1 LCD Monitor"
  Vendor: LGD "C088T 156WF1"
  Device: eisa 0x0215 
  Resolution: 1920x1080@60Hz
  Size: 345x194 mm
  Detailed Timings #0:
     Resolution: 1920x1080
     Horizontal: 1920 1968 2000 2080 (+48 +80 +160) -hsync
       Vertical: 1080 1083 1088 1111 (+3 +8 +31) +vsync
    Frequencies: 138.50 MHz, 66.59 kHz, 59.93 Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

39: None 00.2: 10002 LCD Monitor
  [Created at monitor.95]
  Unique ID: aHB6.g4DerC9yFH1
  Hardware Class: monitor
  Model: "C088T 156WF1 LCD Monitor"
  Vendor: LGD "C088T 156WF1"
  Device: eisa 0x0215 
  Resolution: 1920x1080@60Hz
  Size: 345x194 mm
  Detailed Timings #0:
     Resolution: 1920x1080
     Horizontal: 1920 1968 2000 2080 (+48 +80 +160) -hsync
       Vertical: 1080 1083 1088 1111 (+3 +8 +31) +vsync
    Frequencies: 138.50 MHz, 66.59 kHz, 59.93 Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
I don't have a Xorg.conf by the way.

---

### Post by mysticalzero on 2013-05-01
Solved. I got it working by removing xserver-xorg-video-ati although it seems odd judging by the fact that it is required for autodetection to work (without explicitly telling Xorg via Xorg.conf which of the subdrivers to load) and yet, for my case, without xserver-xorg-video-ati and a Xorg.conf file, it still works. If someone could chip in a reason for this peculiarity, that will be awesome. Either way, I'm glad that everything turns out fine.

```

ricky@ci5-Studio-XPS-1647:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
   1920x1080      59.9*+
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0     60.0  
   1280x1024      59.9     60.0  
   1440x900       59.9     59.9  
   1280x960       60.0     59.9  
   1280x854       59.9  
   1360x768       59.8     60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x720       59.9  
   1152x768       59.8  
   1024x768      120.1     60.0     59.9  
   960x720       120.0  
   928x696       120.1  
   896x672       120.0  
   960x600       120.0  
   960x540       120.0  
   800x600       120.0     60.3     59.9     56.2  
   840x525       120.0    119.8  
   800x512       120.3  
   848x480        59.7  
   700x525       120.0  
   720x480        59.7  
   640x512       120.0  
   720x450       119.8  
   640x480       120.0     59.9     59.4  
   680x384       119.6    119.9  
   576x432       120.1  
   512x384       120.0  
   400x300       120.6    112.7  
   320x240       120.1  
DisplayPort-0 disconnected (normal left inverted right x axis y axis)

```

---

