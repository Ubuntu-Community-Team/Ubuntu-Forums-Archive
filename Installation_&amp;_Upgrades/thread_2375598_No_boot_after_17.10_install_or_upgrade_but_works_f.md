---
title: "No boot after 17.10 install or upgrade but works fine after 17.04 install..."
date: 2017-10-25
forum: Installation &amp; Upgrades
---

### Post by kb8aob on 2017-10-25
I have tried several times/ways to install 17.10 mate on an old Shuttle "desktop" from a CD with install success but it will not boot when done. I do the same with a CD of 17.04 and presto it works fine. I have used the same CD of 17.10 to install on an old Dell D600 and it works like a charm and is what I am using to type this. 

Using the boot-able install of 17.04 on the Shuttle I have let the system upgrade to 17.10 and same problem -- it will not boot when restarted. 

Weird... 

Ideas?

---

### Post by mörgæs on 2017-10-26
Hi, welcome to the fora.

Please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the terminal, run it and post lshw.txt in CODE tags. Can be done from 17.04 or 17.10 as you prefer.

---

### Post by kb8aob on 2017-10-26
```
computer
    description: Desktop Computer
    product: XS35 (To Be Filled By O.E.M.)
    vendor: Standard
    version: To Be Filled By O.E.M.
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=[REMOVED]
  *-core
       description: Motherboard
       product: B10IE01
       vendor: Shuttle
       physical id: 0
       version: To be filled by O.E.M.
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080015
          date: 06/23/2011
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Atom(TM) CPU D525   @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.10
          serial: [REMOVED]
          slot: CPU 1
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts cpuid aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dtherm
          configuration: cores=2 enabledcores=2 id=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 48KiB
             capacity: 48KiB
             capabilities: internal write-back data
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
             configuration: level=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.12.10
          serial: [REMOVED]
          size: 1800MHz
          capabilities: ht
          configuration: id=2
        *-logicalcpu:0
             description: Logical CPU
             physical id: 2.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 2.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 2.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 2.4
             capabilities: logical
     *-pci
          description: Host bridge
          product: Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:fe980000-fe9fffff ioport:cc00(size=8) memory:d0000000-dfffffff memory:fe800000-fe8fffff memory:c0000-dffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fe780000-fe7fffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:24 memory:fe978000-fe97bfff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:d000(size=4096) memory:fea00000-feafffff ioport:c0400000(size=2097152)
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:feaffc00-feaffcff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:feaff800-feaff8ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:18 memory:feaff400-feaff4ff
           *-network
                description: Ethernet interface
                product: JMC250 PCI Express Gigabit Ethernet Controller
                vendor: JMicron Technology Corp.
                physical id: 0.5
                bus info: pci@0000:02:00.5
                logical name: enp2s0f5
                version: 03
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=full ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:25 memory:feaf4000-feaf7fff ioport:dc00(size=128) ioport:d800(size=256)
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:e000(size=4096) memory:feb00000-febfffff ioport:c0600000(size=2097152)
           *-network
                description: Wireless interface
                product: RTL8188CE 802.11b/g/n WiFi Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 01
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192ce driverversion=4.13.0-16-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:19 ioport:e800(size=256) memory:febfc000-febfffff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c880(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c800(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 2
                   bus info: usb@3:2
                   version: 24.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c480(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c400(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.13.0-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.13
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Keyboard
                   product: Dell QuietKey Keyboard
                   vendor: Dell
                   physical id: 2
                   bus info: usb@5:2
                   version: 1.50
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=70mA speed=2Mbit/s
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fe977c00-fe977fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.13.0-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb
                   description: Mass storage device
                   product: MT1887
                   vendor: MediaTek Inc
                   physical id: 6
                   bus info: usb@1:6
                   logical name: scsi2
                   version: 0.00
                   serial: [REMOVED]
                   capabilities: usb-2.00 atapi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
                 *-cdrom
                      description: DVD-RAM writer
                      product: CDDVDW SE-218CB
                      vendor: TSSTcorp
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/cdrom
                      logical name: /dev/cdrw
                      logical name: /dev/dvd
                      logical name: /dev/dvdrw
                      logical name: /dev/sr0
                      version: TS00
                      capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                      configuration: status=open
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff90(size=16) memory:c0800000-c08003ff
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MQ01ABD1
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1U
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=260f7011
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 498MiB
                capacity: 500MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2017-10-25 04:52:38 filesystem=ntfs label=System Reserved modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 194GiB
                capacity: 194GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2017-10-25 04:52:58 filesystem=ntfs state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 736GiB
                capacity: 736GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   version: 1.0
                   serial: [REMOVED]
                   size: 736GiB
                   capacity: 736GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration: created=2017-10-24 21:57:50 filesystem=ext4 lastmountpoint=/ modified=2017-10-26 11:35:10 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-10-26 11:35:53 state=mounted
```

---

### Post by kb8aob on 2017-10-26
I have also noted it will boot into 17.10 if I select the recover mode and once in the menu select the boot normally it will then boot okay. But that needs to be repeated the next time as it will not boot directly.

---

### Post by mörgæs on 2017-10-27
There are some reports of similar bugs for Atom processors with Intel graphics:
[https://bugs.launchpad.net/ubuntu/+bug/1724639](https://bugs.launchpad.net/ubuntu/+bug/1724639)

As you can see there is attention on the problem. 

I suggest that you stay with 17.04 until support runs out in january. At that time you can try 17.10 and its new kernel again.

---

### Post by kb8aob on 2017-10-27
Okay Thanks

---

