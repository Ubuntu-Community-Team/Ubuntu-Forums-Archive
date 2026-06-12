---
title: "Problems getting new GFX card to run. Trying to find info in the bootlog, help?"
date: 2020-03-16
forum: Installation &amp; Upgrades
---

### Post by mykle-law on 2020-03-16
[COLOR=#1C1E21][FONT=&quot]How far into things from turning on the computer does the linux bootlog begin recording information?




if I get to a bootloader, does that indicate a boot record should have been created already, or is that just right after posting, before any boot information is stored and recorded?



[/FONT][/COLOR]

---

### Post by TheFu on 2020-03-18
From the manpage:
```
       journalctl may be used to query the contents of the systemd(1) journal as written by systemd-journald.service(8).

       If called without parameters, it will show the full contents of the journal, starting with the oldest entry collected.

```

And dmesg shows everything from the boot:
```
$ dmesg 
[    0.000000] Linux version 4.15.0-88-generic (buildd@lcy01-amd64-026) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.12))
 #88~16.04.1-Ubuntu SMP Wed Feb 12 04:18:19 UTC 2020 (Ubuntu 4.15.0-88.88~16.04.1-generic 4.15.18)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] x86/fpu: x87 FPU will use FXSAVE
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000dfffdfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dfffe000-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feffc000-0x00000000feffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fffc0000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000011fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: Bochs Bochs, BIOS Bochs 01/01/2011
[    0.000000] Hypervisor detected: KVM
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x120000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
...

```
So, it appears that just after the kernel gets loaded, instruction pointer set to zero and "run" is invoked.

---

