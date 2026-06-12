---
title: "Can't get Wireless working for ASUS 1005PE"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Tails on 2010-03-07
Hi all,

I fresh installed Ubuntu 10.04 Alpha 3 onto my 1005PE (bought it yesterday).... but the problem is that my wireless isn't working... I tried to install the linux-backports-modeules-wireless-2.6.32-15-generic-pae  talked in this thread.
[http://ubuntuforums.org/showthread.php?p=8923973](http://ubuntuforums.org/showthread.php?p=8923973)


but the wireless still isn't working..... so..... anyone has any other fixes?

Thx.. ^_^

---

### Post by Ibidem on 2010-03-07
Are you really using the PAE kernel on there? The drivers you installed are strictly for PAE kernels, as indicated by that "-pae" at the end.  
If you have "linux-generic", 2.6.32.15 installed, try installing "linux-backports-modules-2.6.32-15-generic".
Ibidem

---

### Post by Tails on 2010-03-07
> **Ibidem said:**
> Are you really using the PAE kernel on there? The drivers you installed are strictly for PAE kernels, as indicated by that "-pae" at the end.  
If you have "linux-generic", 2.6.32.15 installed, try installing "linux-backports-modules-2.6.32-15-generic".
Ibidem

yes..... i am when i install that it also install pae kernel, I rebooted the computer using the pae kernel....

---

### Post by uRock on 2010-03-07
Go to Ubuntu Software Center and install the linux-backports-module. [IMG]http://ubuntuforums.org/attachment.php?attachmentid=149149&d=1267854956[/IMG]

---

### Post by uRock on 2010-03-07
I had the same problem.

---

### Post by Tails on 2010-03-07
> **iRock said:**
> Go to Ubuntu Software Center and install the linux-backports-module. 

ya... i did install that package...
linux-backports-modeules-wireless-2.6.32-15-generic-pae

but i did it though command-line tho....... just wondering, did u use pae kernel after install?

thanks.. ^_^

---

### Post by uRock on 2010-03-07
> **Tails said:**
> ya... i did install that package...
linux-backports-modeules-wireless-2.6.32-15-generic-pae

but i did it though command-line tho....... just wondering, did u use pae kernel after install?

thanks.. ^_^

Yes. I was using it up until a few hours ago. I reinstalled Karmic after messing Lucid up.

---

### Post by uRock on 2010-03-07
> **Tails said:**
> ya... i did install that package...
linux-backports-modeules-wireless-2.6.32-15-generic-pae

but i did it though command-line tho....... just wondering, did u use pae kernel after install?

thanks.. ^_^

Is the wireless working now?

---

### Post by Tails on 2010-03-07
> **iRock said:**
> Is the wireless working now?

nope, thats why I opened this thread...... as I already did that step before posting... hehe... :popcorn:

meh... may be I will just install the Ubuntu 9.10..... but then I would miss the super fast boot-up... ;)

---

### Post by uRock on 2010-03-08
> **Tails said:**
> nope, thats why I opened this thread...... as I already did that step before posting... hehe... :popcorn:

meh... may be I will just install the Ubuntu 9.10..... but then I would miss the super fast boot-up... ;)

That bites. Mine was connecting, but I was having other issues.

---

### Post by James Little on 2010-03-31
I had to compile the bleeding edge wireless drivers from wireless.kernel.org to get wifi working on my 1005PE. It's the same on both Karmic and Lucid. I didn't have connection problems, rather the hardware was completely undetected by the driver shipping in the Ubuntu kernel (and I guess 2.6.32 in general).

More details are on my blog: 
[http://www.jameslittle.me.uk/asus-1005pe-ubuntu/]("http://www.jameslittle.me.uk/asus-1005pe-ubuntu/")

@iRock - it's interesting that your wifi kinda worked; the reason for failure of my chip seems to be a completely new device ID that was not in the driver. So I'm starting to think that the 1005PE could be shipping with various chips? The info here is also conflicting: 
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005PE](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005PE)

(see the Ubuntu 9.10 Karmic 64 bit section). My testing was with UNR. Seems this page may need to be corrected?

---

### Post by Tails on 2010-03-31
> **James Little said:**
> 
@iRock - it's interesting that your wifi kinda worked; the reason for failure of my chip seems to be a completely new device ID that was not in the driver. So I'm starting to think that the 1005PE could be shipping with various chips? The info here is also conflicting: 
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005PE](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005PE)

(see the Ubuntu 9.10 Karmic 64 bit section). My testing was with UNR. Seems this page may need to be corrected?

o.....  i c......... this explain y some people works and some ppl doesn't.... currently I am using Windows driver on Ubuntu as a temp solution, I guess I will install the 10.04 beta again and ur solution in this easter holiday and c how it goes... ^^

---

