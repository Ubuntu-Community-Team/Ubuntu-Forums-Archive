---
title: "Two monitors, how to set it as &quot;1&quot; and &quot;2&quot;?"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2006-11-30
I have installed a Geforce 7600 card and it is working, but not as I would like it.

My Acer AL1921 (digital) should be on the left side and my Buffalo (analog) should be on the right side (as in Windows).

I could not figure out how to set it the screens into this order.

The resolution is also different.
Acer AL1921 can up to 1280x1024, while Buffalo can only 1024x768.

I was hoping it can be managed to get the highest resolution 1280x1024 on Acer AL1921 (full screen) and the same resolution on Buffalo as a virtual bigger screen than physically. I could not figure that out.

My /etc/X11/xorg.conf ends with:

> Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV37GL [Quadro FX 330/GeForce PCX 5300]"
         Driver      "nvidia"
         VendorName  "Asus"
         BoardName   "NVIDIA GeForce EN7600GS Silent"
         Option      "TwinView"                 "true"
         Option      "RenderAccel"              "true"
         Option      "UseEdidFreqs"             "true"
         Option      "MetaModes"                "1600x1200,1024x768;1280x1024,1024x768;1024x768,1024x768;800x600,800x600;640x480,640x480"
         Option      "SecondMonitorHorizSync"   "30-110"
         Option      "SecondMonitorVertRefresh" "50-160"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV37GL [Quadro FX 330/GeForce PCX 5300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200""1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


---

### Post by Scunizi on 2006-11-30
Here's a copy of my xorg running dual monitors (a little different setup). I have LCD/DVI monitor (1280x1024) on the right and CRT (1024x768) on left.  

```
Section "ServerLayout"
 Identifier	"xinerama"
 Screen	0 "Screen0"
 Screen	1 "Screen1" RightOf "Screen0"
 InputDevice    "Generic Keyboard"
 InputDevice    "Configured Mouse"
 Option "Xinerama" "1"
EndSection

Section "Files"

 # path to defoma fonts
 FontPath        "/usr/share/X11/fonts/misc"
 FontPath        "/usr/share/X11/fonts/cyrillic"
 FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
 FontPath        "/usr/share/X11/fonts/Type1"
 FontPath        "/usr/share/X11/fonts/100dpi"
 FontPath        "/usr/share/X11/fonts/75dpi"
 FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
 Load           "i2c"
 Load           "bitmap"
 Load           "ddc"
 Load           "extmod"
 Load           "freetype"
 Load           "glx"
 Load           "int10"
 Load           "type1"
 Load           "vbe"
EndSection

Section "InputDevice"
 Identifier     "Generic Keyboard"
 Driver         "kbd"
 Option         "CoreKeyboard"
 Option         "XkbRules" "xorg"
 Option         "XkbModel" "pc104"
 Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
 Identifier     "Configured Mouse"
 Driver         "mouse"
 Option         "CorePointer"
 Option         "Device" "/dev/input/mice"
 Option         "Protocol" "ExplorerPS/2"
 Option         "ZAxisMapping" "4 5"
 Option         "Emulate3Buttons" "true"
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSection


Section "Monitor"
 Identifier	"Envision"
 Option	"dpms"
 HorizSync 30.0-81.0
 VertRefresh 56-75
EndSection

Section "Monitor"
 Identifier	"HSD HN199D"
 Option	"dpms"
 HorizSync 30.0-98.0
 VertRefresh 50-160
EndSection

Section "Device"
    Identifier  "Nvidia0"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       0
 #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    #Option "ConnectedMonitor" "CRT"
    Option "UseDisplayDevice" "CRT"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    #Option "AllowGLXWithComposite" "true"
    Option "NvAgp" "3"
    Option "UseEdidDpi" "TRUE"
EndSection

Section "Device"
    Identifier  "Nvidia1"
    VendorName  "PNY"
    BoardName   "GeForce 6600 GT"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
    Screen       1
    #SINCE NVIDIA VERSION 1.0-8756 YOU MUST USE UseDisplayDevice INSTEAD OF ConnectedMonitor TO GET XINERAMA WORK:
    #Option "ConnectedMonitor" "DFP"
    Option "NvAgp" "3"
    Option "UseDisplayDevice" "DFP"
    Option "NoLogo" "0"
    Option "RenderAccel" "true"
    #Option "AllowGLXWithComposite" "true"
    Option "UseEdidDpi" "TRUE"
EndSection

Section "Screen"
    Identifier	"Screen0"
    Device	"Nvidia0"
    Monitor	"Envision"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1024x768" "800x600"
    EndSubsection
EndSection

Section "Screen"
    Identifier	"Screen1"
    Device	"Nvidia1"
    Monitor	"HSD HN199D"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600"
    EndSubsection
EndSection

```

I hope this helps... If you need to reverse position of the screens, flip flop the identifiers in the appropriate locations.

---

### Post by mojoman on 2006-12-02
Hi,

Scunizi,
I think I'm gonna give your version a go i order to get my projector set up as dual monitor (twinview has only given me headache so far). 

I saw this line in your xorg.conf
```
Section "Extensions"
 Option "Composite" "Enable"
EndSection
```
what does it control? The projector is connected with HDMI, should this be changed?

Also, how can I find out what version of nVidia I'm using?

Thanks
/mojoman

---

### Post by Scunizi on 2006-12-02
Hi mojoman,  Sorry for the late reply.  For some reason the email servers didn't deliver you post until 4pm Pacific Standard time.  That would be GMT-8.  

The composit extension is something neccessary for the xinerama to function properly.  It doesn't relate to CRT or DVI or HDMI (DVI w/ audio).  I'm running a CRT & DVI monitor off a dual head nvidia card.  

The drivers I installed were from synaptic.  Search for nvidia-glx and install that.  I didn't attempt to install the binary drivers... too many problems.  Synaptic is easier.  After installing the drivers, look at my xorg.conf again and you'll see where I changed the driver from vesa or nv to nvidia.  You have to do that at the sudo level, save, then CTRL ALT Backspace to restart x with the new values.  While it's restarting you should see the nvidia splash screen briefly.  If you blink you might miss it.  After everything loads, open a terminal and type glxgears -printfps and you'll have a nice moving graphic of three gears and in the terminal box you'll start seeing FPS numbers.  Don't take those to heart.  I heard they are not actual ie accuract numbers, but are handy for referance if you are trying to tweek things.;)

---

