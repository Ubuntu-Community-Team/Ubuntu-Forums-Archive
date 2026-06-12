---
title: "ATI Xpress 200M, sometimes it works..."
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by umberstark on 2009-09-15
and most fo the time it doesn't.

I just can't wrap my head around this, with the latest Karmic it's literally a lottery as to whether I'll get to the login screen or not. Most of the time it's "not". X just seems to fail to initialise.

I understand that the 200M is no longer supported by ATI (who will never see another penny of my money), but the fact that sometimes X initialise and sometimes it doesn't is beyond strange. I worry about it being a hardware problem, except windows 7 has no problems with it.

I read about a bit but haven't been able to find anything concrete on this. Anyone having the samer trouble? Is there a resolution (or will there be, before Karmic goes "gold")?

---

### Post by Sand &amp; Mercury on 2009-09-15
Uh oh. That's bad news for me.

---

### Post by jaakan on 2009-09-16
Which version of that chip set do you have?

here is what I have Dell Vostro 1000 with a clean install from Karmic Koala Alpha 4 and using ext4 as /

I don't have that issue.

lspci -nnvv

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
	Subsystem: Dell Device [1028:022a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 66 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at c8000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at 9000 [size=256]
	Region 2: Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel modules: radeon, radeonfb

---

### Post by Lollerke on 2009-09-16
I have the same problem with ATI Radeon Xpress 200M ( RC410M [1002-5A62 / 1179-FF31  (Rev 00)] ).

---

### Post by umberstark on 2009-09-17
It's the Intel Chipset variant (DAC runs at 400MHz rather than 300).

"ATI Radeon Xpress Series (0x5A62)"

It's the same, or similar to Lollerke's I see (1002-5A62).

EDIT: Forgot to note that this is on a Fujitsu Siemens LI-1718 laptop.

---

### Post by guayusa on 2009-10-08
Same problem here - it began with Jaunty and is the same in Karmic. Intrepid is fine. See also: [https://bugs.launchpad.net/bugs/444192](https://bugs.launchpad.net/bugs/444192)

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
	Subsystem: Toshiba America Info Systems Device 0001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at ce00 [size=256]
	Region 2: Memory at ffdf0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at ffd00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

---

### Post by umberstark on 2009-10-08
With the Beta and xsplash, I don't seem to have this problem anymore. It seems as if xsplash somehow fixed my problem.

I do, on the other hand, suffer this bug: [https://bugs.launchpad.net/bugzilla/+bug/305301]("https://bugs.launchpad.net/bugzilla/+bug/305301")

The above can be solved by disabling DRI in a created (there isn't one by default) xorg.conf, which does work, but Gnome always feels a but, I don't know, sluggish/old etc with desktop effects disabled (which disabling DRI does).

End of the day, I'll never touch another desktop or laptop with ATI/AMD GPU's after this one.

---

