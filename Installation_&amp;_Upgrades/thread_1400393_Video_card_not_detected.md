---
title: "Video card not detected"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by DaveInPhx on 2010-02-06
Working on a friend's PC, which was previously running XP and got a very nasty virus infection. I convinced him to try Ubuntu, showed him the interface running on my own machine and he was hooked.  Backed up all his data to network, completely erased the hard disk and install Ubuntu.  Sounds easy, right?

Installed 9.10, it didn't detect the video card and xorg.conf was missing from /etc/X11.  After some messing around trying to get it to work, I realised that the  
     sudo dpkg-reconfigure -phigh xserver-xorg  command wasn't working properly and didn't produce the menu shown in the screenshots.  After some digging I found that this was a bug in 9.10, so to make the job easier, I wiped the drive again and started again on 9.04.

With 9.04, at least the xorg.conf file was there, but had no entries under configured video device. I tried adding "vesa", "via", "openchrome" (all on separate attempts), all to no avail. I retried the dpkg -reconfigure command above. still no menu.

Now several days into this "easy" install, I rolled back to the LTS release (8.04 - hardy) and installed that instead.  Still no video card detection, and resolution is obstinately stuck at 800x600. Tried the same string of tests again, and now admitting defeat and asking for help!!!

_The relevant output from lspci is:_
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

_The output from xrandr is:_
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0 

The sections from xorg.conf are currently:
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

Any suggestions would be much appreciated!

---

### Post by mushwars on 2010-02-06
That xorg.conf is naked, it is missing SEVERAL vital lines. 

If you could do two things for me, pastebin the /var/log/Xorg.0.log

and try this

```
sudo X -configure
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo cp ~/xorg.conf.net /etc/X11/xorg.conf
startx
```

if that doesnt work pastebin that Xorg log as well.

cheers.

---

### Post by DaveInPhx on 2010-02-06
I copied the logfile to desktop and attached it - changed it to .doc for the uploader.

I'm running in X at the moment to post this, so the commands failed:
sudo X -configure
X already running

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bak
done

sudo cp ~/xorg.conf.net /etc/X11/xorg.conf
file does not exist

---

### Post by DaveInPhx on 2010-02-06
Target monitor for this system is a Envision h17ol
# Max Resolution 1280 x 1024 / 75.0 Hz
# Max Sync Rate (V x H) 75.0 Hz x 83.0 KHz

Current monitor is my own LG W2053
# Max Resolution 1600 x 900 / 60.0 Hz
# Max Sync Rate (V x H) 75.0 Hz x 83.0 KHz

---

### Post by DaveInPhx on 2010-02-06
Rebooted and dropped into terminal; Ran the sudo X -configure from there. This produced a new file /root/xorg.conf.new ..... 
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    RgbPath      "/etc/X11/rgb"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
    Load  "xtrap"
    Load  "record"
    Load  "dri"
    Load  "GLcore"
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

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "VBEModes"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "HWCursor"               # [<bool>]
        #Option     "SWCursor"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoRAM"               # <i>
        #Option     "ActiveDevice"           # [<str>]
        #Option     "LCDDualEdge"            # [<bool>]
        #Option     "BusWidth"               # [<str>]
        #Option     "Center"                 # [<bool>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForcePanel"             # [<bool>]
        #Option     "TVDotCrawl"             # [<bool>]
        #Option     "TVDeflicker"            # <i>
        #Option     "TVType"                 # [<str>]
        #Option     "TVOutput"               # [<str>]
        #Option     "DisableVQ"              # [<bool>]
        #Option     "DRIXINERAMA"            # [<bool>]
        #Option     "DisableIRQ"             # [<bool>]
        #Option     "EnableAGPDMA"           # [<bool>]
        #Option     "NoAGPFor2D"             # [<bool>]
        #Option     "NoXVDMA"                # [<bool>]
        #Option     "ExaNoComposite"         # [<bool>]
    Identifier  "Card0"
    Driver      "via"
    VendorName  "Unknown Vendor"
    BoardName   "Unknown Board"
    BusID       "PCI:1:0:0"
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

```

On running a test server with this file, it produced a grey staticy screen (think a tv with no signal, but not moving) and the mouse pointer became a black X with white tips. It didn't progress from there and I had to kill it to get out of it.

---

### Post by DaveInPhx on 2010-02-06
Here is the logfile from the test server run ....

(had to figure out which log it was!)

Still using the .doc extension as the .txt extension is limited to 19kb

---

### Post by DaveInPhx on 2010-02-07
I didn't see any replies, so I've been "playing" with it a bit, pulling bits and pieces from different posts. I've managed to get it to 1024x768 using the following xorg.conf :-
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
        Driver          "via"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
```

Please don't ask me why or how, but it works!   

How can I add back the lower resolutions to make them optional while keeping the 1024x768 as the default?

---

