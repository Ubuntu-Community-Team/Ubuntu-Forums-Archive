---
title: "Add module to ubuntu server - minimal virtual machine"
date: 2014-06-25
forum: Installation &amp; Upgrades
---

### Post by wannesd on 2014-06-25
So,

I've setup a minimal virtual machine, which doesn't load a lot of modules.
I have 1 piece of hardware passed through to it, but the module is missing (it is in the normal server installation)
How do I add this?

Here's my output from lspci -v:

> 0b:00.0 Serial Attached SCSI controller: Adaptec PMC-Sierra PM8001 SAS HBA [Series 6H] (rev 05)        Subsystem: Adaptec Device 0800
        Physical Slot: 192
        Flags: fast devsel, IRQ 10
        Memory at fd4d0000 (64-bit, non-prefetchable) [size=64K]
        Memory at fd4e0000 (64-bit, non-prefetchable) [size=64K]
        Memory at fd4f0000 (32-bit, non-prefetchable) [size=64K]
        Memory at fd480000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>


Where it should be 

> 02:00.0 Serial Attached SCSI controller: Adaptec PMC-Sierra PM8001 SAS HBA [Series 6H] (rev 05) Subsystem: Adaptec Device 0800
 Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx+
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 32 bytes
 Interrupt: pin A routed to IRQ 16
 Region 0: Memory at fe5f0000 (64-bit, non-prefetchable) [size=64K]
 Region 2: Memory at fe5e0000 (64-bit, non-prefetchable) [size=64K]
 Region 4: Memory at fe5d0000 (32-bit, non-prefetchable) [size=64K]
 Region 5: Memory at fe580000 (32-bit, non-prefetchable) [size=256K]
 Expansion ROM at fe400000 [disabled] [size=1M]
 Capabilities: <access denied>
 Kernel driver in use: pm80xx


Note that the "Kernel driver in use" part is missing.

I tried adding it with > [FONT=Ubuntu Mono]sudo modprobe pm80xx [/FONT]
But that just gives me > [FONT=Ubuntu Mono]modprobe: FATAL: Module pm80xx not found.[/FONT]

Any idea on how I could install this module?

---

