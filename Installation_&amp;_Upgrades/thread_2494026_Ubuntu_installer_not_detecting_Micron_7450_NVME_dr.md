---
title: "Ubuntu installer not detecting Micron 7450 NVME drive on SMC AS-4125GS-TNRT2"
date: 2024-01-03
forum: Installation &amp; Upgrades
---

### Post by KoSoVaR on 2024-01-03
Hi all! This one has me stumped and hoping for some help from the community.

Summary of problem: Ubuntu doesn’t recognize a Micron NVMe drive during install but Rocky does just fine.

Non exhaustive list of things tried
 - exhaustive BIOS settings review and modifications
 - install Rocky 9.3 recognizes the drive and works just fine with the nvme kernel module
 - physical install of equivalent micron m.2 drive, which Ubuntu does recognize

Hardware Platform: SuperMicro AS-4125GS-TNRT2 ([https://www.supermicro.com/en/products/system/gpu/4u/as-4125gs-tnrt2](https://www.supermicro.com/en/products/system/gpu/4u/as-4125gs-tnrt2)). Please note this is an AMD Genoa server.

NVMe drive for OS: Micron 7450 Pro (MTFDKCB960TFR1BC, [https://www.micron.com/products/ssd/product-lines/7450](https://www.micron.com/products/ssd/product-lines/7450))
Firmware: E2MU200

I’ve combed through the manual and BIOS and have lost hair over it. I have dumped all settings, including hidden ones to a spreadsheet and can’t seem to identify anything that is amiss.

What is really stumping me is that when I boot a Rocky 9.3 installer on this machine I see the NVMe drive and can install Rocky just fine. nvme kernel module is used as seen below:

c6:00.0 Non-Volatile memory controller: Micron Technology Inc 7450 PRO NVMe SSD (rev 01)
        Subsystem: Micron Technology Inc Device 2000
        Kernel driver in use: nvme
        Kernel modules: nvme

Now when I try Ubuntu (latest, or through MaaS), the drive isn’t recognized. I can’t install Ubuntu on the machine locally because the drive isn’t recognized.

I tried putting the same Micron 7450 m.2 equivalent in the m.2 slot and it recognized just fine. Ubuntu installs and the world is happy. However this isn’t an acceptable approach for my use case, as I would like to install the OS on a removable NVMe drive and not the internal m.2 slot.

---

### Post by MAFoElffen on 2024-01-03
> **KoSoVaR said:**
> 

Now when I try Ubuntu (latest, or through MaaS), the drive isn’t recognized. I can’t install Ubuntu on the machine locally because the drive isn’t recognized.

I tried putting the same Micron 7450 m.2 equivalent in the m.2 slot and it recognized just fine. Ubuntu installs and the world is happy. However this isn’t an acceptable approach for my use case, as I would like [COLOR=#ff0000]to install the OS on a removable NVMe drive and not the internal m.2[/COLOR] slot.
So wht abrand and model of USB3.2 to M.2 NVMe drive enclosure are you trying to use? And in which USB port of your Motherboard?

---

### Post by olzi on 2024-08-06
I have the same problem with SuperMicro AS-4125GS-TNRT2. Ubuntu 24.04 LTS does not detect the NVMe drives. Tried Rocky 9.4 and it detected the drives. I have Samsung and Kioxia NVMe disks.

Did you resolve this problem?

---

### Post by him610 on 2024-08-06
FWIW, back during the pandemic I thought I would try Rocky Linux. Downloaded it, put it on a USB stick, and installed it on one of my computers, gave it a whole disk. After booting up, I had some issues with Rocky and came to the conclusion I would stick with my trusted friendly Xubuntu.
Xubuntu would not recognize the disk with Rocky on it. I don't know why; I just never figured it out. Eventually, I was able to completely wipe the drive and reformat it.

---

### Post by ubfan1 on 2024-08-06
The Orico M.2 NVME SSD enclosure works just fine on my MSI GP66 USB3 (5GB/Sec).  Did a full install of Ubuntu 24.04 onto it and have been running a couple months. the only thing I did to alter the system was to add a udev rule so TRIM would work. To /etc/udev/rules.d, add the file 50-usb-ssd-trim.rules containing:
ACTION=="add|change", ATTRS{idVendor}=="0bda", ATTRS{idProduct}=="9210", SUBSYSTEM=="scsi_disk", ATTR{provisioning_mode}="unmap"
Change vendor/productId for your device. The SSD I used was a Hynix 256GB I'd pulled from another machine.

---

### Post by olzi on 2024-08-07
The NVMe hot-swap disks are connected using the U.3 connector directly via PCIe 5.0 protocol. No USB here...

The disks are Kioxia CM7-R disks: [https://apac.kioxia.com/en-apac/business/ssd/enterprise-ssd/cm7-r.html](https://apac.kioxia.com/en-apac/business/ssd/enterprise-ssd/cm7-r.html)

Tested Almalinux 9 and the disks was detected. Something is wrong with the nvme driver/kernel that comes with Ubuntu...

Almalinux 9 comes with kernel 5.14.0-427.13.1.el9_4.x86_64

lspci info (almalinux):

[SIZE=1][FONT=courier new]43:00.0 0108: 1e0f:0013 (rev 01) (prog-if 02 [NVM Express])
        Subsystem: 1e0f:0043
        Physical Slot: 15
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 419
        NUMA node: 0
        IOMMU group: 29
        Region 0: Memory at f0310000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at f0300000 [disabled] [size=64K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [70] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 1024 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset+ SlotPowerLimit 0.000W
                DevCtl: CorrErr- NonFatalErr- FatalErr+ UnsupReq-
                        RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+ FLReset-
                        MaxPayload 256 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- NonFatalErr- FatalErr- UnsupReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 32GT/s, Width x4, ASPM not supported
                        ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
                LnkCtl: ASPM Disabled; RCB 64 bytes, Disabled- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 32GT/s (ok), Width x4 (ok)
                        TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+ NROPrPrP- LTR-
                         10BitTagComp+ 10BitTagReq- OBFF Not Supported, ExtFmt- EETLPPrefix-
                         EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit-
                         FRS- TPHComp- ExtTPHComp-
                         AtomicOpsCap: 32bit- 64bit- 128bitCAS-
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- LTR- OBFF Disabled,
                         AtomicOpsCtl: ReqEn-
                LnkCap2: Supported Link Speeds: 2.5-32GT/s, Crosslink- Retimer+ 2Retimers+ DRS-
                LnkCtl2: Target Link Speed: 32GT/s, EnterCompliance- SpeedDis-
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete+ EqualizationPhase1+
                         EqualizationPhase2+ EqualizationPhase3+ LinkEqualizationRequest-
                         Retimer- 2Retimers- CrosslinkRes: Upstream Port
        Capabilities: [b0] MSI-X: Enable+ Count=129 Masked-
                Vector table: BAR=0 offset=00005200
                PBA: BAR=0 offset=0000d600
        Capabilities: [d0] Vital Product Data
                Product Name: KIOXIA ESSD
                Read-only fields:
                        [PN] Part number: KIOXIA KCMYXRUG15T3                     
                        [EC] Engineering changes: 0001
                        [SN] Serial number: 1EB0A04U0LP3        
                        [MN] Manufacture ID: 1E0F
                        [RV] Reserved: checksum good, 26 byte(s) reserved
                End
        Capabilities: [100 v2] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO+ CmpltAbrt- UnxCmplt+ RxOF+ MalfTLP+ ECRC+ UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr-
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr-
                AERCap: First Error Pointer: 00, ECRCGenCap+ ECRCGenEn- ECRCChkCap+ ECRCChkEn-
                        MultHdrRecCap+ MultHdrRecEn- TLPPfxPres- HdrLogCap-
                HeaderLog: 00000000 00000000 00000000 00000000
        Capabilities: [148 v1] Device Serial Number 8c-e3-8e-e3-00-aa-dd-30
        Capabilities: [168 v1] Alternative Routing-ID Interpretation (ARI)
                ARICap: MFVC- ACS-, Next Function: 0
                ARICtl: MFVC- ACS-, Function Group: 0
        Capabilities: [178 v1] Secondary PCI Express
                LnkCtl3: LnkEquIntrruptEn- PerformEqu-
                LaneErrStat: 0
        Capabilities: [198 v1] Physical Layer 16.0 GT/s <?>
        Capabilities: [1c0 v1] Lane Margining at the Receiver <?>
        Capabilities: [1e8 v1] Extended Capability ID 0x2a
        Capabilities: [210 v1] Single Root I/O Virtualization (SR-IOV)
                IOVCap: Migration-, Interrupt Message Number: 000
                IOVCtl: Enable- Migration- Interrupt- MSE- ARIHierarchy+
               IOVSta: Migration-
                Initial VFs: 32, Total VFs: 32, Number of VFs: 0, Function Dependency Link: 00
                VF offset: 1, stride: 1, Device ID: 0013
                Supported Page Size: 00000553, System Page Size: 00000001
                Region 0: Memory at 0000000000000000 (64-bit, non-prefetchable)
                VF Migration: offset: 00000000, BIR: 0
        Kernel driver in use: nvme
        Kernel modules: nvme[/FONT][/SIZE]


Same lspci output (-nvv) from Ubuntu 24.04 (kernel: 6.8.0-38-lowlatency):

[SIZE=1][FONT=courier new]43:00.0 0108: 1e0f:0013 (rev 01) (prog-if 02 [NVM Express])
    Subsystem: 1e0f:0043
    Physical Slot: 15
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 10
    NUMA node: 0
    IOMMU group: 29
    Expansion ROM at <ignored> [disabled]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [70] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 1024 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset+ SlotPowerLimit 0W
        DevCtl:    CorrErr- NonFatalErr- FatalErr+ UnsupReq-
            RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+ FLReset-
            MaxPayload 256 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- NonFatalErr- FatalErr- UnsupReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 32GT/s, Width x4, ASPM not supported
            ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp+
        LnkCtl:    ASPM Disabled; RCB 64 bytes, Disabled- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 32GT/s, Width x4
            TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis+ NROPrPrP- LTR-
             10BitTagComp+ 10BitTagReq- OBFF Not Supported, ExtFmt- EETLPPrefix-
             EmergencyPowerReduction Not Supported, EmergencyPowerReductionInit-
             FRS- TPHComp- ExtTPHComp-
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- LTR- 10BitTagReq- OBFF Disabled,
             AtomicOpsCtl: ReqEn-
        LnkCap2: Supported Link Speeds: 2.5-32GT/s, Crosslink- Retimer+ 2Retimers+ DRS-
        LnkCtl2: Target Link Speed: 32GT/s, EnterCompliance- SpeedDis-
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance Preset/De-emphasis: -6dB de-emphasis, 0dB preshoot
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete+ EqualizationPhase1+
             EqualizationPhase2+ EqualizationPhase3+ LinkEqualizationRequest-
             Retimer- 2Retimers- CrosslinkRes: Upstream Port
    Capabilities: [b0] MSI-X: Enable- Count=129 Masked-
        Vector table: BAR=0 offset=00005200
        PBA: BAR=0 offset=0000d600
    Capabilities: [d0] Vital Product Data
        Product Name: KIOXIA ESSD
        Read-only fields:
            [PN] Part number: KIOXIA KCMYXRUG15T3                     
            [EC] Engineering changes: 0001
            [SN] Serial number: 1EB0A04U0LP3        
            [MN] Manufacture ID: 1E0F
            [RV] Reserved: checksum good, 26 byte(s) reserved
        End
    Capabilities: [100 v2] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO+ CmpltAbrt- UnxCmplt+ RxOF+ MalfTLP+ ECRC+ UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- AdvNonFatalErr-
        AERCap:    First Error Pointer: 00, ECRCGenCap+ ECRCGenEn- ECRCChkCap+ ECRCChkEn-
            MultHdrRecCap+ MultHdrRecEn- TLPPfxPres- HdrLogCap-
        HeaderLog: 00000000 00000000 00000000 00000000
    Capabilities: [148 v1] Device Serial Number 8c-e3-8e-e3-00-aa-dd-30
    Capabilities: [168 v1] Alternative Routing-ID Interpretation (ARI)
        ARICap:    MFVC- ACS-, Next Function: 0
        ARICtl:    MFVC- ACS-, Function Group: 0
    Capabilities: [178 v1] Secondary PCI Express
        LnkCtl3: LnkEquIntrruptEn- PerformEqu-
        LaneErrStat: 0
    Capabilities: [198 v1] Physical Layer 16.0 GT/s <?>
    Capabilities: [1c0 v1] Lane Margining at the Receiver <?>
    Capabilities: [1e8 v1] Extended Capability ID 0x2a
    Capabilities: [210 v1] Single Root I/O Virtualization (SR-IOV)
        IOVCap:    Migration- 10BitTagReq- Interrupt Message Number: 000
        IOVCtl:    Enable- Migration- Interrupt- MSE- ARIHierarchy+ 10BitTagReq-
        IOVSta:    Migration-
        Initial VFs: 32, Total VFs: 32, Number of VFs: 0, Function Dependency Link: 00
        VF offset: 1, stride: 1, Device ID: 0013
        Supported Page Size: 00000553, System Page Size: 00000001
        Region 0: Memory at 0000000000000000 (64-bit, non-prefetchable)
        VF Migration: offset: 00000000, BIR: 0
    Kernel modules: nvme[/FONT][/SIZE]

When comparing the output there are a number of differences, mainly that ubuntu has no "Kernel driver in use". But also note that MSI-X is enabled in alma, but disabled in ubuntu...

---

