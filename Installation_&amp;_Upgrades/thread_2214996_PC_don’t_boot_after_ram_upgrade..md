---
title: "PC don’t boot after ram upgrade."
date: 2014-04-04
forum: Installation &amp; Upgrades
---

### Post by lagostefano-l on 2014-04-04
My problem is this.
Recently I bought a set of ram, the reason is for upgrade not  because I had a problem , but because I want to do a dual boot.
After placing both ram in the computer motherboard it wont boot, and stuck in black screen showing the option that says to click if you want to get into the BIOS (ESC) or where to boot from (DEL). When this happened, the keyboard does not work .

So no available testing with both ram on the m/b.
The following applies for the set of ram tested both chips but individually (one at a time) on each slot of motherboard every time .
The first enters and when I open the terminal and the command "sudo lshw" and code it crashes, the same happens if I try to open a browser.
The second gives me the result of "sudo lshw", but after a quick period it crashes too (by crashing I mean that GUI freeze).
In short , after a few seconds you will get stuck with both of them.
 
So far I tried and checked:
1) To run memtest from grub (with each chip separately) and after login to blue screen it restarts automatically – I suppose it fails.
2) To run from LiveCD 12.04 & 13.10. It shows that with 13.10 it can keep going a little longer and running smoother but eventually it will freeze.
3) I checked for faulty capacitors on the motherboard.
 
So far I really need to try these ram on another pc just to confirm they are not damaged –but I don’t have this option yet.
There is possibility that the motherboard need the last two updates after it’s version installed –but I don’t have the proper equipment for this (UPS) or the knowledge.


