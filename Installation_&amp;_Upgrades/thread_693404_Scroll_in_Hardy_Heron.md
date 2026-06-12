---
title: "Scroll in Hardy Heron"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by shashank314 on 2008-02-11
I install Hardy Heron on my presario 2200 series laptop. Now the scroll on the touchpad is not working. I was working fine with Gutsy. I looked up on the forum and installed gsynaptics to in an attempt to get it working but the package keeps on asking me to add the line
option "SHMConfig" "true" 
to xorg.conf. I already tried various options like adding a section module with load "synaptics" but nothing seems to work. I also restarted the system after every change I tried.

I am pasting the present version of the xorg.conf below

 Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "intl"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier "Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizEdgeScroll" "0"
        Option "VertScrollDelta" "0"
        Option "SHMConfig" "true"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
EndSection

Section "Module"
        Load "synaptics"
EndSection

---

