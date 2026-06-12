---
title: "Logitech G7 Errors"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-09-27
[COLOR=Olive]**Goal:  Activate Side button for page back.**[/COLOR]

**Configuration:**
Feisty 7.04

**Edited xorg.conf file**
Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

[COLOR=RoyalBlue]Section "InputDevice"
        Identifier      "Logitech G7"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection[/COLOR]

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "NVidia GeForce 6600"
    Driver        "nvidia"
    BusID        "PCI:1:5:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Viewsonic VX2235wm"
    Option        "DPMS"
    HorizSync    30-130
    VertRefresh    50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVidia GeForce 6600"
    Monitor        "Viewsonic VX2235wm"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Logitech G7" "CorePointer"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

**/proc/bus/input/devices** File
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=056a Product=0016 Version=0403
N: Name="Wacom Graphire4 6x8"
P: Phys=
S: Sysfs=/class/input/input2
H: Handlers=mouse1 event2 ts1 
B: EV=1f
B: KEY=1c63 0 70011 0 0 0 0 0 0 0 0
B: REL=100
B: ABS=100 3000003
B: MSC=1

I: Bus=0003 Vendor=046d Product=c219 Version=0110
N: Name="Logitech Logitech Cordless RumblePad 2"
P: Phys=usb-0000:00:13.2-2.5/input0
S: Sysfs=/class/input/input3
H: Handlers=event3 js0 
B: EV=b
B: KEY=fff0000 0 0 0 0 0 0 0 0 0
B: ABS=30027

I: Bus=0003 Vendor=045e Product=00db Version=0111
N: Name="Microsoft Natural&#65533; Ergonomic Keyboard 4000"
P: Phys=usb-0000:00:13.0-1.1/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: LED=107

I: Bus=0003 Vendor=045e Product=00db Version=0111
N: Name="Microsoft Natural&#65533; Ergonomic Keyboard 4000"
P: Phys=usb-0000:00:13.0-1.1/input1
S: Sysfs=/class/input/input5
H: Handlers=kbd event5 
B: EV=10000f
B: KEY=7fff 2c3027 bf004440 0 0 1 10f80 8807c407 ffe77bfa d9715fff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=1 0

[COLOR=RoyalBlue]I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.0-1.2/input0
S: Sysfs=/class/input/input6
H: Handlers=mouse2 event6 ts2 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143[/COLOR]

[COLOR=RoyalBlue]I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:13.0-1.2/input1
S: Sysfs=/class/input/input7
H: Handlers=kbd event7 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 1 f80 8807c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0[/COLOR]

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input8
H: Handlers=kbd event8 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input9
H: Handlers=kbd event9 
B: EV=3
B: KEY=100000 0 0 0

[COLOR=Red]**Error Msg:**[/COLOR]
X Server does not start.  Can only boot to recovery mode.  Here is a summary of the error msg.

[COLOR=Red]Logitech G7-USB-0000:00:13.-1.2 /input1: Absolute Touch 'DIGI_Touch

The XKeyboard Keymap Compiler (xkbcomp) reports: Warning Multiple Names for Keycode 211
[/COLOR]
Can someone out there help me.  As you can see I did follow the popular threads and I cannot see any typos.

One thing I did notice is that "Logitech USB Reciever" is repeated twice in two sections in the **/proc/bus/input/devices** File

Sorry this was so long but I could not see any other way but to list everything accurately.  Who ever wrote the HowTo on this might have some insight in what is going on.  Some people say they did the above and got it working.  One person is said to have a G7 and another a similar G5.

Any help would be really appreciated.:)

---

