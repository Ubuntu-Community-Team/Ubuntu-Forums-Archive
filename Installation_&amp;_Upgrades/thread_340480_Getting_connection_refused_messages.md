---
title: "Getting connection refused messages"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2007-01-17
Hi all,
      I successfully installed ubuntu but im unable to update it, this is the error being shown :-

```
Err http://archive.ubuntu.com dapper Release.gpg
  Could not connect to 192.168.1.1:6588 (192.168.1.1). - connect (111 Connection refused)
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to 192.168.1.1:6588 (192.168.1.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to 192.168.1.1:6588 (192.168.1.1). - connect (111 Connection refused)
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to 192.168.1.1:6588 (192.168.1.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to 192.168.1.1:6588 (192.168.1.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to 192.168.1.1:6588 (192.168.1.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to 192.168.1.1:6588 (192.168.1.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to 192.168.1.1:6588 (192.168.1.1). - connect (111 Connection refused)

```now im able to ping to the gateway which 192.168.1.1 


```
  ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.446 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.527 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.442 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.442 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.440 ms
```

 I'm able to surf on the net using the same connection

This is in System > Admin > Networking/Network Settings :-

```
 Configuration :- Static IP Address
IP Address 192.168.1.5
Subnet Mask 255.255.255.0
Gateway Address :- 192.168.1.1
```

DNS Servers are given as :-

61.1.96.71
61.1.96.69

          so plz. lemme know wht the issue might be 

lspci gives this :-

