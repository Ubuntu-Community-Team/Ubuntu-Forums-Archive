---
title: "HOWTO install proprietary ATI driver in Karmic"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by roalt on 2009-10-13
Hi all,

I installed Ubuntu Karmic on my old PC with a ATI 9800 pro card. I noticed that my desktop was not really responsive with user interaction (as opposed to my previous Hardy installation), so I thought to give the ATI proprietary drivers a try. 

But how do you install them? I've read something about doing:

 **sudo apt-get install fglrx-installer**

.. but it says "*E: Couldn't find package fglrx-installer*"

So, how do I install them ? I also see there is no /etc/X11/xorg.conf anymore, so I wouldn't know how to change the driver after installation.

Or could there be some other reason for the 'sluggish behaviour'?

---

### Post by taavikko on 2009-10-13
The fglrx drivers won't work on that particular hardware, ATI has dropped support for them.

As for the performance, disable compiz if that improves the situation.

---

### Post by Longinus00 on 2009-10-13
> **roalt said:**
> Hi all,

I installed Ubuntu Karmic on my old PC with a ATI 9800 pro card. I noticed that my desktop was not really responsive with user interaction (as opposed to my previous Hardy installation), so I thought to give the ATI proprietary drivers a try. 

But how do you install them? I've read something about doing:

 **sudo apt-get install fglrx-installer**

.. but it says "*E: Couldn't find package fglrx-installer*"

So, how do I install them ? I also see there is no /etc/X11/xorg.conf anymore, so I wouldn't know how to change the driver after installation.

Or could there be some other reason for the 'sluggish behaviour'?

What exactly is sluggish about your desktop? Can you describe it? I have a 9800 and the open source drivers seem to be working fine, even with compiz.

---

### Post by roalt on 2009-10-14
> **Longinus00 said:**
> What exactly is sluggish about your desktop? Can you describe it? I have a 9800 and the open source drivers seem to be working fine, even with compiz.

Well, in the first instance, everything works fine. But if you click from one window to the other one, it takes sometimes like 1-2 seconds before the new window becomes highlighted. I first thought it was because my computer was thrashing (I have 1GB of RAM), but it also happens with less applications open. I do have compiz running and have not yet tried to turn that off (but you do not seem to have this problem?).

I will try to get some more measurements from my system (CPU load, reaction time, etc.)

---

### Post by roalt on 2009-10-14
I did some additional tests:

* If I run thunderbird (2.0.0.23 20090817) it is a guarantee that my system becomes slow. The Xorg process goes beyond 90% if you do anything with thunderbird.

* Without thunderbird running, it seems to work better, although I've encountered some complete freezes of my system. I had to press the reset button on my machine to recover. I do not seem to find any evidence of a system Oops in my loggings unfortunately.

---

### Post by jocko on 2009-10-14
I have a radeon 9600 pro with similar poor performance as you describe with the automatic default options. I manage to get much better performance if I create a xorg.conf with some extra options (I'm not sure which ones made the difference).


This is my xorg.conf. I think you should be able to use it as it is. The only problem I've noticed is that openGL seems to render some artefacts on the screen. That can probably be fixed by inactivating one of the options in the device section (but I don't know which...):
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
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
EndSection

Section "Device"
        Option        "EnableDepthMoves"    "True"
        Option        "EnablePageFlip"    "True"
        Option        "DMAForXv"        "True"
        Option        "AccelDFS"        "True"
        Option        "ColorTiling"        "True"
        Option        "RenderAccel"        "True"
    Option        "VGAAccess"        "True"
        Option        "AccelMethod"        "EXA"
        Option        "DRI"            "True"
    Option        "MigrationHeuristics"    "greedy"
    Option        "TripleBuffer"        "True"
    Option        "EXAOptimizeMigration"  "true"
        Option        "EXANoComposite"    "No"
    Option        "BackingStore"        "true"
    Option        "AGPMode"        "8"
    Identifier    "Card0"
    Driver        "radeon"
    VendorName    "ATI Technologies Inc"
    BoardName    "RV350 AP [Radeon 9600]"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    Option     "Accel"    "True"
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Extensions"
    Option "RENDER" "Enable"
    Option "Composite" "True"
    Option "XVideo" "Enable"
    Option "XINERAMA" "False"
EndSection

Section "DRI"
    Mode        0666
EndSection
```
To create a xorg.conf, just run this in as terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
Copy/paste my xorg.conf into the empty text file that opens, save and close gedit. Then restart X (Alt+SysRq+k or log out or reboot).

---

### Post by roalt on 2009-10-14
> **jocko said:**
> I have a radeon 9600 pro with similar poor performance as you describe with the automatic default options. I manage to get much better performance if I create a xorg.conf with some extra options (I'm not sure which ones made the difference).
...
To create a xorg.conf, just run this in as terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
Copy/paste my xorg.conf into the empty text file that opens, save and close gedit. Then restart X (Alt+SysRq+k or log out or reboot).

Wow, that helps a lot! My desktop becomes much more responsive. I wonder what change in the xorg file causes this performance boost!

I've not seen openGL artifacts (yet). I did notice that Google Earth is slow, but to be honest, I do not know if the new open source drivers can handle google earth well. 

So there is still live in my old AGP-based video card (due to the AGP->PCI transfer there is not much of an update available).

---

