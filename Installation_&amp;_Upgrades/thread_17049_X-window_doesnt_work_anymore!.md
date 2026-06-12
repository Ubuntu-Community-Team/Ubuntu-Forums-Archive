---
title: "X-window doesnt work anymore!"
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by granite230 on 2005-02-25
So... I had Ubuntu Linux up and running for a while and then I wanted to install Cedega. 

The installation guide asked me to test a few things. It asked me to type *glxgears* into the terminal and the FPS had to be >500.  My terminal showed something <500 so maybe I needed to install some new Nvidia drivers. 
I'm only a newbie so I wasn't 100% sure so I decided just to try it. 

Somewhere on the web I found a howto on how to install the drivers or whatever... I found something and it said that I had to change a few things in the /etc/X11/XF86Config-4 file.

It looked something like this (the **bold** parts show the changes I've made):

Section "Files"
    # Multiple FontPath entries are allowed (they are concatenated together)
    # By default, Mandrake 6.0 and later now use a font server independent of
    # the X server to render fonts.
    RgbPath	"/usr/X11R6/lib/X11/rgb"
    FontPath "unix/:-1"
EndSection

Section "ServerFlags"
    #DontZap # disable <Crtl><Alt><BS> (server abort)
    AllowMouseOpenFail # allows the server to start up even if the mouse doesn't work
    #DontZoom # disable <Crtl><Alt><KP_+>/<KP_-> (resolution switching)
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
**#**  Load "dri"
    Load "dbe"
**#**  Load "GLcore"
    Load "glx" # 3D layer
    Load "synaptics"
EndSection

Section "InputDevice"
    Identifier "Keyboard1"
    Driver "Keyboard"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "es"
    Option "XkbCompat" ""
    Option "XkbOptions" ""
EndSection

Section "InputDevice"
  Driver  	"synaptics"
  Identifier  	"Mouse1"
  Option 	"Device"  	"/dev/psaux"
  Option	"Protocol"	"auto-dev"
  Option	"LeftEdge"      "1900"
  Option	"RightEdge"     "5400"
  Option	"TopEdge"       "1900"
  Option	"BottomEdge"    "4000"
  Option	"FingerLow"	"25"
  Option	"FingerHigh"	"30"
  Option	"MaxTapTime"	"180"
  Option	"MaxTapMove"	"220"
  Option	"VertScrollDelta" "100"
  Option	"MinSpeed"	"0.02"
  Option	"MaxSpeed"	"0.18"
  Option	"AccelFactor" "0.0010"
  Option	"SHMConfig"	"on"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
#  Option	"Repeater"	"/dev/ps2mouse"
EndSection

Section "InputDevice"
        Identifier  "LIRC-Mouse"
        Driver      "mouse"
        Option      "Device" "/dev/lircm"
        Option      "Protocol" "IntelliMouse"
        Option      "SendCoreEvents"
        Option      "Buttons" "5"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier "monitor1"
    VendorName "Generic"
    ModelName "Flat Panel 1600x1200"
    HorizSync 75
    VertRefresh 60
EndSection

Section "Device"
    Identifier "device1"
    Driver "radeon *This part said nv but I changed that to **nvidia***"
    Screen 0
    BusID "PCI:1:0:0"
    Option "DPMS"
    Option "EnablePageFlip" "true"
    #Option "AGPFastWrite"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    
    Subsection "Display"
        Depth 8
        Modes "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Modes "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Modes "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Modes "1600x1200" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "LIRC-Mouse"
    Screen "screen1"
EndSection

Section "ServerLayout"
    Identifier "layout2"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "LIRC-Mouse"
    Screen "screen1"
EndSection

**#**Section "DRI"
**#**	Mode 0666
**#**EndSection

So after I saved the file and rebooted, my X-Window system wouldn't work anymore! Now I can only use the command line and I don't know how to change it back! 

When I log in as root and type: *edit etc/F11/XF86Config-4* I still can't change it back! I can't seem to open the file... I don't know the commands. Is there a way to open/modify it so I can undo the changes?

---

### Post by alastair on 2005-02-25
Login as normal.

Then type :

sudo vi /etc/X11/XF86Config-4

Find the line that says :

 Driver "nvidia"

Put your cursor on the "i" - press "x" to delete the4 chars "idia".

Go to the line that says :

# Load "dri"

Put your cursor on the "#", press "x" to delete it.

Then, to save the file, press :

:wq

Then try starting X again.

---

### Post by granite230 on 2005-02-25
Yeah it works!

Thanx a lot!

---

### Post by alastair on 2005-02-25
Good stuff.

Note - this replaces the (currently) not working nvidia driver with the opensource "nv" driver. You can take a copy of this file and use it as a working backup, in case you screw things up :

sudo cp -p /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.nv.working

You can copy it back to XF86Config-4 if you need to fix things up ever.

---

