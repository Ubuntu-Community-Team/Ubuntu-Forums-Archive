---
title: "Slow performance in new install"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by CrimsonJustice on 2010-03-12
I purchased a Radeon 4350 so I could use my older machine for ubuntu. Originally, I tried hardy, as I had a disc laying around from an old install. Trying to run the hardy live cd, it would go through the boot sequence, and do the loading bar that is part of the normal startup, but after that, the screen would mess up and the computer would seem to freeze.

Well, I thought, perhaps there was just some compatibility issue because of the card. So I went and downloaded the karmic koala live cd to try out. This one worked, it booted up into gnome and would let me play...with one problem. The mouse was horrid. When moving it around the screen, it's choppy. Almost like the screen was being drawn at 4 fps. So I installed the os, and decided to try out the proprietary drivers. After trying out both the fglrx from ubuntu repositories and the ati one, I get ~700fps in gears with no slowdowns or anything, but the mouse still runs horridly. I've tried a few mouse tweaks but I'm really quite lost here. Even with the resolution jacked down to 640x480 and no desktop effects, it performs just as poorly.

What can I do to resolve this issue? Never had a mouse problem before... Even if it means going back to  9.04, 8.10, or 8.04, as long as I can get it working, I'll be happy.

---

### Post by CrimsonJustice on 2010-03-15
Through some help on IRC and reading a couple bazillion guides, I've updated a few things on karmic, but the cursor is still not working properly.

I have updated my kernel to 2.6.32, as these versions have support for the r7xx series of radeon cards with the radeon driver. I've compiled the radeon driver and mesa and my card is now running proper acceleration. 

> $ glxinfo | grep OpenGL
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RV710 954F) 20090101  TCL
OpenGL version string: 2.0 Mesa 7.8-devel
OpenGL shading language version string: 1.10Here is the xorg.conf section pertaining to the mouse, as well as the video:

> Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"

EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "R520 [Radeon X1800]"
    BusID       "PCI:1:0:0"
EndSection

Also of note is the fact that the cursor is running with hardware acceleration as far as I can tell. From my Xorg.0.log:

> (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00640000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00644000

I'll be workign with the guys on IRC later, but any suggestions would be wonderful!

---

