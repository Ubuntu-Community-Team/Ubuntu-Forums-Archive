---
title: "gsynaptics not working"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by BobvanderPoel on 2010-05-02
Installed lucid on my laptop and mostly no problems ...

However, the touch pad is driving me nuts. I've tried to set it with the gsynaptics program (system->Preferences->touchpad). It sort-of works, but the settings don't seem to "take". They certainly do not reset on a new boot.

Yes, in my System->Preferences->Startup Applications I have "touchpad" enabled.

If I try from a terminal I get a bunch of errors:

bob@MellowLap:~$ gsynaptics-init

** (gsynaptics-init:1897): WARNING **: Using synclient
bob@MellowLap:~$ X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  37 (X_ChangeDeviceProperty)
  Value in failed request:  0x112
  Serial number of failed request:  22
  Current serial number in output stream:  23

Did some searching a find comments about doing stuff in /etc/X11/xorg.conf ... but there is no such file on my system.

Please help. The overly sensitive touchpad is not nice. It was all working nicely on karmic!

I have a acer travelmate 2480.

Thanks

---

### Post by BobvanderPoel on 2010-05-06
Okay, I think I have this solved.

Problem is that I should not be using gsynaptics. When you install this package it inserts a <touchpad> entry in you system menu. Don't do this :)

Instead,use System->Preferences->Mouse which has a touchpad tab. This works fine.

I think that there is a conflict between the 2 touchpad settings. Unfortunate, since the gsynaptics has more options.

Hope this helps.

---

