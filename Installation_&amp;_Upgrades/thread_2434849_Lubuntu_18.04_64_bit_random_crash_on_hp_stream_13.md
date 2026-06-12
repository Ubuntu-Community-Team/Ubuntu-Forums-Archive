---
title: "Lubuntu 18.04 64 bit random crash on hp stream 13"
date: 2020-01-12
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2020-01-12
Hi,
I installed lubuntu 18.04 64 bit updated to the latest version with kernel 5.0.0-37-generic. The notebook has some problems that I can't detect. If I open demanding applications like brave browsers or firefox, it slows down, then it crashes and I am forced to turn it off by the power button. Other times it works for a few minutes.
I tried to do a memtest and it was passed successfully without any error. I can't understand what it could depend on.

I manually installed the driver of the wireless adapter RTL8723BE by following a thread on ubuntu forum.
Any idea?

```

sudo lshw
mattia-hp-stream            
    description: Notebook
    product: HP Stream Notebook PC 13 (N8J59EA#ABZ)
    vendor: HP
    version: Type1ProductConfigId
    serial: 
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
     configuration: boot=normal chassis=notebook family=103C_5335KV G=N  L=CON B=HP S=STR X=Null sku=N8J59EA#ABZ  uuid=35434436-3133-354B-4C33-334B33314435
  *-core
       description: Motherboard
       product: 817D
       vendor: HP
       physical id: 0
       version: 39.13
       serial: PFLJQ028J191DQ
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.1E
          date: 07/26/2016
          size: 64KiB
          capacity: 3008KiB
           capabilities: pci upgrade shadowing cdboot bootselect edd  int9keyboard int14serial int17printer int10video acpi usb zipboot  biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU  N3050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU  N3050  @ 1.60GHz
          serial: To Be Filled By O.E.M.
          slot: CHV
          size: 1427MHz
          capacity: 2160MHz
          width: 64 bits
          clock: 83MHz
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr  pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx  fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon  pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid  aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est  tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer  aes rdrand lahf_lm 3dnowprefetch epb pti ibrs ibpb stibp tpr_shadow vnmi  flexpriority ept vpid tsc_adjust smep erms dtherm ida arat md_clear  cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
     *-cache
          description: L1 cache
          physical id: 5
          slot: L1 Cache
          size: 24KiB
          capacity: 24KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: Row of chips DDR3 Synchronous 1600 MHz (0,6 ns)
             vendor: Hynix
             physical id: 0
             serial: Not Available
             slot: Top - on board
             size: 2GiB
             width: 8 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: Row of chips DDR Synchronous [empty]
             physical id: 1
             slot: Top - on board
     *-pci
          description: Host bridge
          product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:120 memory:90000000-90ffffff memory:80000000-8fffffff ioport:2000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
             vendor: Intel Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:118 memory:91414000-91414fff
        *-usb
             description: USB controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:115 memory:91400000-9140ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.0.0-37-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=7 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: HP Truevision HD
                   vendor: Sonix Technology Co., Ltd.
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.03
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:1
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 4
                   bus info: usb@1:4
                   version: 88.31
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb
                      description: Bluetooth wireless interface
                      product: Bluetooth Radio
                      vendor: Realtek
                      physical id: 3
                      bus info: usb@1:4.3
                      version: 2.00
                      serial: 00e04c000001
                      capabilities: bluetooth usb-2.10
                      configuration: driver=btusb maxpower=500mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.0.0-37-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:1
             description: Encryption controller
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:119 memory:91300000-913fffff memory:91200000-912fffff
        *-multimedia
             description: Audio device
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:121 memory:91410000-91413fff
        *-pci:0
             description: PCI bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:91100000-911fffff
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:116 memory:91100000-91100fff
        *-pci:1
             description: PCI bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:1000(size=4096) memory:91000000-910fffff
           *-network
                description: Wireless interface
                product: RTL8723BE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlo1
                version: 00
                serial: 68:14:01:0f:9c:89
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                 configuration: broadcast=yes driver=rtl8723be  driverversion=5.0.0-37-generic firmware=N/A ip=10.0.1.252 latency=0  link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:19 ioport:1000(size=256) memory:91000000-91003fff
        *-isa
             description: ISA bridge
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial UNCLAIMED
             description: SMBus
             product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:91415000-9141501f ioport:2040(size=32)
  *-battery
       product: ME03037
       vendor: 33342
       physical id: 1
       version: ManufDate
       serial: DummySerialNumber
       slot: Primary
       capacity: 37050mWh
       configuration: voltage=11,4V
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: OEM Define 3
       capacity: 75mWh

```

---

### Post by CatKiller on 2020-01-12
> **erotavlas said:**
> If I open demanding applications like brave browsers or firefox, it slows down, then it crashes and I am forced to turn it off by the power button. Other times it works for a few minutes. 
That sounds like it's out of memory. You only have 2 GB and browsers, depending on which sites you're visiting and what scripts those sites are running, can use over 1 GB all by themselves. It doesn't look like you can add more RAM to that machine, so reducing memory usage is your only option. Browser extensions that prevent scripts from running might help somewhat.

---

### Post by erotavlas on 2020-01-12
> **CatKiller said:**
> That sounds like it's out of memory. You only have 2 GB and browsers, depending on which sites you're visiting and what scripts those sites are running, can use over 1 GB all by themselves. It doesn't look like you can add more RAM to that machine, so reducing memory usage is your only option. Browser extensions that prevent scripts from running might help somewhat.  Thank you for your fast reply. I setup 2 GB of swap. I monitored with htop, the RAM is full whereas the system gets stuck even if the swap does not become full. In theory it just should slow down. Any idea?

---

### Post by CatKiller on 2020-01-12
> **erotavlas said:**
> Thank you for your fast reply. I setup 2 GB of swap. I monitored with htop, the RAM is full whereas the system gets stuck even if the swap does not become full. In theory it just should slow down. Any idea?

Linux really struggles with low memory situations, and knowing what to swap and when. It's an area of ongoing research. It's very difficult to find something that works for all the workloads that Linux is used for. Not getting in that situation is the only thing that will absolutely work. The OS itself is lightweight, it's the applications that are the issue. In particular, the hordes of unknown applications that get run by advertisers and websites when you visit webpages. You can control what you launch yourself, but they could be doing anything.

---

### Post by Autodave on 2020-01-12
If you can get into Firefox, try installing *uBlock.*

---

### Post by erotavlas on 2020-01-12
> **CatKiller said:**
> Linux really struggles with low memory situations, and knowing what to swap and when. It's an area of ongoing research. It's very difficult to find something that works for all the workloads that Linux is used for. Not getting in that situation is the only thing that will absolutely work. The OS itself is lightweight, it's the applications that are the issue. In particular, the hordes of unknown applications that get run by advertisers and websites when you visit webpages. You can control what you launch yourself, but they could be doing anything.

I solved by installing lubuntu 19.10 64 bit. So it was something related to the kernel or to the desktop environment.

---

### Post by CelticWarrior on 2020-01-12
> **erotavlas said:**
> I solved by installing lubuntu 19.10 64 bit. So it was something related to the kernel or to the desktop environment.

Kernel is the same but the DE in Lubuntu is much lighter so yes, that's the difference. It's the right choice for so little RAM.

---

