---
title: "Intel 945gm karmic configuring xorg.conf"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oshunluvr on 2009-10-27
I am having several issues with my 945GM Intel card using Karmic. I updated early to Karmic because the newer kernel and xorg and intel driver are supposed to work better than previous editions. 

There seems to be almost no information on the web about setting things up with this combo - I assume because everything is bleeding edge and no one has reported their work. One of the first things I've run into is most of the "Options" and "Modules" from earlier setups are now either invalid or not needed.

My hope is this thread becomes a repository of sorts about using the newest xorg and intel video drivers.

My hardware:
Monitor: Panasonic TH-50PHD7uy Plasma ( 1366x766 )
Intel 945GM built-in
Connected via VGA cable (yuck, but all other ports in use)

Software:
Ubuntu 9.04 32bit updated to Karmic via update manager
Kernel 2.6.31-14-generic
xserver-intel-2.9.0

I am using this machine for a media computer and little else. I went with 32bit because I wanted Hulu Desktop, Boxee, and XBMC to run without recompiling or other 64 bit related issues.

First Issue:
Initial startup with intel driver caused a very small (640x480???) zoomed resolution (desktop edges were not visible) repeated across the screen and this flashed or rolled constantly. Reviewing log file showed both VGA and LVDS ports were being outputted to, but nothing is connected to the LVDS output. This fixed it:
Add to Section Device:
               Option "monitor-LVDS" "LVDS"

and add:
    Section "Monitor"
               Identifier "LVDS"
               Option "Ignore" "True"
    EndSection

NOTE: this is a second monitor section, do not remove or edit the first one!

Current issues:
Can't get resolution right - 1366x768 is native screen size, but I am yet unsuccessful. I can get close, but the whole desktop is several mm's to the left or too tall. Adjusting the modeline to correct the left-of-center causes the desktop to expand up and down.

Many errors in log file. Mostly to do with dri and a missing /dev/dri/card0 file. See errors/warnings list below.

While test my desired apps - XBMC is painfully S-L-O-W. Other apps seem OK so this may not be video driver related.

I would like any advice, bit I would also like others trying to setup intel video to report success/failure. 

Log errors and warnings
```
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x68000 (TV_CTL) changed from 0x400c0000 to 0x000c0000
(WW) intel(0): DRI2: failed to open drm device
(WW) intel(0): drmSetMaster failed: Bad file descriptor
(WW) intel(0): ESR is 0x00000011, page table error, instruction error
(WW) intel(0): PGTBL_ER is 0x00000010, display A pte
(WW) intel(0): Existing errors found in hardware state.
(EE) intel(0): [drm] Failed to open DRM device for : No such file or directory
(EE) intel(0): Failed to become DRM master.
(EE) intel(0): Failed to initialize kernel memory manager


```

---

