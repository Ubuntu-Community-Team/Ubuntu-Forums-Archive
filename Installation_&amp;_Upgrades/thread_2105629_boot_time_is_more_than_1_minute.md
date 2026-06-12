---
title: "boot time is more than 1 minute"
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by curiousgally on 2013-01-16
All,

I have recently purchased a machine with OEM installed windows8 on a hdd. i swapped the hdd with a SSD and installed Ubuntu on it. Windows8 was loading up in less than 20 seconds. Now ubuntu on the SSD takes more than a minute to load.:sad:

I do have other problems like my system doesn't directly pick up linux from the start etc. I manually have to interrupt the boot and select ubuntu to boot up. But the boot time i'm talking of is the time taken after I chose ubuntu to boot from the boot options.

Please find the attached bootchart image. I'm new to this and can somebody help me out on what seems to be wrong at the boot time.

thanks.

---

### Post by hydn79 on 2013-01-16
Do you have a bigger version of that image?

---

### Post by curiousgally on 2013-01-16
Ohh,,
it does automatic conversion from png->jpg.

sorry abt that..please find the attached archived png file.

Thanks.

---

### Post by curiousgally on 2013-01-19
I dont' see any activity other than kthreadd,kworker etc right from 0 seconds..all other activity starts off at only 50 seconds. What could be going wrong? Any help is appreciated !!!

---

### Post by curiousgally on 2013-01-28
Can somebody help me. >1 minute is not at all acceptable to me on a SSD !!!!

---

### Post by oldfred on 2013-01-28
I have never understood boot charts, but look at dmesg. You can use Log File Viewer or look in /var/log.
I look for long times between entires, outright errors at mounting or loading something, or repeated tries and then failure or maybe success. Sometimes boot parameters then help on timing or correctly loading driver.

On my 6 year old desktop with a Microcenter SSD (not real fast), dmesg says about 10 sec from pressing enter in grub menu to working system - first entry to last entry. With my system BIOS/grub takes about 15 sec so my total boot time is about 25 sec.

But if system was Windows 8 pre-installed it is UEFI. Did you install Ubuntu in BIOS or UEFI mode? 
And did you turn off fast boot in UEFI?  That is so you can get to UEFI menu from Windows.
And turn off secure boot?

