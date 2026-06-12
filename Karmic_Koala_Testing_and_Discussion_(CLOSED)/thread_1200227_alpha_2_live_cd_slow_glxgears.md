---
title: "alpha 2 live cd slow glxgears"
date: 2009-06-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-06-29
running alpha 2 cd on acer aspire 3680 specs follow
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1.83 ghz w/ 1 gig ram


ran glx gears was getting 2100-2800 fps, no desktop effects enabled.

compared to jaunty with full desktop effects enabled (custom), kubuntu-desktop installed (but running gnome with gdm, still prefer it), and gdesklets running as well and get 4100-4500 fps.

I've done no tweaking what-so-ever with video drivers in either one.  Is this a problem?  Anyone know what's up with this?

ps.. truck driver, might be a few days before I can get back to you.

---

### Post by budluva04 on 2009-06-29
do you have direct rendering enabled? is the hardware driver enabled? does compiz work? if you answer no to any of these....well there's your problem :P

---

### Post by psyke83 on 2009-06-29
The first problem: you assume that glxgears is a benchmark. **It is not**.

The Intel driver is now using DRI2 and UXA acceleration - which has different performance characteristics to the older DRI1/EXA. The most notable difference is that glxgears generally gives a lower score compared to the older acceleration framework, but real-world games and 3D applications have much better performance than before.

Take a look at my Intel guide for more details on the state of the Intel drivers (and why glxgears is useless).

---

### Post by buzzmandt on 2009-06-30
thank you psyke, that's good to know and i won't use glxgears for pretty much anything anymore....

I still don't think my intel video card drivers are installing, can't enable desktop effects and graphics just don't look.... well, as good.  but will start a new thread for the new problem

---

### Post by psyke83 on 2009-06-30
> **buzzmandt said:**
> thank you psyke, that's good to know and i won't use glxgears for pretty much anything anymore....

I still don't think my intel video card drivers are installing, can't enable desktop effects and graphics just don't look.... well, as good.  but will start a new thread for the new problem

Desktop effects (i.e. compiz) may seem a little slower with UXA/DRI2, but I suspect that's because DRI2 uses vertical synchronization by default (whereas vertical synchronization isn't even possible with compiz and DRI1, due to the way indirect rendering works). Things may seem to lag more, but there will be no tearing when dragging windows, etc.

Apparently, performance with vertical synchronization will improve a lot more when the Intel driver implements triple buffering, but it is possible to disable synchronization in the meantime and restore some performance in compiz. The driver option is called "SwapWaitBuffers" and is only available with the newer xorg-edgers drivers for the moment. 

Note that aside from compiz, 3D performance should be superior (games, for example).

---

### Post by buzzmandt on 2009-06-30
well, compiz is fine, when drivers load (or whatever is going on)  please see my new post for more information.... kinda weird.

---

### Post by psyke83 on 2009-06-30
> **buzzmandt said:**
> well, compiz is fine, when drivers load (or whatever is going on)  please see my new post for more information.... kinda weird.

Compiz may blacklist your chipset. You can override this behaviour, but you can naturally expect instability.

See: [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

---

