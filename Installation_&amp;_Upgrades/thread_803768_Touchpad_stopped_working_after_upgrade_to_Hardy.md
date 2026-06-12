---
title: "Touchpad stopped working after upgrade to Hardy"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by Doojek9 on 2008-05-22
Hi all.

Recently upgraded to Hardy and ever since my touchpad stopped working completely. during the upgrade, ksynaptics that I've had has been removed, but later I've reinstalled it. Installed also gsynaptics but nothing seems to be working.

here's the output of tpconfig:

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).

and the related section of xorg.conf:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "AlwaysCore"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "LeftEdge" "1700"
Option "RightEdge" "5300"
Option "TopEdge" "1700"
Option "BottomEdge" "4200"
Option "FingerLow" "25"
Option "FingerHigh" "30"
Option "MaxTapTime" "0"
Option "MaxTapMove" "220"
Option "VertScrollDelta" "100"
Option "MinSpeed" "0.06"
Option "MaxSpeed" "0.12"
Option "AccelFactor" "0.0010"
Option "SHMConfig" "on"
EndSection

Using Toshiba Satellite A100 series.

Thanks.

---

