---
title: "Ubuntu 10.10 - i7 16GB Ram - Where did my ram go?"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by sswittch on 2011-04-05
Ok, I decided to install Ubuntu 10.10 x64 on my Laptop and run Windows 7 in Virtualbox.  I have 16GB of Ram installed but cannot work out where its gone.

Can anyone shed some light on this for me please as I'm wanting to allocate 8GB or so to my Windows Operating System.

I'm guessing I'm going to have to reinstall but if someone could give me some advice first that would be much appreciated.

```
root@slaeya-i7:/home/slaeya# free -mt
             total       used       free     shared    buffers     cached
Mem:          2959        661       2297          0         33        334
-/+ buffers/cache:        293       2665
Swap:        19337          0      19337
Total:       22297        661      21635

```

```
root@slaeya-i7:/home/slaeya# top

top - 11:37:45 up 14 min,  2 users,  load average: 0.66, 0.62, 0.39
Tasks: 245 total,   3 running, 242 sleeping,   0 stopped,   0 zombie
Cpu0  : 16.4%us,  1.3%sy,  0.0%ni, 82.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  : 23.5%us,  1.3%sy,  0.0%ni, 73.7%id,  1.6%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.6%us,  0.0%sy,  0.0%ni, 99.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.6%us,  0.0%sy,  0.0%ni, 99.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.3%us,  0.3%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.6%si,  0.0%st
Cpu5  :  5.0%us,  0.3%sy,  0.0%ni, 94.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  : 13.8%us,  0.0%sy,  0.0%ni, 86.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :  0.6%us,  0.6%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3030264k total,   759048k used,  2271216k free,    35352k buffers
Swap: 19802108k total,        0k used, 19802108k free,   403024k cached

```

---

### Post by tgm4883 on 2011-04-05
> **sswittch said:**
> Ok, I decided to install Ubuntu 10.10 x64 on my Laptop and run Windows 7 in Virtualbox.  I have 16GB of Ram installed but cannot work out where its gone.

Can anyone shed some light on this for me please as I'm wanting to allocate 8GB or so to my Windows Operating System.

I'm guessing I'm going to have to reinstall but if someone could give me some advice first that would be much appreciated.

```
root@slaeya-i7:/home/slaeya# free -mt
             total       used       free     shared    buffers     cached
Mem:          2959        661       2297          0         33        334
-/+ buffers/cache:        293       2665
Swap:        19337          0      19337
Total:       22297        661      21635

```

```
root@slaeya-i7:/home/slaeya# top

top - 11:37:45 up 14 min,  2 users,  load average: 0.66, 0.62, 0.39
Tasks: 245 total,   3 running, 242 sleeping,   0 stopped,   0 zombie
Cpu0  : 16.4%us,  1.3%sy,  0.0%ni, 82.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  : 23.5%us,  1.3%sy,  0.0%ni, 73.7%id,  1.6%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.6%us,  0.0%sy,  0.0%ni, 99.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.6%us,  0.0%sy,  0.0%ni, 99.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.3%us,  0.3%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.6%si,  0.0%st
Cpu5  :  5.0%us,  0.3%sy,  0.0%ni, 94.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  : 13.8%us,  0.0%sy,  0.0%ni, 86.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :  0.6%us,  0.6%sy,  0.0%ni, 98.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3030264k total,   759048k used,  2271216k free,    35352k buffers
Swap: 19802108k total,        0k used, 19802108k free,   403024k cached

```

Odd. Whats the output of 
```
uname -a
```

---

### Post by sswittch on 2011-04-05
> **tgm4883 said:**
> Odd. Whats the output of 
```
uname -a
```

```
Linux slaeya-i7 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
```

