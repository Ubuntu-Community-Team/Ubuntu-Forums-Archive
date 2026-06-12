---
title: "nVidia video artifacts in X"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by fpurdue on 2007-08-06
I have been running feisty on my hp nc6400 laptop for quite some time and think it works like a rockstar and when I got my new hp xw9400 workstation for work I decided to make feisty the primary os on it as well.  

The system is an x64 Opteron dual core 2216 with 2GB of ram, sata disks,  a Quadro FX 1500, and (3) 19" HP L1906 monitors (only one is in use so far) and is fast as hell but I am getting a bizarre shadow/affect/blurry issue on my monitors.  Basically as soon as I load X I see the "image" of the screen but I also see a faint identical shadow image moved a few millimeters to the right.  The effect is similar to wearing a pair of glasses that are just a little bit off (or having a few too many drinks and getting back on your computer).  If I take a screenshot and open it on another workstation I don't see the artifacts (so it isn't a monitor thing)

This is a brand new install of Ubuntu, completely stock and the issue happens with either the stock drivers that came with Ubuntu or the closed source drivers from nVidia's website.

Here are the important parts of my xorg.conf:

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "Monitor"
    Identifier     "HP L1906"
    VendorName     "HP"
    ModelName      "HP L1906"
    HorizSync       83.0
    VertRefresh     76.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1500"

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "HP L1906"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection

---

### Post by fpurdue on 2007-08-09
Okay I need to be put to sleep over this one.

One of my interns just pointed out the one thing I never occurred to me - 

"Did you make sure the cable isn't bad"

Monitor works fine now :)

---

