---
title: "Intel Chipset ACPI issues"
date: 2009-06-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 00b00nt00 on 2009-06-21
My Medion MIM 2230 laptop will not suspend without crashing, nor will it turn off without the power button being pressed.

This has been an issue with every version of Ubuntu I have tried (8.04-9.10)

Here are the specs:

&#65279;Processor
Intel(R) Celeron(R) M CPU 410 @ 1.46GHz
Memory
2052MB (322MB used)
Operating System
Ubuntu karmic (development branch)
Date/Time
Sun 21 Jun 2009 13:41:15 JST
Display
Resolution
1280x800 pixels
OpenGL Renderer
Mesa DRI Intel(R) 945GM GEM 20090418 2009Q1 x86/MMX/SSE2
X11 Vendor
The X.Org Foundation
Multimedia
Audio Adapter
HDA-Intel - HDA Intel
Input Devices
Power Button
Lid Switch
Sleep Button
Macintosh mouse button emulation
AT Translated Set 2 keyboard
Video Bus
PC Speaker
SynPS/2 Synaptics TouchPad
HDA Digital PCBeep
SCSI Disks
ATA Hitachi HTS54321
TSSTcorp CD/DVDW SN-S082D
Operating System
Version
Kernel
Linux 2.6.30-9-generic (i686)
Compiled
#10-Ubuntu SMP Fri Jun 12 13:05:04 UTC 2009
C Library
GNU C Library version 2.9 (stable)
Default C Compiler
GNU C Compiler version 4.4.0 (Ubuntu 4.4.0-6ubuntu2) 
Distribution
Ubuntu karmic (development branch)


I had an 8 year-old Compaq Armada E500 running Ubuntu flawlessly. What gives?

---

### Post by diebels on 2009-06-21
Have you had a look at log files in /var/log ?

Maybe you need a bios update?

---

### Post by 00b00nt00 on 2009-06-21
This is the only error I could find in the logs relating to suspend:

medion kernel: [  371.993891] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0

This is the BIOS info:

Date		: 09/08/2006
Vendor		: INSYDE
Version		: M1.07
-Board-
Name		: MIM 2230
Vendor		: Notebook

I can't find an update on the manufacturer's web-site, so I think it's current.

---