```
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0336
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1336
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2336
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3336
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4336
0000:00:00.5 PIC: VIA Technologies, Inc.: Unknown device 5336
0000:00:00.6 Host bridge: VIA Technologies, Inc.: Unknown device 6290
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7336
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
0000:00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
0000:00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
0000:00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCIE Bridge
0000:00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc.: Unknown device 3230 (rev 01)
0000:04:01.0 0403: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

while dmesg gives this :-

```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001bfb0000 (usable)
[4294667.296000]  BIOS-e820: 000000001bfb0000 - 000000001bfbe000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001bfbe000 - 000000001bfe0000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001bfe0000 - 000000001c000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 447MB LOWMEM available.
[4294667.296000] found SMP MP-table at 000ff780
[4294667.296000] On node 0 totalpages: 114608
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 110512 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fa850
[4294667.296000] ACPI: RSDT (v001 A M I  OEMRSDT  0x06000613 MSFT 0x00000097) @ 0x1bfb0000
[4294667.296000] ACPI: FADT (v002 A M I  OEMFACP  0x06000613 MSFT 0x00000097) @ 0x1bfb0200
[4294667.296000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000613 MSFT 0x00000097) @ 0x1bfb0390
[4294667.296000] ACPI: MCFG (v001 A M I  OEMMCFG  0x06000613 MSFT 0x00000097) @ 0x1bfb03f0
[4294667.296000] ACPI: OEMB (v001 A M I  AMI_OEM  0x06000613 MSFT 0x00000097) @ 0x1bfbe040
[4294667.296000] ACPI: DSDT (v001  A0571 A0571000 0x00000000 INTL 0x02002026) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] ACPI: Local APIC address 0xfee00000
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] Processor #0 15:12 APIC version 16
[4294667.296000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[4294667.296000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfecc0000] gsi_base[24])
[4294667.296000] IOAPIC[1]: apic_id 2, version 3, address 0xfecc0000, GSI 24-47
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[4294667.296000] ACPI: IRQ0 used by override.
[4294667.296000] ACPI: IRQ2 used by override.
[4294667.296000] ACPI: IRQ9 used by override.
[4294667.296000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[4294667.296000] Using ACPI (MADT) for SMP configuration information
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e2c00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda9 ro quiet splash
[4294667.296000] mapped APIC to ffffd000 (fee00000)
[4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
[4294667.296000] mapped IOAPIC to ffffb000 (fecc0000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 2195.651 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.354000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.354000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294667.362000] Memory: 443700k/458432k available (1976k kernel code, 14124k reserved, 606k data, 288k init, 0k highmem)
[4294667.362000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.422000] Calibrating delay using timer specific routine.. 4391.33 BogoMIPS (lpj=2195669)
[4294667.422000] Security Framework v1.0.0 initialized
[4294667.422000] SELinux:  Disabled at boot.
[4294667.422000] Mount-cache hash table entries: 512
[4294667.422000] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[4294667.422000] CPU: After vendor identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[4294667.422000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294667.422000] CPU: L2 Cache: 512K (64 bytes/line)
[4294667.422000] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000010 00000000 00000000 00000000
[4294667.422000] mtrr: v2.0 (20020519)
[4294667.422000] CPU: AMD Athlon(tm) 64 Processor 3200+ stepping 00
[4294667.422000] Enabling fast FPU save and restore... done.
[4294667.422000] Enabling unmasked SIMD FPU exception support... done.
[4294667.422000] Checking 'hlt' instruction... OK.
[4294667.426000] checking if image is initramfs... it is
[4294667.891000] Freeing initrd memory: 6837k freed
[4294667.899000] ACPI: Looking for DSDT ... not found!
[4294667.901000] ENABLING IO-APIC IRQs
[4294667.901000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[4294668.012000] NET: Registered protocol family 16
[4294668.012000] EISA bus registered
[4294668.012000] ACPI: bus type pci registered
[4294668.012000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[4294668.012000] PCI: Using MMCONFIG
[4294668.013000] ACPI: Subsystem revision 20051216
[4294668.016000] ACPI: Interpreter enabled
[4294668.016000] ACPI: Using IOAPIC for interrupt routing
[4294668.017000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.017000] PCI: Probing PCI hardware (bus 00)
[4294668.021000] Boot video device is 0000:01:00.0
[4294668.021000] PCI: Transparent bridge - 0000:00:13.1
[4294668.021000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.044000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[4294668.044000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PA._PRT]
[4294668.045000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[4294668.045000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[4294668.045000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[4294668.046000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[4294668.046000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.046000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[4294668.046000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[4294668.046000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.047000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.047000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[4294668.047000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[4294668.047000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.047000] pnp: PnP ACPI init
[4294668.050000] pnp: PnP ACPI: found 15 devices
[4294668.050000] PnPBIOS: Disabled by ACPI PNP
[4294668.050000] PCI: Using ACPI for IRQ routing
[4294668.050000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.050000] PCI: Cannot allocate resource region 8 of bridge 0000:00:02.0
[4294668.050000] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0
[4294668.066000] pnp: 00:06: ioport range 0x290-0x297 has been reserved
[4294668.066000] PCI: Bridge: 0000:00:01.0
[4294668.066000]   IO window: disabled.
[4294668.066000]   MEM window: fa000000-fbefffff
[4294668.066000]   PREFETCH window: d0000000-dfffffff
[4294668.066000] PCI: Bridge: 0000:00:02.0
[4294668.066000]   IO window: disabled.
[4294668.066000]   MEM window: disabled.
[4294668.066000]   PREFETCH window: disabled.
[4294668.066000] PCI: Bridge: 0000:00:03.0
[4294668.066000]   IO window: disabled.
[4294668.066000]   MEM window: disabled.
[4294668.066000]   PREFETCH window: disabled.
[4294668.066000] PCI: Bridge: 0000:00:13.0
[4294668.066000]   IO window: disabled.
[4294668.066000]   MEM window: fbf00000-fbffffff
[4294668.066000]   PREFETCH window: disabled.
[4294668.066000] PCI: Bridge: 0000:00:13.1
[4294668.066000]   IO window: disabled.
[4294668.066000]   MEM window: disabled.
[4294668.066000]   PREFETCH window: disabled.
[4294668.066000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[4294668.066000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 169
[4294668.066000] PCI: Via IRQ fixup for 0000:00:02.0, from 10 to 9
[4294668.066000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294668.066000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 177
[4294668.066000] PCI: Via IRQ fixup for 0000:00:03.0, from 10 to 1
[4294668.066000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[4294668.066000] PCI: Setting latency timer of device 0000:00:13.0 to 64
[4294668.066000] PCI: Setting latency timer of device 0000:00:13.1 to 64
[4294668.067000] audit: initializing netlink socket (disabled)
[4294668.067000] audit(1169060574.066:1): initialized
[4294668.067000] VFS: Disk quotas dquot_6.5.1
[4294668.067000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.067000] Initializing Cryptographic API
[4294668.067000] io scheduler noop registered
[4294668.067000] io scheduler anticipatory registered
[4294668.067000] io scheduler deadline registered
[4294668.067000] io scheduler cfq registered
[4294668.067000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 169
[4294668.067000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[4294668.067000] assign_interrupt_mode Found MSI capability
[4294668.067000] Allocate Port Service[pcie00]
[4294668.067000] Allocate Port Service[pcie01]
[4294668.067000] Allocate Port Service[pcie02]
[4294668.067000] Allocate Port Service[pcie03]
[4294668.067000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 177
[4294668.067000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[4294668.067000] assign_interrupt_mode Found MSI capability
[4294668.067000] Allocate Port Service[pcie00]
[4294668.067000] Allocate Port Service[pcie01]
[4294668.067000] Allocate Port Service[pcie02]
[4294668.067000] Allocate Port Service[pcie03]
[4294668.067000] isapnp: Scanning for PnP cards...
[4294668.424000] isapnp: No Plug & Play device found
[4294668.433000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[4294668.433000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.433000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.433000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294668.433000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.434000] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294668.435000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.435000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294668.435000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294668.435000] mice: PS/2 mouse device common for all mice
[4294668.435000] EISA: Probing bus 0 at eisa.0
[4294668.435000] EISA: Detected 0 cards.
[4294668.435000] NET: Registered protocol family 2
[4294668.445000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[4294668.445000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[4294668.445000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294668.445000] TCP: Hash tables configured (established 16384 bind 16384)
[4294668.445000] TCP reno registered
[4294668.445000] TCP bic registered
[4294668.445000] NET: Registered protocol family 1
[4294668.445000] NET: Registered protocol family 8
[4294668.445000] NET: Registered protocol family 20
[4294668.445000] Using IPI Shortcut mode
[4294668.445000] ACPI wakeup devices:
[4294668.445000] PCI0 PS2K PS2M UAR2 USB1 USB2 USB3 USB4 ILAN PCI1 PCI2 PWRB
[4294668.445000] ACPI: (supports S0 S1 S3 S4 S5)
[4294668.445000] Freeing unused kernel memory: 288k freed
[4294668.457000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294668.481000] vga16fb: initializing
[4294668.481000] vga16fb: mapped to 0xc00a0000
[4294668.648000] Console: switching to colour frame buffer device 80x25
[4294668.648000] fb0: VGA16 VGA frame buffer device
[4294669.753000] Capability LSM initialized
[4294669.778000] ACPI: Processor [CPU1] (supports 16 throttling states)
[4294670.135000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[4294670.135000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 0
[4294670.135000] VP_IDE: chipset revision 7
[4294670.135000] VP_IDE: not 100% native mode: will probe irqs later
[4294670.135000] VP_IDE: Unknown VIA SouthBridge, disabling DMA.
[4294670.202000] Probing IDE interface ide0...
[4294670.232000] usbcore: registered new driver usbfs
[4294670.232000] usbcore: registered new driver hub
[4294670.232000] USB Universal Host Controller Interface driver v2.3
[4294670.232000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 209
[4294670.232000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 1
[4294670.232000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[4294670.233000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294670.233000] uhci_hcd 0000:00:10.0: irq 209, io base 0x0000c800
[4294670.233000] hub 1-0:1.0: USB hub found
[4294670.233000] hub 1-0:1.0: 2 ports detected
[4294670.334000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 217
[4294670.334000] PCI: Via IRQ fixup for 0000:00:10.1, from 5 to 9
[4294670.334000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[4294670.334000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294670.334000] uhci_hcd 0000:00:10.1: irq 217, io base 0x0000c400
[4294670.334000] hub 2-0:1.0: USB hub found
[4294670.334000] hub 2-0:1.0: 2 ports detected
[4294670.435000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 225
[4294670.435000] PCI: Via IRQ fixup for 0000:00:10.2, from 4 to 1
[4294670.435000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[4294670.435000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294670.435000] uhci_hcd 0000:00:10.2: irq 225, io base 0x0000c000
[4294670.435000] hub 3-0:1.0: USB hub found
[4294670.435000] hub 3-0:1.0: 2 ports detected
[4294670.536000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 233
[4294670.536000] PCI: Via IRQ fixup for 0000:00:10.3, from 5 to 9
[4294670.536000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[4294670.536000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294670.536000] uhci_hcd 0000:00:10.3: irq 233, io base 0x0000b800
[4294670.536000] hub 4-0:1.0: USB hub found
[4294670.536000] hub 4-0:1.0: 2 ports detected
[4294670.628000] hda: ST3802110A, ATA DISK drive
[4294670.638000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 225
[4294670.638000] PCI: Via IRQ fixup for 0000:00:10.4, from 4 to 1
[4294670.638000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[4294670.638000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[4294670.638000] ehci_hcd 0000:00:10.4: irq 225, io mem 0xf9fffc00
[4294670.638000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[4294670.639000] hub 5-0:1.0: USB hub found
[4294670.639000] hub 5-0:1.0: 8 ports detected
[4294671.240000] Probing IDE interface ide1...
[4294672.289000] hdd: SAMSUNG CD-R/RW SW-252S, ATAPI CD/DVD-ROM drive
[4294672.340000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.340000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.345000] hda: max request size: 1024KiB
[4294672.383000] hda: Host Protected Area detected.
[4294672.383000]        current capacity is 156299375 sectors (80025 MB)
[4294672.383000]        native  capacity is 156301488 sectors (80026 MB)
[4294672.499000] hda: Host Protected Area disabled.
[4294672.499000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63
[4294672.524000] hda: cache flushes supported
[4294672.524000]  hda: hda1 hda2 < hda5 hda6 hda7 hda8 hda9 >
[4294672.613000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294672.613000] Uniform CD-ROM driver Revision: 3.20
[4294673.380000] Attempting manual resume
[4294673.419000] EXT3-fs: mounted filesystem with ordered data mode.
[4294673.428000] kjournald starting.  Commit interval 5 seconds
[4294700.004000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294700.026000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294700.718000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294700.718000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 233
[4294700.718000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 9
[4294700.718000] eth0: VIA Rhine II at 0x1b400, 00:18:f3:da:7f:e8, IRQ 233.
[4294700.719000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[4294700.746000] input: PC Speaker as /class/input/input1
[4294701.068000] Real Time Clock Driver v1.12
[4294701.352000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4294701.355000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[4294701.476000] Floppy drive(s): fd0 is 1.44M
[4294701.492000] FDC 0 is a post-1991 82077
[4294701.548000] parport: PnPBIOS parport detected.
[4294701.548000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294701.656000] ts: Compaq touchscreen protocol output
[4294701.758000] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 50
[4294701.758000] PCI: Via IRQ fixup for 0000:04:01.0, from 5 to 2
[4294701.758000] PCI: Setting latency timer of device 0000:04:01.0 to 64
[4294701.846000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[4294702.038000] lp0: using parport0 (interrupt-driven).
[4294702.076000] Adding 514040k swap on /dev/hda8.  Priority:-1 extents:1 across:514040k
[4294702.122000] EXT3 FS on hda9, internal journal
[4294702.292000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294702.292000] md: bitmap version 4.39
[4294702.758000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294703.660000] cdrom: open failed.
[4294763.897000] NET: Registered protocol family 17
[4294768.384000] ACPI: Power Button (FF) [PWRF]
[4294768.384000] ACPI: Power Button (CM) [PWRB]
[4294768.478000] ibm_acpi: ec object not found
[4294768.500000] pcc_acpi: loading...
[4294769.218000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[4294769.226000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[4294775.803000] ppdev: user-space parallel port driver
[4294776.175000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294776.175000] apm: overridden by ACPI.
[4294783.205000] Bluetooth: Core ver 2.8
[4294783.205000] NET: Registered protocol family 31
[4294783.205000] Bluetooth: HCI device and connection manager initialized
[4294783.205000] Bluetooth: HCI socket layer initialized
[4294783.307000] hda-intel: Invalid position buffer, using LPIB read method instead.
[4294783.395000] Bluetooth: L2CAP ver 2.8
[4294783.395000] Bluetooth: L2CAP socket layer initialized
[4294783.414000] Bluetooth: RFCOMM socket layer initialized
[4294783.414000] Bluetooth: RFCOMM TTY layer initialized
[4294783.414000] Bluetooth: RFCOMM ver 1.7
[4294798.376000] NET: Registered protocol family 10
[4294798.376000] lo: Disabled Privacy Extensions
[4294798.376000] IPv6 over IPv4 tunneling driver
[4294808.906000] eth0: no IPv6 routers present
[4295831.890000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4295842.154000] eth0: no IPv6 routers present
[4297218.858000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4297228.991000] eth0: no IPv6 routers present

```

---

### Post by bapoumba on 2007-01-17
hello :)

Please post the output to :
```
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /etc/apt/apt.conf
ifconfig
```

Are you behind a proxy ?

---

### Post by ShirishAg75 on 2007-01-17
Thnx for giving the hint, I was behind proxy for quite sometime but just changed the networking so tht proxy is no longer needed but the required changes weren't done hence it was giving the requests to port 6688 or something similar to the effect. :) Mods, plz. close this thread.

---

