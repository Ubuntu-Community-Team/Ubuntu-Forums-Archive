---
title: "ATI radeon 9100IGP in Xubuntu 11.04"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by jesseconibear on 2011-06-30
I was a casual ubuntu user for the last few years but have now taken the plunge into a full Xubuntu laptop install as my only operating system.  I am pretty good with computers but my linux/ubuntu knowledge is average at best.

I installed catalyst for this card, and kept getting something like a "card not found message".  so i did a purge and reinstall of opensource drivers.  this is where i start to have a few questions.

jesse@jclaptop:~$ **lspci -nn | grep VGA**
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] [1002:5835]

jesse@jclaptop:~$ [B]lspci -v -s 01:05.0
[/B]01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 006b
    Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 16
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 9000 [size=256]
    Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

to me it looks like it is saying that it is a 256M shared video card.  i believe it is a 128M.  (in wondows xp for the last 5 years it has been).  also under my Syspeek it says i have 874Mb memory, which makes sense of 1028Mb - 874 Mb = 128Mb for my video.

anyone have any input?  also flash games run like crap but flash video seem ok, is this something if have to learn to live with or is the something i can do to optimize my card?

sorry in advance if i am breaking any posting etiquette, this is my first post.
thanks
jesse

---

### Post by jesseconibear on 2011-06-30
tried this, i think i see that there is 128M VRAM.

anyone know what the line fb: conflicting [   24.943785] fb hw usage radeondrmfb vs VESA VGA - removing generic driver.

just trying to get my video card running optimally, from a lot researching it seems like video cards are the trickiest thing for linux

jesse@jclaptop:~$ **dmesg | grep drm**
[   24.644348] [drm] Initialized drm 1.1.0 20060810
[   24.943619] [drm] radeon defaulting to kernel modesetting.
[   24.943630] [drm] radeon kernel modesetting enabled.
**[   24.943785] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver**
[   24.950292] [drm] initializing kernel modesetting (RS300 0x1002:0x5835).
[   24.950388] [drm] register mmio base: 0xD0100000
[   24.950392] [drm] register mmio size: 65536
[   24.950956] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   24.950961] [drm] Driver supports precise vblank timestamp query.
[   24.950991] [drm] radeon: irq initialized.
[   24.951244] [drm] Detected VRAM RAM=128M, BAR=256M
[   24.951256] [drm] RAM width 64bits DDR
[   24.952111] [drm] radeon: 128M of VRAM memory ready
[   24.952116] [drm] radeon: 32M of GTT memory ready.
[   24.954274] [drm] Loading R200 Microcode
[   25.162551] [drm] radeon: ring at 0x00000000D2001000
[   25.162577] [drm] ring test succeeded in 0 usecs
[   25.163243] [drm] radeon: ib pool ready.
[   25.163449] [drm] ib test succeeded in 0 usecs
[   25.164000] [drm] Panel ID String: SEC                     
[   25.164097] [drm] Panel Size 1280x800
[   25.164259] [drm] Radeon Display Connectors
[   25.164265] [drm] Connector 0:
[   25.164269] [drm]   VGA
[   25.164274] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   25.164278] [drm]   Encoders:
[   25.164283] [drm]     CRT1: INTERNAL_DAC2
[   25.164286] [drm] Connector 1:
[   25.164290] [drm]   LVDS
[   25.164294] [drm]   Encoders:
[   25.164297] [drm]     LCD1: INTERNAL_LVDS
[   25.164301] [drm] Connector 2:
[   25.164305] [drm]   S-video
[   25.164308] [drm]   Encoders:
[   25.164311] [drm]     TV1: INTERNAL_DAC2
[   25.228778] [drm] fb mappable at 0xE0040000
[   25.228782] [drm] vram apper at 0xE0000000
[   25.228785] [drm] size 4096000
[   25.228787] [drm] fb depth is 24
[   25.228790] [drm]    pitch is 5120
[   25.229412] fb0: radeondrmfb frame buffer device
[   25.229417] drm: registered panic notifier
[   25.229445] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0

---

### Post by jesseconibear on 2011-06-30
this doesn't look good, i used glxinfo and got this

jesse@jclaptop:~$ **glxinfo**
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

---

### Post by jerrrys on 2011-06-30
looks like your card should work with vesa driver, but will not support 3D.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Radeon+Mobility+9100+IGP&as_qdr=m6&sa=Google+Search&lang=en#956](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Radeon+Mobility+9100+IGP&as_qdr=m6&sa=Google+Search&lang=en#956)

drivers

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Radeon+Mobility+9100+IGP+drivers&as_qdr=m6&sa=Google+Search&lang=en#1001](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Radeon+Mobility+9100+IGP+drivers&as_qdr=m6&sa=Google+Search&lang=en#1001)

---

### Post by jesseconibear on 2011-06-30
thanks for the help, ya that page definatley says that 3d is not supported with this card. 

that sucks, but i do at least i do not really use this laptop for games.  still plays vlc media great.

---

