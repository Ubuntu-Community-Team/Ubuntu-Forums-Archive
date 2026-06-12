---
title: "ASUS M2N32-SLI Deluxe 4GB, 7.04 only 3GB recognizes"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by parcival39 on 2007-04-30
Hi,
I have here Ubuntu 32bit 7.04.

Hardware: ASUS M2N32-SLI Deluxe 4GB

Ubuntu recognizes only 3GB. Is there a possibility that the complete 4GB is recognized?

Thanks for each assistance.

Stefan

Info:
message.log
Apr 30 10:22:26 ubuntu syslogd 1.4.1#20ubuntu4: restart.
Apr 30 10:22:26 ubuntu kernel: Inspecting /boot/System.map-2.6.20-15-generic
Apr 30 10:22:27 ubuntu kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
Apr 30 10:22:27 ubuntu kernel: Symbols match kernel version 2.6.20.
Apr 30 10:22:27 ubuntu kernel: No module symbols loaded - kernel modules not enabled. 
Apr 30 10:22:27 ubuntu kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
Apr 30 10:22:27 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 30 10:22:27 ubuntu kernel: [    0.000000] sanitize start
Apr 30 10:22:27 ubuntu kernel: [    0.000000] sanitize end
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 00000000bfde0000 end: 00000000bfee0000 type: 1
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000bfee0000 size: 0000000000003000 end: 00000000bfee3000 type: 4
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000bfee3000 size: 000000000000d000 end: 00000000bfef0000 type: 3
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000bfef0000 size: 0000000000010000 end: 00000000bff00000 type: 2
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000f0000000 size: 0000000004000000 end: 00000000f4000000 type: 2
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() start: 0000000100000000 size: 0000000040000000 end: 0000000140000000 type: 1
Apr 30 10:22:27 ubuntu kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfee0000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bfef0000 - 00000000bff00000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 0000000000000000 - 000000000009f000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 00000000000f0000 - 0000000000100000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 0000000000100000 - 00000000bfee0000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 00000000bfef0000 - 00000000bff00000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 00000000f0000000 - 00000000f4000000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 00000000fec00000 - 0000000100000000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions start: 0000000100000000 - 0000000140000000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions endfor: 0000000000000000 - 000000000009f000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions endfor: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions endfor: 00000000000f0000 - 0000000000100000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions endfor: 0000000000100000 - 00000000bfee0000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions endfor: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions endfor: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions endfor: 00000000bfef0000 - 00000000bff00000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions endfor: 00000000f0000000 - 00000000f4000000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  limit_regions endfor: 00000000fec00000 - 0000000100000000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000] user-defined physical RAM map:
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  user: 0000000000000000 - 000000000009f000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  user: 000000000009f000 - 00000000000a0000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  user: 00000000000f0000 - 0000000000100000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  user: 0000000000100000 - 00000000bfee0000 (usable)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  user: 00000000bfee0000 - 00000000bfee3000 (ACPI NVS)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  user: 00000000bfee3000 - 00000000bfef0000 (ACPI data)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  user: 00000000bfef0000 - 00000000bff00000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  user: 00000000f0000000 - 00000000f4000000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000]  user: 00000000fec00000 - 0000000100000000 (reserved)
Apr 30 10:22:27 ubuntu kernel: [    0.000000] 2174MB HIGHMEM available.
Apr 30 10:22:27 ubuntu kernel: [    0.000000] 896MB LOWMEM available.
Apr 30 10:22:27 ubuntu kernel: [    0.000000] found SMP MP-table at 000f5fa0
Apr 30 10:22:27 ubuntu kernel: [    0.000000] Zone PFN ranges:
Apr 30 10:22:27 ubuntu kernel: [    0.000000]   DMA             0 ->     4096
Apr 30 10:22:27 ubuntu kernel: [    0.000000]   Normal       4096 ->   229376
Apr 30 10:22:27 ubuntu kernel: [    0.000000]   HighMem    229376 ->   786144
Apr 30 10:22:27 ubuntu kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 30 10:22:27 ubuntu kernel: [    0.000000]     0:        0 ->   786144

---

### Post by RawMustard on 2007-04-30
Any 32bit operating system can only see 3 gig of ram, if you want to use more, you need to install a 64bit system on hardware that supports it.

---

### Post by parcival39 on 2007-04-30
hmm,

I thinks the kernel is compiled with PAE.

```
CONFIG_HIGHMEM4G=y
```

Help PAE with this problem not?

thx

Stefan

---

### Post by brimbleshoes on 2007-05-02
I have the same problem... its a dell optiplex 745 -- 4GB memory

Is there a kernel package with that parameter set?  I have a hard time believing that someone else hasn't had this problem...

CONFIG_HIGHMEM4G=y

or

CONFIG_HIGHMEM64G=y


anyone?

---

### Post by brimbleshoes on 2007-05-02
ok...

so the 
linux-image-server-bigiron
linux-image-server

both have support for over 3G of memory -- but no restricted modules for fglrx!

grrr....

---

### Post by brimbleshoes on 2007-05-02
So I need to recompile the generic kernel with support for over 3G of memory turned on...

Never done it before ... anyone that can help?  Or maybe there is already one built...?

thanks in advance

tom

---

