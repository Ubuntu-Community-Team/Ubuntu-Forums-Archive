---
title: "Black screen after update to 12.10 (bumblebee, ppa:ubuntu-x-swat/x-updates)"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by Germanunkol on 2012-11-22
Hi,

I upgraded to 12.10 last night.
However, it did not go well. After reboot, I now only get a black screen.
My setup:
Ubuntu 12.04 (updated to 12.10)
Bumblebee and Xorg-edgers and bumblebee-nvidia

Most of the time, when I boot, I still get to the console CTRL+ALT+F1, but sometimes I don't.
Output of dmesg showed me something like:
(note that gdm, lightdm and failsafe-x all fail... this sounds bad?)
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-18-generic (buildd@allspice) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 (Ubuntu 3.5.0-18.29-generic 3.5.7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=b9d69b06-cee5-477e-aa92-eaa1b3bd1f28 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000c99d9fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c99da000-0x00000000c9d36fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9d37000-0x00000000c9d43fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000c9d44000-0x00000000ca142fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca143000-0x00000000ca149fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ca14a000-0x00000000ca1d4fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca1d5000-0x00000000ca28afff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ca28b000-0x00000000ca69dfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca69e000-0x00000000ca69efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca69f000-0x00000000ca6e1fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ca6e2000-0x00000000cadf4fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cadf5000-0x00000000caff2fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000caff3000-0x00000000caffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cb800000-0x00000000cf9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.7 present.
[    0.000000] DMI: CLEVO CO.                        W150ER                          /W150ER                          , BIOS 4.6.5 04/25/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x22f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FE0000000 write-back
[    0.000000]   2 base 220000000 mask FF0000000 write-back
[    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   4 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   5 base 0CC000000 mask FFC000000 uncachable
[    0.000000]   6 base 0CB800000 mask FFF800000 uncachable
[    0.000000]   7 base 22F800000 mask FFF800000 uncachable
[    0.000000]   8 base 22F600000 mask FFFE00000 uncachable
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 8704MB, range: 256MB, type WB
[    0.000000] reg 3, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 4, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 5, base: 3264MB, range: 64MB, type UC
[    0.000000] reg 6, base: 3256MB, range: 8MB, type UC
[    0.000000] reg 7, base: 8952MB, range: 8MB, type UC
[    0.000000] reg 8, base: 8950MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8110M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: 0G
[    0.000000]  gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: -256M
[    0.000000]  gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: 0G
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: 2M
[    0.000000]  gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: 2M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: -254M
[    0.000000]  gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: 2M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1022M
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 54M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 22M
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 512M     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 9      lose cover RAM: 6M
[    0.000000]  gran_size: 8M     chunk_size: 2G     num_reg: 10      lose cover RAM: 6M
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 30M
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 512M     num_reg: 10      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 9      lose cover RAM: 14M
[    0.000000]  gran_size: 16M     chunk_size: 2G     num_reg: 10      lose cover RAM: 14M
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 512M     num_reg: 10      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 9      lose cover RAM: 46M
[    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 10      lose cover RAM: 46M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 7      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 7      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 9      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 8      lose cover RAM: 110M
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 9      lose cover RAM: 110M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 6      lose cover RAM: 174M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 8      lose cover RAM: 174M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 9      lose cover RAM: 174M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 8      lose cover RAM: 174M
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 9      lose cover RAM: 174M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 4      lose cover RAM: 430M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 4      lose cover RAM: 430M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 5      lose cover RAM: 430M
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 6      lose cover RAM: 430M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 4      lose cover RAM: 430M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 5      lose cover RAM: 430M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 6      lose cover RAM: 430M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 3      lose cover RAM: 942M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 3      lose cover RAM: 942M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 2      lose cover RAM: 1966M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820: update [mem 0xcb800000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd860-0x000fd86f] mapped at [ffff8800000fd860]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xcaffffff]
[    0.000000]  [mem 0x00000000-0xcaffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xcaffffff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x22f5fffff]
[    0.000000]  [mem 0x100000000-0x22f5fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x22f5fffff @ [mem 0xcaff6000-0xcaffffff]
[    0.000000] RAMDISK: [mem 0x362e8000-0x3716bfff]
[    0.000000] ACPI: RSDP 00000000000f0490 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000c9d37088 0008C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000c9d3fe28 000F4 (v04                 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000c9d371a0 08C84 (v02                 00000017 INTL 20051117)
[    0.000000] ACPI: FACS 00000000ca289f80 00040
[    0.000000] ACPI: APIC 00000000c9d3ff20 00092 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000c9d3ffb8 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000c9d40000 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000c9d40040 00EA5 (v01 TrmRef PtidDevc 00001000 INTL 20091112)
[    0.000000] ACPI: ptal 00000000c9d40ee8 00020 (v00                 414F4C5F D_ER 54455048)
[    0.000000] ACPI: HPET 00000000c9d40f08 00038 (v01                 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000c9d40f40 0036D (v01                 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000c9d412b0 008E4 (v01                 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000c9d41b98 00A92 (v01                 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000c9d42630 00574 (v01                 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000c9d42ba8 00FB1 (v01                 00001000 INTL 20051117)
[    0.000000] ACPI: BGRT 00000000c9d43b60 00038 (v00                 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22f5fffff]
[    0.000000]   NODE_DATA [mem 0x22f5fc000-0x22f5fffff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880226c00000-ffff88022ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xc99d9fff]
[    0.000000]   node   0: [mem 0xca14a000-0xca1d4fff]
[    0.000000]   node   0: [mem 0xca69e000-0xca69efff]
[    0.000000]   node   0: [mem 0xca6e2000-0xcadf4fff]
[    0.000000]   node   0: [mem 0xcaff3000-0xcaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x22f5fffff]
[    0.000000] On node 0 totalpages: 2069778
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3911 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 806853 pages, LIFO batch:31
[    0.000000]   Normal zone: 19416 pages used for memmap
[    0.000000]   Normal zone: 1223208 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000c99da000 - 00000000c9d37000
[    0.000000] PM: Registered nosave memory: 00000000c9d37000 - 00000000c9d44000
[    0.000000] PM: Registered nosave memory: 00000000c9d44000 - 00000000ca143000
[    0.000000] PM: Registered nosave memory: 00000000ca143000 - 00000000ca14a000
[    0.000000] PM: Registered nosave memory: 00000000ca1d5000 - 00000000ca28b000
[    0.000000] PM: Registered nosave memory: 00000000ca28b000 - 00000000ca69e000
[    0.000000] PM: Registered nosave memory: 00000000ca69f000 - 00000000ca6e2000
[    0.000000] PM: Registered nosave memory: 00000000cadf5000 - 00000000caff3000
[    0.000000] PM: Registered nosave memory: 00000000cb000000 - 00000000cb800000
[    0.000000] PM: Registered nosave memory: 00000000cb800000 - 00000000cfa00000
[    0.000000] PM: Registered nosave memory: 00000000cfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] e820: [mem 0xcfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88022f200000 s83584 r8192 d22912 u262144
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2033972
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-18-generic root=UUID=b9d69b06-cee5-477e-aa92-eaa1b3bd1f28 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8050356k/9164800k available (6717k kernel code, 885688k absent, 228756k reserved, 6453k data, 928k init)
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
[    0.004000] Detected 2294.739 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4589.47 BogoMIPS (lpj=9178956)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000025] Security Framework initialized
[    0.000036] AppArmor: AppArmor initialized
[    0.000037] Yama: becoming mindful.
[    0.000531] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.002610] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.003537] Mount-cache hash table entries: 256
[    0.003690] Initializing cgroup subsys cpuacct
[    0.003692] Initializing cgroup subsys memory
[    0.003699] Initializing cgroup subsys devices
[    0.003700] Initializing cgroup subsys freezer
[    0.003701] Initializing cgroup subsys blkio
[    0.003703] Initializing cgroup subsys perf_event
[    0.003727] CPU: Physical Processor ID: 0
[    0.003728] CPU: Processor Core ID: 0
[    0.003732] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.003732] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.004135] mce: CPU supports 9 MCE banks
[    0.004148] CPU0: Thermal monitoring enabled (TM1)
[    0.004154] using mwait in idle threads.
[    0.006222] ACPI: Core revision 20120320
[    0.014713] ftrace: allocating 25135 entries in 99 pages
[    0.027191] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066854] CPU0: Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz stepping 09
[    0.171848] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.171853] ... version:                3
[    0.171854] ... bit width:              48
[    0.171854] ... generic registers:      4
[    0.171855] ... value mask:             0000ffffffffffff
[    0.171856] ... max period:             000000007fffffff
[    0.171857] ... fixed-purpose events:   3
[    0.171858] ... event mask:             000000070000000f
[    0.171987] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.172064] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 Ok.
[    0.267190] Brought up 8 CPUs
[    0.267192] Total of 8 processors activated (36715.82 BogoMIPS).
[    0.274549] devtmpfs: initialized
[    0.275558] EVM: security.selinux
[    0.275560] EVM: security.SMACK64
[    0.275560] EVM: security.capability
[    0.275596] PM: Registering ACPI NVS region [mem 0xca1d5000-0xca28afff] (745472 bytes)
[    0.275607] PM: Registering ACPI NVS region [mem 0xca69f000-0xca6e1fff] (274432 bytes)
[    0.276241] dummy:
[    0.276273] RTC time: 16:54:45, date: 11/22/12
[    0.276303] NET: Registered protocol family 16
[    0.276381] Trying to unpack rootfs image as initramfs...
[    0.276438] ACPI: bus type pci registered
[    0.276484] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.276486] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.285617] PCI: Using configuration type 1 for base access
[    0.286435] bio: create slab <bio-0> at 0
[    0.286500] ACPI: Added _OSI(Module Device)
[    0.286502] ACPI: Added _OSI(Processor Device)
[    0.286504] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.286505] ACPI: Added _OSI(Processor Aggregator Device)
[    0.287931] ACPI: EC: Look up EC in DSDT
[    0.289320] ACPI: Executed 1 blocks of module-level executable AML code
[    0.419757] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.420149] ACPI: SSDT 00000000ca0e3018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.420513] ACPI: Dynamic OEM Table Load:
[    0.420515] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.455920] ACPI: SSDT 00000000ca0e4a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.456311] ACPI: Dynamic OEM Table Load:
[    0.456313] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.483775] ACPI: SSDT 00000000ca0e9c18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.484138] ACPI: Dynamic OEM Table Load:
[    0.484140] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.510008] Freeing initrd memory: 14864k freed
[    1.016237] ACPI: Interpreter enabled
[    1.016243] ACPI: (supports S0 S3 S4 S5)
[    1.016262] ACPI: Using IOAPIC for interrupt routing
[    1.022894] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.023064] ACPI: No dock devices found.
[    1.023068] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.023327] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    1.023697] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    1.023699] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    1.023701] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.023702] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    1.023704] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    1.023705] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    1.023707] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    1.023708] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    1.023710] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    1.023711] pci_root PNP0A08:00: host bridge window [mem 0xcfa00000-0xfeafffff]
[    1.023737] PCI host bridge to bus 0000:00
[    1.023739] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.023741] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.023742] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.023743] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    1.023745] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    1.023746] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    1.023748] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    1.023749] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    1.023751] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    1.023752] pci_bus 0000:00: root bus resource [mem 0xcfa00000-0xfeafffff]
[    1.023760] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    1.023795] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    1.023827] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.023845] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    1.023856] pci 0000:00:02.0: reg 10: [mem 0xf7400000-0xf77fffff 64bit]
[    1.023863] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.023868] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    1.023920] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    1.023942] pci 0000:00:14.0: reg 10: [mem 0xf7a00000-0xf7a0ffff 64bit]
[    1.024015] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    1.024038] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    1.024061] pci 0000:00:16.0: reg 10: [mem 0xf7a1a000-0xf7a1a00f 64bit]
[    1.024138] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.024171] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    1.024192] pci 0000:00:1a.0: reg 10: [mem 0xf7a18000-0xf7a183ff]
[    1.024285] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.024312] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    1.024327] pci 0000:00:1b.0: reg 10: [mem 0xf7a10000-0xf7a13fff 64bit]
[    1.024398] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.024420] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    1.024502] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.024528] pci 0000:00:1c.2: [8086:1e14] type 01 class 0x060400
[    1.024610] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.024635] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
[    1.024716] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.024749] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    1.024770] pci 0000:00:1d.0: reg 10: [mem 0xf7a17000-0xf7a173ff]
[    1.024863] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.024888] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    1.025015] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    1.025033] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    1.025041] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    1.025048] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    1.025056] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    1.025063] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    1.025071] pci 0000:00:1f.2: reg 24: [mem 0xf7a16000-0xf7a167ff]
[    1.025117] pci 0000:00:1f.2: PME# supported from D3hot
[    1.025134] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    1.025149] pci 0000:00:1f.3: reg 10: [mem 0xf7a15000-0xf7a150ff 64bit]
[    1.025171] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    1.025229] pci 0000:01:00.0: [10de:0fd1] type 00 class 0x030000
[    1.025240] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
[    1.025250] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    1.025261] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    1.025268] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    1.025275] pci 0000:01:00.0: reg 30: [mem 0xf7000000-0xf707ffff pref]
[    1.031381] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.031386] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    1.031404] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    1.031407] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    1.031453] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.031538] pci 0000:03:00.0: [8086:0887] type 00 class 0x028000
[    1.031576] pci 0000:03:00.0: reg 10: [mem 0xf7900000-0xf7901fff 64bit]
[    1.031760] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    1.039381] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    1.039402] pci 0000:00:1c.2:   bridge window [mem 0xf7900000-0xf79fffff]
[    1.039525] pci 0000:04:00.0: [10ec:5289] type 00 class 0xff0000
[    1.039587] pci 0000:04:00.0: reg 10: [mem 0xf7800000-0xf780ffff]
[    1.040098] pci 0000:04:00.0: supports D1 D2
[    1.040100] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    1.040270] pci 0000:04:00.2: [10ec:8168] type 00 class 0x020000
[    1.040332] pci 0000:04:00.2: reg 10: [io  0xd000-0xd0ff]
[    1.040443] pci 0000:04:00.2: reg 18: [mem 0xf2104000-0xf2104fff 64bit pref]
[    1.040508] pci 0000:04:00.2: reg 20: [mem 0xf2100000-0xf2103fff 64bit pref]
[    1.040810] pci 0000:04:00.2: supports D1 D2
[    1.040811] pci 0000:04:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.047438] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    1.047442] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    1.047445] pci 0000:00:1c.3:   bridge window [mem 0xf7800000-0xf78fffff]
[    1.047451] pci 0000:00:1c.3:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    1.047470] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.047582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.047614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.047642] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.047674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    1.047777]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.047866]  pci0000:00: ACPI _OSC control (0x1d) granted
[    1.051458] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.051498] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.051535] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    1.051570] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.051606] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.051642] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.051679] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.051717] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 10 11 12 14 15)
[    1.051788] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.051795] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    1.051796] vgaarb: loaded
[    1.051797] vgaarb: bridge control possible 0000:01:00.0
[    1.051798] vgaarb: no bridge control possible 0000:00:02.0
[    1.051920] SCSI subsystem initialized
[    1.051952] libata version 3.00 loaded.
[    1.051967] ACPI: bus type usb registered
[    1.051980] usbcore: registered new interface driver usbfs
[    1.051986] usbcore: registered new interface driver hub
[    1.052000] usbcore: registered new device driver usb
[    1.052049] PCI: Using ACPI for IRQ routing
[    1.053630] PCI: pci_cache_line_size set to 64 bytes
[    1.053692] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    1.053694] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.053695] e820: reserve RAM buffer [mem 0xc99da000-0xcbffffff]
[    1.053698] e820: reserve RAM buffer [mem 0xca1d5000-0xcbffffff]
[    1.053700] e820: reserve RAM buffer [mem 0xca69f000-0xcbffffff]
[    1.053702] e820: reserve RAM buffer [mem 0xcadf5000-0xcbffffff]
[    1.053704] e820: reserve RAM buffer [mem 0xcb000000-0xcbffffff]
[    1.053705] e820: reserve RAM buffer [mem 0x22f600000-0x22fffffff]
[    1.053774] NetLabel: Initializing
[    1.053775] NetLabel:  domain hash size = 128
[    1.053776] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.053784] NetLabel:  unlabeled traffic allowed by default
[    1.053828] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.053833] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.055846] Switching to clocksource hpet
[    1.060537] AppArmor: AppArmor Filesystem Enabled
[    1.060552] pnp: PnP ACPI init
[    1.060561] ACPI: bus type pnp registered
[    1.060778] pnp 00:00: [bus 00-3e]
[    1.060780] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.060781] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.060783] pnp 00:00: [io  0x0d00-0xffff window]
[    1.060784] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.060786] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.060787] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.060789] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.060790] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.060791] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.060793] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.060794] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.060795] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.060797] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.060798] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.060800] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.060801] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.060802] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.060804] pnp 00:00: [mem 0xcfa00000-0xfeafffff window]
[    1.060805] pnp 00:00: [mem 0x00010000-0x0001ffff window]
[    1.060850] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.060869] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    1.060896] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    1.060899] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.060908] pnp 00:02: [io  0x0000-0x001f]
[    1.060910] pnp 00:02: [io  0x0081-0x0091]
[    1.060911] pnp 00:02: [io  0x0093-0x009f]
[    1.060912] pnp 00:02: [io  0x00c0-0x00df]
[    1.060914] pnp 00:02: [dma 4]
[    1.060928] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.060934] pnp 00:03: [mem 0xff000000-0xffffffff]
[    1.060947] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    1.061007] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    1.061023] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.061033] pnp 00:05: [io  0x002e-0x002f]
[    1.061034] pnp 00:05: [io  0x004e-0x004f]
[    1.061036] pnp 00:05: [io  0x0061]
[    1.061037] pnp 00:05: [io  0x0063]
[    1.061038] pnp 00:05: [io  0x0065]
[    1.061039] pnp 00:05: [io  0x0067]
[    1.061040] pnp 00:05: [io  0x0070]
[    1.061042] pnp 00:05: [io  0x0080]
[    1.061043] pnp 00:05: [io  0x0092]
[    1.061044] pnp 00:05: [io  0x00b2-0x00b3]
[    1.061045] pnp 00:05: [io  0x0680-0x069f]
[    1.061047] pnp 00:05: [io  0x0200-0x020f]
[    1.061048] pnp 00:05: [io  0xffff]
[    1.061049] pnp 00:05: [io  0xffff]
[    1.061051] pnp 00:05: [io  0x0400-0x0453]
[    1.061053] pnp 00:05: [io  0x0458-0x047f]
[    1.061054] pnp 00:05: [io  0x0500-0x057f]
[    1.061055] pnp 00:05: [io  0x164e-0x164f]
[    1.061084] system 00:05: [io  0x0680-0x069f] has been reserved
[    1.061086] system 00:05: [io  0x0200-0x020f] has been reserved
[    1.061087] system 00:05: [io  0xffff] has been reserved
[    1.061089] system 00:05: [io  0xffff] has been reserved
[    1.061091] system 00:05: [io  0x0400-0x0453] has been reserved
[    1.061092] system 00:05: [io  0x0458-0x047f] has been reserved
[    1.061094] system 00:05: [io  0x0500-0x057f] has been reserved
[    1.061095] system 00:05: [io  0x164e-0x164f] has been reserved
[    1.061097] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.061105] pnp 00:06: [io  0x0070-0x0077]
[    1.061113] pnp 00:06: [irq 8]
[    1.061129] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.061149] pnp 00:07: [io  0x0454-0x0457]
[    1.061173] system 00:07: [io  0x0454-0x0457] has been reserved
[    1.061175] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.061193] pnp 00:08: [io  0x0010-0x001f]
[    1.061195] pnp 00:08: [io  0x0022-0x003f]
[    1.061196] pnp 00:08: [io  0x0044-0x005f]
[    1.061197] pnp 00:08: [io  0x0072-0x007f]
[    1.061198] pnp 00:08: [io  0x0080]
[    1.061199] pnp 00:08: [io  0x0084-0x0086]
[    1.061201] pnp 00:08: [io  0x0088]
[    1.061202] pnp 00:08: [io  0x008c-0x008e]
[    1.061203] pnp 00:08: [io  0x0090-0x009f]
[    1.061204] pnp 00:08: [io  0x00a2-0x00bf]
[    1.061206] pnp 00:08: [io  0x00e0-0x00ef]
[    1.061207] pnp 00:08: [io  0x04d0-0x04d1]
[    1.061235] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    1.061237] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.061243] pnp 00:09: [io  0x00f0-0x00ff]
[    1.061248] pnp 00:09: [irq 13]
[    1.061263] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.061274] pnp 00:0a: [io  0x0060]
[    1.061275] pnp 00:0a: [io  0x0064]
[    1.061279] pnp 00:0a: [irq 1]
[    1.061295] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.061323] pnp 00:0b: [io  0x0060]
[    1.061324] pnp 00:0b: [io  0x0064]
[    1.061328] pnp 00:0b: [irq 12]
[    1.061346] pnp 00:0b: Plug and Play ACPI device, IDs ETD0403 PNP0f13 (active)
[    1.062287] pnp 00:0c: [mem 0xfed1c000-0xfed1ffff]
[    1.062289] pnp 00:0c: [mem 0xfed10000-0xfed17fff]
[    1.062290] pnp 00:0c: [mem 0xfed18000-0xfed18fff]
[    1.062291] pnp 00:0c: [mem 0xfed19000-0xfed19fff]
[    1.062293] pnp 00:0c: [mem 0xf8000000-0xfbffffff]
[    1.062294] pnp 00:0c: [mem 0xfed20000-0xfed3ffff]
[    1.062295] pnp 00:0c: [mem 0xfed90000-0xfed93fff]
[    1.062296] pnp 00:0c: [mem 0xfed45000-0xfed8ffff]
[    1.062298] pnp 00:0c: [mem 0xff000000-0xffffffff]
[    1.062299] pnp 00:0c: [mem 0xfee00000-0xfeefffff]
[    1.062300] pnp 00:0c: [mem 0xcfa00000-0xcfa00fff]
[    1.062345] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.062346] system 00:0c: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.062348] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.062350] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.062352] system 00:0c: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.062353] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.062355] system 00:0c: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.062357] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.062358] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    1.062360] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.062362] system 00:0c: [mem 0xcfa00000-0xcfa00fff] has been reserved
[    1.062364] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.062685] pnp 00:0d: [mem 0x20000000-0x201fffff]
[    1.062686] pnp 00:0d: [mem 0x40000000-0x401fffff]
[    1.062738] system 00:0d: [mem 0x20000000-0x201fffff] has been reserved
[    1.062740] system 00:0d: [mem 0x40000000-0x401fffff] could not be reserved
[    1.062742] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.062756] pnp: PnP ACPI: found 14 devices
[    1.062757] ACPI: ACPI bus type pnp unregistered
[    1.068627] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    1.068630] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    1.068632] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    1.068635] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    1.068638] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.068649] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    1.068654] pci 0000:00:1c.2:   bridge window [mem 0xf7900000-0xf79fffff]
[    1.068662] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    1.068665] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    1.068669] pci 0000:00:1c.3:   bridge window [mem 0xf7800000-0xf78fffff]
[    1.068673] pci 0000:00:1c.3:   bridge window [mem 0xf2100000-0xf21fffff 64bit pref]
[    1.068706] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.068707] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.068709] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.068710] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.068712] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.068713] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.068715] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    1.068716] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    1.068718] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    1.068719] pci_bus 0000:00: resource 13 [mem 0xcfa00000-0xfeafffff]
[    1.068721] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    1.068722] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    1.068724] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    1.068726] pci_bus 0000:03: resource 1 [mem 0xf7900000-0xf79fffff]
[    1.068727] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    1.068729] pci_bus 0000:04: resource 1 [mem 0xf7800000-0xf78fffff]
[    1.068730] pci_bus 0000:04: resource 2 [mem 0xf2100000-0xf21fffff 64bit pref]
[    1.068753] NET: Registered protocol family 2
[    1.068895] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.069483] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.070538] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.070659] TCP: Hash tables configured (established 524288 bind 65536)
[    1.070661] TCP: reno registered
[    1.070671] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.070696] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.070763] NET: Registered protocol family 1
[    1.070778] pci 0000:00:02.0: Boot video device
[    1.107842] PCI: CLS 64 bytes, default 64
[    1.107844] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.107846] software IO TLB [mem 0xc59da000-0xc99d9fff] (64MB) mapped at [ffff8800c59da000-ffff8800c99d9fff]
[    1.108357] audit: initializing netlink socket (disabled)
[    1.108364] type=2000 audit(1353603285.996:1): initialized
[    1.129884] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.131317] VFS: Disk quotas dquot_6.5.2
[    1.131348] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.131705] fuse init (API version 7.19)
[    1.131771] msgmni has been set to 15752
[    1.132035] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.132055] io scheduler noop registered
[    1.132056] io scheduler deadline registered (default)
[    1.132075] io scheduler cfq registered
[    1.132155] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.132239] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.132340] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    1.132438] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    1.132509] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    1.132511] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.132514] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    1.132529] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    1.132533] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    1.132547] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    1.132548] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    1.132552] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    1.132566] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    1.132567] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    1.132569] pci 0000:04:00.2: Signaling PME through PCIe PME interrupt
[    1.132572] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    1.132581] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.132595] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.132628] intel_idle: MWAIT substates: 0x21120
[    1.132629] intel_idle: v0.4 model 0x3A
[    1.132630] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.135221] ACPI: AC Adapter [AC] (on-line)
[    1.135283] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.135287] ACPI: Power Button [PWRB]
[    1.135312] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.135314] ACPI: Sleep Button [SLPB]
[    1.135341] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.152184] ACPI: Lid Switch [LID0]
[    1.152212] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.152214] ACPI: Power Button [PWRF]
[    1.152274] ACPI: Requesting acpi_cpufreq
[    1.157119] thermal LNXTHERM:00: registered as thermal_zone0
[    1.157121] ACPI: Thermal Zone [TZ0] (65 C)
[    1.157137] ACPI: Battery Slot [BAT] (battery present)
[    1.157171] GHES: HEST is not enabled!
[    1.157218] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.161979] Linux agpgart interface v0.103
[    1.162956] brd: module loaded
[    1.163495] loop: module loaded
[    1.163563] ahci 0000:00:1f.2: version 3.0
[    1.163613] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.169581] ACPI: Battery Slot [BAT] (battery present)
[    1.175789] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x17 impl SATA mode
[    1.175792] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst
[    1.175796] ahci 0000:00:1f.2: setting latency timer to 64
[    1.200049] scsi0 : ahci
[    1.200102] scsi1 : ahci
[    1.200146] scsi2 : ahci
[    1.200188] scsi3 : ahci
[    1.200227] scsi4 : ahci
[    1.200268] scsi5 : ahci
[    1.200502] ata1: SATA max UDMA/133 abar m2048@0xf7a16000 port 0xf7a16100 irq 44
[    1.200504] ata2: SATA max UDMA/133 abar m2048@0xf7a16000 port 0xf7a16180 irq 44
[    1.200506] ata3: SATA max UDMA/133 abar m2048@0xf7a16000 port 0xf7a16200 irq 44
[    1.200507] ata4: DUMMY
[    1.200508] ata5: SATA max UDMA/133 abar m2048@0xf7a16000 port 0xf7a16300 irq 44
[    1.200509] ata6: DUMMY
[    1.200695] Fixed MDIO Bus: probed
[    1.200724] tun: Universal TUN/TAP device driver, 1.6
[    1.200725] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.200757] PPP generic driver version 2.4.2
[    1.200788] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.200814] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.200816] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.200822] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.200845] ehci_hcd 0000:00:1a.0: debug port 2
[    1.204722] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.204733] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7a18000
[    1.215733] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.215767] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.215769] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.215771] usb usb1: Product: EHCI Host Controller
[    1.215772] usb usb1: Manufacturer: Linux 3.5.0-18-generic ehci_hcd
[    1.215774] usb usb1: SerialNumber: 0000:00:1a.0
[    1.215852] hub 1-0:1.0: USB hub found
[    1.215856] hub 1-0:1.0: 2 ports detected
[    1.215907] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.215910] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.215914] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.215931] ehci_hcd 0000:00:1d.0: debug port 2
[    1.219820] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.219831] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7a17000
[    1.231727] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.231756] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.231757] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.231759] usb usb2: Product: EHCI Host Controller
[    1.231760] usb usb2: Manufacturer: Linux 3.5.0-18-generic ehci_hcd
[    1.231762] usb usb2: SerialNumber: 0000:00:1d.0
[    1.231830] hub 2-0:1.0: USB hub found
[    1.231832] hub 2-0:1.0: 2 ports detected
[    1.231871] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.231881] uhci_hcd: USB Universal Host Controller Interface driver
[    1.231918] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.231921] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.231924] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.232000] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.232005] xhci_hcd 0000:00:14.0: irq 16, io mem 0xf7a00000
[    1.232046] xhci_hcd 0000:00:14.0: irq 45 for MSI/MSI-X
[    1.232086] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.232088] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.232089] usb usb3: Product: xHCI Host Controller
[    1.232091] usb usb3: Manufacturer: Linux 3.5.0-18-generic xhci_hcd
[    1.232092] usb usb3: SerialNumber: 0000:00:14.0
[    1.232146] xHCI xhci_add_endpoint called for root hub
[    1.232147] xHCI xhci_check_bandwidth called for root hub
[    1.232163] hub 3-0:1.0: USB hub found
[    1.232169] hub 3-0:1.0: 4 ports detected
[    1.232209] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.232212] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.232228] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.232229] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.232231] usb usb4: Product: xHCI Host Controller
[    1.232232] usb usb4: Manufacturer: Linux 3.5.0-18-generic xhci_hcd
[    1.232233] usb usb4: SerialNumber: 0000:00:14.0
[    1.232281] xHCI xhci_add_endpoint called for root hub
[    1.232282] xHCI xhci_check_bandwidth called for root hub
[    1.232297] hub 4-0:1.0: USB hub found
[    1.232303] hub 4-0:1.0: 4 ports detected
[    1.232392] usbcore: registered new interface driver libusual
[    1.232421] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:ELNM] at 0x60,0x64 irq 1,12
[    1.237113] i8042: Detected active multiplexing controller, rev 1.1
[    1.238582] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.238586] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.238592] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.238594] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.238595] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.238697] mousedev: PS/2 mouse device common for all mice
[    1.238924] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.238957] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.239010] device-mapper: uevent: version 1.0.3
[    1.239055] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.239165] cpuidle: using governor ladder
[    1.239316] cpuidle: using governor menu
[    1.239317] EFI Variables Facility v0.08 2004-May-17
[    1.239476] ashmem: initialized
[    1.239564] TCP: cubic registered
[    1.239641] NET: Registered protocol family 10
[    1.239794] NET: Registered protocol family 17
[    1.239809] Key type dns_resolver registered
[    1.239985] PM: Hibernation image not present or could not be loaded.
[    1.239993] registered taskstats version 1
[    1.240907] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.242439] Key type trusted registered
[    1.244654] Key type encrypted registered
[    1.247155]   Magic number: 4:273:945
[    1.247175] tty tty2: hash matches
[    1.247198] cpu cpu0: hash matches
[    1.247274] rtc_cmos 00:06: setting system clock to 2012-11-22 16:54:46 UTC (1353603286)
[    1.248440] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.248441] EDD information not available.
[    1.519611] ata5: SATA link down (SStatus 0 SControl 300)
[    1.519644] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.519691] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.519725] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.520212] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.520215] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.520216] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.520619] ata2.00: ATA-9: M4-CT128M4SSD2, 000F, max UDMA/100
[    1.520625] ata2.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.521194] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.521196] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.521198] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.521723] ata2.00: configured for UDMA/100
[    1.521877] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.521883] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.521886] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.523456] ata3.00: ATAPI: Optiarc DVD RW AD-7740H, 1.00, max UDMA/100
[    1.526034] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.526037] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.526039] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.526093] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.526095] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.526097] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.527599] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.527615] ata3.00: configured for UDMA/100
[    1.532407] ata1.00: ATA-8: ST1000LM024 HN-M101MBB, 2AR10002, max UDMA/133
[    1.532409] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.538831] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.538838] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.538842] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.545118] ata1.00: configured for UDMA/133
[    1.545362] scsi 0:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 2AR1 PQ: 0 ANSI: 5
[    1.545493] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.545534] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.545675] sd 0:0:0:0: [sda] Write Protect is off
[    1.545678] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.545794] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.601698]  sda: sda1 sda2 sda3 < sda5 >
[    1.602843] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.603055] scsi 1:0:0:0: Direct-Access     ATA      M4-CT128M4SSD2   000F PQ: 0 ANSI: 5
[    1.603167] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.603233] sd 1:0:0:0: [sdb] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    1.603451] sd 1:0:0:0: [sdb] Write Protect is off
[    1.603453] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.603507] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.604651]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    1.605294] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.605862] scsi 2:0:0:0: CD-ROM            Optiarc  DVD RW AD-7740H  1.00 PQ: 0 ANSI: 5
[    1.607830] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.607833] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.607941] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.607994] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    1.609073] Freeing unused kernel memory: 928k freed
[    1.609149] Write protecting the kernel read-only data: 12288k
[    1.611880] Freeing unused kernel memory: 1464k freed
[    1.613999] Freeing unused kernel memory: 1120k freed
[    1.624598] udevd[133]: starting version 175
[    1.644587] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.644746] r8169 0000:04:00.2: irq 46 for MSI/MSI-X
[    1.644905] r8169 0000:04:00.2: eth0: RTL8411 at 0xffffc90000c7e000, 00:90:f5:d2:ca:8c, XID 08800800 IRQ 46
[    1.644908] r8169 0000:04:00.2: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.658741] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    1.658743] EXT4-fs (sdb1): write access will be enabled during recovery
[    1.659920] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.659927] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.660196] hub 1-1:1.0: USB hub found
[    1.660284] hub 1-1:1.0: 6 ports detected
[    1.771465] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.776351] EXT4-fs (sdb1): recovery complete
[    1.781902] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    1.903796] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.903802] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.904065] hub 2-1:1.0: USB hub found
[    1.904158] hub 2-1:1.0: 6 ports detected
[    2.071314] usb 3-2: new low-speed USB device number 2 using xhci_hcd
[    2.092827] usb 3-2: New USB device found, idVendor=045e, idProduct=00a4
[    2.092832] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.092835] usb 3-2: Product: Microsoft(R) Compact Optical Mouse
[    2.092838] usb 3-2: Manufacturer: Microsoft
[    2.093103] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.107277] Refined TSC clocksource calibration: 2294.786 MHz.
[    2.107283] Switching to clocksource tsc
[    2.175425] usb 2-1.5: new full-speed USB device number 3 using ehci_hcd
[    2.268399] usb 2-1.5: New USB device found, idVendor=147e, idProduct=1002
[    2.268405] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.268408] usb 2-1.5: Product: TouchStrip Fingerprint Sensor     
[    2.268424] usb 2-1.5: Manufacturer: UPEK
[    2.339320] usb 2-1.6: new high-speed USB device number 4 using ehci_hcd
[    2.496339] Adding 9764860k swap on /dev/sdb5.  Priority:-1 extents:1 across:9764860k SS
[    2.498227] usb 2-1.6: New USB device found, idVendor=5986, idProduct=0308
[    2.498229] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.498231] usb 2-1.6: Product: BisonCam, NB Pro
[    2.498232] usb 2-1.6: Manufacturer: BisonCam, NB Pro
[    2.500784] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.503389] udevd[395]: starting version 175
[    2.508489] lp: driver loaded but no devices found
[    2.520845] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    2.525043] [drm] Initialized drm 1.1.0 20060810
[    2.528422] mei 0000:00:16.0: setting latency timer to 64
[    2.528480] mei 0000:00:16.0: irq 47 for MSI/MSI-X
[    2.543741] wmi: Mapper loaded
[    2.545129] mei 0000:00:16.0: wd: failed to find the client
[    2.545441] i915 0000:00:02.0: setting latency timer to 64
[    2.547062] pci 0000:00:00.0: Intel Ivybridge Chipset
[    2.547155] pci 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    2.548231] pci 0000:00:00.0: detected 65536K stolen memory
[    2.548953] type=1400 audit(1353603287.796:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=582 comm="apparmor_parser"
[    2.549261] type=1400 audit(1353603287.796:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=582 comm="apparmor_parser"
[    2.549436] type=1400 audit(1353603287.796:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=582 comm="apparmor_parser"
[    2.552424] cfg80211: Calling CRDA to update world regulatory domain
[    2.559537] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    2.559540] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[    2.560623] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    2.560625] iwlwifi 0000:03:00.0: pci_resource_base = ffffc90005a28000
[    2.560627] iwlwifi 0000:03:00.0: HW Revision ID = 0xC4
[    2.560703] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
[    2.568801] Linux video capture interface: v2.00
[    2.569766] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0308)
[    2.574010] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input5
[    2.574069] usbcore: registered new interface driver uvcvideo
[    2.574071] USB Video Class driver (1.1.1)
[    2.579580] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
[    2.581867] usbcore: registered new interface driver usbhid
[    2.581870] usbhid: USB HID core driver
[    2.584680] i915 0000:00:02.0: irq 49 for MSI/MSI-X
[    2.584687] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    2.584687] [drm] Driver supports precise vblank timestamp query.
[    2.585287] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    2.585288] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[    2.594493] device-mapper: multipath: version 1.4.0 loaded
[    2.613735] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[    2.613924] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.613926] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.613927] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.613928] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    2.613929] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[    2.613930] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[    2.613982] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    2.616094] cfg80211: World regulatory domain updated:
[    2.616096] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    2.616097] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.616098] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.616099] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.616100] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.616101] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.618802] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
[    2.619263] input: Microsoft Microsoft(R) Compact Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input6
[    2.619394] hid-generic 0003:045E:00A4.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft(R) Compact Optical Mouse] on usb-0000:00:14.0-2/input0
[    2.622619] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
[    2.624052] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
[    2.625533] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x12
[    2.626502] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x12
[    2.627626] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x12
[    2.628623] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x12
[    2.629856] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    2.630555] iwlwifi 0000:03:00.0: device EEPROM VER=0x81c, CALIB=0x6
[    2.630557] iwlwifi 0000:03:00.0: Device SKU: 0x150
[    2.630559] iwlwifi 0000:03:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[    2.630575] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    2.630621] Registered led device: phy0-led
[    2.630641] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    2.632501] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    2.634106] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.639357] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[    2.654511] init: failsafe main process (907) killed by TERM signal
[    2.666500] ppdev: user-space parallel port driver
[    2.668767] Bluetooth: Core ver 2.16
[    2.668784] NET: Registered protocol family 31
[    2.668786] Bluetooth: HCI device and connection manager initialized
[    2.668787] Bluetooth: HCI socket layer initialized
[    2.668788] Bluetooth: L2CAP socket layer initialized
[    2.668793] Bluetooth: SCO socket layer initialized
[    2.671269] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.671272] Bluetooth: BNEP filters: protocol multicast
[    2.673533] Bluetooth: RFCOMM TTY layer initialized
[    2.673538] Bluetooth: RFCOMM socket layer initialized
[    2.673539] Bluetooth: RFCOMM ver 1.11
[    2.681696] type=1400 audit(1353603287.928:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=995 comm="apparmor_parser"
[    2.681994] type=1400 audit(1353603287.928:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=995 comm="apparmor_parser"
[    2.691889] type=1400 audit(1353603287.940:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1022 comm="apparmor_parser"
[    2.692138] type=1400 audit(1353603287.940:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1021 comm="apparmor_parser"
[    2.692215] type=1400 audit(1353603287.940:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1022 comm="apparmor_parser"
[    2.692392] type=1400 audit(1353603287.940:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1021 comm="apparmor_parser"
[    2.730663] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    2.738229] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[    2.817502] init: alsa-restore main process (1088) terminated with status 19
[    2.894466] bbswitch: version 0.4.2
[    2.894473] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.894481] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[    2.894544] bbswitch: detected an Optimus _DSM function
[    2.894550] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    2.895792] bbswitch: disabling discrete graphics
[    2.895927] bbswitch: Result of Optimus _DSM call: 11000059
[    3.007553] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    3.015114] iwlwifi 0000:03:00.0: Radio type=0x2-0x0-0x0
[    3.094831] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.095048] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.101633] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[    3.171913] r8169 0000:04:00.2: eth0: link down
[    3.172489] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.229064] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.265215] psmouse serio2: elantech: assuming hardware version 3 (with firmware version 0x250f01)
[    3.362437] psmouse serio2: elantech: Synaptics capabilities query result 0x18, 0x17, 0x0b.
[    3.372613] fbcon: inteldrmfb (fb0) is primary device
[    3.372691] Console: switching to colour frame buffer device 240x67
[    3.372714] fb0: inteldrmfb frame buffer device
[    3.372714] drm: registered panic notifier
[    3.372756] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    3.372780] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    3.372811] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input7
[    3.463946] acpi device:4d: registered as cooling_device8
[    3.463991] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.464047] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[    3.464180] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.464228] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    3.464235] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.464237] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    3.464239] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    3.464243] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.464247] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[    3.464249] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20120320/utaddress-251)
[    3.464253] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    3.464255] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    3.464349] snd_hda_intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[    3.475542] init: gdm main process (1363) killed by TERM signal
[    3.484045] init: plymouth-splash main process (1377) terminated with status 1
[    3.684875] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio2/input/input9
[    3.764653] init: lightdm main process (1366) terminated with status 1
[    4.012110] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    4.012245] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    4.012351] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    4.012460] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    4.012588] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    4.149924] wlan0: authenticate with 24:65:11:02:fe:b2
[    4.160859] wlan0: send auth to 24:65:11:02:fe:b2 (try 1/3)
[    4.178720] wlan0: authenticated
[    4.182332] wlan0: associate with 24:65:11:02:fe:b2 (try 1/3)
[    4.188938] wlan0: RX AssocResp from 24:65:11:02:fe:b2 (capab=0x431 status=0 aid=3)
[    4.190551] wlan0: associated
[    4.191025] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    4.191106] cfg80211: Calling CRDA for country: DE
[    4.193556] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[    4.193558] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193560] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[    4.193562] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193563] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[    4.193565] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193566] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[    4.193568] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193569] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[    4.193571] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193572] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[    4.193574] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193575] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[    4.193577] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193578] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[    4.193580] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193581] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[    4.193583] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193584] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[    4.193586] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193587] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[    4.193589] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193590] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[    4.193592] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193593] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[    4.193595] cfg80211: 2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[    4.193597] cfg80211: Regulatory domain changed to country: DE
[    4.193598] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    4.193600] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    4.193601] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    4.193603] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    4.193604] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[    4.390418] pci 0000:01:00.0: power state changed by ACPI to D3
[   18.770124] init: failsafe-x main process (1390) terminated with status 1
```

... and /var/log/syslog is here:
[http://ubuntuone.com/3BbMU2qJgz1M4GiKQyzNd5](http://ubuntuone.com/3BbMU2qJgz1M4GiKQyzNd5)

I used to get a lot of this:
Nov 22 17:35:00 HERMES kernel: [    8.161748] init: bumblebeed main process (1782) terminated with status 1
Nov 22 17:35:00 HERMES kernel: [    8.161771] init: bumblebeed main process ended, respawning
but then I reinstalled
bbswitch-dkms, bumblebee and bumblebee-nvidia (apparently, there was some error with bbswitch-dkms for ubuntu 12.10) and now it's not giving me that error any more.
I also tried purging xorg-edgers, but it won't let me do that any more.

Is there a way how I can find out what exactly is going wrong? Or can someone tell from the logs above?

Thanks...

---