```
slaeya@slaeya-i7:~$ lshw

slaeya-i7
    description: Notebook
    product: Aspire 5745G
    vendor: Acer
    version: V1.16
    serial: LXPU302106017008C12500
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook uuid=E1E9C79D-84CA-4C90-BC3C-C80AA96C1A93
  *-core
       description: Motherboard
       product: ZR7
       vendor: Acer
       physical id: 0
       version: Base Board Version
       serial: 016GZOMBQTF0013A
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: V1.16 (08/09/2010)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: CM3X4GSD1066
             physical id: 0
             serial: 00000000
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:1
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: CM3X4GSD1066
             physical id: 1
             serial: 00000000
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:2
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: CM3X4GSD1066
             physical id: 2
             serial: 00000000
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
        *-bank:3
             description: SODIMM Synchronous 1067 MHz (0.9 ns)
             product: CM3X4GSD1066
             physical id: 3
             serial: 00000000
             slot: DIMM3
             size: 4GiB
             width: 64 bits
             clock: 1067MHz (0.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU       Q 720  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 2f
          bus info: cpu@0
          version: 6.14.5
          serial: 0001-06E5-0000-0000-0000-0000
          slot: CPU
          size: 933MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 1066MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: id=5
        *-cache:0
             description: L3 cache
             physical id: 30
             slot: L3 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 32
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 33
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 5.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 5.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 5.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 5.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 5.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 5.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 5.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 5.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 5.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 5.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 5.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 5.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 5.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 5.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 5.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 5.10
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 31
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DMI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pci msi pciexpress pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:3000(size=4096) memory:d2000000-d30fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GT216 [GeForce GT 330M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:d3080000-d30fffff
           *-multimedia
                description: Audio device
                product: High Definition Audio Controller
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:d3000000-d3003fff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Core Processor System Management Registers
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: Core Processor Semaphore and Scratchpad Registers
             vendor: Intel Corporation
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:2 UNCLAIMED
             description: System peripheral
             product: Core Processor System Control and Status Registers
             vendor: Intel Corporation
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pciexpress cap_list
             configuration: latency=0
        *-generic:3 UNCLAIMED
             description: System peripheral
             product: Core Processor Miscellaneous Registers
             vendor: Intel Corporation
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:4 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Link
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-generic:5 UNCLAIMED
             description: System peripheral
             product: Core Processor QPI Routing and Protocol Registers
             vendor: Intel Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:d7106100-d710610f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:d7105c00-d7105fff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:50 memory:d7100000-d7103fff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:2000(size=4096) memory:d6100000-d70fffff ioport:d3100000(size=16777216)
           *-network
                description: Ethernet interface
                product: AR8151 v1.0 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: c8:0a:a9:6c:1a:93
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:49 memory:d6100000-d613ffff ioport:2000(size=128)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:47 ioport:1000(size=4096) memory:d5100000-d60fffff ioport:d4100000(size=16777216)
           *-network
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 78:e4:00:2c:87:20
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:d5100000-d510ffff
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d7105800-d7105bff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:48 ioport:4048(size=8) ioport:4054(size=4) ioport:4040(size=8) ioport:4050(size=4) ioport:4020(size=32) memory:d7105000-d71057ff
           *-disk
                description: ATA Disk
                product: ST95005620AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SD23
                serial: 5YX0EL3P
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00092c50
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 386a01f2-4ab0-41ae-89e6-92bebf59081d
                   size: 446GiB
                   capacity: 446GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-04-06 21:04:44 filesystem=ext4 lastmountpoint=/&#65533;&#65533;&#65533;kG&#65533;&#65533;H&#65533;&#65533;4b&#65533;P~&#65533;&#65533;&#65533;l!&#65533;H&#65533;&#65533;@~&#65533;&#65533;0S&#65533;&#65533;0S&#65533;&#65533;G&#65533;&#65533;h~&#65533;&#65533;yo!&#65533;&#65533;d modified=2011-04-06 11:18:19 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-04-06 11:22:58 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 18GiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT31N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d7106000-d71060ff ioport:4000(size=32)
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:03.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:03.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Core Processor Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:3f:03.4
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:3f:04.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:3f:04.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:3f:04.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:3f:04.3
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:3f:05.0
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:3f:05.1
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:3f:05.2
          version: 04
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:3f:05.3
          version: 04
          width: 32 bits
          clock: 33MHz
  *-power UNCLAIMED
       description: OEM_Define1
       product: OEM_Define5
       vendor: OEM_Define2
       physical id: 1
       version: OEM_Define6
       serial: OEM_Define3
       capacity: 75mWh
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 2
       version: 10/12/2007
       serial: Battery 0
       slot: Fake

```

---

### Post by cariboo on 2011-04-05
> Linux slaeya-i7 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 **i686** GNU/Linux

There's your problem bolded in the quote, you're running a 32-bit version, and not using at least a pae kernel. I'd suggest installing a 64-bit version.

You can get the ubuntu-10.10-desktop-amd64.iso   [here]("http://releases.ubuntu.com/10.10/")

---

### Post by sswittch on 2011-04-05
> **cariboo907 said:**
> There's your problem bolded in the quote, you're running a 32-bit version, and not using at least a pae kernel. I'd suggest installing a 64-bit version.

You can get the ubuntu-10.10-desktop-amd64.iso   [here]("http://releases.ubuntu.com/10.10/")

Now I feel stupid, downloading now.  Thanks for the help

---

