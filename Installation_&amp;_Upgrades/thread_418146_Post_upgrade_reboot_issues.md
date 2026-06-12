---
title: "Post upgrade reboot issues"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by hibernatus on 2007-04-22
Hi, 

CONFIGURATION
==========

CPU => amd x86_64
Graphique card => Ati radeon 9200 SE
Screen : ViewSonic VA1912w

Attached files 
========
Xorg.0.log
xorg.conf

ISSUE
====

at the end of the upgrade gdm doesn't start the error provide in Xorg.0.log show

> (--) Assigning device section with no busID to primary device
(EE) No devices detected.

Fatal server error:
no screens found


Can you help me please?

Thanks

---

### Post by heimo on 2007-04-22
I'd try changing fglrx to ati, adding VertRefresh and HorizSync lines and changing 1440x1440 to 1440x900. Below are sections I'd make changes to. There's high chance this won't work either, but could give some more information. Before making changes, backup your existing xorg.conf.

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
    Identifier   "VA1912wSERIE"
    Option        "DPMS"
    HorizSync   30-82
    VertRefresh 50-85
EndSection

Section "Device"
    Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
    Driver      "ati"
    BusID       "PCI:1:0:0"
EndSection


Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
    Monitor    "VA1912wSERIE"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
        Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768"
    EndSubSection
EndSection


Section "DRI"
    Mode         0666
EndSection
```


Monitor specs:
[http://www.viewsoniceurope.com/UK/Products/LCDE2/VA1912w.htm#features](http://www.viewsoniceurope.com/UK/Products/LCDE2/VA1912w.htm#features)

---

### Post by hibernatus on 2007-04-22
Hi,

Thanks for your answer, but unfortunatly this doesn't work.

I upload the new log 

Thanks for your help

---

### Post by heimo on 2007-04-22
This is the relevant part:
```
(EE) Problem parsing the config file
(EE) Error parsing the config file
```

There's probably typo by me or you in the xorg.conf.

---

### Post by hibernatus on 2007-04-22
Thanks for your help

this is working now 

\\:D/

---

### Post by hibernatus on 2007-04-22
Hi,

Unfortunatly, i have post the reply to fast.

My screen froze really fastly => :@

After somme reshearch it's seem that's it's linked to my graphique card (ATI RADEON 9200 SE) . i had success fully setup it under the version 6.05 and 6.10.

But it's seem that the new ATI driver and FGLRX doesn't support anny more this card :-(

So i have place as driver "vesa" but can somme one explain me and give me a step by step procedure to configure my 1440X900 resolution on the new ubuntu realese 7.04 and allso setup the 3D

Thanks

---

### Post by hibernatus on 2007-04-22
Hi,

 to solve my issue i have i have decided to reinstall the old driver 

but unfortunatly here what's i receved 
> 
fakeroot sh ./ati-driver-installer-8.28.8.run --buildpkg ubuntu/feisty
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
The distribution 'ubuntu' is not supported
Removing temporary directory: fglrx-install

---

### Post by Artemis3 on 2007-04-22
With your card you don't need closed drivers. This seems to be true at least with rv350 or earlier, so use:

driver "radeon"

And get rid of fglx, use aiglx for beryl usage. I tested it with a Radeon 9500 rv350; and games work nicely.

---

### Post by hibernatus on 2007-04-24
Hi 

i have tested with driver = "radeon" 

=> same thing the xserveur start and after few seconds it froze 

:confused: :(

---

