---
title: "Attempted Installation on Posiflex KS-2615"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by luskwater on 2010-12-17
[NOTE: originally, this had the incorrect model "KS-2615".  Apologies.]

I have been attempting to install Ubuntu 10.10 (Maverick) on a Posiflex KS-2615 touch-screen terminal (ordinarily used for POS).  This model uses a Via C7 1.5GHz processor, and has a built-in resistive touch-screen monitor (1024x768 ).

Once the installer gets to the point where it produces a graphical display, the display becomes unreadable.  I don't have a technical term to describe it, so I'll show my age by saying, "It looks like horizontal hold on the TV is messed up."  I get narrow bands of gray slowly moving up over a mostly-purple screen, with "snow" moving diagonally across it.  

I cannot find any video specs for this machine, so I don't know what it might be looking for.

Thoughts on directions to go in getting this installed, please?

---

### Post by luskwater on 2010-12-30
OK, here's an update, but not a solution.

I've done a text-only install successfully, more or less.

X will start with the openchrome driver and the via (kernel) driver that comes with the installation.  

I created a file using Xorg --configure to begin figuring out where to go.

I've created some .conf files in the appropriate xorg.conf.d directory.
52-device-posiflex.conf contains a Device section specifying the openchrome driver and identifying the device on the PCI bus.

52-monitor-posiflex.conf widens the default HorizSync range and VertRefresh range in the hope of capturing something close to what's required.  (The Posiflex tech-support folks have not got back to me with the required specs for the screen.)  I also have several ModeLine entries generated with the cvt tool.

```

        HorizSync       28-85
        VertRefresh     50-100
        ModeLine "1024x768_65.0"   65.0   1024 1048 1184 1344  768  771  777  806 -hsync -vsync
        Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
        Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync

```The screen .conf file specifies these three modes:
```

        DefaultDepth 16
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Virtual 1024 768
                Modes "1024x768_60.00" "1024x768_75.00" "1024x768_65.0"
        EndSubSection

```I've tried changing the Depth and DefaultDepth from 24 to 16, based on random ideas from web-reading.

After all of this, Xorg generates a bunch of valid modes, and I cycle through them (I believe) using <Ctrl>-<Alt>-<Kp+>, and the pretty patterns on the screen change, but I don't get a readable screen.

Any ideas?

---

### Post by luskwater on 2011-01-03
In the xorg conf file 52-device-posiflex.conf, I have a Device section setting the options for the openchrome driver.  This now reads

```

Section "Device"
    Identifier  "Card0"
    Driver      "openchrome"
    BusID       "PCI:1:0:0"
    Option      "VBEModes"  "true"
EndSection

```The "VBEModes" option allows standard VESA modes, which may not use the full driver capabilities, but at least appears to work (for me).

52-monitor-posiflex.conf now contains
```

Section "Monitor"
    Identifier    "Monitor0"
    VendorName    "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync     28-85
    VertRefresh    60
    Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

```The change of interest would be setting VertRefresh to 60 (which is the value used by Windows drivers running on the factory release of this device).

Finally, 52-screen-posiflex.conf now contains
```

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth 32
    SubSection "Display"
        Viewport   0 0
        Depth     32
        Virtual 1024 768
        Modes "1024x768_60.00" 
    EndSubSection
EndSection

```This uses only the one mode (instead of the three I was trying), and specifies a 32-bit depth (again, from checking out a Windows system).

I'm pretty sure the most important change was the VBEModes boolean, but I wanted to be thorough in case anyone is following in my steps here.

---

### Post by luskwater on 2011-01-05
I commented out the VBEModes boolean, and the screen was garbled on startup, so it *is* the VBEModes option.

---

### Post by nogayev on 2011-01-27
Hello. Your post really helped me to configure the display.:P
But there is still a problem to get the touchscreen working. If you can please help me to solve this problem.

---

### Post by luskwater on 2011-01-27
> **nogayev said:**
> Hello. Your post really helped me to configure the display.:P But there is still a problem to get the touchscreen working. If you can please help me to solve this problem.

I don't recall doing anything special for the touchscreen.  The 6215 is an (internal) USB touchscreen, I believe, and worked out of the box.  In fact, it irritated me that the screen was garbled, but it still "beep!"ed happily when I touched the screen.

I'll see if there was anything I did in particular, but I tend to doubt it in this case.

---

