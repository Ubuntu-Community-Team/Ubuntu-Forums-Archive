---
title: "Ubuntu 18.04, Installation on SDCard"
date: 2018-05-24
forum: Installation &amp; Upgrades
---

### Post by guicar on 2018-05-24
Hello world !

I have an Sdcard related issue on my fresh Ubuntu 18.0 install.

Mmc2 is my future boot device as I started from a live Usb cd stick
When i put this same Sd card on a Cardreader hub then Ubuntu boot is fine and I don't have any error using dmesg.
So the issue **is not related **to the card itself. 

**Dmesg** result when booting on live usb stick

[ 2331.156735] mmcblk2: error -110 sending status command, retrying
[ 2331.213011] mmc2: Tuning timeout, falling back to fixed sampling clock
[ 2331.213737] mmcblk2: error -110 sending status command, retrying
[ 2331.214485] mmcblk2: error -110 sending status command, aborting
[ 2331.214518] print_req_error: I/O error, dev mmcblk2, sector 194432
[ 2341.464673] mmc2: Timeout waiting for hardware interrupt.
[ 2341.464703] mmc2: sdhci: ============ SDHCI REGISTER DUMP ===========
[ 2341.464726] mmc2: sdhci: Sys addr:  0x00000008 | Version:  0x00001002
[ 2341.464739] mmc2: sdhci: Blk size:  0x00007200 | Blk cnt:  0x00000008
[ 2341.464753] mmc2: sdhci: Argument:  0x0002f780 | Trn mode: 0x0000003b
[ 2341.464767] mmc2: sdhci: Present:   0x01ff0001 | Host ctl: 0x00000017
[ 2341.464780] mmc2: sdhci: Power:     0x0000000f | Blk gap:  0x00000080
[ 2341.464793] mmc2: sdhci: Wake-up:   0x00000000 | Clock:    0x00000007
[ 2341.464806] mmc2: sdhci: Timeout:   0x0000000a | Int stat: 0x00000000
[ 2341.464819] mmc2: sdhci: Int enab:  0x02ff008b | Sig enab: 0x02ff008b
[ 2341.464832] mmc2: sdhci: AC12 err:  0x00000000 | Slot int: 0x00000000
[ 2341.464846] mmc2: sdhci: Caps:      0x0568c8b2 | Caps_1:   0x00000807
[ 2341.464859] mmc2: sdhci: Cmd:       0x0000123a | Max curr: 0x00000000
[ 2341.464873] mmc2: sdhci: Resp[0]:   0x00000000 | Resp[1]:  0x301017a2
[ 2341.464886] mmc2: sdhci: Resp[2]:   0x55534430 | Resp[3]:  0x00000000
[ 2341.464897] mmc2: sdhci: Host ctl2: 0x0000800b
[ 2341.464912] mmc2: sdhci: ADMA Err:  0x00000000 | ADMA Ptr: 0x35820200
[ 2341.464921] mmc2: sdhci: ============================================
[ 2341.465465] mmcblk2: error -110 sending status command, retrying
[ 2341.466184] mmcblk2: error -110 sending status command, retrying
[ 2341.466384] mmcblk2: error -110 sending status command, aborting
[ 2341.466413] print_req_error: I/O error, dev mmcblk2, sector 194432
[ 2341.466445] Buffer I/O error on dev mmcblk2p1, logical block 24048, async page read
[ 2351.704490] mmc2: Timeout waiting for hardware interrupt.
[ 2351.704515] mmc2: sdhci: ============ SDHCI REGISTER DUMP ===========
[ 2351.704532] mmc2: sdhci: Sys addr:  0x00000002 | Version:  0x00001002
[ 2351.704546] mmc2: sdhci: Blk size:  0x00007200 | Blk cnt:  0x00000002
[ 2351.704560] mmc2: sdhci: Argument:  0x00000802 | Trn mode: 0x0000003b
[ 2351.704573] mmc2: sdhci: Present:   0x01ff0001 | Host ctl: 0x00000017
[ 2351.704587] mmc2: sdhci: Power:     0x0000000f | Blk gap:  0x00000080
[ 2351.704600] mmc2: sdhci: Wake-up:   0x00000000 | Clock:    0x00000007
[ 2351.704613] mmc2: sdhci: Timeout:   0x0000000a | Int stat: 0x00000000
[ 2351.704628] mmc2: sdhci: Int enab:  0x02ff008b | Sig enab: 0x02ff008b
[ 2351.704641] mmc2: sdhci: AC12 err:  0x00000000 | Slot int: 0x00000000
[ 2351.704655] mmc2: sdhci: Caps:      0x0568c8b2 | Caps_1:   0x00000807
[ 2351.704670] mmc2: sdhci: Cmd:       0x0000123a | Max curr: 0x00000000
[ 2351.704684] mmc2: sdhci: Resp[0]:   0x00000000 | Resp[1]:  0x301017a2
[ 2351.704697] mmc2: sdhci: Resp[2]:   0x55534430 | Resp[3]:  0x00000000
[ 2351.704710] mmc2: sdhci: Host ctl2: 0x0000800b
[ 2351.704723] mmc2: sdhci: ADMA Err:  0x00000000 | ADMA Ptr: 0x35820200
[ 2351.704732] mmc2: sdhci: ============================================
[ 2351.705360] mmcblk2: error -110 sending status command, retrying
[ 2351.706102] mmcblk2: error -110 sending status command, retrying
[ 2351.706285] mmcblk2: error -110 sending status command, aborting
[ 2351.706315] print_req_error: I/O error, dev mmcblk2, sector 2050
[ 2351.706550] EXT4-fs (mmcblk2p1): unable to read superblock
[ 2361.944264] mmc2: Timeout waiting for hardware interrupt.
[ 2361.944291] mmc2: sdhci: ============ SDHCI REGISTER DUMP ===========
[ 2361.944312] mmc2: sdhci: Sys addr:  0x00000002 | Version:  0x00001002
[ 2361.944328] mmc2: sdhci: Blk size:  0x00007200 | Blk cnt:  0x00000002
[ 2361.944341] mmc2: sdhci: Argument:  0x00000802 | Trn mode: 0x0000003b
[ 2361.944355] mmc2: sdhci: Present:   0x01ff0001 | Host ctl: 0x00000017
[ 2361.944368] mmc2: sdhci: Power:     0x0000000f | Blk gap:  0x00000080
[ 2361.944381] mmc2: sdhci: Wake-up:   0x00000000 | Clock:    0x00000007
[ 2361.944394] mmc2: sdhci: Timeout:   0x0000000a | Int stat: 0x00000000
[ 2361.944407] mmc2: sdhci: Int enab:  0x02ff008b | Sig enab: 0x02ff008b
[ 2361.944420] mmc2: sdhci: AC12 err:  0x00000000 | Slot int: 0x00000000
[ 2361.944434] mmc2: sdhci: Caps:      0x0568c8b2 | Caps_1:   0x00000807
[ 2361.944447] mmc2: sdhci: Cmd:       0x0000123a | Max curr: 0x00000000
[ 2361.944460] mmc2: sdhci: Resp[0]:   0x00000000 | Resp[1]:  0x301017a2
[ 2361.944474] mmc2: sdhci: Resp[2]:   0x55534430 | Resp[3]:  0x00000000
[ 2361.944485] mmc2: sdhci: Host ctl2: 0x0000800b
[ 2361.944498] mmc2: sdhci: ADMA Err:  0x00000000 | ADMA Ptr: 0x35820200
[ 2361.944510] mmc2: sdhci: ============================================


