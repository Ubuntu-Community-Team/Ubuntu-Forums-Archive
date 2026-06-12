---
title: "Gutsy Does Not Recognize Logitech Wireless KB &amp; Mouse Properly."
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by Vienna01 on 2008-04-07
Gutsy Does Not Recognize Wireless KB & Mouse Properly.

PC is Dell Dimension 8300, nVidia FX 5200, Pentium 4.

I have tried many of the posted solutions described for similar Logitech issues on this forum unsuccessfully. 

**I am trying to get Gutsy to properly recognize my Logitech Wireless S510 KB and LX5 Mouse. Gutsy seems to think the mouse is one emulating a Macintosh mouse.**

I have included data for two setups

One was the Logitech KB & Mouse wirelessly connected to a Logitech receiver, and them the receiver is connected to the PC via PS/2. The KB link from the receiver actually terminates as a USB connector and uses a USB to PS/2 adapter to connect to the  PC.

The other environment was a debugging attempt with a Dell PS/2 KB and an HP PS/2 connected mouse.

I thought Gutsy is supposed to id the hardware at start up. It seems to try but gets it wrong. When I substituted the Dell KB & HP mouse, Gutsy _did _change the sections in the /proc/bus/input/devices file. However, the /etc/X11/xorg.conf file seems to be the _same_ under both the wired and the wireless set ups. The values I got for the **mouse section **in the /proc/bus/input/devices file when the wireless KB & Mouse were connected **are very different from those others **seem to get.

Suggestions of how I can get the Logitech Wireless KB & Mouse working properly are very much appreciated. 

_Here are the KB & Mouse Sections from the config files_:

[B]Logitech LX5 wireless mouse & S510 Wireless KB
 Mouse & KB sections of file "/proc/bus/input/devices[/B]"

**MOUSE SECTION**
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

**KEYBOARD SECTION**
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7


[B]
Logitech LX5 wireless mouse & S510 Wireless KB
 Mouse & KB sections of file "/etc/X11/xorg.conf"[/B]

**KEYBOARD SECTION**
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

**MOUSE SECTION**
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection
[B]
Directly Connected Via PS/2, HP KB & HP Mouse
  KB & Mouse sections of file "/proc/bus/input/devices[/B]"

MOUSE SECTION
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

KEYBOARD SECTION
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

[B]
Directly Connected Via PS/2, Dell KB & HP Mouse
Mouse & KB sections of file "/etc/X11/xorg.conf"[/B]

Exactly the same as with the wireless KB & mouse
!Surprised!

---

