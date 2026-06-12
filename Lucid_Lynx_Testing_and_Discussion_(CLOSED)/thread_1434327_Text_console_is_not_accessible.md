---
title: "Text console is not accessible"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by megaexception on 2010-03-20
After upgrade to lucid, i am not able to switch to text console (using ctrl-alt-f1..f6).when i try to change vt, i get screen frozen (same image, no video mode change) and cursor disappeared, and no my input displayed.
but still i can return to X using ctrl-alt-f7.


i think it is related to KMS or plymouth introduced in Lucid.
is there known fixes or workarounds to this problem?

p.s. this is my video card info:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Acer Incorporated [ALI] Device 027f
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 28
        Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
        Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Region 4: I/O ports at 4110 [size=8]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
                Address: fee0100c  Data: 4199
        Capabilities: [d0] Power Management version 3
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: i915

```

---

### Post by megaexception on 2010-03-21
removing plymouth (apt-get purge plymouth) helped.now i can watch boot process, and more important, i gain capability to change virtual terminals ctrl-alt-fN and use text console :)


i never liked plymouth, so i am not sorry. but then i have few new problems:
* initrd complains it cannot start plymouth
* apt-get purge plymouth also removed cryptsetup, but i need it

---

