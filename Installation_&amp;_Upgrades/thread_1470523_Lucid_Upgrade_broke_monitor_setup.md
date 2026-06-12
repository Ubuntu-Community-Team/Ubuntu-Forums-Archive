---
title: "Lucid Upgrade broke monitor setup"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Cyclops_ on 2010-05-02
Hey all,

Here is my issue:

Upon upgrading from Karmic to Lucid, Everything comes up, seemingly fine.  Once logged in to the OS, my three monitors show the desktop wallpaper as well as all the icons on the desktop.  A few programs that I have set to autostart do so.

*However* for some reason, I can only access one of the three monitors.  (And not the one with the gnome-panel.)  As soon as I drag my mouse from my third monitor onto the one next to it, I loose complete control of it, and it starts dancing all over the place.  If I try to drag a window from one screen to the next (using Alt-Left CLick + drag and not moving the mouse onto the other monitor), the the app goes from one side of the working monitor to the other side (like it's wrapping around).  Though I can see it on the other monitor for a little bit until I get it far enough for it to wrap.

Here is my xorg.conf:
```

Section "Files"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    #FontPath        "/usr/share/fonts/X11/util"
    #FontPath        "/usr/share/fonts/X11/encodings"
    #FontPath        "unix/:7100"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 75.0
    VertRefresh     56.0 - 61.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "KTC W2408S"
    HorizSync       31.0 - 75.0
    VertRefresh     56.0 - 63.0
    #Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "NTS MB24W"
    HorizSync       30.0 - 74.0
    VertRefresh     50.0 - 61.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option         "AllowGLXWithComposite" "true"
    Option         "UseCompositeWrapper" "true"
    Option         "NoLogo" "True"
    Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "true"
    Option         "UseCompositeWrapper" "true"
    Option         "AddARGBGLXVisuals" "true"
    Option         "NoLogo" "True"
    Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    # Removed Option "TwinView" "1"
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load    "glx"
    Disable    "dri2"
    #Load           "freetype"
    #Disable    "dri2"
    #Load           "dri"
    #Load           "type1"
EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 3840 0
    Screen      1  "Screen1" 0 0
    Screen      2  "Screen2" 1920 0
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Mouse0" "CorePointer"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "Xinerama" "1"
    Option         "AIGLX" "true"
    #Option         "XGL" "true"
EndSection

Section "Device"
    Identifier     "Device0"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    BusID          "PCI:3:0:0"
    Screen          0
    Driver    "nvidia"
EndSection

Section "Device"
    Identifier     "Device1"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    BusID          "PCI:4:0:0"
    Driver    "nvidia"
EndSection

Section "Device"
    Identifier     "Device2"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTS 250"
    Option         "AllowGLXWithComposite" "true"
    Option         "UseCompositeWrapper" "true"
    Option         "NoLogo" "True"
    Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
    Option         "AddARGBGLXVisuals" "true"
    BusID          "PCI:3:0:0"
    Screen          1
    Driver    "nvidia"
    #Option         "XAANoOffscreenPixmaps"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

```

Let me know what else I can post that will help!

Thanks!

---

### Post by quixote on 2010-05-04
Lucid uses the "nouveau" driver, which is an open source nvidia driver.  For me, it's been working *way* better than the nvidia drivers did, but maybe in your 3-screen set up (wow!) that's not the case.  Your xorg.conf does imply you're still using nvidia drivers, but maybe it's worth checking what, exactly, is going on.  Synaptic will show you if nouveau is installed.  If yes, it's probably uninstalled the nvidia drivers.  There's some more info [here]("http://nouveau.freedesktop.org/wiki/UbuntuPackages").  Also perhaps search the forums for "nouveau nvidia Lucid" (without quotes).

---

### Post by m1ndctrl on 2010-05-04
I'm actually working on getting 4 monitors running with Xgl on 10.04 at the moment.

I feel that I'm very close, except that when I employ the Xgl-sessions file for karmic - X loads, but gnome does not. Also, like you cyclops, I get bizarre window rendering on one card and gnome will not load.

The errors I receive can be viewed here (.xsession-errors): [http://pastebin.com/cDA9HKvA](http://pastebin.com/cDA9HKvA)

Now, even though gnome-settings-daemon, panel and etc will not start, i can run any program from terminal. Furthermore, when I run 'compiz --replace' i actually have composite windowing working; the windows are wobbly and all that jazz.

Can anyone shed any light?

If I can get this working I'll post a how-to for everyone to use. Oh, and I'm running xserver-xgl from hardy days.

---

### Post by johansson.seb on 2010-05-08
Yep, this is a bug in Xorg. Have a look at [Bug #563100]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/563100").

> According to the Xorg people working with the bug, in Xinerama mode - event coordinates are relative to the primary secreen - Screen 0. But, in the version of Xorg that now is in use with Lucid (1.7.6) event coordinates are unsigned integers.

With unsigned integers, negative coordinates can not be represented, thus xorg can not function with screens above or to the left of Screen 0. So, if you can, let your upper-left screen be Screen 0.

The xorg people have a patch that seems to be working (simply changing back to signed ints). I hope that this will make it into an updated ubuntu Lucid package soon.

> As Daniel Dadap wrote, this seems to correspond to the Xorg bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=24986](https://bugs.freedesktop.org/show_bug.cgi?id=24986)

---

### Post by dino99 on 2010-05-08
remind that oldish xorg.conf can caused strange errors, note that lucid dont need xorg.conf by default

1) always use genuine lucid nvidia driver except with the more recent cards
2) check x-swat ppa for updated packages
3) recreate custom xorg.conf with: Xorg -configure

---