**cat /proc/version**
Linux version 4.15.0-20-generic (buildd@lgw01-amd64-039) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018
[B]
Device Information[/B]

BIOS Information
    Vendor: American Megatrends Inc.
    Version: 5.11
    Release Date: 10/12/2017
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 6144 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 5.11

System Information
    Manufacturer: CHUWI INNOVATION AND TECHNOLOGY(SHENZHEN)CO.LTD
    Product Name: Hi10 plus tablet
    Version: Hampoo_reserve
    Serial Number: 0123456789ABCDEF
    UUID: 03000200-0400-0500-0006-000700080009
    Wake-up Type: Power Switch
    SKU Number: P1D6_C189B_Hi10_plus
    Family: CherryTrail CR -- Hampoo

Processor Information
    Socket Designation: SOCKET 0
    Type: Central Processor
    Family: Atom
    Manufacturer: Intel
    ID: C4 06 04 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 76, Stepping 4
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Atom(TM) x5-Z8350 CPU @ 1.44GHz
    Voltage: 1.2 V
    External Clock: 80 MHz
    Max Speed: 2400 MHz
    Current Speed: 1440 MHz
    Status: Populated, Enabled
    Upgrade: Socket BGA1155
    L1 Cache Handle: 0x0032
    L2 Cache Handle: 0x0033
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Fill By OEM
    Part Number: Fill By OEM
    Core Count: 4
    Core Enabled: 4
    Thread Count: 4
    Characteristics:
        64-bit capable

Any input is most welcome ;)

---

