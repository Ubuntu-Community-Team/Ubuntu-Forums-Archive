---
title: "lucid on my toshiba can't see my d-link router."
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by chicoinc on 2010-04-12
Hi Sorry if i have overlooked a thread.

I'm running Lucid on a Toshiba satellite L500-13p. 
I have keept Vista (what a pice of C... and installed ubuntu. I think it's called dual booting. 

My problem is that Lucid Can't find my D-link router. My wifi can see my neighbours and the one across the street. But not mine. 

accoding to lspci -vv i have a realtek card in the computer.

[I]14:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8151
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at 4000 [size=256]
	Region 1: Memory at f2200000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl819xSE
	Kernel modules: r8192se_pci
[/I]

I have tried installing the card again with the driver from realteks homepage but still no luck. 

And just for info my Eee 901 running ubuntu karmic works fine and finds my router just fine.

Hope you can help. And you can overlook the typos :-)

Michael

---

### Post by chicoinc on 2010-04-19
finally i fixed it.
After I deleted the original driver (from /lib/modules/<version>/kernel/ubuntu) and installed the new one

and thanks to #10 ([http://ubuntuforums.org/showthread.php?p=9143281#post9143281](http://ubuntuforums.org/showthread.php?p=9143281#post9143281)) for explaning it 

1: Download the latest driver from Realtek's site:
[http://www.realtek.com/downloads/dow...Downloads=true](http://www.realtek.com/downloads/dow...Downloads=true) (it's the RTL8192SE one)

2: Unpack the archive, cd into the folder.

3: sudo su

4: make

5: make install

6: reboot

7: Enjoy wireless

That did it for me.

---

