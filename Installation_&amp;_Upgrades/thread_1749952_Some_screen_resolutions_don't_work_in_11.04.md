---
title: "Some screen resolutions don't work in 11.04"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by TerenceShek on 2011-05-05
After upgrading from 10.10 to 11.04, I find that I can not successfully set the screen resolution of an external monitor to 1280x1024, for instance. The screen draws blocks of graphics in strange places & doesn't seem to erase properly. This screen resolution worked in 10.10, as did all the display options. However, now that I've upgraded only resolutions of 1024x768 & lower work OK. Is this is a bug in 11.04?

My hardware: Dell Inspiron Mini 10v, Intel Atom CPU N270 1.60GHz, 1GB RAM

---

### Post by Taffman on 2011-05-05
I've just installed v10 for as a total Ubuntu (Linux)newbie. I cant select 1280x1024 it's just not in the list of options available. The screen looks terrible which is a shame as I really want to ditch Windows Vista. anyone know how I can add the resolution setting. My Monitor is a Samsung SyncMaster 913n which under Windows is a 'plug and play' device and does not require any additional drivers, could this be my problem?

---

### Post by TerenceShek on 2011-05-11
So far I haven't found a way to get the Unity interface to work at a high screen resolution on my external Dell monitor. I've also noticed other oddities, such as the launcher bar appearing on the 10v laptop screen, even though I used xrandr to configure the external monitor as the primary monitor. Things are fine if I login using Ubuntu Classic (No Effects), & I'll just do that for the time being, on the assumption that a future upgrade will fix the bug.

---

### Post by MAFoElffen on 2011-05-11
> **TerenceShek said:**
> After upgrading from 10.10 to 11.04, I find that I can not successfully set the screen resolution of an external monitor to 1280x1024, for instance. The screen draws blocks of graphics in strange places & doesn't seem to erase properly. This screen resolution worked in 10.10, as did all the display options. However, now that I've upgraded only resolutions of 1024x768 & lower work OK. Is this is a bug in 11.04?

My hardware: Dell Inspiron Mini 10v, Intel Atom CPU N270 1.60GHz, 1GB RAM
There is an open LP bug on this, but... I have an idea.

If you first set the monitors to mirror in the GUI monitor utility...
 ```
 
gnome-display-properties

```or go to it in system settings... and select the "Mirror" checkbox...

Then in a terminal, query the monitor using xranr
```

xrandr -q

```It should return the supported modes of any attached monitors and their device names.  

You could then use hwinfo to query your video hardware
```

hwinfo --framebuffer

```To check the support modes of you video card...

You could then use that data to use in your xorg.conf to try to set each monitor at a supported resolution.  (Or you could create an xsession .xprofile file...) a snippet from xorg.conf would look similar to this:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 0,0
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 
    SubSection     "Display"
        Depth       24
        Modes "1920x1250" "1630x1024" "1440x1024" "1280x1024"  "1024x768"   "800x600" "640x480"
     EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 
    SubSection     "Display"
        Depth       24
        Modes         "1280x1024"  "1024x768"   "800x600 "640x480" 
    EndSubSection
EndSection

```Notice that this is just an example snippet.  Take "your" generated xorg.conf and add the supported "modes" that you copied down from xrandr to a "Mode" line in the Screen Section > Display Subsection... Add them to your xorg.conf file as per the device name returned by xrandr.  

Notes:
1. The modes have to be something your video hardware supports (returned by hwinfo).
2. The first mode in the mode line will be the default mode.  You will then be able to switch modes in a gnome session via the hotkeys <cntrl><alt><+> or <cntrl><alt<->  It will cycle up/down this mode list to change it.

---

