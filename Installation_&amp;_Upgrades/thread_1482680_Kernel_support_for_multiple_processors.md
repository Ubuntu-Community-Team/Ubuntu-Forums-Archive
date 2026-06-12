---
title: "Kernel support for multiple processors?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by pwaugh on 2010-05-13
I just installed the latest version of Ubuntu 10.04 LTS, and am wondering if support for my dual AMD processors is built into the generic kernel, or do I need to compile a custom kernel?

I have an HP tx2-1025dx touchsmart.

lshw gives:

```

patrick
    description: Notebook
    product: HP TouchSmart tx2 Notebook PC
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF91103WQ
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=434E4639-3131-3033-5751-00238B8C3A85
  *-core
       description: Motherboard
       product: 3045
       vendor: Quanta
       physical id: 0
       version: 16.0B
       serial: None
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.14 (05/13/2009)
          size: 1MiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: AMD Turion(tm) X2 Dual-Core Mobile RM-72
          vendor: Advanced Micro Devices [AMD]
          physical id: a
          bus info: cpu@0
          version: AMD Turion(tm) X2 Dual-Core Mobile RM-72
          serial: NotSupport
          slot: Socket M2/S1G1
          size: 525MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 1800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: c
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: EBE21UE8ACUA-8G-E
             vendor: 0000000000FE7F7F
             physical id: 0
             serial: 7F7FFE00000000004A0903240619F2
             slot: SODIMM 0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: EBE21UE8ACUA-8G-E
             vendor: 0000000000FE7F7F
             physical id: 1
             serial: 7F7FFE00000000004A090324061AC3
             slot: SODIMM 1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:5000(size=4096) memory:d2300000-d24fffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:29 memory:c0000000-cfffffff(prefetchable) ioport:5000(size=256) memory:d2400000-d240ffff memory:d2300000-d23fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=8192) memory:d1300000-d22fffff ioport:d0000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:d1200000-d12fffff ioport:d1000000(size=1048576)
           *-network
                description: Wireless interface
                product: BCM4328 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth1
                version: 03
                serial: 00:21:00:bd:a1:d0
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:17 memory:d1200000-d1203fff memory:d1000000-d10fffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:2000(size=4096) memory:b0000000-b00fffff ioport:d1100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 02
                serial: 00:23:8b:8c:3a:85
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:28 ioport:2000(size=256) memory:d1110000-d1110fff(prefetchable) memory:d1100000-d110ffff(prefetchable) memory:d1120000-d112ffff(prefetchable)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             logical name: scsi3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:6038(size=8) ioport:604c(size=4) ioport:6030(size=8) ioport:6048(size=4) ioport:6010(size=16) memory:d2509000-d25093ff
           *-disk
                description: ATA Disk
                product: ST9320320AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: HP07
                serial: 5SX3X01P
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000f095a
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 321fc710-25b6-489b-a236-28579084a479
                   size: 287GiB
                   capacity: 287GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-04-30 19:47:00 filesystem=ext4 lastmountpoint=/ï¿œï¿œ.ï¿œï¿œï¿œï¿œï¿œï¿œÔï¿œï¿œ.ï¿œï¿œï¿œ49ï¿œï¿œï¿œ3ï¿œ-ï¿œï¿œï¿œ\ï¿œ,ï¿œï¿œï¿œï¿œnï¿œï¿œï¿œï¿œï¿œï¿œï¿œ;ï¿œ modified=2010-04-30 20:14:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-09 00:57:08 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 10GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T50L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: SC04
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:d2508000-d2508fff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:d2507000-d2507fff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:d2509500-d25095ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d2506000-d2506fff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d2505000-d2505fff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:d2509400-d25094ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6000(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:d2500000-d2503fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:1000(size=4096)
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:d2504000-d2504fff
     *-pci:1
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 40
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 11h [Turion X2, Athlon X2, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@1:4
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdb

```

---

### Post by bukwirm on 2010-05-13
It should be fine - try 'cat /proc/cpuinfo' to be sure.

---

### Post by pwaugh on 2010-05-13
> **bukwirm said:**
> It should be fine - try 'cat /proc/cpuinfo' to be sure.

Seems you are correct, I got this:

```

patrick@patrick:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Dual-Core Mobile RM-72
stepping	: 1
cpu MHz		: 525.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4200.71
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 17
model		: 3
model name	: AMD Turion(tm) X2 Dual-Core Mobile RM-72
stepping	: 1
cpu MHz		: 525.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch osvw skinit
bogomips	: 4189.81
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

patrick@patrick:~$ 

```

Thanks for the assistance.

patrick

---

