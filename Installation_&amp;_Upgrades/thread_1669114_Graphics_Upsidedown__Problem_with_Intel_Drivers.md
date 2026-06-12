---
title: "Graphics Upsidedown:  Problem with Intel Drivers?"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by mbusha on 2011-01-17
Hi all -- 

I'm fairly new to Ubuntu and hopefully I posted this query in the right category.  I have a strange problem where the graphics on my screen appear upside  down (see attached image of my Desktop -- I'm definitely not this good  with photo shop!).  Here's some additional information and background that may help:
 
I'm running Ubuntu 10.10 in gnome on a Lenovo T510 with nVidia NVS 3100M Optimus card.

Upon installation, the graphics generally appeared fine, although my laptop would frequently lock up when I connected an external monitor.  To solve this, I (unsuccessfully) tried installing the nVidia drivers, eventually realizing that nVidia doesn't seem to support the 3100M Optimus card on linux.  I removed al thel nvidia* packages I had  installed using both Synaptic and then reinstalling the xserver-xorg nouveau and intel drivers in an attempt to return to my original configuration.  This is when the graphics became upside down.  There was also no xorg.conf file (there hadn't been one when I first installed ubuntu), but I was able to start the computer in limited graphics mode by copying /etc/X11/xorg.conf.failsafe to /etc/X11/xorg.conf.  However, graphics effects utilities, such as compiz, stopped working.  

Also, I don't think this is a screen rotation issue because 1) my mouse works correctly, 2) the inversion seems to be happening almost at the icon, in that the top toolbar remains at the top of the screen, it's just inverted, and 3) (this is probably the strangest bit) the desktop icons and menu locations are "where they should be" as opposed to "where they appear."  In other words, if I want to open the file whose icon appears in the bottom left corner of my desktop in the attached image, I need to click on the apparently empty space in the top right corner where the icon would be if the graphics weren't inverted.  

Since then I've tried several other things, including:

-Removing the nVidia drivers through the brute-force command 
sudo find / -type f -name "nvidia*" -exec rm -f {} \; 
as was suggested [here]("http://newyork.ubuntuforums.org/showthread.php?p=10358898#post10358898") for uninstallation.  

-Generated a xorg.conf file by shutting down gnome and using "Xorg -configure".  The  file this generated is pasted below.  

While the xorg.conf file generated above still left the graphics upside down, I discovered that they righted themselves if I replaced the driver for Device, Card1 (which I'm assuming is my integrated graphics card) from intel to fbdev, i.e., I changed line 101 from
       Driver      "intel"
to
       Driver      "fbdev"
However, utilities like compiz continued not to function and I'm only able to mirror displays when I connect to an external monitor, so I'm guessing the right drivers aren't being loaded.  

I'd love to hear any thoughts/suggestions that anyone has!


------------------------

Contents of my xorg.config file:

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
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
    Load  "extmod"
    Load  "dri"
    Load  "record"
    Load  "dri2"
    Load  "dbe"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
    Identifier  "Card1"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
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
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
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
    SubSection "Display"
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

### Post by mbusha on 2011-01-19
In case anyone else experiences this problem, I think I managed to resolve it.  It looks like it was an issue with compiz communicating correctly with my video drivers.  I wound up doing a complete removal for all installed packages mentioning compiz using synaptic, and then did a re-install for xserver-xorg, xserver-xorg-core, and xserver-xorg-video-<intel, nouveau, nv>.  Then restarted and reinstalled compiz.  I then followed some of the incstructions [here]("http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html"), in particular running "compiz --replace" and adding that command to my startup package.  Things seem to be working now.

---

### Post by mbusha on 2011-01-19
In case anyone else is having this problem, I think I managed to fix everything.  It looks like the issue was with the communication between compiz and my video drivers.  I used synaptic to do a complete removal of all installed packages having to do with compiz, and then reinstalled xserver-xorg, xserver-xorg-core, xserver-xorg-video-<nouveau, nv, intel>.  Then I removed my xorg.conf file to force ubuntu to detect my hardware settings on startup and restarted my computer.  Since everything was working fine at this point, I reinstalled compiz, again from synaptic.  Then I had to follow some of the instructions from [this page]("http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html") and activated compiz using the command "compiz --replace".  That seemed to do the trick!  I actually had to add the "compiz --replace" command to my startup applications, but so far everything seems to be working.

---

### Post by mbusha on 2011-01-19
In case anyone else is having this problem, I think I managed to fix  everything.  It looks like the issue was with the communication between  compiz and my video drivers.  I used synaptic to do a complete removal  of all installed packages having to do with compiz, and then reinstalled  xserver-xorg, xserver-xorg-core, xserver-xorg-video-<nouveau, nv,  intel>.  Then I removed my xorg.conf file to force ubuntu to detect  my hardware settings on startup and restarted my computer.  Since  everything was working fine at this point, I reinstalled compiz, again  from synaptic.  Then I had to follow some of the instructions from [this page]("http://www.webupd8.org/2010/11/install-compiz-0921-in-ubuntu-1010.html")  and activated compiz using the command "compiz --replace".  That seemed  to do the trick!  I actually had to add the "compiz --replace" command  to my startup applications, but so far everything seems to be working.

---

