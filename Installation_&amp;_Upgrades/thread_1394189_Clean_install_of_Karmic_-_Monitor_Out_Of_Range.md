---
title: "Clean install of Karmic - Monitor Out Of Range"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by danduq on 2010-01-30
Hi,

I've just installed Karmic and get an Out Of Range message on my monitor when starting.

I had to use the alternate install in order to get Karmic on there in the first place.

I have an Nvidia GeForce 7600 GS, and a BenQ FP767-12 TFT.

Output of lspci;
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

Not sure how to get my xorg.conf as I can only get to a shell. Here are (what I think are) the important bits;
```

Section "ServerLayout"
 Identifier "X.org Configured"
 Screen 0 "screen0" 0 0
EndSection

Section "Module"
 Load "dbe"
 Load "extmod"
 Load "dri"
 Load "dri2"
 Load "record"
 Load "glx"
EndSection

Section "Monitor"
 Identifier "Monitor0"
 VendorName "Monitor Vendor"
 ModelName "Monitor Model"
EndSection

Section "Device"
 Identifier "Card0"
 Driver "fbdev"
 VendorName "nVidia Corporation"
 BoardName "G73 [GeForce 7600 GS]"
 BusID "PCI:1:0:0"
EndSection

```

I've tried commenting out ALL of the "Device" stuff and using Driver "vesa", but this does not help.

If I try to run Xorg -configure I get a segfault;
```

(EE) open /dev/fb0: No such file or directory
...
Saw signal 11. Server aborting.
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11
Segmentation fault

```

Any help gratefully received!

Cheers.

---

### Post by danduq on 2010-01-31
I've managed to fix this now. For anyone else who has this problem and finds this thread, here's what I did...

I was able to boot to the shell, it was only X that wouldn't start, so I created a new blank /etc/X11/xorg.conf file with the following settings;
```

Section "Monitor"
        Identifier  "BenQ FP767-12"
        VendorName  "BenQ"
        ModelName   "FP767-12"
        HorizSync   48-62
        VertRefresh 65-80
EndSection

Section "Screen"
        Identifier  "BenQ"
        Device      "Generic Video Card"
        Monitor     "BenQ FP767-12"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
        Screen      0
EndSection

```

I got the HorizSync and VertRefresh ranges from the manual for my monitor which I found online using Google (on another machine), and looked at the rates for a 1024x768 resolution.

I then ran "startx", and leapt for joy as I saw a mouse cursor appear!

Once I got to the desktop, I went to System - Administration - Hardware Drivers and picked the recommended nVidia driver.

I now have a lovely 1280x1024 resolution with Extra Visual Effects enabled.  :D

---

