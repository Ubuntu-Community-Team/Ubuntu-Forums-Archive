---
title: "Ubuntu 9.10 + Atheros/Attansic network card"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NJC on 2009-09-26
Booted Ubuntu 9.04 Alpha 6 and I get the ominous circling network icon and no connection. I tried to follow instructions here:

[https://wiki.ubuntu.com/DebuggingNetworkManager](https://wiki.ubuntu.com/DebuggingNetworkManager)

Output lspci -vvv:

```


01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device 8304
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 27
    Region 0: Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at ec00 [size=128]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Address: 00000000fee0300c  Data: 4189
    Capabilities: [58] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 4096 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag- AttnBtn+ AttnInd+ PwrInd+ RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 unlimited, L1 unlimited
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [180] Device Serial Number ff-8c-24-00-b4-00-b6-ff
    Kernel driver in use: ATL1E
    Kernel modules: atl1e
```Is this worthy of a bug report? If it is of value to the community I will pursue ... otherwise my Ubuntuforums searches rendered little information about a specific network problem with Attansic/Atheros.

EDIT: Bug filed [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/437445](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/437445)

---

