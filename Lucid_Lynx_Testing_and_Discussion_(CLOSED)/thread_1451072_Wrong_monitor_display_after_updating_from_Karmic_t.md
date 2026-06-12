---
title: "Wrong monitor display after updating from Karmic to Lucid"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by saito80 on 2010-04-10
Hi to everyone.

Recently I update to Lucid Lynx, everything went fine except my monitor configuration. I have a Dell Inspiron 6400 laptop with Ati Mobility x1400. I used to work with an external monitor and expanding the desktop on my 2 displays. I have a samsung syncmaster 2253lw, optimal resolution of 1680 x 1050. On Karmic using ATI propietary drivers this dual monitor configuration worked fine. I read about an issue of Lucid with ATI propietary driver, so at this moment I'm not using it. My problem is that when I try to use my samsung monitor along with my laptop LCD, the image on the monitor is wrong with waves moving upwards. This is my xorg.conf file.

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Virtual    3120 1050
    EndSubSection
EndSection

Section "Module"
    Load        "glx"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    screen "Default Screen"
    # commented out by update-manager, HAL is now used
    #    Inputdevice    "Synaptics Touchpad"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "ati"
EndSection

Maybe I need additional manual configuration on my xorg file..??
Any help will be appreciate..!!
Francisco.

---

### Post by Kalibur on 2010-04-13
I have a dell xt and I get no GUI at all after setup and after upgrading.  Am giving it one more try.:confused:

---

