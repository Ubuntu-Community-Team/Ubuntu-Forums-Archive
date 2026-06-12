---
title: "ACPI Probelsm on install"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by vanderkerkoff on 2008-01-16
Hello everyone

I've installed ubuntu gutsy gibbon onto a HP ML350 box.

I keep getting these errors on boot, the system works fine, but it's worrying me.

Can anyone tell me what is going on?

Here's the error from dmesg

[    1.450000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[    1.450000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.1
[    1.450000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.2
[    1.450000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.3
[    1.460000] PCI: Device 0000:00:00.0 not found by BIOS

Here's the devices they relate to on lspci -vv

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Compaq Computer Corporation Unknown device 3201
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 5000 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Compaq Computer Corporation Unknown device 3201
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 18
	Region 4: I/O ports at 5020 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Compaq Computer Corporation Unknown device 3201
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 19
	Region 4: I/O ports at 5040 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Compaq Computer Corporation Unknown device 3201
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at 5060 [size=32]

---

### Post by Pumalite on 2008-01-16
How are your USB connections working?

---

### Post by vanderkerkoff on 2008-01-16
I'm never going to use one, it's a web server.

Think it's okay to ignore?

---

### Post by Pumalite on 2008-01-16
I would.

---

### Post by vanderkerkoff on 2008-01-16
I will

thanks for your advice Pumalite, adn I wont hold you repsonsible in any way for anything that happens from this point on.

promise

:-)

---

### Post by Pumalite on 2008-01-16
I'll hold you to your word.

---

### Post by vanderkerkoff on 2008-01-17
it's all I have so I don't give it lightly

:-)

---

