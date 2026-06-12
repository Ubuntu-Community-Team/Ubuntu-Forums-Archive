---
title: "DVB S2 Mantis  not started &amp; no MAC"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by magictails on 2010-06-04
hi

all ok except 


Skystar HD2 (b):  1822:4e35 / Subsystem: 1ae4:0003 

lspc -vv

03:06.0  Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge  Controller [Ver 1.0] (rev 01)
    Subsystem: Device 1ae4:0003
     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-  Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF-  FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort-  >SERR- <PERR- INTx-
    Latency: 64 (2000ns min, 63750ns max)
     Interrupt: pin A routed to IRQ 3
    Region 0: Memory at fdeff000  (32-bit, prefetchable) [size=4K]

lspci -vvn

03:06.0 0480:  1822:4e35 (rev 01)
    Subsystem: 1ae4:0003
    Control: I/O- Mem+  BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR-  FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr-  DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-  INTx-
    Latency: 64 (2000ns min, 63750ns max)
    Interrupt: pin  A routed to IRQ 3
    Region 0: Memory at fdeff000 (32-bit,  prefetchable) [size=4K]


after looking in GG i tried 3 instal  how to but nothing change


 mutliproto , mantis drivers , v4l ,

i lost this 2 lines
Kernel driver in use: Mantis
       Kernel modules: mantis


la MAc not readed

card ok with win32 on Dvbdream & BDA.dev  108

correct  answser are  

*********************************************************************
dmesg

...

found  a UNKNOWN PCI UNKNOWN device on (00:07.0),
Mantis Rev 1 [1ae4:0003],  irq: 21, latency: 32
memory: 0xdddff000, mmio: 0xf8d3c000
MAC  Address=[00:08:c9:e0:28:9e]
mantis_alloc_buffers (0): DMA=0x35d10000  cpu=0xf5d10000 size=65536
mantis_alloc_buffers (0): RISC=0x35eef000  cpu=0xf5eef000 size=1000
DVB: registering new adapter (Mantis dvb  adapter)
mantis_ca_init (0): Registering EN50221 device
mantis_ca_init  (0): Registered EN50221 device
mantis_hif_init (0): Adapter(0)  Initializing Mantis Host Interface

ls -l /dev/dvb/adapter0

************************************

thank for advance 



sorry it's not the good section for post

 				
 			 			 			**En ligne**

---