Summary:
[B]sudo lshw
[/B]```
desktop       
    description: Desktop Computer
    product: To Be Filled By O.E.M. (To Be Filled By O.E.M.)
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: vsyscall32
     configuration: chassis=desktop family=To Be Filled By O.E.M. sku=To  Be Filled By O.E.M. uuid=0593C46A-1E02-2911-C383-D027881540E7
  *-core
       description: Motherboard
       product: H55MXV Series
       vendor: Foxconn
       physical id: 0
       version: 1.0
       serial: UL81041027741
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080015
          date: 07/22/2010
          size: 64KiB
          capacity: 8128KiB
           capabilities: isa pci pnp apm upgrade shadowing escd cdboot  bootselect socketedrom edd int13floppy1200 int13floppy720  int13floppy2880 int5printscreen int9keyboard int14serial int17printer  int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 3066MHz
          capacity: 3066MHz
          width: 64 bits
          clock: 133MHz
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr  pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx  fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon  pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64  monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2  popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 30
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 4GiB
             width: 64 bits
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 18
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Core Processor PCI Express x16 root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 18
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:f8000000-fbefffff ioport:d4000000(size=201326592)
           *-display
                description: VGA compatible controller
                product: GF106 [GeForce GTS 450]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                 resources: irq:46 memory:f8000000-f8ffffff  memory:d8000000-dfffffff memory:d4000000-d5ffffff ioport:dc00(size=128)  memory:fbe80000-fbefffff
           *-multimedia
                description: Audio device
                product: GF106 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:fbe7c000-fbe7ffff
        *-communication
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:44 memory:f7fffc00-f7fffc0f
        *-usb:0
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7ffc000-f7ffc3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:f7ff8000-f7ffbfff
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:e000(size=4096) memory:fbf00000-fbffffff ioport:f6f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 03
                serial: d0:27:88:15:40:e7
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                 capabilities: pm msi pciexpress msix vpd bus_master  cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt  1000bt-fd autonegotiation
                configuration:  autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI  duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no  multicast=yes port=MII speed=10Mbit/s
                resources:  irq:43 ioport:e800(size=256) memory:f6fff000-f6ffffff  memory:f6ff8000-f6ffbfff memory:fbfe0000-fbffffff
        *-usb:1
             description: USB controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7ff6000-f7ff63ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a6
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 5 Series/3400 Series Chipset 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
              resources: irq:19 ioport:cc00(size=8) ioport:c880(size=4)  ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=16)  ioport:c080(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 06
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7fff800-f7fff8ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 5 Series/3400 Series Chipset 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 06
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
              resources: irq:19 ioport:bc00(size=8) ioport:b880(size=4)  ioport:b800(size=8) ioport:b480(size=4) ioport:b400(size=16)  ioport:b080(size=16)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f7ffe000-f7ffefff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:02.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:02.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST31000528AS
             vendor: Seagate
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sda
             version: CC38
             serial: 9VP9RH7N
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00008b71
           *-volume:0
                description: Linux swap volume
                physical id: 1
                bus info: scsi@1:0.1.0,1
                logical name: /dev/sda1
                version: 1
                serial: e9e8f60a-2418-4ec0-a855-21cbe5d6969d
                size: 18GiB
                capacity: 18GiB
                capabilities: primary bootable nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.1.0,2
                logical name: /dev/sda2
                size: 912GiB
                capacity: 912GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /home
                   capacity: 838GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 74GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7260S
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.5
       logical name: wlan0
       serial: d8:5d:4c:92:49:a7
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=carl9170  driverversion=3.11.0-18-generic firmware=1.9.6 ip=192.168.1.2 link=yes  multicast=yes wireless=IEEE 802.11bgn
```
New Ram:
KINGSTON KHX1333C9D3B1K2/8G 8GB (2X4GB) HYPERX BLU DDR3 DUAL CHANNEL KIT
[http://www.kingston.com/us/memory/hyperx/blu](http://www.kingston.com/us/memory/hyperx/blu)
Size: 8GV (2 x 4GB).
Memory Type: DDR3 - 1333MHz 240-Pin Unbuffered DIMM.
Channel Speed&#8203;&#8203;: 1333MHz.
Timings: 9-9-9-27.
Operating voltage: 1.65V.
Row Cycle Time (tRC): 49.5ns (min).
Refresh to Active / Refresh Command Time (tRFC): 110ns.
Row Active Time (tRAS): 36ns (min).
Operating temperature: 0 ° C - 85 ° C.
 
Motherboard:
Foxconn - Socket 1156 - H55MXV
link: [http://www.foxconnchannel.com/ProductDe ... -us0000488]("http://www.foxconnchannel.com/ProductDetail.aspx?T=motherboard&U=en-us0000488")
Intel® Core™ i7, Core™ i5, Core™ i3processors, Socket LGA1156
Supports Intel® 45nm Hi-K CPU
Dual channel DDR3 1333/1066/800 x 2 DIMMs, Max. 8GB
1* PCIe2.0 x16, 1* PCIe x1, 2* PCI
6* SATA II
5.1 channel HDA
Gigabit LAN
12 USB 2.0 ports
 
Graphics Card:
GeForce GTS450
Link: [http://www.geforce.com/hardware/desktop ... ifications]("http://www.geforce.com/hardware/desktop-gpus/geforce-gts-450/specifications")
GPU Engine Specs
CUDA Cores - 192
Graphics Clock (MHz) - 783 MHz
Processor Clock (MHz) - 1566 MHz
Texture Fill Rate (billion/sec) - 25.1
Memory Specs
Memory Clock - 1804 (3608 data rate) MHz
Memory Interface - GDDR5
Memory Interface Width - 128-bit
Memory Bandwidth (GB/sec) - 57.7
Feature Support
OpenGL - 4.2
Bus Support- PCI-E 2.0 x 16
Supported Technologies - SLI, DirectX 11, CUDA, 3D Vision, PhysX
SLI Options<p>1 - 2-way
 
**CPU:**
4x Intel(R)Core(TM) i3 CPU 540 @3.07GHz
 
All responses are welcomed and thank you for your time in advance.

---

### Post by lagostefano-l on 2014-04-04
I am closing this post as i come to conclusion that this might be hardware issue.
Sorry for spamming, if possible please delete the entire post.
Regards
The Rabbit

---

### Post by mörgæs on 2014-04-04
We don't delete posts, but please mark it 'solved'.

---

