---
title: "Screen tearing effect with or without nvidia drivers"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by Linux-Djihad on 2010-12-13
Hello,
obviously (my) Ubuntu has problems with the x window system. Every time  when I move any window, this window looks rough and choppy on the edges. Actually it's a tearing effect.  First of all, I though it's a compiz problem but obviously it's related to the x window system. I have had this  problem since Ubuntu 9.10 and now it's getting annoying. I switched back  to nv driver instead of nvidia but no difference. I tried to change the  refresh rate, but I can't generate a modeline above 61Hz (because of  the LCD's limit). Obviously that's not the problem. Then I tried to set  in xorg.con +vsync -hsync and contrariwise but no changes.
I wonder which setting leads to such a behaviour. Is there some kind of  antialiasing parameter to set anywhere in xorg? Or is there some kind of  "sync to vblank" like in 3D settings? Or maybe some kind of acceleration? When I move the windows, it looks  like an appearing white background for a split second. I can recognize  that phenomenon even better when I move a window above another window,  especially above the dark brown menu bar. I tried to record that  behaviour with mydesktoprecord but ironically you would not see any  rough and choppy in this record.


  Here is my xorg.conf
```
Section "ServerLayout"
 Identifier     "X.org Configured"
 Screen         0 "Screen0" 0 0
 InputDevice    "Mouse0" "CorePointer"
 InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
 ModulePath   "/usr/lib/xorg/modules"
 FontPath     "/usr/share/fonts/X11/misc"
 FontPath     "/usr/share/fonts/X11/cyrillic"
 FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
 FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
 FontPath     "/usr/share/fonts/X11/Type1"
 FontPath     "/usr/share/fonts/X11/100dpi"
 FontPath     "/usr/share/fonts/X11/75dpi"
 FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath     "built-ins"
EndSection

Section "Module"
 Load  "glx"
 Load  "dbe"
 Load  "record"
 Load  "dri2"
 Load  "dri"
 Load  "extmod"
EndSection

Section "InputDevice"
 Identifier  "Keyboard0"
 Driver      "kbd"
EndSection

Section "InputDevice"
 Identifier  "Mouse0"
 Driver      "mouse"
 Option     "Protocol" "auto"
 Option     "Device" "/dev/input/mice"
 Option     "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
 Identifier   "SamsungSyncMasterP2770"
 HorizSync    30-75
 VertRefresh  56-61
 Modeline "1920x1080@60" 182.28 1920 1952 2640 2672 1080 1102 1113 1135 -HSync +VSync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"            # [<bool>]
        #Option     "HWcursor"            # [<bool>]
        #Option     "NoAccel"             # [<bool>]
        #Option     "ShadowFB"            # [<bool>]
        #Option     "UseFBDev"            # [<bool>]
        #Option     "Rotate"              # [<str>]
        #Option     "VideoKey"            # <i>
        #Option     "FlatPanel"           # [<bool>]
        #Option     "FPDither"            # [<bool>]
        #Option     "CrtcNumber"          # <i>
        #Option     "FPScale"             # [<bool>]
        #Option     "FPTweak"             # <i>
        #Option     "DualHead"            # [<bool>]
 Identifier  "Card0"
 Driver      "nv"
 BusID       "PCI:1:0:0"
EndSection

Section "Screen"
 Identifier "Screen0"
 Device     "Card0"
 Monitor    "SamsungSyncMasterP2770"
 DefaultDepth 24
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
 SubSection "Display"
  Viewport   0 0
  Depth     15
 EndSubSection
 SubSection "Display"
  Viewport   0 0
  Depth     16
 EndSubSection
 SubSection "Display"
  Depth     24
  Modes  "1920x1080@60"
 EndSubSection
```EndSection

