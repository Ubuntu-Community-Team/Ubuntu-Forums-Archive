---
title: "ACPI Warning after installation"
date: 2014-03-14
forum: Installation &amp; Upgrades
---

### Post by lakeswimmer2 on 2014-03-14
Hello everyone,

I am an Ubuntu beginner, I have installed 13.10 64bit on Asus H81 Plus motherboard and dmesg is giving following log, I fear hardware may encounter problems, thanks in advance

```

[    0.000000] BIOS-e820: [mem 0x00000000ba59d000-0x00000000ba5a3fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cc8be000-0x00000000cc8d3fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cc8d4000-0x00000000cce0ffff] ACPI NVS
[    0.000000] ACPI: RSDP 00000000000f0490 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000cc8c2080 00074 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000cc8cea00 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000cc8c2188 0C871 (v02 ALASKA    A M I 00000024 INTL 20091112)
[    0.000000] ACPI: FACS 00000000cce0e080 00040
[    0.000000] ACPI: APIC 00000000cc8ceb10 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000cc8ceb88 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000cc8cebd0 00539 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cc8cf110 00AD8 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: MCFG 00000000cc8cfbe8 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cc8cfc28 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000cc8cfc60 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000cc8cffd0 0329E (v01 SaSsdt  SaSsdt  00003000 INTL 20091112)
[    0.000000] ACPI: BGRT 00000000cc8d32c8 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.003889] ACPI: Core revision 20130517
[    0.009268] ACPI: All ACPI Tables successfully acquired
[    0.106056] PM: Registering ACPI NVS region [mem 0xba59d000-0xba5a3fff] (28672 bytes)
[    0.106057] PM: Registering ACPI NVS region [mem 0xcc8d4000-0xcce0ffff] (5488640 bytes)
[    0.106754] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.106755] ACPI: bus type PCI registered
[    0.106757] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.111905] ACPI: Added _OSI(Module Device)
[    0.111906] ACPI: Added _OSI(Processor Device)
[    0.111907] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.111908] ACPI: Added _OSI(Processor Aggregator Device)
[    0.113185] ACPI: EC: Look up EC in DSDT
[    0.114734] ACPI: Executed 1 blocks of module-level executable AML code
[    0.116478] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.118694] ACPI: SSDT 00000000cc8b3c18 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.119019] ACPI: Dynamic OEM Table Load:
[    0.119020] ACPI: SSDT           (null) 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.130778] ACPI: SSDT 00000000cc8b3618 005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.131150] ACPI: Dynamic OEM Table Load:
[    0.131151] ACPI: SSDT           (null) 005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.138686] ACPI: SSDT 00000000cc8b2d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.139008] ACPI: Dynamic OEM Table Load:
[    0.139009] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.147108] ACPI: Interpreter enabled
[    0.147113] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.147117] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.147127] ACPI: (supports S0 S3 S4 S5)
[    0.147128] ACPI: Using IOAPIC for interrupt routing
[    0.147146] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.147248] ACPI: No dock devices found.
[    0.152927] ACPI: Power Resource [FN00] (off)
[    0.152974] ACPI: Power Resource [FN01] (off)
[    0.153020] ACPI: Power Resource [FN02] (off)
[    0.153063] ACPI: Power Resource [FN03] (off)
[    0.153107] ACPI: Power Resource [FN04] (off)
[    0.153674] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.153804] acpi PNP0A08:00: Requesting ACPI _OSC control (0x1d)
[    0.153931] acpi PNP0A08:00: ACPI _OSC control (0x18) granted
[    0.154387] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.154594] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.154885] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.155007] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.155113] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.155223] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.155329] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.155491] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.155930] acpiphp: Slot [1] registered
[    0.156156] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.162812] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.162992] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.163551] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.163584] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.163616] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.163647] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.163677] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.163708] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.163739] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.163770] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.164057] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.164062] ACPI: \_SB_.PCI0: notify handler is installed
[    0.164108] Found 1 acpi root devices
[    0.164255] ACPI: bus type ATA registered
[    0.164282] ACPI: bus type USB registered
[    0.164361] PCI: Using ACPI for IRQ routing
[    0.170655] pnp: PnP ACPI init
[    0.170661] ACPI: bus type PNP registered
[    0.170720] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.170734] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.170744] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.170807] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.170834] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.170916] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.170929] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.170955] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.171004] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.171231] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.171258] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.171405] pnp 00:0b: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.171428] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.171720] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.171889] pnp: PnP ACPI: found 14 devices
[    0.171890] ACPI: bus type PNP unregistered
[    0.430565] ACPI: Power Button [PWRB]
[    0.430586] ACPI: Power Button [PWRF]
[    0.430631] ACPI: Fan [FAN0] (off)
[    0.430645] ACPI: Fan [FAN1] (off)
[    0.430660] ACPI: Fan [FAN2] (off)
[    0.430673] ACPI: Fan [FAN3] (off)
[    0.430685] ACPI: Fan [FAN4] (off)
[    0.430719] ACPI: Requesting acpi_cpufreq
[    0.431060] ACPI: Thermal Zone [TZ00] (28 C)
[    0.431186] ACPI: Thermal Zone [TZ01] (30 C)
[    6.707768] parport_pc 00:09: reported by Plug and Play ACPI
[    6.970217] asus_wmi: Backlight controlled by ACPI video driver
[    7.006957] acpi device:56: registered as cooling_device9
[    7.006980] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    7.007162] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[    7.007165] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.007168] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 1 (20130517/utaddress-251)
[    7.007169] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPR_ 2 (20130517/utaddress-251)
[    7.007171] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.007172] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 1 (20130517/utaddress-251)
[    7.007173] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPR_ 2 (20130517/utaddress-251)
[    7.007175] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver



```

---

