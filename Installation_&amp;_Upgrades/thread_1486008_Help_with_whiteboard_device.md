---
title: "Help with whiteboard device"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by kencamargo on 2010-05-17
Hello,

I am trying to set up a device for use with ubuntu Lucid, the knuckleheads that support it only reply to me that they just support Ubuntu 9.04...

It's called eBeam projector, and it consists of a pen with some kind of sensor that communicates to a device that sits on the corner of a projection screen an is connected in turn with the computer. 

The xorg.conf bit related to it under Ubuntu 9.4 is as follows:

Section "InputDevice"
    Driver    "ebeam"
    Identifier    "whiteboard-wand"
    Option    "Color"    "wand"
EndSection

Section "ServerLayout"
            Identifier "Default Layout"
            Screen     "Default Screen"
            InputDevice    "whiteboard-wand"    "SendCoreEvents"
EndSection

I read that the support for this kind of hardware was moved to the kernel under Lucid, and the configuration now has to be done via udev. I have no clue on how to translate the above to the appropriate format, could someone please help?

Thanks in advance,
Ken

---

