---
title: "Very slow boot up after upgrade to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by specialblend on 2011-10-15
After I select ubuntu in my grub menu, my keyboard and mouse turn off and I get a purple screen.  The purple screen lasts about a minute and once I get to the login screen, I have to wait another minute for my keyboard and mouse to come back to life.

Can anyone help me decipher my dmesg output?

```
[    0.185295] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.185297] system 00:01: [io  0x0800-0x0805] has been reserved
[    0.185299] system 00:01: [io  0x0290-0x0294] has been reserved
[    0.185301] system 00:01: [io  0x0880-0x088f] has been reserved
[    0.185303] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.185312] pnp 00:02: [dma 4]
[    0.185313] pnp 00:02: [io  0x0000-0x000f]
[    0.185314] pnp 00:02: [io  0x0080-0x0090]
[    0.185316] pnp 00:02: [io  0x0094-0x009f]
[    0.185317] pnp 00:02: [io  0x00c0-0x00df]
[    0.185338] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.185373] pnp 00:03: [irq 0 disabled]
[    0.185381] pnp 00:03: [irq 8]
[    0.185382] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    0.185403] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.185422] pnp 00:04: [io  0x0070-0x0073]
[    0.185442] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.185448] pnp 00:05: [io  0x0061]
[    0.185469] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.185476] pnp 00:06: [io  0x00f0-0x00ff]
[    0.185480] pnp 00:06: [irq 13]
[    0.185502] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.185582] pnp 00:07: [io  0x03f0-0x03f5]
[    0.185584] pnp 00:07: [io  0x03f7]
[    0.185588] pnp 00:07: [irq 6]
[    0.185589] pnp 00:07: [dma 2]
[    0.185619] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.185735] pnp 00:08: [io  0x03f8-0x03ff]
[    0.185739] pnp 00:08: [irq 4]
[    0.185779] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.185902] pnp 00:09: [io  0x0378-0x037f]
[    0.185907] pnp 00:09: [irq 7]
[    0.185943] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.186029] pnp 00:0a: [io  0x0400-0x04cf]
[    0.186030] pnp 00:0a: [io  0x04d2-0x04ff]
[    0.186068] system 00:0a: [io  0x0400-0x04cf] has been reserved
[    0.186070] system 00:0a: [io  0x04d2-0x04ff] has been reserved
[    0.186072] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.186198] pnp 00:0b: [mem 0xf4000000-0xf7ffffff]
[    0.186239] system 00:0b: [mem 0xf4000000-0xf7ffffff] has been reserved
[    0.186242] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.186341] pnp 00:0c: [mem 0x000d3000-0x000d3fff]
[    0.186343] pnp 00:0c: [mem 0x000f0000-0x000f7fff]
[    0.186344] pnp 00:0c: [mem 0x000f8000-0x000fbfff]
[    0.186345] pnp 00:0c: [mem 0x000fc000-0x000fffff]
[    0.186347] pnp 00:0c: [mem 0xdfeb0000-0xdfefffff]
[    0.186348] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.186350] pnp 00:0c: [mem 0x00100000-0xdfeaffff]
[    0.186351] pnp 00:0c: [mem 0xfec00000-0xfec00fff]
[    0.186352] pnp 00:0c: [mem 0xfed10000-0xfed1dfff]
[    0.186354] pnp 00:0c: [mem 0xfed20000-0xfed8ffff]
[    0.186355] pnp 00:0c: [mem 0xfee00000-0xfee00fff]
[    0.186357] pnp 00:0c: [mem 0xffb00000-0xffb7ffff]
[    0.186358] pnp 00:0c: [mem 0xfff00000-0xffffffff]
[    0.186359] pnp 00:0c: [mem 0x000e0000-0x000effff]
[    0.186413] system 00:0c: [mem 0x000d3000-0x000d3fff] has been reserved
[    0.186415] system 00:0c: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.186417] system 00:0c: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.186419] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.186421] system 00:0c: [mem 0xdfeb0000-0xdfefffff] could not be reserved
[    0.186423] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.186425] system 00:0c: [mem 0x00100000-0xdfeaffff] could not be reserved
[    0.186427] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.186429] system 00:0c: [mem 0xfed10000-0xfed1dfff] has been reserved
[    0.186431] system 00:0c: [mem 0xfed20000-0xfed8ffff] could not be reserved
[    0.186433] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.186435] system 00:0c: [mem 0xffb00000-0xffb7ffff] has been reserved
[    0.186437] system 00:0c: [mem 0xfff00000-0xffffffff] has been reserved
[    0.186439] system 00:0c: [mem 0x000e0000-0x000effff] has been reserved
[    0.186441] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.186454] pnp 00:0d: [mem 0xffb80000-0xffbfffff]
[    0.186482] pnp 00:0d: Plug and Play ACPI device, IDs INT0800 (active)
[    0.186487] pnp: PnP ACPI: found 14 devices
[    0.186488] ACPI: ACPI bus type pnp unregistered
[    0.192073] PCI: max bus depth: 1 pci_try_num: 2
[    0.192111] pci 0000:00:1c.3: BAR 15: assigned [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.192114] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0200000-0xf03fffff]
[    0.192116] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.192119] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.192122] pci 0000:01:00.0: BAR 6: assigned [mem 0xfb000000-0xfb01ffff pref]
[    0.192124] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.192126] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.192128] pci 0000:00:01.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    0.192131] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.192134] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.192136] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.192140] pci 0000:00:1c.0:   bridge window [mem 0xf0200000-0xf03fffff]
[    0.192143] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.192147] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    0.192150] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.192153] pci 0000:00:1c.3:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.192156] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.192161] pci 0000:04:00.0: BAR 6: assigned [mem 0xfde00000-0xfde0ffff pref]
[    0.192163] pci 0000:00:1c.4: PCI bridge to [bus 04-04]
[    0.192165] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.192169] pci 0000:00:1c.4:   bridge window [mem 0xfd900000-0xfd9fffff]
[    0.192172] pci 0000:00:1c.4:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.192177] pci 0000:05:00.0: BAR 6: assigned [mem 0xfdc00000-0xfdc0ffff pref]
[    0.192179] pci 0000:00:1c.5: PCI bridge to [bus 05-05]
[    0.192181] pci 0000:00:1c.5:   bridge window [io  0xb000-0xbfff]
[    0.192184] pci 0000:00:1c.5:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.192187] pci 0000:00:1c.5:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.192192] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.192193] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.192197] pci 0000:00:1e.0:   bridge window [mem 0xfda00000-0xfdafffff]
[    0.192200] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.192216] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.192219] pci 0000:00:01.0: setting latency timer to 64
[    0.192223] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.192226] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.192230] pci 0000:00:1c.0: setting latency timer to 64
[    0.192237] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.192240] pci 0000:00:1c.3: setting latency timer to 64
[    0.192244] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.192247] pci 0000:00:1c.4: setting latency timer to 64
[    0.192253] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.192256] pci 0000:00:1c.5: setting latency timer to 64
[    0.192261] pci 0000:00:1e.0: setting latency timer to 64
[    0.192264] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.192265] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.192267] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.192269] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    0.192270] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    0.192272] pci_bus 0000:00: resource 9 [mem 0xdff00000-0xfebfffff]
[    0.192274] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.192275] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
[    0.192277] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.192279] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.192281] pci_bus 0000:02: resource 1 [mem 0xf0200000-0xf03fffff]
[    0.192282] pci_bus 0000:02: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.192284] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.192286] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.192287] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.192289] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.192291] pci_bus 0000:04: resource 1 [mem 0xfd900000-0xfd9fffff]
[    0.192293] pci_bus 0000:04: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
[    0.192294] pci_bus 0000:05: resource 0 [io  0xb000-0xbfff]
[    0.192296] pci_bus 0000:05: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.192298] pci_bus 0000:05: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    0.192299] pci_bus 0000:06: resource 1 [mem 0xfda00000-0xfdafffff]
[    0.192301] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.192303] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.192304] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.192306] pci_bus 0000:06: resource 7 [mem 0x000c0000-0x000dffff]
[    0.192307] pci_bus 0000:06: resource 8 [mem 0xfed40000-0xfed44fff]
[    0.192309] pci_bus 0000:06: resource 9 [mem 0xdff00000-0xfebfffff]
[    0.192338] NET: Registered protocol family 2
[    0.192454] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.193321] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.196212] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.196589] TCP: Hash tables configured (established 524288 bind 65536)
[    0.196591] TCP reno registered
[    0.196599] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.196630] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.196754] NET: Registered protocol family 1
[    0.228042] pci 0000:01:00.0: Boot video device
[    0.228057] PCI: CLS 4 bytes, default 64
[    0.228059] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.228061] Placing 64MB software IO TLB between ffff8800dbeaa000 - ffff8800dfeaa000
[    0.228062] software IO TLB at phys 0xdbeaa000 - 0xdfeaa000
[    0.228303] audit: initializing netlink socket (disabled)
[    0.228312] type=2000 audit(1318630827.224:1): initialized
[    0.251820] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.269333] VFS: Disk quotas dquot_6.5.2
[    0.269380] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.269799] fuse init (API version 7.16)
[    0.269859] msgmni has been set to 7890
[    0.270086] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.270108] io scheduler noop registered
[    0.270109] io scheduler deadline registered
[    0.270138] io scheduler cfq registered (default)
[    0.270222] pcieport 0000:00:01.0: setting latency timer to 64
[    0.270244] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.270275] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.270304] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.270345] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.270374] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.270416] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.270445] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
[    0.270486] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.270514] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    0.270571] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.270588] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.270620] intel_idle: MWAIT substates: 0x22220
[    0.270622] intel_idle: does not run on family 6 model 23
[    0.270679] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.270683] ACPI: Power Button [PWRB]
[    0.270721] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.270723] ACPI: Power Button [PWRF]
[    0.270744] ACPI: acpi_idle registered with cpuidle
[    0.270762] Marking TSC unstable due to TSC halts in idle
[    0.271735] ERST: Table is not found!
[    0.271772] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.292109] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.369107] Freeing initrd memory: 13412k freed
[    0.452424] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.452661] Linux agpgart interface v0.103
[    0.453529] brd: module loaded
[    0.453884] loop: module loaded
[    0.453989] ata_piix 0000:00:1f.2: version 2.13
[    0.454001] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.454004] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.454040] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.454246] scsi0 : ata_piix
[    0.454306] scsi1 : ata_piix
[    0.454650] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    0.454654] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    0.454668] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.454672] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.454705] ata_piix 0000:00:1f.5: setting latency timer to 64
[    0.454844] scsi2 : ata_piix
[    0.454888] scsi3 : ata_piix
[    0.455144] ata3: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf200 irq 19
[    0.455147] ata4: SATA max UDMA/133 cmd 0xf400 ctl 0xf300 bmdma 0xf208 irq 19
[    0.455196] pata_acpi 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.455217] pata_acpi 0000:03:00.1: setting latency timer to 64
[    0.455227] pata_acpi 0000:03:00.1: PCI INT B disabled
[    0.455420] Fixed MDIO Bus: probed
[    0.455436] PPP generic driver version 2.4.2
[    0.455459] tun: Universal TUN/TAP device driver, 1.6
[    0.455461] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.455514] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.455530] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.455542] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.455545] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.455569] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.459475] ehci_hcd 0000:00:1a.7: cache line size of 4 is not supported
[    0.459485] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[    0.472010] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.472129] hub 1-0:1.0: USB hub found
[    0.472134] hub 1-0:1.0: 6 ports detected
[    0.472201] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.472211] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.472213] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.472236] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.476141] ehci_hcd 0000:00:1d.7: cache line size of 4 is not supported
[    0.476151] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[    0.492011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.492114] hub 2-0:1.0: USB hub found
[    0.492118] hub 2-0:1.0: 6 ports detected
[    0.492185] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.492193] uhci_hcd: USB Universal Host Controller Interface driver
[    0.492207] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.492212] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.492214] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.492242] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.492270] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff00
[    0.492351] hub 3-0:1.0: USB hub found
[    0.492354] hub 3-0:1.0: 2 ports detected
[    0.492399] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.492404] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.492406] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.492430] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.492455] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fe00
[    0.492534] hub 4-0:1.0: USB hub found
[    0.492537] hub 4-0:1.0: 2 ports detected
[    0.492577] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.492581] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.492583] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.492606] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.492625] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000fd00
[    0.492702] hub 5-0:1.0: USB hub found
[    0.492704] hub 5-0:1.0: 2 ports detected
[    0.492746] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.492750] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.492753] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.492773] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.492792] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[    0.492869] hub 6-0:1.0: USB hub found
[    0.492872] hub 6-0:1.0: 2 ports detected
[    0.492915] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.492919] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.492921] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.492947] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.492969] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[    0.493045] hub 7-0:1.0: USB hub found
[    0.493047] hub 7-0:1.0: 2 ports detected
[    0.493090] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.493094] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.493096] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.493120] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.493139] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[    0.493219] hub 8-0:1.0: USB hub found
[    0.493221] hub 8-0:1.0: 2 ports detected
[    0.493292] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.525975] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    0.525977] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    0.782569] ata4: SATA link down (SStatus 0 SControl 300)
[    0.782720] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.782780] mousedev: PS/2 mouse device common for all mice
[    0.782860] rtc_cmos 00:04: RTC can wake from S4
[    0.782934] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.782954] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.783019] device-mapper: uevent: version 1.0.3
[    0.783067] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.783094] cpuidle: using governor ladder
[    0.783125] cpuidle: using governor menu
[    0.783127] EFI Variables Facility v0.08 2004-May-17
[    0.783310] TCP cubic registered
[    0.783395] NET: Registered protocol family 10
[    0.783734] NET: Registered protocol family 17
[    0.783745] Registering the dns_resolver key type
[    0.783806] PM: Hibernation image not present or could not be loaded.
[    0.783815] registered taskstats version 1
[    0.791232] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    0.796398]   Magic number: 15:681:350
[    0.796482] rtc_cmos 00:04: setting system clock to 2011-10-14 22:20:28 UTC (1318630828)
[    0.797424] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.797426] EDD information not available.
[    0.936049] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.944123] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203N, SB01, max UDMA/100
[    0.960123] ata3.00: configured for UDMA/100
[    1.152014] usb 1-4: new high speed USB device number 4 using ehci_hcd
[    1.248060] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.248073] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.248188] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.248199] ata1.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.264295] ata1.00: ATA-7: INTEL SSDSA2M080G2GC, 2CV102HA, max UDMA/133
[    1.264297] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.264370] ata2.00: HPA detected: current 490348559, native 490350672
[    1.264372] ata2.00: ATA-8: WDC WD2503ABYX-01WERA0, 01.01S01, max UDMA/133
[    1.264374] ata2.00: 490348559 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.264446] ata1.01: ATA-8: WDC WD20EADS-00S2B0, 01.00A01, max UDMA/133
[    1.264448] ata1.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.264517] ata2.01: ATA-8: WDC WD20EARS-00MVWB0, 50.0AB50, max UDMA/133
[    1.264519] ata2.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.272327] ata1.00: configured for UDMA/133
[    1.272385] ata2.00: configured for UDMA/133
[    1.280365] ata2.01: configured for UDMA/133
[    1.280922] ata1.01: configured for UDMA/133
[    1.281027] scsi 0:0:0:0: Direct-Access     ATA      INTEL SSDSA2M080 2CV1 PQ: 0 ANSI: 5
[    1.281119] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.281130] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.281169] sd 0:0:0:0: [sda] Write Protect is off
[    1.281172] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.281194] scsi 0:0:1:0: Direct-Access     ATA      WDC WD20EADS-00S 01.0 PQ: 0 ANSI: 5
[    1.281269] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.281271] sd 0:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.281306] sd 0:0:1:0: [sdb] Write Protect is off
[    1.281309] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.281325] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.281334] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2503ABYX-0 01.0 PQ: 0 ANSI: 5
[    1.281417] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    1.281460] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.281534] scsi 1:0:1:0: Direct-Access     ATA      WDC WD20EARS-00M 50.0 PQ: 0 ANSI: 5
[    1.281541] sd 1:0:0:0: [sdc] 490348559 512-byte logical blocks: (251 GB/233 GiB)
[    1.281573] sd 1:0:0:0: [sdc] Write Protect is off
[    1.281575] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.281589] sd 1:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.281604] sd 1:0:1:0: Attached scsi generic sg3 type 0
[    1.281705] sd 1:0:1:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    1.281754] sd 1:0:1:0: [sdd] Write Protect is off
[    1.281756] sd 1:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[    1.281779] sd 1:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.282332] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203N  SB01 PQ: 0 ANSI: 5
[    1.285445] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.285448] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.285525] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.285571] sr 2:0:0:0: Attached scsi generic sg4 type 5
[    1.287272]  sdb: sdb1
[    1.287479] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.288027]  sda: sda1 sda2 sda3 < sda5 >
[    1.288324] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.293837]  sdc: sdc1
[    1.732866]  sdd: sdd1
[    1.732937] sd 1:0:0:0: [sdc] Attached SCSI disk
[    1.733056] sd 1:0:1:0: [sdd] Attached SCSI disk
[    1.734342] Freeing unused kernel memory: 984k freed
[    1.734507] Write protecting the kernel read-only data: 10240k
[    1.734649] Freeing unused kernel memory: 20k freed
[    1.738183] Freeing unused kernel memory: 1400k freed
[    1.748884] udevd[90]: starting version 173
[    1.796943] ahci 0000:03:00.0: version 3.0
[    1.796957] ahci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.799227] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.799243] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.799271] r8169 0000:04:00.0: setting latency timer to 64
[    1.799321] r8169 0000:04:00.0: irq 45 for MSI/MSI-X
[    1.799851] r8169 0000:04:00.0: eth0: RTL8168c/8111c at 0xffffc90000650000, 00:24:1d:2d:2e:d6, XID 1c4000c0 IRQ 45
[    1.804061] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.804077] r8169 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.804108] r8169 0000:05:00.0: setting latency timer to 64
[    1.804155] r8169 0000:05:00.0: irq 46 for MSI/MSI-X
[    1.804476] r8169 0000:05:00.0: eth1: RTL8168c/8111c at 0xffffc90000652000, 00:1f:d0:81:6b:2e, XID 1c4000c0 IRQ 46
[    1.812174] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.812178] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    1.812184] ahci 0000:03:00.0: setting latency timer to 64
[    1.815166] firewire_ohci 0000:06:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.815863] scsi4 : ahci
[    1.817344] scsi5 : ahci
[    1.817409] ata5: SATA max UDMA/133 abar m8192@0xfdbfe000 port 0xfdbfe100 irq 19
[    1.817413] ata6: SATA max UDMA/133 abar m8192@0xfdbfe000 port 0xfdbfe180 irq 19
[    1.817455] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.817480] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    1.817792] scsi6 : pata_jmicron
[    1.819916] Floppy drive(s): fd0 is 1.44M
[    1.820706] scsi7 : pata_jmicron
[    1.821047] ata7: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 16
[    1.821049] ata8: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 16
[    1.835769] FDC 0 is a post-1991 82077
[    1.868140] firewire_ohci: Added fw-ohci device 0000:06:07.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.964587] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    2.136032] ata5: SATA link down (SStatus 0 SControl 300)
[    2.136069] ata6: SATA link down (SStatus 0 SControl 300)
[    2.368091] firewire_core: created device fw0: GUID 0043d76a0000241d, S400
[    2.548343] udevd[330]: starting version 173
[    2.567339] Adding 1997820k swap on /dev/sda5.  Priority:-1 extents:1 across:1997820k SS
[    2.580511] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    2.808910] type=1400 audit(1318656030.509:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=486 comm="apparmor_parser"
[    2.809187] type=1400 audit(1318656030.509:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=486 comm="apparmor_parser"
[    2.809366] type=1400 audit(1318656030.509:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=486 comm="apparmor_parser"
[    2.940790] r8169 0000:04:00.0: eth0: link down
[    2.941275] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.947216] r8169 0000:05:00.0: eth1: link down
[    2.947224] r8169 0000:05:00.0: eth1: link down
[    2.947523] ADDRCONF(NETDEV_UP): eth1: link is not ready
[    2.952476] lp: driver loaded but no devices found
[    3.125680] parport_pc 00:09: reported by Plug and Play ACPI
[    3.125728] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    3.187430] nvidia: module license 'NVIDIA' taints kernel.
[    3.187433] Disabling lock debugging due to kernel taint
[    3.372491] ppdev: user-space parallel port driver
[    3.392593] lp0: using parport0 (interrupt-driven).
[    3.477577] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.477617] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[    3.477636] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    3.540340] hda_codec: ALC889A: BIOS auto-probing.
[    3.567018] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input2
[    3.891211] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.891219] nvidia 0000:01:00.0: setting latency timer to 64
[    3.891223] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    3.891615] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[    3.904485] type=1400 audit(1318656031.605:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=859 comm="apparmor_parser"
[    3.905822] type=1400 audit(1318656031.605:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=860 comm="apparmor_parser"
[    3.906031] type=1400 audit(1318656031.605:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=861 comm="apparmor_parser"
[    3.906315] type=1400 audit(1318656031.605:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=861 comm="apparmor_parser"
[    3.906494] type=1400 audit(1318656031.605:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=861 comm="apparmor_parser"
[    3.910788] type=1400 audit(1318656031.609:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=865 comm="apparmor_parser"
[    3.958738] init: failsafe main process (820) killed by TERM signal
[    3.961309] init: apport pre-start process (900) terminated with status 1
[    3.974184] init: apport post-stop process (939) terminated with status 1
[    3.991790] Bluetooth: Core ver 2.16
[    3.991823] NET: Registered protocol family 31
[    3.991824] Bluetooth: HCI device and connection manager initialized
[    3.991826] Bluetooth: HCI socket layer initialized
[    3.991827] Bluetooth: L2CAP socket layer initialized
[    3.991966] Bluetooth: SCO socket layer initialized
[    3.993553] Bluetooth: RFCOMM TTY layer initialized
[    3.993556] Bluetooth: RFCOMM socket layer initialized
[    3.993557] Bluetooth: RFCOMM ver 1.11
[    4.006138] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.006140] Bluetooth: BNEP filters: protocol multicast
[    4.097925] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[    5.136318] r8169 0000:05:00.0: eth1: link up
[    5.136668] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   15.248008] eth1: no IPv6 routers present
[   16.264037] usb 1-4: device descriptor read/64, error -110
[   31.480037] usb 1-4: device descriptor read/64, error -110
[   31.696017] usb 1-4: new high speed USB device number 5 using ehci_hcd
[   46.808019] usb 1-4: device descriptor read/64, error -110
[   62.024028] usb 1-4: device descriptor read/64, error -110
[   62.240031] usb 1-4: new high speed USB device number 6 using ehci_hcd
[   72.648078] usb 1-4: device not accepting address 6, error -110
[   72.760037] usb 1-4: new high speed USB device number 7 using ehci_hcd
[   83.168079] usb 1-4: device not accepting address 7, error -110
[   83.168089] hub 1-0:1.0: unable to enumerate USB device on port 4
[   83.373769] vesafb: mode is 640x480x32, linelength=2560, pages=0
[   83.373772] vesafb: scrolling: redraw
[   83.373775] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   83.373782] mtrr: type mismatch for f9000000,200000 old: write-back new: write-combining
[   83.373786] mtrr: type mismatch for f9000000,100000 old: write-back new: write-combining
[   83.373789] mtrr: type mismatch for f9000000,80000 old: write-back new: write-combining
[   83.373792] mtrr: type mismatch for f9000000,40000 old: write-back new: write-combining
[   83.373796] mtrr: type mismatch for f9000000,20000 old: write-back new: write-combining
[   83.373799] mtrr: type mismatch for f9000000,10000 old: write-back new: write-combining
[   83.373802] mtrr: type mismatch for f9000000,8000 old: write-back new: write-combining
[   83.373806] mtrr: type mismatch for f9000000,4000 old: write-back new: write-combining
[   83.373809] mtrr: type mismatch for f9000000,2000 old: write-back new: write-combining
[   83.373812] mtrr: type mismatch for f9000000,1000 old: write-back new: write-combining
[   83.374071] vesafb: framebuffer at 0xf9000000, mapped to 0xffffc90005800000, using 1216k, total 1216k
[   83.374131] audit_printk_skb: 21 callbacks suppressed
[   83.374133] type=1400 audit(1318656111.071:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1159 comm="apparmor_parser"
[   83.374183] Console: switching to colour frame buffer device 80x30
[   83.374196] fb0: VESA VGA frame buffer device
[   83.379015] type=1400 audit(1318656111.075:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1159 comm="apparmor_parser"
[   83.391576] init: plymouth-splash main process (1162) terminated with status 1
[   83.394078] init: gdm main process (1169) killed by TERM signal
[   83.544044] usb 4-1: new full speed USB device number 2 using uhci_hcd
[   83.968019] usb 4-2: new full speed USB device number 3 using uhci_hcd
[   85.601361] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   99.080033] usb 4-2: device descriptor read/64, error -110
[  114.296037] usb 4-2: device descriptor read/64, error -110
[  114.512039] usb 4-2: new full speed USB device number 4 using uhci_hcd
[  129.624035] usb 4-2: device descriptor read/64, error -110
[  144.840034] usb 4-2: device descriptor read/64, error -110
[  145.056040] usb 4-2: new full speed USB device number 5 using uhci_hcd
[  155.464022] usb 4-2: device not accepting address 5, error -110
[  155.576031] usb 4-2: new full speed USB device number 6 using uhci_hcd
[  165.984086] usb 4-2: device not accepting address 6, error -110
[  165.984096] hub 4-0:1.0: unable to enumerate USB device on port 2
[  165.998136] input: Razer  Razer Mamba Charging Dock as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3
[  165.998248] generic-usb 0003:1532:000F.0001: input,hidraw0: USB HID v1.11 Mouse [Razer  Razer Mamba Charging Dock] on usb-0000:00:1a.1-1/input0
[  166.001244] input: Razer  Razer Mamba Charging Dock as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input4
[  166.001318] generic-usb 0003:1532:000F.0002: input,hidraw1: USB HID v1.11 Keyboard [Razer  Razer Mamba Charging Dock] on usb-0000:00:1a.1-1/input1
[  166.001333] usbcore: registered new interface driver usbhid
[  166.001334] usbhid: USB HID core driver
[  166.224042] usb 5-1: new full speed USB device number 2 using uhci_hcd
[  166.404142] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input5
[  166.404217] generic-usb 0003:1532:0109.0003: input,hidraw2: USB HID v1.10 Keyboard [Razer Razer Lycosa] on usb-0000:00:1a.2-1/input0
[  166.408941] input: Razer Razer Lycosa as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.1/input/input6
[  166.409009] generic-usb 0003:1532:0109.0004: input,hidraw3: USB HID v1.10 Device [Razer Razer Lycosa] on usb-0000:00:1a.2-1/input1

```

---

### Post by specialblend on 2011-10-15
Unplugging my usb connected Brother printer seems to have fixed it. I still am not sure what the "mtrr: type mismatch" errors are about, but at least boot time is manageable now.

---

