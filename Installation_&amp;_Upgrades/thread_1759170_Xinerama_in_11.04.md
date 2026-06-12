---
title: "Xinerama in 11.04"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by mukk85 on 2011-05-15
Hello,

I recently upgraded from 10.10 to 11.04 and everything was working great. I had dual monitors working with Xinerama however when I tried to install the latest ATI drivers I suddenly could not login with Xinerama enabled. I originally setup my drivers in ubuntu 10.04, but it worked right through until I just tried to upgrade them the other day.

I have tried both the ubuntu shipped drivers and the drivers from the ati website following the tutorial here: [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

EDIT: I did have compiz running with Xinerama in ubuntu 10.10

I have been searching everywhere and I have not been able to find any solution for this, wondering if anyone else is having this problem? or if someone could give me a hand with a solution.

Thanks.

---

### Post by kl0x on 2011-05-26
Solved? How?

---

### Post by joserf on 2011-06-24
> **kl0x said:**
> Solved? How?


friend,  had no answer to our friend up but decided as follows, I have an ati hd  6870, is attached pictures, leave the disabled xinerama and follow as  images, excuse my English because I'm Brazilian

joserf

---

### Post by tamashumi on 2011-07-03
I have this problem too. Fresh install 11.04. ATI HD 4870

With Xinerama can't log in to desktop. Keeps dropping me back to login screen.
Without Xinerama I can't drag windows to 2nd screen.

I don't think this thread is ready to be marked as solved.

Any solutions?

---

### Post by gcoram on 2011-10-13
Same here.
Firstly, once you cant login how do you turn off xinerama.
I can boot off a live ubuntu usb or probably even ctrl-alt to a terminal but then what ?
Any cli control for catalyst ?

---

### Post by tamashumi on 2011-10-13
I got this to working state by just using old xorg.conf from my  previous 9.04.
It seems ATI screwed something in CCC xorg.conf generation as my previous one was made through it. Well, with some tuning after ofc :)

I'll post my xorg.conf here just after I reboot into Ubuntu in couple of minutes.

```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen-0" 0 0
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "0-DFP3"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1920x1200"
        Option      "TargetRefresh" "60"
        Option      "Position" "1024 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
        Option      "Primary" "true"
EndSection

Section "Monitor"
        Identifier   "0-DFP5"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1280x1024"
        Option      "TargetRefresh" "75"
        Option      "Position" "0 0"
        Option      "Rotate" "left"
        Option      "Disable" "false"
EndSection

Section "Device"
        Identifier  "aticonfig-Device-0"
        Driver      "fglrx"
        Option      "Monitor-DFP3" "0-DFP3"
        Option      "Monitor-DFP5" "0-DFP5"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen-0"
        Device     "aticonfig-Device-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   3200 3200
                Depth     24
        EndSubSection
EndSection

```

EDIT: 
Check the master screen display line under first monitor's section. I've changed graphic card today and this line helped to place Unity Launchbar (aka Dash) to appropriate monitor. 
Ati Radeon HD 6950, Catalyst 11.9, Ubuntu 11.04

You may need to correct monitors settings // 'Monitor-DFP'
To check monitor - port name assignment list it with ```
xrandr -q
```

---

