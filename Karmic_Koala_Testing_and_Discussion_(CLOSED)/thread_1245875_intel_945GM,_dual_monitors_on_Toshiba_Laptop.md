---
title: "intel 945GM, dual monitors on Toshiba Laptop"
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by interknighterrant on 2009-08-21
Ok I've had an interesting week or so.  My laptop worked flawlessly in Jaunty up until the time I plugged in an external monitor I had just bought.  At which point compiz broke and I was faced with what many users had from the get go for intel graphics.

After a LOT of testing and rummaging through proposed solutions, and none of them working, I decided to downgrade.  However, I noticed there was an alpha out of Karmic and thought I would give it a try before downgrading (look forward and not to the past!)


MUCH MUCH MUCH better.  Compiz is sharp, fluid, beautiful.  I never did benchmark my system in any meaningful manner so I can't give specifics.  Thank you thank you all who have been involved.


[SIZE="6"]THE PROBLEM:[/SIZE]
Ok, so here is where it is confusing.  During the live disk and up to this point my laptop's built in monitor has had a problem in Karmic.  Both the external monitor and the laptop have a 1440x900 resolution, differing refresh rates though.

I have tried to do the built in System > Preferences > Display to change it up, and when it tries it looks like the image extends beyond the external monitor and I only see the bottom 15 - 20 pixels of the screen, no improvement in the LCD on the laptop.  I searched for the quick solution and nothing popped up.  Any clues on where to hunt first?  I am thinking of messing with the xorg.conf file and seeing where that leads me.  Any / all advice would be appreciated.  I'll jot down anything I find in case this helps someone else.


lspci -vv:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0007
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at ffd80000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at cff8 [size=8]
	Region 2: Memory at e0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at ffd40000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
```

---

### Post by lenticular on 2009-09-09
No solutions, but I have the same problem on my Sony TZ130.

---

### Post by nanog on 2009-09-10
Your post is confusing. Could you please spell out the exact issue with your screen resolution.

Xorg.conf is pretty much just a place holder with intel drivers. 

Xrandr is now used to set modes:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

You may also have an edid bug. If so, please report it.

I also heartily recommend the edgers ppa. Screaming fast intel with no resolution limitation (e.g. 1440x900 and 1200x800 running at the same time...booyah!)

---