If you can boot you do not need nomodeset, but may need other parameters
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

            [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

            [SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w

---

### Post by curiousgally on 2013-01-28
Thanks oldfred.

My machine came pre-installed with Windows8 but then I replaced the hard disk with a SSD and installed ubuntu on the whole drive. The boot chart somehow says there is no activity until the first 50 seconds. There is a LED on the laptop which blinks on disk access. So I see the first blink at around 50 seconds after I select ubuntu from the boot list and then the login page comes up in less than 15 seconds (after the first blink). So I feel the first disk access is what is taking time.

I will look at the links you provided.

Appreciate your help.!!!
Thanks.

---

### Post by curiousgally on 2013-01-28
Following is the dmesg file output after boot

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-22-generic (buildd@komainu) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 (Ubuntu 3.5.0-22.34-generic 3.5.7.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-22-generic root=UUID=73d4fc0c-63e6-48f7-99b7-e58c2d3e2a46 ro quiet splash elevator=noop vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008ffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000090000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000b0160fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b0161000-0x00000000b0362fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000b0363000-0x00000000b694efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000b694f000-0x00000000bae9efff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bae9f000-0x00000000baf9efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000baf9f000-0x00000000baffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bafff000-0x00000000baffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bb000000-0x00000000bf9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f80f8000-0x00000000f80f8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023e5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by Lenovo
[    0.000000] efi:  ACPI=0xbaffe000  ACPI 2.0=0xbaffe014  SMBIOS=0xbae9e000 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000005a000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x000000000005a000-0x000000000005c000) (0MB)
[    0.000000] efi: mem03: type=3, attr=0xf, range=[0x000000000005c000-0x0000000000087000) (0MB)
[    0.000000] efi: mem04: type=4, attr=0xf, range=[0x0000000000087000-0x0000000000088000) (0MB)
[    0.000000] efi: mem05: type=3, attr=0xf, range=[0x0000000000088000-0x0000000000090000) (0MB)
[    0.000000] efi: mem06: type=0, attr=0xf, range=[0x0000000000090000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem07: type=3, attr=0xf, range=[0x0000000000100000-0x0000000000110000) (0MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000000110000-0x0000000001460000) (19MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000001460000-0x0000000002000000) (11MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x0000000002000000-0x0000000003350000) (19MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x0000000003350000-0x0000000020000000) (460MB)
[    0.000000] efi: mem12: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020200000) (2MB)
[    0.000000] efi: mem13: type=7, attr=0xf, range=[0x0000000020200000-0x00000000362e2000) (352MB)
[    0.000000] efi: mem14: type=2, attr=0xf, range=[0x00000000362e2000-0x0000000037169000) (14MB)
[    0.000000] efi: mem15: type=7, attr=0xf, range=[0x0000000037169000-0x0000000040004000) (142MB)
[    0.000000] efi: mem16: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem17: type=7, attr=0xf, range=[0x0000000040005000-0x00000000812ea000) (1042MB)
[    0.000000] efi: mem18: type=2, attr=0xf, range=[0x00000000812ea000-0x00000000adb32000) (712MB)
[    0.000000] efi: mem19: type=4, attr=0xf, range=[0x00000000adb32000-0x00000000adb52000) (0MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x00000000adb52000-0x00000000b014b000) (37MB)
[    0.000000] efi: mem21: type=4, attr=0xf, range=[0x00000000b014b000-0x00000000b0161000) (0MB)
[    0.000000] efi: mem22: type=0, attr=0xf, range=[0x00000000b0161000-0x00000000b0363000) (2MB)
[    0.000000] efi: mem23: type=4, attr=0xf, range=[0x00000000b0363000-0x00000000b0b22000) (7MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x00000000b0b22000-0x00000000b0d33000) (2MB)
[    0.000000] efi: mem25: type=1, attr=0xf, range=[0x00000000b0d33000-0x00000000b0d51000) (0MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x00000000b0d51000-0x00000000b2aca000) (29MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x00000000b2aca000-0x00000000b3078000) (5MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x00000000b3078000-0x00000000b325a000) (1MB)
[    0.000000] efi: mem29: type=4, attr=0xf, range=[0x00000000b325a000-0x00000000b325b000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x00000000b325b000-0x00000000b326b000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x00000000b326b000-0x00000000b45f9000) (19MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x00000000b45f9000-0x00000000b460b000) (0MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x00000000b460b000-0x00000000b460d000) (0MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x00000000b460d000-0x00000000b460e000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x00000000b460e000-0x00000000b5f4f000) (25MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x00000000b5f4f000-0x00000000b60c3000) (1MB)
[    0.000000] efi: mem37: type=2, attr=0xf, range=[0x00000000b60c3000-0x00000000b60cd000) (0MB)
[    0.000000] efi: mem38: type=3, attr=0xf, range=[0x00000000b60cd000-0x00000000b694f000) (8MB)
[    0.000000] efi: mem39: type=5, attr=0x800000000000000f, range=[0x00000000b694f000-0x00000000b69f1000) (0MB)
[    0.000000] efi: mem40: type=5, attr=0x800000000000000f, range=[0x00000000b69f1000-0x00000000b6b4f000) (1MB)
[    0.000000] efi: mem41: type=6, attr=0x800000000000000f, range=[0x00000000b6b4f000-0x00000000b76f8000) (11MB)
[    0.000000] efi: mem42: type=6, attr=0x800000000000000f, range=[0x00000000b76f8000-0x00000000ba59f000) (46MB)
[    0.000000] efi: mem43: type=0, attr=0xf, range=[0x00000000ba59f000-0x00000000babe9000) (6MB)
[    0.000000] efi: mem44: type=0, attr=0xf, range=[0x00000000babe9000-0x00000000bae9b000) (2MB)
[    0.000000] efi: mem45: type=0, attr=0xf, range=[0x00000000bae9b000-0x00000000bae9d000) (0MB)
[    0.000000] efi: mem46: type=0, attr=0xf, range=[0x00000000bae9d000-0x00000000bae9f000) (0MB)
[    0.000000] efi: mem47: type=10, attr=0xf, range=[0x00000000bae9f000-0x00000000baef5000) (0MB)
[    0.000000] efi: mem48: type=10, attr=0xf, range=[0x00000000baef5000-0x00000000baf9f000) (0MB)
[    0.000000] efi: mem49: type=9, attr=0xf, range=[0x00000000baf9f000-0x00000000bafdb000) (0MB)
[    0.000000] efi: mem50: type=9, attr=0xf, range=[0x00000000bafdb000-0x00000000bafff000) (0MB)
[    0.000000] efi: mem51: type=4, attr=0xf, range=[0x00000000bafff000-0x00000000bb000000) (0MB)
[    0.000000] efi: mem52: type=7, attr=0xf, range=[0x0000000100000000-0x000000023e600000) (5094MB)
[    0.000000] efi: mem53: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem54: type=0, attr=0x0, range=[0x00000000bb000000-0x00000000bfa00000) (74MB)
[    0.000000] efi: mem55: type=11, attr=0x8000000000000001, range=[0x00000000f80f8000-0x00000000f80f9000) (0MB)
[    0.000000] efi: mem56: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: LENOVO 2359CTO/2359CTO, BIOS G4ET62WW (2.04 ) 09/13/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x23e600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BB000000 mask FFF000000 uncachable
[    0.000000]   5 base 100000000 mask F00000000 write-back
[    0.000000]   6 base 200000000 mask FC0000000 write-back
[    0.000000]   7 base 23F000000 mask FFF000000 uncachable
[    0.000000]   8 base 23E800000 mask FFF800000 uncachable
[    0.000000]   9 base 23E600000 mask FFFE00000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xbb000 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000050000] 50000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xbaffffff]
[    0.000000]  [mem 0x00000000-0xbaffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xbaffffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x23e5fffff]
[    0.000000]  [mem 0x100000000-0x23e5fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x23e5fffff @ [mem 0xb60c7000-0xb60ccfff]
[    0.000000] RAMDISK: [mem 0x362e2000-0x37168fff]
[    0.000000] ACPI: RSDP 00000000baffe014 00024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 00000000baffe170 000B4 (v01 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: FACP 00000000bafe8000 0010C (v05 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: DSDT 00000000bafea000 0FF0E (v01 LENOVO TP-G4    00002040 INTL 20061109)
[    0.000000] ACPI: FACS 00000000baf5a000 00040
[    0.000000] ACPI: TCPA 00000000baffd000 00032 (v02    PTL   LENOVO 06040000 LNVO 00000001)
[    0.000000] ACPI: SSDT 00000000baffc000 00408 (v01 LENOVO TP-SSDT2 00000200 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000baffb000 00033 (v01 LENOVO TP-SSDT1 00000100 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000baffa000 00797 (v01 LENOVO SataAhci 00001000 INTL 20061109)
[    0.000000] ACPI: HPET 00000000bafe6000 00038 (v01 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: APIC 00000000bafe5000 00098 (v01 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: MCFG 00000000bafe4000 0003C (v01 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: ECDT 00000000bafe3000 00052 (v01 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: FPDT 00000000bafe2000 00064 (v01 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: ASF! 00000000bafe9000 000A5 (v32 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000bafe1000 0003E (v01 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: UEFI 00000000bafe0000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: MSDM 00000000bafdf000 00055 (v03 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: SSDT 00000000bafde000 00C31 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000bafdd000 00A7E (v01  PmRef    CpuPm 00003000 INTL 20061109)
[    0.000000] ACPI: UEFI 00000000bafdc000 002A6 (v01 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: DBG2 00000000bafdb000 000E9 (v00 LENOVO TP-G4    00002040 PTL  00000002)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023e5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23e5fffff]
[    0.000000]   NODE_DATA [mem 0x23e5fc000-0x23e5fffff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880235c00000-ffff88023dbfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23e5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0008ffff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xb0160fff]
[    0.000000]   node   0: [mem 0xb0363000-0xb694efff]
[    0.000000]   node   0: [mem 0xbafff000-0xbaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x23e5fffff]
[    0.000000] On node 0 totalpages: 2050765
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 77 pages reserved
[    0.000000]   DMA zone: 3827 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 726413 pages, LIFO batch:31
[    0.000000]   Normal zone: 20376 pages used for memmap
[    0.000000]   Normal zone: 1283688 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000090000 - 00000000000c0000
[    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000b0161000 - 00000000b0363000
[    0.000000] PM: Registered nosave memory: 00000000b694f000 - 00000000bae9f000
[    0.000000] PM: Registered nosave memory: 00000000bae9f000 - 00000000baf9f000
[    0.000000] PM: Registered nosave memory: 00000000baf9f000 - 00000000bafff000
[    0.000000] PM: Registered nosave memory: 00000000bb000000 - 00000000bfa00000
[    0.000000] PM: Registered nosave memory: 00000000bfa00000 - 00000000f80f8000
[    0.000000] PM: Registered nosave memory: 00000000f80f8000 - 00000000f80f9000
[    0.000000] PM: Registered nosave memory: 00000000f80f9000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 0000000100000000
[    0.000000] e820: [mem 0xbfa00000-0xf80f7fff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023e200000 s83584 r8192 d22912 u262144
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2013928
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-22-generic root=UUID=73d4fc0c-63e6-48f7-99b7-e58c2d3e2a46 ro quiet splash elevator=noop vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7905432k/9410560k available (6719k kernel code, 1207500k absent, 297628k reserved, 6451k data, 932k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2394.380 MHz processor.
[    0.000004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.76 BogoMIPS (lpj=9577520)
[    0.000009] pid_max: default: 32768 minimum: 301
[    0.052093] Security Framework initialized
[    0.052116] AppArmor: AppArmor initialized
[    0.052117] Yama: becoming mindful.
[    0.053063] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.057047] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.058843] Mount-cache hash table entries: 256
[    0.059121] Initializing cgroup subsys cpuacct
[    0.059124] Initializing cgroup subsys memory
[    0.059137] Initializing cgroup subsys devices
[    0.059139] Initializing cgroup subsys freezer
[    0.059141] Initializing cgroup subsys blkio
[    0.059143] Initializing cgroup subsys perf_event
[    0.059186] CPU: Physical Processor ID: 0
[    0.059188] CPU: Processor Core ID: 0
[    0.059195] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.059195] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.059937] mce: CPU supports 9 MCE banks
[    0.059960] CPU0: Thermal monitoring enabled (TM1)
[    0.059975] using mwait in idle threads.
[    0.063823] ACPI: Core revision 20120320
[    0.079904] ftrace: allocating 25143 entries in 99 pages
[    0.102714] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.142348] CPU0: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz stepping 09
[    0.246487] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.246496] ... version:                3
[    0.246498] ... bit width:              48
[    0.246499] ... generic registers:      4
[    0.246501] ... value mask:             0000ffffffffffff
[    0.246503] ... max period:             000000007fffffff
[    0.246504] ... fixed-purpose events:   3
[    0.246506] ... event mask:             000000070000000f
[    0.246747] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.246885] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 Ok.
[    0.345316] Brought up 8 CPUs
[    0.345321] Total of 8 processors activated (38310.08 BogoMIPS).
[    0.358659] devtmpfs: initialized
[    0.360585] EVM: security.selinux
[    0.360588] EVM: security.SMACK64
[    0.360589] EVM: security.capability
[    0.360663] PM: Registering ACPI NVS region [mem 0xbae9f000-0xbaf9efff] (1048576 bytes)
[    0.361865] dummy: 
[    0.361910] RTC time: 18:44:00, date: 01/28/13
[    0.361968] NET: Registered protocol family 16
[    0.362112] Trying to unpack rootfs image as initramfs...
[    0.362232] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.362236] ACPI: bus type pci registered
[    0.362505] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.362509] PCI: not using MMCONFIG
[    0.362511] PCI: Using configuration type 1 for base access
[    0.364078] bio: create slab <bio-0> at 0
[    0.364199] ACPI: Added _OSI(Module Device)
[    0.364202] ACPI: Added _OSI(Processor Device)
[    0.364204] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.364206] ACPI: Added _OSI(Processor Aggregator Device)
[    0.367110] ACPI: EC: EC description table is found, configuring boot EC
[    0.375521] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.493980] ACPI: SSDT 00000000bae3a018 00A01 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.494736] ACPI: Dynamic OEM Table Load:
[    0.494740] ACPI: SSDT           (null) 00A01 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)
[    0.528998] ACPI: SSDT 00000000bae3ba98 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.529793] ACPI: Dynamic OEM Table Load:
[    0.529797] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20061109)
[    0.560730] ACPI: SSDT 00000000bae39d98 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.561465] ACPI: Dynamic OEM Table Load:
[    0.561469] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20061109)
[    0.586553] ACPI: Interpreter enabled
[    0.586559] ACPI: (supports S0 S3 S4 S5)
[    0.586595] ACPI: Using IOAPIC for interrupt routing
[    0.586627] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.620954] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
[    0.637193] ACPI: Power Resource [PUBS] (on)
[    0.641503] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.642755] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.642762] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.642889] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.642931] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.642934] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.642937] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.642942] pci_root PNP0A08:00: host bridge window [mem 0xbfa00000-0xfebfffff]
[    0.642944] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed4bfff]
[    0.642987] PCI host bridge to bus 0000:00
[    0.642991] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.642994] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.642997] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.643000] pci_bus 0000:00: root bus resource [mem 0xbfa00000-0xfebfffff]
[    0.643003] pci_bus 0000:00: root bus resource [mem 0xfed40000-0xfed4bfff]
[    0.643017] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.643082] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.643139] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.643178] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.643197] pci 0000:00:02.0: reg 10: [mem 0xf1400000-0xf17fffff 64bit]
[    0.643208] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.643216] pci 0000:00:02.0: reg 20: [io  0x6000-0x603f]
[    0.643320] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.643361] pci 0000:00:14.0: reg 10: [mem 0xf3a20000-0xf3a2ffff 64bit]
[    0.643504] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.643546] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.643588] pci 0000:00:16.0: reg 10: [mem 0xf3a35000-0xf3a3500f 64bit]
[    0.643730] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.643793] pci 0000:00:19.0: [8086:1502] type 00 class 0x020000
[    0.643828] pci 0000:00:19.0: reg 10: [mem 0xf3a00000-0xf3a1ffff]
[    0.643846] pci 0000:00:19.0: reg 14: [mem 0xf3a3b000-0xf3a3bfff]
[    0.643864] pci 0000:00:19.0: reg 18: [io  0x6080-0x609f]
[    0.643983] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.644031] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.644068] pci 0000:00:1a.0: reg 10: [mem 0xf3a3a000-0xf3a3a3ff]
[    0.644225] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.644273] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.644303] pci 0000:00:1b.0: reg 10: [mem 0xf3a30000-0xf3a33fff 64bit]
[    0.644453] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.644498] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.644659] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.644708] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.644864] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.644911] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    0.645070] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.645136] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.645173] pci 0000:00:1d.0: reg 10: [mem 0xf3a39000-0xf3a393ff]
[    0.645335] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.645376] pci 0000:00:1f.0: [8086:1e55] type 00 class 0x060100
[    0.645579] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.645621] pci 0000:00:1f.2: reg 10: [io  0x60a8-0x60af]
[    0.645639] pci 0000:00:1f.2: reg 14: [io  0x60b4-0x60b7]
[    0.645656] pci 0000:00:1f.2: reg 18: [io  0x60a0-0x60a7]
[    0.645670] pci 0000:00:1f.2: reg 1c: [io  0x60b0-0x60b3]
[    0.645687] pci 0000:00:1f.2: reg 20: [io  0x6060-0x607f]
[    0.645704] pci 0000:00:1f.2: reg 24: [mem 0xf3a38000-0xf3a387ff]
[    0.645806] pci 0000:00:1f.2: PME# supported from D3hot
[    0.645844] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.645879] pci 0000:00:1f.3: reg 10: [mem 0xf3a34000-0xf3a340ff 64bit]
[    0.645928] pci 0000:00:1f.3: reg 20: [io  0xefa0-0xefbf]
[    0.646035] pci 0000:01:00.0: [10de:0def] type 00 class 0x030000
[    0.646050] pci 0000:01:00.0: reg 10: [mem 0xf0000000-0xf0ffffff]
[    0.646066] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.646082] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.646093] pci 0000:01:00.0: reg 24: [io  0x5000-0x507f]
[    0.646105] pci 0000:01:00.0: reg 30: [mem 0xfff80000-0xffffffff pref]
[    0.656429] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.656434] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.656438] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    0.656444] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.656609] pci 0000:02:00.0: [1180:e823] type 00 class 0x088001
[    0.656630] pci 0000:02:00.0: MMC controller base frequency changed to 50Mhz.
[    0.656661] pci 0000:02:00.0: reg 10: [mem 0xf3101000-0xf31010ff]
[    0.656877] pci 0000:02:00.0: supports D1 D2
[    0.656880] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.656993] pci 0000:02:00.3: [1180:e832] type 00 class 0x0c0010
[    0.657023] pci 0000:02:00.3: reg 10: [mem 0xf3100000-0xf31007ff]
[    0.657236] pci 0000:02:00.3: supports D1 D2
[    0.657239] pci 0000:02:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.664477] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.664484] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.664491] pci 0000:00:1c.0:   bridge window [mem 0xf3100000-0xf39fffff]
[    0.664502] pci 0000:00:1c.0:   bridge window [mem 0xf1800000-0xf1ffffff 64bit pref]
[    0.664878] pci 0000:03:00.0: [8086:0085] type 00 class 0x028000
[    0.665219] pci 0000:03:00.0: reg 10: [mem 0xf3000000-0xf3001fff 64bit]
[    0.666793] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.676523] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.676537] pci 0000:00:1c.1:   bridge window [mem 0xf3000000-0xf30fffff]
[    0.676634] pci 0000:00:1c.2: PCI bridge to [bus 04-0b]
[    0.676642] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.676648] pci 0000:00:1c.2:   bridge window [mem 0xf2800000-0xf2ffffff]
[    0.676660] pci 0000:00:1c.2:   bridge window [mem 0xf2000000-0xf27fffff 64bit pref]
[    0.676696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.676823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG_._PRT]
[    0.676865] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.676908] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.676944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.677108]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.677267]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.677268] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.680706] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.680790] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.680869] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.680948] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.681022] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.681098] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.681173] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.681249] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.681428] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.681441] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.681445] vgaarb: loaded
[    0.681446] vgaarb: bridge control possible 0000:01:00.0
[    0.681448] vgaarb: no bridge control possible 0000:00:02.0
[    0.681695] SCSI subsystem initialized
[    0.681755] libata version 3.00 loaded.
[    0.681793] ACPI: bus type usb registered
[    0.681821] usbcore: registered new interface driver usbfs
[    0.681832] usbcore: registered new interface driver hub
[    0.681863] usbcore: registered new device driver usb
[    0.681961] PCI: Using ACPI for IRQ routing
[    0.685730] PCI: pci_cache_line_size set to 64 bytes
[    0.685977] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.685979] e820: reserve RAM buffer [mem 0xb0161000-0xb3ffffff]
[    0.685982] e820: reserve RAM buffer [mem 0xb694f000-0xb7ffffff]
[    0.685984] e820: reserve RAM buffer [mem 0xbb000000-0xbbffffff]
[    0.685986] e820: reserve RAM buffer [mem 0x23e600000-0x23fffffff]
[    0.686111] NetLabel: Initializing
[    0.686113] NetLabel:  domain hash size = 128
[    0.686115] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.686128] NetLabel:  unlabeled traffic allowed by default
[    0.686213] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.686223] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.688249] Switching to clocksource hpet
[    0.696973] AppArmor: AppArmor Filesystem Enabled
[    0.697000] pnp: PnP ACPI init
[    0.697019] ACPI: bus type pnp registered
[    0.697601] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.697605] pnp 00:00: [mem 0x000c0000-0x000c3fff]
[    0.697607] pnp 00:00: [mem 0x000c4000-0x000c7fff]
[    0.697610] pnp 00:00: [mem 0x000c8000-0x000cbfff]
[    0.697613] pnp 00:00: [mem 0x000cc000-0x000cffff]
[    0.697615] pnp 00:00: [mem 0x000d0000-0x000d3fff]
[    0.697618] pnp 00:00: [mem 0x000d4000-0x000d7fff]
[    0.697620] pnp 00:00: [mem 0x000d8000-0x000dbfff]
[    0.697626] pnp 00:00: [mem 0x000dc000-0x000dffff]
[    0.697628] pnp 00:00: [mem 0x000e0000-0x000e3fff]
[    0.697631] pnp 00:00: [mem 0x000e4000-0x000e7fff]
[    0.697633] pnp 00:00: [mem 0x000e8000-0x000ebfff]
[    0.697635] pnp 00:00: [mem 0x000ec000-0x000effff]
[    0.697638] pnp 00:00: [mem 0x000f0000-0x000fffff]
[    0.697641] pnp 00:00: [mem 0x00100000-0xbf9fffff]
[    0.697643] pnp 00:00: [mem 0xfec00000-0xfed3ffff]
[    0.697646] pnp 00:00: [mem 0xfed4c000-0xffffffff]
[    0.697727] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.697731] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
[    0.697735] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
[    0.697738] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
[    0.697741] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
[    0.697744] system 00:00: [mem 0x000d0000-0x000d3fff] has been reserved
[    0.697747] system 00:00: [mem 0x000d4000-0x000d7fff] has been reserved
[    0.697750] system 00:00: [mem 0x000d8000-0x000dbfff] has been reserved
[    0.697753] system 00:00: [mem 0x000dc000-0x000dffff] has been reserved
[    0.697756] system 00:00: [mem 0x000e0000-0x000e3fff] has been reserved
[    0.697759] system 00:00: [mem 0x000e4000-0x000e7fff] has been reserved
[    0.697762] system 00:00: [mem 0x000e8000-0x000ebfff] has been reserved
[    0.697765] system 00:00: [mem 0x000ec000-0x000effff] has been reserved
[    0.697768] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.697772] system 00:00: [mem 0x00100000-0xbf9fffff] could not be reserved
[    0.697775] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.697779] system 00:00: [mem 0xfed4c000-0xffffffff] has been reserved
[    0.697784] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.697816] pnp 00:01: [bus 00-3f]
[    0.697819] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.697822] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.697825] pnp 00:01: [io  0x0d00-0xffff window]
[    0.697828] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.697830] pnp 00:01: [mem 0x000c0000-0x000c3fff window]
[    0.697833] pnp 00:01: [mem 0x000c4000-0x000c7fff window]
[    0.697836] pnp 00:01: [mem 0x000c8000-0x000cbfff window]
[    0.697838] pnp 00:01: [mem 0x000cc000-0x000cffff window]
[    0.697841] pnp 00:01: [mem 0x000d0000-0x000d3fff window]
[    0.697843] pnp 00:01: [mem 0x000d4000-0x000d7fff window]
[    0.697846] pnp 00:01: [mem 0x000d8000-0x000dbfff window]
[    0.697849] pnp 00:01: [mem 0x000dc000-0x000dffff window]
[    0.697851] pnp 00:01: [mem 0x000e0000-0x000e3fff window]
[    0.697854] pnp 00:01: [mem 0x000e4000-0x000e7fff window]
[    0.697856] pnp 00:01: [mem 0x000e8000-0x000ebfff window]
[    0.697859] pnp 00:01: [mem 0x000ec000-0x000effff window]
[    0.697862] pnp 00:01: [mem 0xbfa00000-0xfebfffff window]
[    0.697864] pnp 00:01: [mem 0xfed40000-0xfed4bfff window]
[    0.697943] pnp 00:01: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.698035] pnp 00:02: [io  0x0010-0x001f]
[    0.698038] pnp 00:02: [io  0x0090-0x009f]
[    0.698041] pnp 00:02: [io  0x0024-0x0025]
[    0.698043] pnp 00:02: [io  0x0028-0x0029]
[    0.698045] pnp 00:02: [io  0x002c-0x002d]
[    0.698048] pnp 00:02: [io  0x0030-0x0031]
[    0.698050] pnp 00:02: [io  0x0034-0x0035]
[    0.698053] pnp 00:02: [io  0x0038-0x0039]
[    0.698055] pnp 00:02: [io  0x003c-0x003d]
[    0.698057] pnp 00:02: [io  0x00a4-0x00a5]
[    0.698060] pnp 00:02: [io  0x00a8-0x00a9]
[    0.698062] pnp 00:02: [io  0x00ac-0x00ad]
[    0.698065] pnp 00:02: [io  0x00b0-0x00b5]
[    0.698067] pnp 00:02: [io  0x00b8-0x00b9]
[    0.698072] pnp 00:02: [io  0x00bc-0x00bd]
[    0.698074] pnp 00:02: [io  0x0050-0x0053]
[    0.698077] pnp 00:02: [io  0x0072-0x0077]
[    0.698079] pnp 00:02: [io  0x0400-0x047f]
[    0.698082] pnp 00:02: [io  0x0500-0x057f]
[    0.698084] pnp 00:02: [io  0x0800-0x080f]
[    0.698087] pnp 00:02: [io  0x15e0-0x15ef]
[    0.698089] pnp 00:02: [io  0x1600-0x167f]
[    0.698092] pnp 00:02: [mem 0xf8000000-0xfbffffff]
[    0.698094] pnp 00:02: [mem 0xfffff000-0xffffffff]
[    0.698097] pnp 00:02: [mem 0xfed1c000-0xfed1ffff]
[    0.698099] pnp 00:02: [mem 0xfed10000-0xfed13fff]
[    0.698102] pnp 00:02: [mem 0xfed18000-0xfed18fff]
[    0.698104] pnp 00:02: [mem 0xfed19000-0xfed19fff]
[    0.698107] pnp 00:02: [mem 0xfed45000-0xfed4bfff]
[    0.698153] pnp 00:02: disabling [mem 0xfffff000-0xffffffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0xfff80000-0xffffffff pref]
[    0.698197] system 00:02: [io  0x0400-0x047f] has been reserved
[    0.698201] system 00:02: [io  0x0500-0x057f] has been reserved
[    0.698204] system 00:02: [io  0x0800-0x080f] has been reserved
[    0.698207] system 00:02: [io  0x15e0-0x15ef] has been reserved
[    0.698210] system 00:02: [io  0x1600-0x167f] has been reserved
[    0.698215] system 00:02: [mem 0xf8000000-0xfbffffff] could not be reserved
[    0.698218] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.698221] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.698225] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.698228] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.698231] system 00:02: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.698235] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.698306] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.698344] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.698358] pnp 00:04: [io  0x0000-0x000f]
[    0.698360] pnp 00:04: [io  0x0080-0x008f]
[    0.698363] pnp 00:04: [io  0x00c0-0x00df]
[    0.698366] pnp 00:04: [dma 4]
[    0.698399] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.698410] pnp 00:05: [io  0x0061]
[    0.698445] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.698456] pnp 00:06: [io  0x00f0]
[    0.698472] pnp 00:06: [irq 13]
[    0.698506] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.698518] pnp 00:07: [io  0x0070-0x0071]
[    0.698528] pnp 00:07: [irq 8]
[    0.698566] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.698577] pnp 00:08: [io  0x0060]
[    0.698580] pnp 00:08: [io  0x0064]
[    0.698589] pnp 00:08: [irq 1]
[    0.698625] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.698642] pnp 00:09: [irq 12]
[    0.698678] pnp 00:09: Plug and Play ACPI device, IDs LEN0015 PNP0f13 (active)
[    0.698726] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.698766] pnp 00:0a: Plug and Play ACPI device, IDs SMO1200 PNP0c31 (active)
[    0.699299] pnp: PnP ACPI: found 11 devices
[    0.699302] ACPI: ACPI bus type pnp unregistered
[    0.706601] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.706678] pci 0000:01:00.0: BAR 6: assigned [mem 0xf1000000-0xf107ffff pref]
[    0.706682] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.706686] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.706691] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf10fffff]
[    0.706695] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.706702] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.706710] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.706719] pci 0000:00:1c.0:   bridge window [mem 0xf3100000-0xf39fffff]
[    0.706726] pci 0000:00:1c.0:   bridge window [mem 0xf1800000-0xf1ffffff 64bit pref]
[    0.706738] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.706747] pci 0000:00:1c.1:   bridge window [mem 0xf3000000-0xf30fffff]
[    0.706763] pci 0000:00:1c.2: PCI bridge to [bus 04-0b]
[    0.706768] pci 0000:00:1c.2:   bridge window [io  0x3000-0x3fff]
[    0.706777] pci 0000:00:1c.2:   bridge window [mem 0xf2800000-0xf2ffffff]
[    0.706784] pci 0000:00:1c.2:   bridge window [mem 0xf2000000-0xf27fffff 64bit pref]
[    0.706847] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.706851] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.706854] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.706857] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfebfffff]
[    0.706860] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed4bfff]
[    0.706863] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.706866] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf10fffff]
[    0.706868] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.706872] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.706874] pci_bus 0000:02: resource 1 [mem 0xf3100000-0xf39fffff]
[    0.706877] pci_bus 0000:02: resource 2 [mem 0xf1800000-0xf1ffffff 64bit pref]
[    0.706880] pci_bus 0000:03: resource 1 [mem 0xf3000000-0xf30fffff]
[    0.706884] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.706886] pci_bus 0000:04: resource 1 [mem 0xf2800000-0xf2ffffff]
[    0.706889] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf27fffff 64bit pref]
[    0.706935] NET: Registered protocol family 2
[    0.707218] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.708411] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.710364] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.710565] TCP: Hash tables configured (established 524288 bind 65536)
[    0.710567] TCP: reno registered
[    0.710588] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.710635] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.710763] NET: Registered protocol family 1
[    0.710784] pci 0000:00:02.0: Boot video device
[    0.710802] pci 0000:00:14.0: power state changed by ACPI to D0
[    0.710810] pci 0000:00:14.0: power state changed by ACPI to D0
[    0.710911] pci 0000:00:1a.0: power state changed by ACPI to D0
[    0.710919] pci 0000:00:1a.0: power state changed by ACPI to D0
[    0.710996] pci 0000:00:1d.0: power state changed by ACPI to D0
[    0.711005] pci 0000:00:1d.0: power state changed by ACPI to D0
[    0.711171] PCI: CLS 64 bytes, default 64
[    0.711174] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.711178] software IO TLB [mem 0xa9b32000-0xadb31fff] (64MB) mapped at [ffff8800a9b32000-ffff8800adb31fff]
[    0.712156] audit: initializing netlink socket (disabled)
[    0.712168] type=2000 audit(1359398640.540:1): initialized
[    0.754039] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.756591] VFS: Disk quotas dquot_6.5.2
[    0.756652] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.757371] fuse init (API version 7.19)
[    0.757485] msgmni has been set to 15574
[    0.757993] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.758034] io scheduler noop registered (default)
[    0.758038] io scheduler deadline registered
[    0.758076] io scheduler cfq registered
[    0.758235] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.758567] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.758592] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.758686] efifb: invalid framebuffer address
[    0.758713] ------------[ cut here ]------------
[    0.758719] WARNING: at /build/buildd/linux-3.5.0/drivers/base/core.c:197 device_release+0x8a/0xa0()
[    0.758721] Hardware name: 2359CTO
[    0.758723] Device 'efifb.0' does not have a release() function, it is broken and must be fixed.
[    0.758724] Modules linked in:
[    0.758730] Pid: 1, comm: swapper/0 Not tainted 3.5.0-22-generic #34-Ubuntu
[    0.758732] Call Trace:
[    0.758740]  [<ffffffff81051c1f>] warn_slowpath_common+0x7f/0xc0
[    0.758746]  [<ffffffff81051d16>] warn_slowpath_fmt+0x46/0x50
[    0.758750]  [<ffffffff8141bd1a>] device_release+0x8a/0xa0
[    0.758756]  [<ffffffff8132b663>] kobject_cleanup+0x43/0x80
[    0.758761]  [<ffffffff81d22ab1>] ? asiliantfb_init+0x34/0x34
[    0.758766]  [<ffffffff8132b52b>] kobject_put+0x2b/0x60
[    0.758770]  [<ffffffff8141ba97>] put_device+0x17/0x20
[    0.758776]  [<ffffffff81421fb7>] platform_device_put+0x17/0x20
[    0.758781]  [<ffffffff81421fde>] platform_device_unregister+0x1e/0x30
[    0.758785]  [<ffffffff81d22ab1>] ? asiliantfb_init+0x34/0x34
[    0.758789]  [<ffffffff81d22d25>] efifb_init+0x274/0x280
[    0.758793]  [<ffffffff81d22a7d>] ? imsttfb_init+0x101/0x101
[    0.758798]  [<ffffffff81d22ab1>] ? asiliantfb_init+0x34/0x34
[    0.758804]  [<ffffffff8100212a>] do_one_initcall+0x12a/0x180
[    0.758809]  [<ffffffff81cf3d3a>] kernel_init+0x140/0x1c9
[    0.758812]  [<ffffffff81cf3588>] ? loglevel+0x31/0x31
[    0.758817]  [<ffffffff8168d024>] kernel_thread_helper+0x4/0x10
[    0.758822]  [<ffffffff81cf3bfa>] ? start_kernel+0x3d2/0x3d2
[    0.758826]  [<ffffffff8168d020>] ? gs_change+0x13/0x13
[    0.758834] ---[ end trace 6ad1b08deb671a92 ]---
[    0.758838] intel_idle: MWAIT substates: 0x21120
[    0.758840] intel_idle: v0.4 model 0x3A
[    0.758841] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.759194] ACPI: AC Adapter [AC] (off-line)
[    0.759280] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.759442] ACPI: Lid Switch [LID]
[    0.759494] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.759500] ACPI: Sleep Button [SLPB]
[    0.759558] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.759562] ACPI: Power Button [PWRF]
[    0.759666] ACPI: Requesting acpi_cpufreq
[    0.809561] Freeing initrd memory: 14876k freed
[    0.820855] thermal LNXTHERM:00: registered as thermal_zone0
[    0.820860] ACPI: Thermal Zone [THM0] (50 C)
[    0.820889] ACPI: Battery Slot [BAT0] (battery present)
[    0.820926] GHES: HEST is not enabled!
[    0.821021] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.822828] Linux agpgart interface v0.103
[    0.824696] brd: module loaded
[    0.825728] loop: module loaded
[    0.825869] ahci 0000:00:1f.2: version 3.0
[    0.825994] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    0.826039] ahci: SSS flag set, parallel bus scan disabled
[    0.826091] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x13 impl SATA mode
[    0.826096] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part ems sxs apst 
[    0.826104] ahci 0000:00:1f.2: setting latency timer to 64
[    0.829873] ACPI: Battery Slot [BAT0] (battery present)
[    0.840599] scsi0 : ahci
[    0.840702] scsi1 : ahci
[    0.840779] scsi2 : ahci
[    0.840859] scsi3 : ahci
[    0.840935] scsi4 : ahci
[    0.841013] scsi5 : ahci
[    0.841724] ata1: SATA max UDMA/133 abar m2048@0xf3a38000 port 0xf3a38100 irq 41
[    0.841728] ata2: SATA max UDMA/133 abar m2048@0xf3a38000 port 0xf3a38180 irq 41
[    0.841730] ata3: DUMMY
[    0.841732] ata4: DUMMY
[    0.841739] ata5: SATA max UDMA/133 abar m2048@0xf3a38000 port 0xf3a38300 irq 41
[    0.841741] ata6: DUMMY
[    0.842100] Fixed MDIO Bus: probed
[    0.842154] tun: Universal TUN/TAP device driver, 1.6
[    0.842156] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.842214] PPP generic driver version 2.4.2
[    0.842278] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.842308] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    0.842317] ehci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    0.842354] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.842360] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.842368] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.842411] ehci_hcd 0000:00:1a.0: debug port 2
[    0.846309] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.846331] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf3a3a000
[    0.856014] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.856042] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.856046] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.856049] usb usb1: Product: EHCI Host Controller
[    0.856052] usb usb1: Manufacturer: Linux 3.5.0-22-generic ehci_hcd
[    0.856054] usb usb1: SerialNumber: 0000:00:1a.0
[    0.856209] hub 1-0:1.0: USB hub found
[    0.856215] hub 1-0:1.0: 3 ports detected
[    0.856300] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.856309] ehci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    0.856340] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.856345] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.856354] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.856387] ehci_hcd 0000:00:1d.0: debug port 2
[    0.860264] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.860283] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf3a39000
[    0.871994] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.872013] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.872016] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.872019] usb usb2: Product: EHCI Host Controller
[    0.872022] usb usb2: Manufacturer: Linux 3.5.0-22-generic ehci_hcd
[    0.872024] usb usb2: SerialNumber: 0000:00:1d.0
[    0.872155] hub 2-0:1.0: USB hub found
[    0.872160] hub 2-0:1.0: 3 ports detected
[    0.872237] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.872257] uhci_hcd: USB Universal Host Controller Interface driver
[    0.872294] xhci_hcd 0000:00:14.0: power state changed by ACPI to D0
[    0.872302] xhci_hcd 0000:00:14.0: power state changed by ACPI to D0
[    0.872347] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    0.872352] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.872358] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.872466] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.872475] xhci_hcd 0000:00:14.0: irq 16, io mem 0xf3a20000
[    0.872557] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    0.872621] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.872624] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.872627] usb usb3: Product: xHCI Host Controller
[    0.872629] usb usb3: Manufacturer: Linux 3.5.0-22-generic xhci_hcd
[    0.872632] usb usb3: SerialNumber: 0000:00:14.0
[    0.872738] xHCI xhci_add_endpoint called for root hub
[    0.872740] xHCI xhci_check_bandwidth called for root hub
[    0.872769] hub 3-0:1.0: USB hub found
[    0.872780] hub 3-0:1.0: 4 ports detected
[    0.872854] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.872861] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.872894] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.872897] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.872900] usb usb4: Product: xHCI Host Controller
[    0.872902] usb usb4: Manufacturer: Linux 3.5.0-22-generic xhci_hcd
[    0.872905] usb usb4: SerialNumber: 0000:00:14.0
[    0.873006] xHCI xhci_add_endpoint called for root hub
[    0.873008] xHCI xhci_check_bandwidth called for root hub
[    0.873037] hub 4-0:1.0: USB hub found
[    0.873048] hub 4-0:1.0: 4 ports detected
[    0.873220] usbcore: registered new interface driver libusual
[    0.873272] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.874725] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.874733] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.874873] mousedev: PS/2 mouse device common for all mice
[    0.875092] rtc_cmos 00:07: RTC can wake from S4
[    0.875263] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.875299] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.875410] device-mapper: uevent: version 1.0.3
[    0.875512] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.875732] cpuidle: using governor ladder
[    0.876054] cpuidle: using governor menu
[    0.876057] EFI Variables Facility v0.08 2004-May-17
[    0.876499] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.894822] ashmem: initialized
[    0.894999] TCP: cubic registered
[    0.895137] NET: Registered protocol family 10
[    0.895405] NET: Registered protocol family 17
[    0.895417] Key type dns_resolver registered
[    0.895600] PM: Hibernation image not present or could not be loaded.
[    0.895615] registered taskstats version 1
[    0.899467] Key type trusted registered
[    0.902996] Key type encrypted registered
[    0.907244]   Magic number: 13:666:747
[    0.907382] rtc_cmos 00:07: setting system clock to 2013-01-28 18:44:01 UTC (1359398641)
[    0.915290] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.915294] EDD information not available.
[    1.167627] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.299887] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.299893] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.300280] hub 1-1:1.0: USB hub found
[    1.300346] hub 1-1:1.0: 6 ports detected
[    1.411266] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.543640] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.543646] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.544033] hub 2-1:1.0: USB hub found
[    1.544106] hub 2-1:1.0: 8 ports detected
[    1.615192] usb 1-1.3: new full-speed USB device number 3 using ehci_hcd
[    1.706814] Refined TSC clocksource calibration: 2394.555 MHz.
[    1.706823] Switching to clocksource tsc
[    1.708172] usb 1-1.3: New USB device found, idVendor=147e, idProduct=2020
[    1.708178] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.708182] usb 1-1.3: Product: Biometric Coprocessor
[    1.708185] usb 1-1.3: Manufacturer: Auth
[    1.778954] usb 1-1.6: new high-speed USB device number 4 using ehci_hcd
[    1.878900] usb 1-1.6: New USB device found, idVendor=04f2, idProduct=b2ea
[    1.878907] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.878911] usb 1-1.6: Product: Integrated Camera
[    1.878914] usb 1-1.6: Manufacturer: Chicony Electronics Co., Ltd.
[    6.192104] ata1: link is slow to respond, please be patient (ready=0)
[   10.833182] ata1: COMRESET failed (errno=-16)
[   16.185196] ata1: link is slow to respond, please be patient (ready=0)
[   20.826280] ata1: COMRESET failed (errno=-16)
[   26.178298] ata1: link is slow to respond, please be patient (ready=0)
[   55.814098] ata1: COMRESET failed (errno=-16)
[   55.814109] ata1: limiting SATA link speed to 1.5 Gbps
[   56.133636] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   56.134008] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[   56.134014] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[   56.134280] ata1.00: ATA-7: SSDSA2SH064G1GC INTEL, 045C8860, max UDMA/133
[   56.134285] ata1.00: 125045424 sectors, multi 16: LBA48 NCQ (depth 31)
[   56.134731] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[   56.134737] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[   56.135024] ata1.00: configured for UDMA/133
[   56.135217] scsi 0:0:0:0: Direct-Access     ATA      SSDSA2SH064G1GC  045C PQ: 0 ANSI: 5
[   56.135475] sd 0:0:0:0: [sda] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
[   56.135484] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   56.135738] sd 0:0:0:0: [sda] Write Protect is off
[   56.135745] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   56.135892] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   56.139427]  sda: sda1 sda2 sda3
[   56.140425] sd 0:0:0:0: [sda] Attached SCSI disk
[   56.453159] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   56.462785] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[   56.469031] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[   56.474798] ata2.00: ATAPI: PLDS DVD-RW DS8A8SH, KU51, max UDMA/100
[   56.481921] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[   56.488144] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[   56.493908] ata2.00: configured for UDMA/100
[   56.505875] scsi 1:0:0:0: CD-ROM            PLDS     DVD-RW DS8A8SH   KU51 PQ: 0 ANSI: 5
[   56.515509] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   56.515515] cdrom: Uniform CD-ROM driver Revision: 3.20
[   56.515754] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   56.515914] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   56.832591] ata5: SATA link down (SStatus 0 SControl 300)
[   56.835171] Freeing unused kernel memory: 932k freed
[   56.835374] Write protecting the kernel read-only data: 12288k
[   56.842025] Freeing unused kernel memory: 1464k freed
[   56.847319] Freeing unused kernel memory: 1120k freed
[   56.891692] udevd[148]: starting version 175
[   56.932913] sdhci: Secure Digital Host Controller Interface driver
[   56.932918] sdhci: Copyright(c) Pierre Ossman
[   56.933547] sdhci-pci 0000:02:00.0: SDHCI controller found [1180:e823] (rev 5)
[   56.933719] mmc0: no vmmc regulator found
[   56.933819] Registered led device: mmc0::
[   56.933985] e1000e: Intel(R) PRO/1000 Network Driver - 2.0.0-k
[   56.933990] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[   56.934058] e1000e 0000:00:19.0: setting latency timer to 64
[   56.934202] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[   56.934288] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   56.964422] mmc0: SDHCI controller on PCI [0000:02:00.0] using DMA
[   56.970125] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[   56.970130] EXT4-fs (sda2): write access will be enabled during recovery
[   57.028354] firewire_ohci 0000:02:00.3: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[   57.158903] EXT4-fs (sda2): orphan cleanup on readonly fs
[   57.158916] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1056674
[   57.158997] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1054923
[   57.159025] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 2752571
[   57.159089] EXT4-fs (sda2): 3 orphan inodes deleted
[   57.159092] EXT4-fs (sda2): recovery complete
[   57.162593] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   57.190409] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 3c:97:0e:54:76:68
[   57.190415] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[   57.190463] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[   57.527631] firewire_core 0000:02:00.3: created device fw0: GUID 3c970eff547668ff, S400
[   57.664606] Adding 8203260k swap on /dev/sda3.  Priority:-1 extents:1 across:8203260k SS
[   57.709224] udevd[393]: starting version 175
[   57.709293] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.761116] lp: driver loaded but no devices found
[   58.050743] Non-volatile memory driver v1.3
[   58.065897] nvidia: module license 'NVIDIA' taints kernel.
[   58.065903] Disabling lock debugging due to kernel taint
[   58.079315] wmi: Mapper loaded
[   58.082280] tpm_tis 00:0a: 1.2 TPM (device-id 0x0, rev-id 78)
[   58.082868] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \_SB_.PCI0.LPC_.PMIO 1 (20120320/utaddress-251)
[   58.082881] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   58.082885] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   58.082891] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \_SB_.PCI0.LPC_.PMIO 1 (20120320/utaddress-251)
[   58.082899] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   58.082905] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPC_.LPIO 1 (20120320/utaddress-251)
[   58.082912] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   58.082915] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   58.084198] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   58.084212] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   58.084221] nvidia 0000:01:00.0: enabling device (0004 -> 0007)
[   58.084240] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   58.084465] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.64  Tue Oct 30 10:58:20 PDT 2012
[   58.094333] mei 0000:00:16.0: setting latency timer to 64
[   58.094444] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[   58.096006] cfg80211: Calling CRDA to update world regulatory domain
[   58.128215] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   58.128221] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   58.128224] thinkpad_acpi: ThinkPad BIOS G4ET62WW (2.04 ), EC unknown
[   58.128228] thinkpad_acpi: Lenovo ThinkPad T530, model 2359CTO
[   58.129392] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   58.130249] thinkpad_acpi: radio switch found; radios are enabled
[   58.130481] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   58.130485] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   58.134176] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[   58.134759] Registered led device: tpacpi::thinklight
[   58.134831] Registered led device: tpacpi::power
[   58.134876] Registered led device: tpacpi::standby
[   58.134912] Registered led device: tpacpi::thinkvantage
[   58.134928] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   58.135057] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   58.137318] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input4
[   58.140484] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x13
[   58.163245] [drm] Initialized drm 1.1.0 20060810
[   58.175634] tpm_tis 00:0a: TPM is disabled/deactivated (0x6)
[   58.177631] Linux video capture interface: v2.00
[   58.179166] uvcvideo: Found UVC 1.00 device Integrated Camera (04f2:b2ea)
[   58.179864] type=1400 audit(1359398698.856:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=638 comm="apparmor_parser"
[   58.180645] type=1400 audit(1359398698.856:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=638 comm="apparmor_parser"
[   58.181115] type=1400 audit(1359398698.856:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=638 comm="apparmor_parser"
[   58.184733] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input5
[   58.184884] usbcore: registered new interface driver uvcvideo
[   58.184888] USB Video Class driver (1.1.1)
[   58.193720] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   58.193726] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   58.193917] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   58.193923] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900057e4000
[   58.193927] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[   58.194348] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[   58.202338] kvm: disabled by bios
[   58.207419] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   58.219354] kvm: disabled by bios
[   58.254593] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x13
[   58.258076] input: HDA Intel PCH Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   58.258230] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   58.258368] input: HDA Intel PCH Dock Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   58.258598] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   58.258606] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x13
[   58.259035] i915 0000:00:02.0: power state changed by ACPI to D0
[   58.259053] i915 0000:00:02.0: power state changed by ACPI to D0
[   58.259414] i915 0000:00:02.0: setting latency timer to 64
[   58.260552] pci 0000:00:00.0: Intel Ivybridge Chipset
[   58.260737] pci 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[   58.263152] pci 0000:00:00.0: detected 65536K stolen memory
[   58.264294] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x13
[   58.269554] kvm: disabled by bios
[   58.273682] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x13
[   58.276240] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x13
[   58.279183] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x13
[   58.281702] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x13
[   58.284122] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   58.293201] cfg80211: World regulatory domain updated:
[   58.293206] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   58.293210] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   58.293214] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   58.293218] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   58.293222] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   58.293225] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   58.294259] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[   58.294717] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   58.294723] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   58.294727] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   58.294731] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   58.294735] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   58.294741] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   58.294919] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   58.301471] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[   58.310986] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   58.310990] iwlwifi 0000:03:00.0: Device SKU: 0x1F0
[   58.310993] iwlwifi 0000:03:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[   58.311024] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   58.311128] Registered led device: phy0-led
[   58.311179] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   58.323047] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   58.331763] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   58.331777] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   58.331779] [drm] Driver supports precise vblank timestamp query.
[   58.385842] kvm: disabled by bios
[   58.412627] kvm: disabled by bios
[   58.516066] kvm: disabled by bios
[   58.558127] usb 1-1.4: new full-speed USB device number 5 using ehci_hcd
[   58.653562] usb 1-1.4: New USB device found, idVendor=0a5c, idProduct=21e6
[   58.653570] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   58.653575] usb 1-1.4: Product: BCM20702A0
[   58.653579] usb 1-1.4: Manufacturer: Broadcom Corp
[   58.653584] usb 1-1.4: SerialNumber: 689423EED431
[   58.698927] Bluetooth: Core ver 2.16
[   58.698953] NET: Registered protocol family 31
[   58.698956] Bluetooth: HCI device and connection manager initialized
[   58.698958] Bluetooth: HCI socket layer initialized
[   58.698960] Bluetooth: L2CAP socket layer initialized
[   58.698965] Bluetooth: SCO socket layer initialized
[   58.724238] usbcore: registered new interface driver btusb
[   58.767706] Bluetooth: can't load firmware, may not work correctly
[   58.799443] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   58.825979] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   58.876280] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000
[   58.876290] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   58.913351] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   58.988335] init: failsafe main process (949) killed by TERM signal
[   58.997675] fbcon: inteldrmfb (fb0) is primary device
[   58.997884] Console: switching to colour frame buffer device 240x67
[   58.997940] fb0: inteldrmfb frame buffer device
[   58.997942] drm: registered panic notifier
[   59.019646] acpi device:01: registered as cooling_device8
[   59.019846] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   59.019981] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input11
[   59.022546] acpi device:0b: registered as cooling_device9
[   59.022665] ACPI: Video Device [VID1] (multi-head: yes  rom: yes  post: no)
[   59.022769] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0a/LNXVIDEO:01/input/input12
[   59.022904] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   59.128490] usb 1-1.4: USB disconnect, device number 5
[   59.361344] ppdev: user-space parallel port driver
[   59.386344] type=1400 audit(1359398700.064:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1060 comm="apparmor_parser"
[   59.387229] type=1400 audit(1359398700.064:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1060 comm="apparmor_parser"
[   59.387668] Bluetooth: RFCOMM TTY layer initialized
[   59.387676] Bluetooth: RFCOMM socket layer initialized
[   59.387680] Bluetooth: RFCOMM ver 1.11
[   59.403917] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   59.403922] Bluetooth: BNEP filters: protocol multicast
[   59.418992] type=1400 audit(1359398700.096:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1099 comm="apparmor_parser"
[   59.419844] type=1400 audit(1359398700.096:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1099 comm="apparmor_parser"
[   59.419878] type=1400 audit(1359398700.096:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1103 comm="apparmor_parser"
[   59.420306] type=1400 audit(1359398700.096:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1099 comm="apparmor_parser"
[   59.420685] type=1400 audit(1359398700.100:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1103 comm="apparmor_parser"
```thanks.

---

### Post by oldfred on 2013-01-28
Changed to code tags to make it easier to review.

But this is issue. It is 55 sec of your boot time.
> 
[    6.192104] ata1: link is slow to respond, please be patient (ready=0)
[   10.833182] ata1: COMRESET failed (errno=-16)
[   16.185196] ata1: link is slow to respond, please be patient (ready=0)
[   20.826280] ata1: COMRESET failed (errno=-16)
[   26.178298] ata1: link is slow to respond, please be patient (ready=0)
[   55.814098] ata1: COMRESET failed (errno=-16)

What mode do you have drives in? I am not sure which device this is but it is having real issues connecting.

---

### Post by curiousgally on 2013-01-28
oldfred,

I get the following info when I do fdisk -l:

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   125045423    62522711+  ee  GPT

```

---

### Post by oldfred on 2013-01-28
I use gpt with no issues, but you cannot use fdisk with gpt drives use gdisk or parted.
       three Linux partitioning tools: the fdisk family [fdisk, sfdisk, and cfdisk], the libparted family [GNU Parted, GParted, Palimpsest Disk Utility, and several others], and the GPT fdisk family [gdisk and sgdisk]. 

    
       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

    
What BIOS mode do you have drives in? 
You have to have AHCI for trim to work.
Are you booting with UEFI or BIOS?

       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by curiousgally on 2013-01-28
oldfred,

Im using my old Intel X25-E ssd which doesn't support TRIM :)
I have set it to AHCI mode only.
I'm tried both UEFI and normal boot mode didn't see any difference.


thanks.

---

### Post by bantuvez on 2013-01-28
[This link]("http://blog.cihar.com/archives/2012/07/13/intel-ssd-firmware-update-linux/") might help.

---

### Post by curiousgally on 2013-02-01
Thanks bantuvez for the link. However the following lines:

linux16 /memdisk
initrd16 /ssd-fw.img

throw errors as bad command on my machine. Some googlins shows these commands work only on x86 machines and mine being a 64 bit it wouldn't work. Any work around for this?

Thanks.

---

### Post by curiousgally on 2013-02-01
I changed the SATA drive to Compatability rather than AHCI and now my SSD boots up in 20seconds. Whats the reasoning here?

---

### Post by oldfred on 2013-02-02
Now that is strange. 
It is my understanding that you have to have AHCI for trim to work. So is there some issue with trim on your drive?

Some suggest using a cron tasks to trim instead of discard, you still should have noatime in fstab to reduce writes.

       fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by curiousgally on 2013-02-02
oldfred,

The ssd I have, Intel X25-E doesn't support TRIM.
I have 'noatime' in fstab to reduce writes.

Thanks.

---

### Post by bantuvez on 2013-02-02
Then  use it with Compatibilty mode. 

With the AHCI mode the SSD would be somewhat faster. Just check the speeds with AHCI on and with AHCI off. If you notice no/minimal difference, then use Compatibility mode. If there is significant difference in speed, then we should continue searching for a solution. Maybe this problem is related to your SATA controller driver. Maybe you could try a BIOS update for your motherboard if there is any newer BIOS for your MB.

Anyway, AHCI is NOT NEEDED for TRIM. TRIM works in IDE mode, whats more, it works even in fakeRAID.

---

### Post by curiousgally on 2013-03-20
bantuvez,

It's been a long time and now I had to boot into windows to get some things done. So i have to manually switch modes between AHCI/Compatability while switching OS. So might as well solve this issue once for all. Can you point me in some direction, cant get anywhere at the moment.

Thanks.

---

