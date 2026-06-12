---
title: "Errors at plymouth screen - usb error , init error and systemd error"
date: 2015-02-23
forum: Installation &amp; Upgrades
---

### Post by akashunbeatable on 2015-02-23
At the plymouth screen I'm being greeted by few errors. Check the dmesg output below (I've highlighted it red wherever possible)
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.16.0-30-generic (buildd@komainu) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #40-Ubuntu SMP Mon Jan 12 22:06:37 UTC 2015 (Ubuntu 3.16.0-30.40-generic 3.16.7-ckt3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-30-generic.efi.signed root=UUID=d320e7e0-3dd8-42f0-b529-38017a456a4b ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000087fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000957affff] usable
[    0.000000] BIOS-e820: [mem 0x00000000957b0000-0x00000000961affff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000961b0000-0x000000009a7befff] usable
[    0.000000] BIOS-e820: [mem 0x000000009a7bf000-0x000000009aebefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009aebf000-0x000000009afbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009afbf000-0x000000009affefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009afff000-0x000000009affffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b000000-0x000000009f9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000015f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0x948f5018-0x94902c57] usable ==> usable
[    0.000000] e820: update [mem 0x948e4018-0x948f4057] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x0000000000087fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] reserve setup_data: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000040005000-0x00000000948e4017] usable
[    0.000000] reserve setup_data: [mem 0x00000000948e4018-0x00000000948f4057] usable
[    0.000000] reserve setup_data: [mem 0x00000000948f4058-0x00000000948f5017] usable
[    0.000000] reserve setup_data: [mem 0x00000000948f5018-0x0000000094902c57] usable
[    0.000000] reserve setup_data: [mem 0x0000000094902c58-0x00000000957affff] usable
[    0.000000] reserve setup_data: [mem 0x00000000957b0000-0x00000000961affff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000961b0000-0x000000009a7befff] usable
[    0.000000] reserve setup_data: [mem 0x000000009a7bf000-0x000000009aebefff] reserved
[    0.000000] reserve setup_data: [mem 0x000000009aebf000-0x000000009afbefff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000009afbf000-0x000000009affefff] ACPI data
[    0.000000] reserve setup_data: [mem 0x000000009afff000-0x000000009affffff] usable
[    0.000000] reserve setup_data: [mem 0x000000009b000000-0x000000009f9fffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ffc80000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000015f5fffff] usable
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0x9affe000  ACPI 2.0=0x9affe014  SMBIOS=0x9aebef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=2, attr=0xf, range=[0x0000000000001000-0x0000000000002000) (0MB)
[    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000002000-0x000000000006f000) (0MB)
[    0.000000] efi: mem03: type=4, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
[    0.000000] efi: mem04: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000088000) (0MB)
[    0.000000] efi: mem05: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem06: type=7, attr=0xf, range=[0x0000000000100000-0x0000000001000000) (15MB)
[    0.000000] efi: mem07: type=2, attr=0xf, range=[0x0000000001000000-0x00000000023f7000) (19MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x00000000023f7000-0x0000000020000000) (476MB)
[    0.000000] efi: mem09: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020200000) (2MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000020200000-0x000000003ec84000) (490MB)
[    0.000000] efi: mem11: type=2, attr=0xf, range=[0x000000003ec84000-0x0000000040000000) (19MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x0000000040000000-0x0000000040004000) (0MB)
[    0.000000] efi: mem13: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000040005000-0x000000006d9ac000) (729MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x000000006d9ac000-0x00000000931c0000) (600MB)
[    0.000000] efi: mem16: type=4, attr=0xf, range=[0x00000000931c0000-0x00000000931e0000) (0MB)
[    0.000000] efi: mem17: type=7, attr=0xf, range=[0x00000000931e0000-0x00000000948e4000) (23MB)
[    0.000000] efi: mem18: type=2, attr=0xf, range=[0x00000000948e4000-0x00000000949e7000) (1MB)
[    0.000000] efi: mem19: type=7, attr=0xf, range=[0x00000000949e7000-0x00000000949e8000) (0MB)
[    0.000000] efi: mem20: type=2, attr=0xf, range=[0x00000000949e8000-0x00000000949eb000) (0MB)
[    0.000000] efi: mem21: type=7, attr=0xf, range=[0x00000000949eb000-0x00000000949ec000) (0MB)
[    0.000000] efi: mem22: type=2, attr=0xf, range=[0x00000000949ec000-0x0000000094ad4000) (0MB)
[    0.000000] efi: mem23: type=4, attr=0xf, range=[0x0000000094ad4000-0x00000000957b0000) (12MB)
[    0.000000] efi: mem24: type=0, attr=0xf, range=[0x00000000957b0000-0x00000000961b0000) (10MB)
[    0.000000] efi: mem25: type=2, attr=0xf, range=[0x00000000961b0000-0x00000000961b1000) (0MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x00000000961b1000-0x00000000961b2000) (0MB)
[    0.000000] efi: mem27: type=2, attr=0xf, range=[0x00000000961b2000-0x00000000961b4000) (0MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x00000000961b4000-0x00000000961b7000) (0MB)
[    0.000000] efi: mem29: type=2, attr=0xf, range=[0x00000000961b7000-0x00000000961bf000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x00000000961bf000-0x000000009629a000) (0MB)
[    0.000000] efi: mem31: type=1, attr=0xf, range=[0x000000009629a000-0x00000000963bf000) (1MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x00000000963bf000-0x0000000097b70000) (23MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x0000000097b70000-0x000000009852f000) (9MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x000000009852f000-0x0000000098535000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x0000000098535000-0x0000000098538000) (0MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x0000000098538000-0x000000009853a000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x000000009853a000-0x00000000985a8000) (0MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x00000000985a8000-0x00000000985b1000) (0MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x00000000985b1000-0x00000000985b8000) (0MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x00000000985b8000-0x00000000985b9000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x00000000985b9000-0x00000000985de000) (0MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x00000000985de000-0x00000000985df000) (0MB)
[    0.000000] efi: mem43: type=4, attr=0xf, range=[0x00000000985df000-0x000000009870a000) (1MB)
[    0.000000] efi: mem44: type=7, attr=0xf, range=[0x000000009870a000-0x000000009870c000) (0MB)
[    0.000000] efi: mem45: type=4, attr=0xf, range=[0x000000009870c000-0x000000009870f000) (0MB)
[    0.000000] efi: mem46: type=7, attr=0xf, range=[0x000000009870f000-0x0000000098712000) (0MB)
[    0.000000] efi: mem47: type=4, attr=0xf, range=[0x0000000098712000-0x0000000098759000) (0MB)
[    0.000000] efi: mem48: type=7, attr=0xf, range=[0x0000000098759000-0x00000000987c2000) (0MB)
[    0.000000] efi: mem49: type=4, attr=0xf, range=[0x00000000987c2000-0x0000000098866000) (0MB)
[    0.000000] efi: mem50: type=7, attr=0xf, range=[0x0000000098866000-0x000000009886c000) (0MB)
[    0.000000] efi: mem51: type=4, attr=0xf, range=[0x000000009886c000-0x000000009886d000) (0MB)
[    0.000000] efi: mem52: type=7, attr=0xf, range=[0x000000009886d000-0x0000000098886000) (0MB)
[    0.000000] efi: mem53: type=4, attr=0xf, range=[0x0000000098886000-0x0000000098901000) (0MB)
[    0.000000] efi: mem54: type=7, attr=0xf, range=[0x0000000098901000-0x0000000098902000) (0MB)
[    0.000000] efi: mem55: type=4, attr=0xf, range=[0x0000000098902000-0x0000000098b4b000) (2MB)
[    0.000000] efi: mem56: type=7, attr=0xf, range=[0x0000000098b4b000-0x0000000098b50000) (0MB)
[    0.000000] efi: mem57: type=4, attr=0xf, range=[0x0000000098b50000-0x0000000098b52000) (0MB)
[    0.000000] efi: mem58: type=7, attr=0xf, range=[0x0000000098b52000-0x0000000098b59000) (0MB)
[    0.000000] efi: mem59: type=4, attr=0xf, range=[0x0000000098b59000-0x0000000098b6b000) (0MB)
[    0.000000] efi: mem60: type=7, attr=0xf, range=[0x0000000098b6b000-0x0000000098b6c000) (0MB)
[    0.000000] efi: mem61: type=4, attr=0xf, range=[0x0000000098b6c000-0x000000009a3bf000) (24MB)
[    0.000000] efi: mem62: type=7, attr=0xf, range=[0x000000009a3bf000-0x000000009a4ef000) (1MB)
[    0.000000] efi: mem63: type=3, attr=0xf, range=[0x000000009a4ef000-0x000000009a7bf000) (2MB)
[    0.000000] efi: mem64: type=5, attr=0x800000000000000f, range=[0x000000009a7bf000-0x000000009a835000) (0MB)
[    0.000000] efi: mem65: type=5, attr=0x800000000000000f, range=[0x000000009a835000-0x000000009a837000) (0MB)
[    0.000000] efi: mem66: type=6, attr=0x800000000000000f, range=[0x000000009a837000-0x000000009a842000) (0MB)
[    0.000000] efi: mem67: type=5, attr=0x800000000000000f, range=[0x000000009a842000-0x000000009a851000) (0MB)
[    0.000000] efi: mem68: type=6, attr=0x800000000000000f, range=[0x000000009a851000-0x000000009a852000) (0MB)
[    0.000000] efi: mem69: type=5, attr=0x800000000000000f, range=[0x000000009a852000-0x000000009a871000) (0MB)
[    0.000000] efi: mem70: type=6, attr=0x800000000000000f, range=[0x000000009a871000-0x000000009a872000) (0MB)
[    0.000000] efi: mem71: type=5, attr=0x800000000000000f, range=[0x000000009a872000-0x000000009a882000) (0MB)
[    0.000000] efi: mem72: type=6, attr=0x800000000000000f, range=[0x000000009a882000-0x000000009a883000) (0MB)
[    0.000000] efi: mem73: type=5, attr=0x800000000000000f, range=[0x000000009a883000-0x000000009a8cb000) (0MB)
[    0.000000] efi: mem74: type=6, attr=0x800000000000000f, range=[0x000000009a8cb000-0x000000009a8cc000) (0MB)
[    0.000000] efi: mem75: type=5, attr=0x800000000000000f, range=[0x000000009a8cc000-0x000000009a8d1000) (0MB)
[    0.000000] efi: mem76: type=6, attr=0x800000000000000f, range=[0x000000009a8d1000-0x000000009a8d2000) (0MB)
[    0.000000] efi: mem77: type=5, attr=0x800000000000000f, range=[0x000000009a8d2000-0x000000009a8f2000) (0MB)
[    0.000000] efi: mem78: type=6, attr=0x800000000000000f, range=[0x000000009a8f2000-0x000000009a935000) (0MB)
[    0.000000] efi: mem79: type=5, attr=0x800000000000000f, range=[0x000000009a935000-0x000000009a9bf000) (0MB)
[    0.000000] efi: mem80: type=6, attr=0x800000000000000f, range=[0x000000009a9bf000-0x000000009aabf000) (1MB)
[    0.000000] efi: mem81: type=0, attr=0xf, range=[0x000000009aabf000-0x000000009adf3000) (3MB)
[    0.000000] efi: mem82: type=0, attr=0xf, range=[0x000000009adf3000-0x000000009aebf000) (0MB)
[    0.000000] efi: mem83: type=10, attr=0xf, range=[0x000000009aebf000-0x000000009af92000) (0MB)
[    0.000000] efi: mem84: type=10, attr=0xf, range=[0x000000009af92000-0x000000009afbf000) (0MB)
[    0.000000] efi: mem85: type=9, attr=0xf, range=[0x000000009afbf000-0x000000009afda000) (0MB)
[    0.000000] efi: mem86: type=9, attr=0xf, range=[0x000000009afda000-0x000000009afff000) (0MB)
[    0.000000] efi: mem87: type=4, attr=0xf, range=[0x000000009afff000-0x000000009b000000) (0MB)
[    0.000000] efi: mem88: type=7, attr=0xf, range=[0x0000000100000000-0x000000015f600000) (1526MB)
[    0.000000] efi: mem89: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem90: type=0, attr=0x0, range=[0x000000009b000000-0x000000009fa00000) (74MB)
[    0.000000] efi: mem91: type=11, attr=0x8000000000000001, range=[0x00000000f0000000-0x00000000f4000000) (64MB)
[    0.000000] efi: mem92: type=11, attr=0x8000000000000001, range=[0x00000000feb00000-0x00000000feb04000) (0MB)
[    0.000000] efi: mem93: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem94: type=11, attr=0x8000000000000001, range=[0x00000000fed10000-0x00000000fed1a000) (0MB)
[    0.000000] efi: mem95: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem96: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem97: type=11, attr=0x8000000000000000, range=[0x00000000ffc80000-0x00000000fff13000) (2MB)
[    0.000000] efi: mem98: type=11, attr=0x8000000000000000, range=[0x00000000fff13000-0x00000000fff40000) (0MB)
[    0.000000] efi: mem99: type=11, attr=0x8000000000000000, range=[0x00000000fff40000-0x0000000100000000) (0MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Acer Aspire V3-571G/VA50_HC_CR, BIOS V2.21 12/16/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x15f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09B000000 mask FFF000000 uncachable
[    0.000000]   3 base 09C000000 mask FFC000000 uncachable
[    0.000000]   4 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   5 base 100000000 mask F80000000 write-back
[    0.000000]   6 base 15F600000 mask FFFE00000 uncachable
[    0.000000]   7 base 15F800000 mask FFF800000 uncachable
[    0.000000]   8 base 160000000 mask FE0000000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x9b000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000082000] 82000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x15f400000-0x15f5fffff]
[    0.000000]  [mem 0x15f400000-0x15f5fffff] page 2M
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x15c000000-0x15f3fffff]
[    0.000000]  [mem 0x15c000000-0x15f3fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x100000000-0x15bffffff]
[    0.000000]  [mem 0x100000000-0x15bffffff] page 2M
[    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20200000-0x40003fff]
[    0.000000]  [mem 0x20200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x40003fff] page 4k
[    0.000000] BRK [0x01fd8000, 0x01fd8fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x40005000-0x957affff]
[    0.000000]  [mem 0x40005000-0x401fffff] page 4k
[    0.000000]  [mem 0x40200000-0x955fffff] page 2M
[    0.000000]  [mem 0x95600000-0x957affff] page 4k
[    0.000000] init_memory_mapping: [mem 0x961b0000-0x9a7befff]
[    0.000000]  [mem 0x961b0000-0x961fffff] page 4k
[    0.000000]  [mem 0x96200000-0x9a5fffff] page 2M
[    0.000000]  [mem 0x9a600000-0x9a7befff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9afff000-0x9affffff]
[    0.000000]  [mem 0x9afff000-0x9affffff] page 4k
[    0.000000] RAMDISK: [mem 0x3ec84000-0x3fffafff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000009AFFE014 000024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 0x000000009AFFE210 0000A4 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 0x000000009AFFB000 00010C (v05 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: DSDT 0x000000009AFEC000 00BC02 (v01 ACRSYS ACRPRDCT 00000000 1025 00040000)
[    0.000000] ACPI: FACS 0x000000009AFBA000 000040
[    0.000000] ACPI: UEFI 0x000000009AFFD000 000236 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: ASF! 0x000000009AFFC000 0000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: HPET 0x000000009AFFA000 000038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: APIC 0x000000009AFF9000 00008C (v03 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MCFG 0x000000009AFF8000 00003C (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000009AFEB000 0006FE (v01 ACRSYS ACRPRDCT 00001000 1025 00040000)
[    0.000000] ACPI: BOOT 0x000000009AFE9000 000028 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: ASPT 0x000000009AFE4000 000034 (v07 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: DBGP 0x000000009AFE3000 000034 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: FPDT 0x000000009AFE1000 000044 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MSDM 0x000000009AFE0000 000055 (v03 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000009AFDF000 0009AA (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000009AFDE000 000A92 (v01 ACRSYS ACRPRDCT 00003000 1025 00040000)
[    0.000000] ACPI: SSDT 0x000000009AFDA000 002185 (v01 ACRSYS ACRPRDCT 00001000 1025 00040000)
[    0.000000] ACPI: BGRT 0x000000009AFDD000 000038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000015f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x15f5fffff]
[    0.000000]   NODE_DATA [mem 0x15f5f5000-0x15f5f9fff]
[    0.000000]  [ffffea0000000000-ffffea00057fffff] PMD -> [ffff88015ac00000-ffff88015ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x15f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00087fff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0x957affff]
[    0.000000]   node   0: [mem 0x961b0000-0x9a7befff]
[    0.000000]   node   0: [mem 0x9afff000-0x9affffff]
[    0.000000]   node   0: [mem 0x100000000-0x15f5fffff]
[    0.000000] On node 0 totalpages: 1020230
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3975 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9775 pages used for memmap
[    0.000000]   DMA32 zone: 625599 pages, LIFO batch:31
[    0.000000]   Normal zone: 6104 pages used for memmap
[    0.000000]   Normal zone: 390656 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] Reserving Intel graphics stolen memory at 0x9ba00000-0x9f9fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x00088000-0x000bffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000c0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0x948e4000-0x948e4fff]
[    0.000000] PM: Registered nosave memory: [mem 0x948f4000-0x948f4fff]
[    0.000000] PM: Registered nosave memory: [mem 0x948f5000-0x948f5fff]
[    0.000000] PM: Registered nosave memory: [mem 0x94902000-0x94902fff]
[    0.000000] PM: Registered nosave memory: [mem 0x957b0000-0x961affff]
[    0.000000] PM: Registered nosave memory: [mem 0x9a7bf000-0x9aebefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9aebf000-0x9afbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9afbf000-0x9affefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b000000-0x9f9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fa00000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf3ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf4000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffc7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffc80000-0xffffffff]
[    0.000000] e820: [mem 0x9fa00000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88015f200000 s83328 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s83328 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1004265
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-30-generic.efi.signed root=UUID=d320e7e0-3dd8-42f0-b529-38017a456a4b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3855000K/4080920K available (7741K kernel code, 1201K rwdata, 3608K rodata, 1360K init, 1308K bss, 225920K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2594.160 MHz processor
[    0.000033] Calibrating delay loop (skipped), value calculated using timer frequency.. 5188.32 BogoMIPS (lpj=10376640)
[    0.000036] pid_max: default: 32768 minimum: 301
[    0.000044] ACPI: Core revision 20140424
[    0.007135] ACPI: All ACPI Tables successfully acquired
[    0.033019] Security Framework initialized
[    0.033054] AppArmor: AppArmor initialized
[    0.033055] Yama: becoming mindful.
[    0.033307] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.034264] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.034718] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.034723] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.034938] Initializing cgroup subsys memory
[    0.034960] Initializing cgroup subsys devices
[    0.034966] Initializing cgroup subsys freezer
[    0.034968] Initializing cgroup subsys net_cls
[    0.034972] Initializing cgroup subsys blkio
[    0.034975] Initializing cgroup subsys perf_event
[    0.034977] Initializing cgroup subsys net_prio
[    0.034983] Initializing cgroup subsys hugetlb
[    0.035005] CPU: Physical Processor ID: 0
[    0.035006] CPU: Processor Core ID: 0
[    0.035011] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.035355] mce: CPU supports 7 MCE banks
[    0.035365] CPU0: Thermal monitoring enabled (TM1)
[    0.035374] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
tlb_flushall_shift: 2
[    0.035491] Freeing SMP alternatives memory: 32K (ffffffff81e82000 - ffffffff81e8a000)
[    0.038169] ftrace: allocating 29303 entries in 115 pages
[    0.051551] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.091262] smpboot: CPU0: Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz (fam: 06, model: 3a, stepping: 09)
[    0.091270] TSC deadline timer enabled
[    0.091292] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.091311] ... version:                3
[    0.091312] ... bit width:              48
[    0.091312] ... generic registers:      4
[    0.091313] ... value mask:             0000ffffffffffff
[    0.091314] ... max period:             0000ffffffffffff
[    0.091315] ... fixed-purpose events:   3
[    0.091316] ... event mask:             000000070000000f
[    0.093019] x86: Booting SMP configuration:
[    0.093021] .... node  #0, CPUs:      #1
[    0.106432] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.106513]  #2 #3
[    0.133298] x86: Booted up 1 node, 4 CPUs
[    0.133301] smpboot: Total of 4 processors activated (20753.28 BogoMIPS)
[    0.136366] devtmpfs: initialized
[    0.138439] evm: security.selinux
[    0.138440] evm: security.SMACK64
[    0.138441] evm: security.SMACK64EXEC
[    0.138442] evm: security.SMACK64TRANSMUTE
[    0.138442] evm: security.SMACK64MMAP
[    0.138443] evm: security.ima
[    0.138444] evm: security.capability
[    0.138491] PM: Registering ACPI NVS region [mem 0x9aebf000-0x9afbefff] (1048576 bytes)
[    0.139247] pinctrl core: initialized pinctrl subsystem
[    0.139308] regulator-dummy: no parameters
[    0.139341] RTC time: 10:32:08, date: 02/23/15
[    0.139387] NET: Registered protocol family 16
[    0.139513] cpuidle: using governor ladder
[    0.139515] cpuidle: using governor menu
[    0.139577] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.139578] ACPI: bus type PCI registered
[    0.139579] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.139646] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.139648] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.139723] PCI: Using configuration type 1 for base access
[    0.141693] ACPI: Added _OSI(Module Device)
[    0.141695] ACPI: Added _OSI(Processor Device)
[    0.141696] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.141697] ACPI: Added _OSI(Processor Aggregator Device)
[    0.144122] ACPI: Executed 1 blocks of module-level executable AML code
[    0.153439] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.153757] ACPI: Dynamic OEM Table Load:
[    0.153766] ACPI: SSDT 0xFFFF880158D91000 00083B (v01 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.157534] ACPI: Dynamic OEM Table Load:
[    0.157541] ACPI: SSDT 0xFFFF880158CF9000 000303 (v01 PmRef  ApIst    00003000 INTL 20120913)
[    0.161436] ACPI: Dynamic OEM Table Load:
[    0.161441] ACPI: SSDT 0xFFFF880158FC4000 000119 (v01 PmRef  ApCst    00003000 INTL 20120913)
[    0.165890] ACPI: Interpreter enabled
[    0.165896] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
[    0.165900] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
[    0.165912] ACPI: (supports S0 S3 S4 S5)
[    0.165913] ACPI: Using IOAPIC for interrupt routing
[    0.165934] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.315707] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.315711] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.315793] \_SB_.PCI0:_OSC invalid UUID
[    0.315794] _OSC request data:1 1f 0 
[    0.315798] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.316165] PCI host bridge to bus 0000:00
[    0.316168] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.316170] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.316171] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.316173] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.316175] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.316176] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.316177] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.316179] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.316180] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.316182] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.316183] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.316185] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.316186] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.316188] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.316189] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.316190] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.316192] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.316193] pci_bus 0000:00: root bus resource [mem 0x9fa00000-0xfeafffff]
[    0.316200] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.316284] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.316314] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.316350] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.316388] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.316403] pci 0000:00:02.0: reg 0x10: [mem 0xb3000000-0xb33fffff 64bit]
[    0.316409] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.316414] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f]
[    0.316511] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.316534] pci 0000:00:14.0: reg 0x10: [mem 0xb3600000-0xb360ffff 64bit]
[    0.316604] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.316642] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.316679] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.316699] pci 0000:00:16.0: reg 0x10: [mem 0xb3614000-0xb361400f 64bit]
[    0.316762] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.316842] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.316864] pci 0000:00:1a.0: reg 0x10: [mem 0xb3619000-0xb36193ff]
[    0.316953] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.317004] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.317044] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.317061] pci 0000:00:1b.0: reg 0x10: [mem 0xb3610000-0xb3613fff 64bit]
[    0.317134] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.317175] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.317209] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.317290] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.317332] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.317366] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.317447] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.317490] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.317536] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.317559] pci 0000:00:1d.0: reg 0x10: [mem 0xb3618000-0xb36183ff]
[    0.317648] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.317699] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.317735] pci 0000:00:1f.0: [8086:1e57] type 00 class 0x060100
[    0.317902] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.317920] pci 0000:00:1f.2: reg 0x10: [io  0x3088-0x308f]
[    0.317928] pci 0000:00:1f.2: reg 0x14: [io  0x3094-0x3097]
[    0.317936] pci 0000:00:1f.2: reg 0x18: [io  0x3080-0x3087]
[    0.317944] pci 0000:00:1f.2: reg 0x1c: [io  0x3090-0x3093]
[    0.317952] pci 0000:00:1f.2: reg 0x20: [io  0x3060-0x307f]
[    0.317960] pci 0000:00:1f.2: reg 0x24: [mem 0xb3617000-0xb36177ff]
[    0.318005] pci 0000:00:1f.2: PME# supported from D3hot
[    0.318071] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.318088] pci 0000:00:1f.3: reg 0x10: [mem 0xb3615000-0xb36150ff 64bit]
[    0.318109] pci 0000:00:1f.3: reg 0x20: [io  0x3040-0x305f]
[    0.318225] pci 0000:01:00.0: [10de:1140] type 00 class 0x030000
[    0.318236] pci 0000:01:00.0: reg 0x10: [mem 0xb2000000-0xb2ffffff]
[    0.318245] pci 0000:01:00.0: reg 0x14: [mem 0xa0000000-0xafffffff 64bit pref]
[    0.318255] pci 0000:01:00.0: reg 0x1c: [mem 0xb0000000-0xb1ffffff 64bit pref]
[    0.318261] pci 0000:01:00.0: reg 0x24: [io  0x2000-0x207f]
[    0.318268] pci 0000:01:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[    0.318324] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.328429] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.328435] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.328439] pci 0000:00:01.0:   bridge window [mem 0xb2000000-0xb2ffffff]
[    0.328446] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.328597] pci 0000:02:00.0: [14e4:16b5] type 00 class 0x020000
[    0.328640] pci 0000:02:00.0: reg 0x10: [mem 0xb3430000-0xb343ffff 64bit pref]
[    0.328669] pci 0000:02:00.0: reg 0x18: [mem 0xb3440000-0xb344ffff 64bit pref]
[    0.328725] pci 0000:02:00.0: reg 0x30: [mem 0xfffff800-0xffffffff pref]
[    0.328876] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.328930] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.329016] pci 0000:02:00.1: [14e4:16bc] type 00 class 0x080501
[    0.329058] pci 0000:02:00.1: reg 0x10: [mem 0xb3400000-0xb340ffff 64bit pref]
[    0.329278] pci 0000:02:00.1: PME# supported from D0 D3hot D3cold
[    0.329404] pci 0000:02:00.2: [14e4:16be] type 00 class 0x088000
[    0.329447] pci 0000:02:00.2: reg 0x10: [mem 0xb3410000-0xb341ffff 64bit pref]
[    0.329664] pci 0000:02:00.2: PME# supported from D0 D3hot D3cold
[    0.329787] pci 0000:02:00.3: [14e4:16bf] type 00 class 0x088000
[    0.329830] pci 0000:02:00.3: reg 0x10: [mem 0xb3420000-0xb342ffff 64bit pref]
[    0.330049] pci 0000:02:00.3: PME# supported from D0 D3hot D3cold
[    0.340517] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.340527] pci 0000:00:1c.0:   bridge window [mem 0xb3400000-0xb34fffff 64bit pref]
[    0.340611] pci 0000:03:00.0: [168c:0034] type 00 class 0x028000
[    0.340641] pci 0000:03:00.0: reg 0x10: [mem 0xb3500000-0xb357ffff 64bit]
[    0.340704] pci 0000:03:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
[    0.340789] pci 0000:03:00.0: supports D1 D2
[    0.340790] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.340826] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.348459] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.348471] pci 0000:00:1c.1:   bridge window [mem 0xb3500000-0xb35fffff]
[    0.420770] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.420818] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.420858] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.420898] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.420938] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.420978] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.421017] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.421057] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.421123] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.421151] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.421235] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.421237] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.421241] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.421242] vgaarb: loaded
[    0.421243] vgaarb: bridge control possible 0000:01:00.0
[    0.421244] vgaarb: no bridge control possible 0000:00:02.0
[    0.421443] SCSI subsystem initialized
[    0.421492] libata version 3.00 loaded.
[    0.421516] ACPI: bus type USB registered
[    0.421531] usbcore: registered new interface driver usbfs
[    0.421538] usbcore: registered new interface driver hub
[    0.421556] usbcore: registered new device driver usb
[    0.421751] PCI: Using ACPI for IRQ routing
[    0.423222] PCI: pci_cache_line_size set to 64 bytes
[    0.423349] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    0.423350] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.423352] e820: reserve RAM buffer [mem 0x948e4018-0x97ffffff]
[    0.423353] e820: reserve RAM buffer [mem 0x948f5018-0x97ffffff]
[    0.423354] e820: reserve RAM buffer [mem 0x957b0000-0x97ffffff]
[    0.423355] e820: reserve RAM buffer [mem 0x9a7bf000-0x9bffffff]
[    0.423357] e820: reserve RAM buffer [mem 0x9b000000-0x9bffffff]
[    0.423358] e820: reserve RAM buffer [mem 0x15f600000-0x15fffffff]
[    0.423457] NetLabel: Initializing
[    0.423459] NetLabel:  domain hash size = 128
[    0.423459] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.423469] NetLabel:  unlabeled traffic allowed by default
[    0.423526] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.423531] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.425568] Switched to clocksource hpet
[    0.430588] AppArmor: AppArmor Filesystem Enabled
[    0.430622] pnp: PnP ACPI init
[    0.430635] ACPI: bus type PNP registered
[    0.430701] pnp 00:00: Plug and Play ACPI device, IDs MSF0001 PNP0303 (active)
[    0.430756] pnp 00:01: Plug and Play ACPI device, IDs ETD0500 PNP0f13 (active)
[    0.430864] system 00:02: [io  0x0680-0x069f] has been reserved
[    0.430866] system 00:02: [io  0xfd60-0xfd63] has been reserved
[    0.430868] system 00:02: [io  0x1000-0x100f] has been reserved
[    0.430869] system 00:02: [io  0xffff] has been reserved
[    0.430871] system 00:02: [io  0xffff] has been reserved
[    0.430873] system 00:02: [io  0x0400-0x0453] could not be reserved
[    0.430874] system 00:02: [io  0x0458-0x047f] has been reserved
[    0.430876] system 00:02: [io  0x0500-0x057f] has been reserved
[    0.430878] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.430880] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.430903] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.430945] system 00:04: [io  0x0454-0x0457] has been reserved
[    0.430947] system 00:04: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.501780] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.501782] system 00:05: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.501784] system 00:05: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.501786] system 00:05: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.501788] system 00:05: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.501789] system 00:05: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.501791] system 00:05: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.501793] system 00:05: [mem 0xff000000-0xff000fff] has been reserved
[    0.501794] system 00:05: [mem 0xff010000-0xffffffff] could not be reserved
[    0.501796] system 00:05: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.501798] system 00:05: [mem 0x9fa00000-0x9fa00fff] has been reserved
[    0.501800] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.501989] system 00:06: [mem 0x20000000-0x201fffff] has been reserved
[    0.501991] system 00:06: [mem 0x40004000-0x40004fff] has been reserved
[    0.501993] system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.502005] pnp: PnP ACPI: found 7 devices
[    0.502006] ACPI: bus type PNP unregistered
[    0.508278] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfff80000-0xffffffff pref]: no compatible bridge window
[    0.508280] pci 0000:02:00.0: can't claim BAR 6 [mem 0xfffff800-0xffffffff pref]: no compatible bridge window
[    0.508283] pci 0000:03:00.0: can't claim BAR 6 [mem 0xffff0000-0xffffffff pref]: no compatible bridge window
[    0.508312] pci 0000:00:1c.0: BAR 14: assigned [mem 0x9fb00000-0x9fbfffff]
[    0.508315] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x80000)
[    0.508317] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.508319] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.508322] pci 0000:00:01.0:   bridge window [mem 0xb2000000-0xb2ffffff]
[    0.508324] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.508328] pci 0000:02:00.0: BAR 6: assigned [mem 0x9fb00000-0x9fb007ff pref]
[    0.508330] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.508335] pci 0000:00:1c.0:   bridge window [mem 0x9fb00000-0x9fbfffff]
[    0.508339] pci 0000:00:1c.0:   bridge window [mem 0xb3400000-0xb34fffff 64bit pref]
[    0.508346] pci 0000:03:00.0: BAR 6: assigned [mem 0xb3580000-0xb358ffff pref]
[    0.508348] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.508353] pci 0000:00:1c.1:   bridge window [mem 0xb3500000-0xb35fffff]
[    0.508362] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.508364] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.508365] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.508367] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.508368] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.508370] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.508371] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.508373] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.508374] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.508376] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.508377] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.508379] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.508380] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.508382] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.508383] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.508385] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.508386] pci_bus 0000:00: resource 20 [mem 0x9fa00000-0xfeafffff]
[    0.508388] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.508389] pci_bus 0000:01: resource 1 [mem 0xb2000000-0xb2ffffff]
[    0.508391] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xb1ffffff 64bit pref]
[    0.508393] pci_bus 0000:02: resource 1 [mem 0x9fb00000-0x9fbfffff]
[    0.508394] pci_bus 0000:02: resource 2 [mem 0xb3400000-0xb34fffff 64bit pref]
[    0.508396] pci_bus 0000:03: resource 1 [mem 0xb3500000-0xb35fffff]
[    0.508424] NET: Registered protocol family 2
[    0.508585] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.508663] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.508767] TCP: Hash tables configured (established 32768 bind 32768)
[    0.508785] TCP: reno registered
[    0.508791] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.508808] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.508862] NET: Registered protocol family 1
[    0.508876] pci 0000:00:02.0: Video device with shadowed ROM
[    0.541814] PCI: CLS 64 bytes, default 64
[    0.541868] Trying to unpack rootfs image as initramfs...
[    0.824943] Freeing initrd memory: 19932K (ffff88003ec84000 - ffff88003fffb000)
[    0.824953] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.824955] software IO TLB [mem 0x8f1c0000-0x931c0000] (64MB) mapped at [ffff88008f1c0000-ffff8800931bffff]
[    0.824998] Simple Boot Flag at 0x44 set to 0x1
[    0.825208] RAPL PMU detected, hw unit 2^-16 Joules, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.825250] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x19
[    0.825256] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x19
[    0.825261] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x19
[    0.825269] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x19
[    0.825324] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.825346] Scanning for low memory corruption every 60 seconds
[    0.825657] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.825692] Initialise system trusted keyring
[    0.825714] audit: initializing netlink subsys (disabled)
[    0.825726] audit: type=2000 audit(1424687527.804:1): initialized
[    0.826079] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.827300] zpool: loaded
[    0.827303] zbud: loaded
[    0.827446] VFS: Disk quotas dquot_6.5.2
[    0.827475] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.827860] fuse init (API version 7.23)
[    0.827934] msgmni has been set to 7679
[    0.827986] Key type big_key registered
[    0.828354] Key type asymmetric registered
[    0.828357] Asymmetric key parser 'x509' registered
[    0.828387] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.828432] io scheduler noop registered
[    0.828435] io scheduler deadline registered (default)
[    0.828475] io scheduler cfq registered
[    0.828540] pcieport 0000:00:01.0: device [8086:0151] has invalid IRQ; check vendor BIOS
[    0.828638] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.828676] pcieport 0000:00:1c.0: device [8086:1e10] has invalid IRQ; check vendor BIOS
[    0.828775] pcieport 0000:00:1c.1: device [8086:1e12] has invalid IRQ; check vendor BIOS
[    0.828893] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.828906] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.828952] efifb: probing for efifb
[    0.828965] efifb: framebuffer at 0xc0000000, mapped to 0xffffc90004800000, using 4128k, total 4128k
[    0.828966] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    0.828967] efifb: scrolling: redraw
[    0.828968] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.831008] Console: switching to colour frame buffer device 170x48
[    0.832868] fb0: EFI VGA frame buffer device
[    0.832892] intel_idle: MWAIT substates: 0x21120
[    0.832893] intel_idle: v0.4 model 0x3A
[    0.832894] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.833103] ACPI: AC Adapter [ACAD] (on-line)
[    0.833187] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
[    0.833190] ACPI: Power Button [PWRB]
[    0.833221] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0D:00/input/input1
[    0.833236] ACPI: Lid Switch [LID0]
[    0.833266] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input2
[    0.833268] ACPI: Sleep Button [SLPB]
[    0.833301] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.833303] ACPI: Power Button [PWRF]
[    0.833558] GHES: HEST is not enabled!
[    0.833646] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.901910] ACPI: Battery Slot [BAT1] (battery absent)
[    0.902002] Linux agpgart interface v0.103
[    0.903229] brd: module loaded
[    0.903732] loop: module loaded
[    0.903911] libphy: Fixed MDIO Bus: probed
[    0.903915] tun: Universal TUN/TAP device driver, 1.6
[    0.903916] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.903964] PPP generic driver version 2.4.2
[    0.904006] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.904011] ehci-pci: EHCI PCI platform driver
[    0.904107] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.904113] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.904126] ehci-pci 0000:00:1a.0: debug port 2
[    0.908038] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.908058] ehci-pci 0000:00:1a.0: irq 16, io mem 0xb3619000
[    0.917905] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.917936] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.917937] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.917939] usb usb1: Product: EHCI Host Controller
[    0.917940] usb usb1: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    0.917942] usb usb1: SerialNumber: 0000:00:1a.0
[    0.918039] hub 1-0:1.0: USB hub found
[    0.918045] hub 1-0:1.0: 2 ports detected
[    0.918202] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.918206] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.918217] ehci-pci 0000:00:1d.0: debug port 2
[    0.922113] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.922130] ehci-pci 0000:00:1d.0: irq 23, io mem 0xb3618000
[    0.933948] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.934001] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.934003] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.934005] usb usb2: Product: EHCI Host Controller
[    0.934006] usb usb2: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    0.934008] usb usb2: SerialNumber: 0000:00:1d.0
[    0.934165] hub 2-0:1.0: USB hub found
[    0.934173] hub 2-0:1.0: 2 ports detected
[    0.934265] ehci-platform: EHCI generic platform driver
[    0.934274] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.934280] ohci-pci: OHCI PCI platform driver
[    0.934289] ohci-platform: OHCI generic platform driver
[    0.934297] uhci_hcd: USB Universal Host Controller Interface driver
[    0.934396] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.934400] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.934493] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.934512] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    0.934568] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.934570] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.934571] usb usb3: Product: xHCI Host Controller
[    0.934573] usb usb3: Manufacturer: Linux 3.16.0-30-generic xhci_hcd
[    0.934574] usb usb3: SerialNumber: 0000:00:14.0
[    0.934727] hub 3-0:1.0: USB hub found
[    0.934738] hub 3-0:1.0: 4 ports detected
[    0.935018] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.935021] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.935053] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.935054] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.935056] usb usb4: Product: xHCI Host Controller
[    0.935057] usb usb4: Manufacturer: Linux 3.16.0-30-generic xhci_hcd
[    0.935058] usb usb4: SerialNumber: 0000:00:14.0
[    0.935212] hub 4-0:1.0: USB hub found
[    0.935223] hub 4-0:1.0: 4 ports detected
[    0.935545] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.949452] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.949458] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.949722] mousedev: PS/2 mouse device common for all mice
[    0.950247] rtc_cmos 00:03: RTC can wake from S4
[    0.950398] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.950427] rtc_cmos 00:03: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.950485] device-mapper: uevent: version 1.0.3
[    0.950580] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.950593] Intel P-state driver initializing.
[    0.950612] Intel pstate controlling: cpu 0
[    0.950634] Intel pstate controlling: cpu 1
[    0.950646] Intel pstate controlling: cpu 2
[    0.950665] Intel pstate controlling: cpu 3
[    0.950692] Consider also installing thermald for improved thermal control.
[    0.950709] ledtrig-cpu: registered to indicate activity on CPUs
[    0.950713] EFI Variables Facility v0.08 2004-May-17
[    0.958812] TCP: cubic registered
[    0.958900] NET: Registered protocol family 10
[    0.959062] NET: Registered protocol family 17
[    0.959079] Key type dns_resolver registered
[    0.959331] Loading compiled-in X.509 certificates
[    0.959995] Loaded X.509 cert 'Magrathea: Glacier signing key: fd44851cc6750f85e8f0c2c69b128263f404d5e3'
[    0.960012] registered taskstats version 1
[    0.961763] Key type trusted registered
[    0.963178] Key type encrypted registered
[    0.964521] AppArmor: AppArmor sha1 policy hashing enabled
[    0.964526] ima: No TPM chip found, activating TPM-bypass!
[    0.964539] evm: HMAC attrs: 0x1
[    0.965007]   Magic number: 3:241:528
[    0.965109] rtc_cmos 00:03: setting system clock to 2015-02-23 10:32:08 UTC (1424687528)
[    0.965174] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.965175] EDD information not available.
[    0.965246] PM: Hibernation image not present or could not be loaded.
[    0.965895] Freeing unused kernel memory: 1360K (ffffffff81d2e000 - ffffffff81e82000)
[    0.965896] Write protecting the kernel read-only data: 12288k
[    0.966775] Freeing unused kernel memory: 440K (ffff880001792000 - ffff880001800000)
[    0.967563] Freeing unused kernel memory: 488K (ffff880001b86000 - ffff880001c00000)
[    0.971149] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.975542] systemd-udevd[124]: starting version 208
[    0.975916] random: systemd-udevd urandom read with 4 bits of entropy available
[    0.995705] pps_core: LinuxPPS API ver. 1 registered
[    0.995707] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.996016] sdhci: Secure Digital Host Controller Interface driver
[    0.996017] sdhci: Copyright(c) Pierre Ossman
[    0.997362] PTP clock support registered
[    0.997734] sdhci-pci 0000:02:00.1: SDHCI controller found [14e4:16bc] (rev 10)
[    0.997922] mmc0: no vqmmc regulator found
[    0.997923] mmc0: no vmmc regulator found
[    0.998052] mmc0: SDHCI controller on PCI [0000:02:00.1] using ADMA
[    1.002065] tg3.c:v3.137 (May 11, 2014)
[    1.002431] ahci 0000:00:1f.2: version 3.0
[    1.002526] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.002544] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.018000] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.018005] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
[    1.026405] scsi0 : ahci
[    1.026504] scsi1 : ahci
[    1.026595] scsi2 : ahci
[    1.026680] scsi3 : ahci
[    1.026764] scsi4 : ahci
[    1.026857] scsi5 : ahci
[    1.026896] ata1: SATA max UDMA/133 abar m2048@0xb3617000 port 0xb3617100 irq 42
[    1.026897] ata2: DUMMY
[    1.026899] ata3: SATA max UDMA/133 abar m2048@0xb3617000 port 0xb3617200 irq 42
[    1.026900] ata4: DUMMY
[    1.026901] ata5: DUMMY
[    1.026902] ata6: DUMMY
[    1.038213] tg3 0000:02:00.0 eth0: Tigon3 [partno(BCM57785) rev 57785100] (PCI Express) MAC address b8:88:e3:b4:46:cb
[    1.038216] tg3 0000:02:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    1.038219] tg3 0000:02:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.038221] tg3 0000:02:00.0 eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    1.230249] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.346223] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.349541] ata1.00: ATA-8: WDC WD7500BPVT-22HXZT3, 01.01A01, max UDMA/133
[    1.349547] ata1.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.353051] ata1.00: configured for UDMA/133
[    1.353335] scsi 0:0:0:0: Direct-Access     ATA      WDC WD7500BPVT-2 1A01 PQ: 0 ANSI: 5
[    1.353664] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.353667] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.353699] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.353700] sd 0:0:0:0: [sda] Write Protect is off
[    1.353702] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.353718] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.362629] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.362631] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.362815] hub 1-1:1.0: USB hub found
[    1.362900] hub 1-1:1.0: 6 ports detected
[    1.424798]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sda10 sda11
[    1.425967] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.474401] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.606934] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.606936] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.607093] hub 2-1:1.0: USB hub found
[    1.607185] hub 2-1:1.0: 8 ports detected
[    1.670444] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.673795] ata3.00: ATAPI: HL-DT-ST DVDRAM GT70N, YP10, max UDMA/133
[    1.676686] ata3.00: configured for UDMA/133
[    1.678500] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    1.681321] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT70N     YP10 PQ: 0 ANSI: 5
[    1.702628] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.702630] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.702778] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.702845] sr 2:0:0:0: Attached scsi generic sg1 type 5[COLOR=#ff0000]
[    1.772408] usb 1-1.1: string descriptor 0 read error: -22[/COLOR]
[    1.772432] usb 1-1.1: New USB device found, idVendor=0489, idProduct=e04e
[    1.772433] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.822520] tsc: Refined TSC clocksource calibration: 2594.107 MHz
[    1.842607] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[    1.991077] usb 1-1.3: New USB device found, idVendor=1bcf, idProduct=2c18
[    1.991084] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.991088] usb 1-1.3: Product: HD WebCam
[    1.991091] usb 1-1.3: Manufacturer: NC.21411.00X24106C60LM0009
[    2.114247] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x550f01)
[    2.143800] psmouse serio1: elantech: Synaptics capabilities query result 0x79, 0x18, 0x0b.
[    2.279518] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input7
[    2.823307] Switched to clocksource tsc
[    3.245478] random: nonblocking pool is initialized
[    3.552370] EXT4-fs (sda10): mounted filesystem with ordered data mode. Opts: (null)
[    5.424406] init: plymouth-upstart-bridge main process (201) terminated with status 1
[    5.424415] init: plymouth-upstart-bridge main process ended, respawning
[    5.425641] init: plymouth-upstart-bridge main process (216) terminated with status 1
[    5.425649] init: plymouth-upstart-bridge main process ended, respawning
[    5.427132] init: plymouth-upstart-bridge main process (218) terminated with status 1
[    5.427142] init: plymouth-upstart-bridge main process ended, respawning
[    5.428453] init: plymouth-upstart-bridge main process (220) terminated with status 1
[    5.428472] init: plymouth-upstart-bridge main process ended, respawning
[    5.429691] init: plymouth-upstart-bridge main process (221) terminated with status 1
[    5.429701] init: plymouth-upstart-bridge main process ended, respawning
[    5.431008] init: plymouth-upstart-bridge main process (223) terminated with status 1
[    5.431015] init: plymouth-upstart-bridge main process ended, respawning
[    5.432175] init: plymouth-upstart-bridge main process (224) terminated with status 1
[    5.432182] init: plymouth-upstart-bridge main process ended, respawning
[    5.433399] init: plymouth-upstart-bridge main process (226) terminated with status 1
[    5.433407] init: plymouth-upstart-bridge main process ended, respawning
[    5.434689] init: plymouth-upstart-bridge main process (228) terminated with status 1
[    5.434709] init: plymouth-upstart-bridge main process ended, respawning
[    5.435903] init: plymouth-upstart-bridge main process (229) terminated with status 1
[    5.435913] init: plymouth-upstart-bridge main process ended, respawning
[    5.437299] init: plymouth-upstart-bridge main process (231) terminated with status 1
[    5.437307] init: plymouth-upstart-bridge respawning too fast, stopped
[   13.585971] Adding 8000508k swap on /dev/sda8.  Priority:-1 extents:1 across:8000508k FS
[COLOR=#ff0000][   13.993476] EXT4-fs (sda10): re-mounted. Opts: errors=remount-ro[/COLOR]
[   14.198369] systemd-udevd[373]: starting version 208
[   14.351258] lp: driver loaded but no devices found
[   14.353684] ppdev: user-space parallel port driver
[   14.391385] wmi: Mapper loaded
[   14.408401] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.413601] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X
[   14.415398] [drm] Initialized drm 1.1.0 20060810
[   14.432516] Bluetooth: Core ver 2.19
[   14.432535] NET: Registered protocol family 31
[   14.432537] Bluetooth: HCI device and connection manager initialized
[   14.432544] Bluetooth: HCI socket layer initialized
[   14.432547] Bluetooth: L2CAP socket layer initialized
[   14.432567] Bluetooth: SCO socket layer initialized
[   14.439164] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
[   14.439171] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.439175] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   14.439179] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x000000000000055f (\_SB_.PCI0.PEG0.PEGP.GPIO) (20140424/utaddress-258)
[   14.439183] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.439185] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   14.439188] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000055f (\_SB_.PCI0.PEG0.PEGP.GPIO) (20140424/utaddress-258)
[   14.439192] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.439193] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   14.439196] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000055f (\_SB_.PCI0.PEG0.PEGP.GPIO) (20140424/utaddress-258)
[   14.439200] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.439201] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.442654] [drm] Memory usable by graphics device = 2048M
[   14.442659] checking generic (c0000000 408000) vs hw (c0000000 10000000)
[   14.442661] fb: switching to inteldrmfb from EFI VGA
[   14.442681] Console: switching to colour dummy device 80x25
[   14.442912] [drm] Replacing VGA console driver
[   14.448506] cfg80211: Calling CRDA to update world regulatory domain
[   14.463073] usbcore: registered new interface driver btusb
[   14.464475] usbcore: registered new interface driver ath3k
[   14.466829] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   14.466839] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   14.466841] [drm] Driver supports precise vblank timestamp query.
[   14.466976] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=none
[   14.494295] AVX version of gcm_enc/dec engaged.
[   14.494964] ath: phy0: ASPM enabled: 0x42
[   14.494967] ath: EEPROM regdomain: 0x6c
[   14.494968] ath: EEPROM indicates we should expect a direct regpair map
[   14.494970] ath: Country alpha2 being used: 00
[   14.494972] ath: Regpair used: 0x6c
[   14.511321] [drm] failed to retrieve link info, disabling eDP
[   14.521433] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.521794] ieee80211 phy0: Atheros AR9462 Rev:2 mem=0xffffc90005080000, irq=17
[   14.531143] intel_rapl: Found RAPL domain package
[   14.531147] intel_rapl: Found RAPL domain core
[   14.531149] intel_rapl: Found RAPL domain uncore
[   14.540432] fbcon: inteldrmfb (fb0) is primary device
[   14.549645] acer_wmi: Acer Laptop ACPI-WMI Extras
[   14.549739] acer_wmi: Function bitmap for Communication Button: 0x801
[   14.549823] acer_wmi: Brightness must be controlled by acpi video driver
[   14.592353] media: Linux media interface: v0.10
[   14.595274] Linux video capture interface: v2.00
[   14.601164] uvcvideo: Found UVC 1.00 device HD WebCam (1bcf:2c18)
[   14.603918] acer_wmi: Enabling Launch Manager failed: 0xe2 - 0x0
[   14.603962] input: Acer WMI hotkeys as /devices/virtual/input/input8
[   14.604401] input: Acer BMA150 accelerometer as /devices/virtual/input/input9
[   14.610078] input: HD WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input10
[   14.610144] usbcore: registered new interface driver uvcvideo
[   14.610145] USB Video Class driver (1.1.1)
[   14.871256] cfg80211: World regulatory domain updated:
[   14.871258] cfg80211:  DFS Master region: unset
[   14.871258] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   14.871259] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.871260] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.871261] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.871261] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.871262] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.925988] audit: type=1400 audit(1424667742.448:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=484 comm="apparmor_parser"
[   14.925992] audit: type=1400 audit(1424667742.448:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=484 comm="apparmor_parser"
[   14.925995] audit: type=1400 audit(1424667742.448:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=484 comm="apparmor_parser"
[   14.926002] audit: type=1400 audit(1424667742.448:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=449 comm="apparmor_parser"
[   14.926007] audit: type=1400 audit(1424667742.448:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=449 comm="apparmor_parser"
[   14.926009] audit: type=1400 audit(1424667742.448:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=449 comm="apparmor_parser"
[   15.223906] Console: switching to colour frame buffer device 170x48
[   15.225489] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   15.225490] i915 0000:00:02.0: registered panic notifier
[   15.231868] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   15.231992] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   15.232179] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:36/LNXVIDEO:00/input/input11
[   15.251790] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.251871] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input12
[   15.251957] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.252315] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   15.271194] sound hdaudioC0D0: ALC269VB: SKU not ready 0x598301f0
[   15.271796] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   15.271799] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.271802] sound hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   15.271804] sound hdaudioC0D0:    mono: mono_out=0x0
[   15.271805] sound hdaudioC0D0:    inputs:
[   15.271808] sound hdaudioC0D0:      Internal Mic=0x1b
[   15.271811] sound hdaudioC0D0:      Mic=0x18
[   15.282765] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   15.282850] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   15.282938] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   15.844076] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[COLOR=#ff0000][   24.760413] init: Error while reading from descriptor: Broken pipe[/COLOR]
[   24.762442] init: failsafe main process (745) killed by TERM signal
[   24.989150] usb 1-1.1: USB disconnect, device number 3
[   25.476489] audit: type=1400 audit(1424667752.992:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=858 comm="apparmor_parser"
[   25.476496] audit: type=1400 audit(1424667752.992:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=858 comm="apparmor_parser"
[   25.477633] audit: type=1400 audit(1424667752.992:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=858 comm="apparmor_parser"
[   25.477638] audit: type=1400 audit(1424667752.992:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=858 comm="apparmor_parser"
[   25.477641] audit: type=1400 audit(1424667752.992:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=858 comm="apparmor_parser"
[   25.484612] audit: type=1400 audit(1424667753.000:13): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=858 comm="apparmor_parser"
[   25.484617] audit: type=1400 audit(1424667753.000:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=858 comm="apparmor_parser"
[   25.484620] audit: type=1400 audit(1424667753.000:15): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=858 comm="apparmor_parser"
[   25.484623] audit: type=1400 audit(1424667753.000:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=858 comm="apparmor_parser"
[   25.484626] audit: type=1400 audit(1424667753.000:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=858 comm="apparmor_parser"
[   25.799834] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.799846] Bluetooth: BNEP filters: protocol multicast
[   25.799852] Bluetooth: BNEP socket layer initialized
[   25.825306] Bluetooth: RFCOMM TTY layer initialized
[   25.825318] Bluetooth: RFCOMM socket layer initialized
[   25.825322] Bluetooth: RFCOMM ver 1.11
[   25.863575] init: cups main process (896) killed by HUP signal
[   25.863587] init: cups main process ended, respawning
[   27.504764] systemd-logind[1047]: New seat seat0.
[   27.523770] systemd-logind[1047]: Watching system buttons on /dev/input/event3 (Power Button)
[   27.523815] systemd-logind[1047]: Watching system buttons on /dev/input/event10 (Video Bus)
[   27.523855] systemd-logind[1047]: Watching system buttons on /dev/input/event0 (Power Button)
[   27.523893] systemd-logind[1047]: Watching system buttons on /dev/input/event1 (Lid Switch)
[   27.523930] systemd-logind[1047]: Watching system buttons on /dev/input/event2 (Sleep Button)
[   27.523968] systemd-logind[1047]: Watching system buttons on /dev/input/event9 (Video Bus)
[   27.599106] tg3 0000:02:00.0: irq 46 for MSI/MSI-X
[   27.599112] tg3 0000:02:00.0: irq 47 for MSI/MSI-X
[   27.599114] tg3 0000:02:00.0: irq 48 for MSI/MSI-X
[   27.599116] tg3 0000:02:00.0: irq 49 for MSI/MSI-X
[   27.599119] tg3 0000:02:00.0: irq 50 for MSI/MSI-X
[   28.163670] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.176857] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.830335] wlan0: authenticate with 00:24:c4:ab:84:50
[   32.837254] wlan0: send auth to 00:24:c4:ab:84:50 (try 1/3)
[   32.838966] wlan0: authenticated
[   32.842868] wlan0: associate with 00:24:c4:ab:84:50 (try 1/3)
[   32.845141] wlan0: RX AssocResp from 00:24:c4:ab:84:50 (capab=0x421 status=0 aid=3)
[   32.845199] wlan0: associated
[   32.845206] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[COLOR=#ff0000][   33.495142] systemd-logind[1047]: Failed to start unit user@112.service: Unknown unit: user@112.service
[   33.495148] systemd-logind[1047]: Failed to start user service: Unknown unit: user@112.service[/COLOR]
[   33.498259] systemd-logind[1047]: New session c1 of user lightdm.
[   33.498277] systemd-logind[1047]: Linked /tmp/.X11-unix/X0 to /run/user/112/X11-display.
[   33.554651] bbswitch: module verification failed: signature and/or  required key missing - tainting kernel
[   33.554858] bbswitch: version 0.7
[   33.554864] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   33.554869] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[   33.554881] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[   33.554951] bbswitch: detected an Optimus _DSM function
[   33.554962] pci 0000:01:00.0: enabling device (0006 -> 0007)
[   33.555002] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[   33.556527] bbswitch: disabling discrete graphics
[   33.556537] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[COLOR=#ff0000][   41.647151] systemd-logind[1047]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   41.647158] systemd-logind[1047]: Failed to start user service: Unknown unit: user@1000.service[/COLOR]
[   41.649992] systemd-logind[1047]: New session c2 of user akash.
[   41.650022] systemd-logind[1047]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   56.081391] audit_printk_skb: 45 callbacks suppressed
[   56.081394] audit: type=1400 audit(1424667783.576:33): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2485 comm="apparmor_parser"
[   56.081401] audit: type=1400 audit(1424667783.576:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2485 comm="apparmor_parser"
[   56.094365] audit: type=1400 audit(1424667783.592:35): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="third_party" pid=2485 comm="apparmor_parser"
```

While I've noticed the usb error on several other distros and several other machines, the other errors are new.

---

### Post by MAFoElffen on 2015-02-23
You didn't mention the errors that you are greeted with in Plymouth... You also did not mention what version of version your are running (14.01? 14.10?) 

I don't see it in your commandline... are you using systemd-shim? Please post the results of
```

dpkg -l|grep systemd

```

---

### Post by akashunbeatable on 2015-02-23
> **MAFoElffen said:**
> You didn't mention the errors that you are greeted with in Plymouth...  You need to scroll down to [COLOR=#ff0000][1.772408], [/COLOR][COLOR=#ff0000][13.993476],  [24.760413], [33.495142], [33.495148], [44.647151] and [44.647158] [/COLOR]
> **MAFoElffen said:**
>  You also did not mention what version of version your are running (14.01? 14.10?) oh! I forgot that. It is ubuntu 14.10
> **MAFoElffen said:**
>  are you using systemd-shim?  What's that?
> **MAFoElffen said:**
>  Please post the results of ```
 dpkg -l|grep systemd 
```
```
akash@akash-ubuntu:~$ dpkg -l|grep systemd
ii  libpam-systemd:amd64                                 208-8ubuntu8.2                             amd64        system and service manager - PAM module
ii  libsystemd-daemon0:amd64                             208-8ubuntu8.2                             amd64        systemd utility library
ii  libsystemd-journal0:amd64                            208-8ubuntu8.2                             amd64        systemd journal utility library
ii  libsystemd-login0:amd64                              208-8ubuntu8.2                             amd64        systemd login utility library
ii  systemd                                              208-8ubuntu8.2                             amd64        system and service manager
ii  systemd-shim                                         8-1ubuntu0.1                               amd64        shim for systemd
```

---