What is very strange is the fact that Xorg.0.log says -vsync although I have set +vsync. Is this a bug?
Look the output at Modeline 1920x1080:
```
...
[   611.720] (II) NV(0): EDID Version: 1.3
[   611.720] (II) NV(0): Digital Display Input
[   611.720] (II) NV(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[   611.720] (II) NV(0): Gamma: 2.20
[   611.720] (II) NV(0): DPMS capabilities: Off
[   611.720] (II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   611.720] (II) NV(0): First detailed timing is preferred mode
[   611.720] (II) NV(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.602
[   611.720] (II) NV(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[   611.720] (II) NV(0): Supported established timings:
[   611.720] (II) NV(0): 720x400@70Hz
[   611.720] (II) NV(0): 640x480@60Hz
[   611.720] (II) NV(0): 640x480@67Hz
[   611.720] (II) NV(0): 640x480@72Hz
[   611.720] (II) NV(0): 640x480@75Hz
[   611.720] (II) NV(0): 800x600@56Hz
[   611.720] (II) NV(0): 800x600@60Hz
[   611.720] (II) NV(0): 800x600@72Hz
[   611.720] (II) NV(0): 800x600@75Hz
[   611.720] (II) NV(0): 832x624@75Hz
[   611.720] (II) NV(0): 1024x768@60Hz
[   611.720] (II) NV(0): 1024x768@70Hz
[   611.720] (II) NV(0): 1024x768@75Hz
[   611.720] (II) NV(0): 1280x1024@75Hz
[   611.720] (II) NV(0): 1152x864@75Hz
[   611.720] (II) NV(0): Manufacturer's mask: 0
[   611.720] (II) NV(0): Supported standard timings:
[   611.720] (II) NV(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   611.720] (II) NV(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   611.720] (II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   611.720] (II) NV(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   611.720] (II) NV(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[   611.720] (II) NV(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[   611.720] (II) NV(0): #6: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[   611.720] (II) NV(0): #7: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   611.720] (II) NV(0): Supported detailed timing:
[   611.720] (II) NV(0): clock: 138.5 MHz   Image Size:  597 x 336 mm
[   611.720] (II) NV(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[   611.720] (II) NV(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[   611.720] (II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 175 MHz
[   611.720] (II) NV(0): Monitor name: SyncMaster
[   611.720] (II) NV(0): Serial No: H9MZ100952
[   611.720] (II) NV(0): EDID (in hex):
[   611.720] (II) NV(0):     00ffffffffffff004c2dec0537324645
[   611.720] (II) NV(0):     03140103803c22782a3481a656489a24
[   611.720] (II) NV(0):     125054bfef80714f8100814081809500
[   611.720] (II) NV(0):     950fa940b3001a3680a070381f403020
[   611.720] (II) NV(0):     350055502100001a000000fd00384b1e
[   611.720] (II) NV(0):     5111000a202020202020000000fc0053
[   611.720] (II) NV(0):     796e634d61737465720a2020000000ff
[   611.720] (II) NV(0):     0048394d5a3130303935320a20200003
[   611.720] (--) NV(0): Trying load detection on VGA1 ... nothing.
[   611.731] (II) NV(0): EDID vendor "SAM", prod id 1516
[   611.731] (II) NV(0): Using hsync ranges from config file
[   611.731] (II) NV(0): Using vrefresh ranges from config file
[   611.731] (II) NV(0): Printing DDC gathered Modelines:
[   611.731] (II) NV(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
[   611.731] (II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   611.731] (II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   611.731] (II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   611.731] (II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   611.731] (II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   611.731] (II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   611.731] (II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   611.731] (II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   611.731] (II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   611.731] (II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   611.731] (II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   611.731] (II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   611.731] (II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   611.731] (II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   611.731] (II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   611.731] (II) NV(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[   611.731] (II) NV(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   611.731] (II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   611.731] (II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[   611.731] (II) NV(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[   611.731] (II) NV(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   611.731] (II) NV(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[   611.731] (II) NV(0): EDID vendor "SAM", prod id 1516
[   611.731] (II) NV(0): Probing for EDID on I2C bus 1...
[   611.736] (II) NV(0):   ... none found
[   611.736] (--) NV(0): Trying load detection on VGA2 ... nothing.
...
```

---