### Post by rickwood on 2010-04-01
Wow - this is odd.  I installed alpha 2 on my Eee 1005PE and both wireless and wired networking work flawlessly out of the box. I've been updating regularly, and wireless continues to work flawlessly. I wonder if the 1005PE wireless network card comes in multiple varieties?

---

### Post by James Little on 2010-04-03
> **rickwood said:**
> Wow - this is odd.  I installed alpha 2 on my Eee 1005PE and both wireless and wired networking work flawlessly out of the box. I've been updating regularly, and wireless continues to work flawlessly. I wonder if the 1005PE wireless network card comes in multiple varieties?

I think this is probably the case. Can you paste the output of: lspci -vvnn
and then we should be able to see what adapter is in your model.

---

### Post by rickwood on 2010-04-03
> **James Little said:**
> I think this is probably the case. Can you paste the output of: lspci -vvnn
and then we should be able to see what adapter is in your model.

Here it is (it's at the bottom). Looks like it's an Atheros AR9285.

```
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ac]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ac]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 28
	Region 0: Memory at f7e00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at dc00 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at f7d00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0100c  Data: 4199
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ac]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f7e80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ce]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 80000000-801fffff
	Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+
			Slot #  0, PowerLimit 0.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0300c  Data: 4161
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+
			Slot #  0, PowerLimit 0.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0300c  Data: 4169
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f7f00000-f7ffffff
	Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [40] Express (v1) Root Port (Slot+), MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
			ExtTag- RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #4, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <256ns, L1 <4us
			ClockPM- Suprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
		SltCap:	AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surpise+
			Slot #  0, PowerLimit 0.000000; Interlock- NoCompl-
		SltCtl:	Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
			Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
		SltSta:	Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
			Changed: MRL- PresDet- LinkState-
		RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
		RootCap: CRSVisible-
		RootSta: PME ReqID 0000, PMEStatus- PMEPending-
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0300c  Data: 4171
	Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Capabilities: [a0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at d480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at d880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at f7cf7c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01)
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]

00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information <?>

00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 27
	Region 0: I/O ports at d080 [size=8]
	Region 1: I/O ports at d000 [size=4]
	Region 2: I/O ports at cc00 [size=8]
	Region 3: I/O ports at c880 [size=4]
	Region 4: I/O ports at c800 [size=32]
	Region 5: Memory at f7cf7800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0100c  Data: 4191
	Capabilities: [70] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a8] SATA HBA <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:83ad]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 11
	Region 4: I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 29
	Region 0: Memory at f7fc0000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at ec00 [size=128]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 41a9
	Capabilities: [58] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 4096 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag- AttnBtn+ AttnInd+ PwrInd+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [6c] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [180] Device Serial Number ff-4e-cb-e0-c9-7c-45-ff
	Kernel driver in use: atl1c
	Kernel modules: atl1c

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Device [1a3b:1089]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f8000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
	Capabilities: [170] Power Budgeting <?>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

---

### Post by James Little on 2010-04-03
Yes, different adapters then. Mine is AR2427, which is the one with the problems. Think the wiki will need updating to reflect this; I know I'm not the only person with the 2427.

---

### Post by dionblundell on 2010-04-17
I have a AR2427 on 1005PE that does not work.
This WILL get it working using GNU drivers. I think that the kernel uses an old wireless build? Not sure why? Anyway, the following works.
Go here:
[http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)
and download the latest drivers, for example:
[URL="http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-16.tar.bz2"]http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-16.tar.bz2
[/URL]
Now extract these files
Open a SHELL, and change into the directory created with the archive, it's probably something like:
```
cd ~/Downloads/compat-wireless-2010-04-16

```now select the driver
```
./scripts/driver-select ath9k
```You now need to build the drivers
```
make
```Now install them with this
```
sudo make install
sudo make unload
sudo modprobe ath9k

```You will need to do ALL the above EACH TIME the kernel is updated.

There is a shell script attached which automates this.
I save it to my Downloads directory and automate the process like this:
```
cd ~/Downloads/compat-wireless-2010-04-16
../wireless-build.sh

```Hope this brings some peace for you.
Networking works perfectly for me on my ASUS 1005PE now

---

### Post by jalapeno on 2010-04-22
This fix worked for me. I have the device with the PCI ID 168c:002c.

I changed the updating script to also download the archive. Please find it attached. To use it, 
[LIST=1]
[*]Download it and put it somewhere say ~/wireless-updates/wireless-build.sh
[*]cd ~/wireless-updates
[*]Change it to be executable chmod u+x wireless-build.sh
[*]Run it ./wireless-build.sh
[/LIST]
The script will download the archive, unpack it, and build and install the drivers (as before).

Now whenever there is a kernel update, just re-run wireless-build.sh, and you will get the latest drivers downloaded and installed.

---

