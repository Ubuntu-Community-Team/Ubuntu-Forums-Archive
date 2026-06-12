---
title: "*ERROR* conflict detected with stolen region"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by murcielago75 on 2014-04-20
I just did clean install of Ubuntu 14.04. 

At some point of tweaking process (possibly after enabling proprietary nvidia drivers), I noticed this message during boot (before BIOS):
```

[     12.181905]   [drm:i915_stolen_to_physical] *ERROR* conflict detected with stolen region:[0xcba00000  -  0xcfa00000]

```
The message just flashes for one second then everything seems to work normally. Does anyone have any idea what this means and how to solve it? 

I tried alternating between proprietary and nouveau drivers. 

I am not an advanced user but I can follow command line indications.


I am pasting output of  sudo lshw
```

mark-z68xp-ud3            
    description: Desktop Computer
    product: Z68XP-UD3 ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-50E549589ADC
  *-core
       description: Motherboard
       product: Z68XP-UD3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F3
          date: 06/15/2011
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2500K CPU
          slot: Socket 1155
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 6MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM 1333 MHz (0,8 ns)
             physical id: 0
             slot: A0
             size: 4GiB
             width: 2244 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0,8 ns)
             physical id: 1
             slot: A1
             size: 4GiB
             width: 2244 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM 1333 MHz (0,8 ns)
             physical id: 2
             slot: A2
             size: 4GiB
             width: 2244 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM 1333 MHz (0,8 ns)
             physical id: 3
             slot: A3
             size: 4GiB
             width: 2244 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:b000(size=4096) memory:f6000000-f9ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: GF104 [GeForce GTX 460]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:46 memory:f6000000-f7ffffff memory:e0000000-e7ffffff memory:ec000000-efffffff ioport:bf00(size=128) memory:e8000000-e807ffff
           *-multimedia
                description: Audio device
                product: GF104 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f9ffc000-f9ffffff
        *-display
             description: Display controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=i915 latency=0
             resources: irq:47 memory:fb400000-fb7fffff memory:d0000000-dfffffff ioport:ff00(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:45 memory:fbfff000-fbfff00f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:fbffe000-fbffe3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:fbff8000-fbffbfff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:cfa00000-cfbfffff ioport:cfc00000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:fbb00000-fbbfffff
           *-pci
                description: PCI bridge
                product: Integrated Technology Express, Inc.
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
                resources: ioport:e000(size=4096) memory:fbb00000-fbbfffff
              *-firewire
                   description: FireWire (IEEE 1394)
                   product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                   vendor: VIA Technologies, Inc.
                   physical id: 2
                   bus info: pci@0000:04:02.0
                   version: c0
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm ohci bus_master cap_list
                   configuration: driver=firewire_ohci latency=32 maxlatency=32
                   resources: irq:17 memory:fbbff000-fbbff7ff ioport:ef00(size=128)
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fba00000-fbafffff
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:41 memory:fbaf8000-fbafffff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:fbe00000-fbefffff
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:42 memory:fbef8000-fbefffff
        *-pci:5
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:d000(size=4096) ioport:fbd00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 06
                serial: 50:e5:49:58:9a:dc
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.105 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:de00(size=256) memory:fbdff000-fbdfffff memory:fbdf8000-fbdfbfff
        *-pci:6
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:c000(size=4096) memory:fbc00000-fbcfffff ioport:cfe00000(size=1048576)
           *-ide
                description: IDE interface
                product: 88SE9172 SATA III 6Gb/s RAID Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm msi pciexpress bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:44 ioport:cf00(size=8) ioport:ce00(size=4) ioport:cd00(size=8) ioport:cc00(size=4) ioport:cb00(size=16) memory:fbcff000-fbcff1ff memory:cfe00000-cfe0ffff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fbffd000-fbffd3ff
        *-isa
             description: ISA bridge
             product: Z68 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:fe00(size=8) ioport:fd00(size=4) ioport:fc00(size=8) ioport:fb00(size=4) ioport:fa00(size=16) ioport:f900(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fbffc000-fbffc0ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f700(size=8) ioport:f600(size=4) ioport:f500(size=8) ioport:f400(size=4) ioport:f300(size=16) ioport:f200(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10EARX-00N
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 51.0
             serial: WD-WCC0S0056539
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=000ce005
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: b516dc2e-c440-486c-bb09-6c05fec23d95
                size: 915GiB
                capacity: 915GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-04-19 00:16:10 filesystem=ext4 lastmountpoint=/ modified=2014-04-20 11:45:34 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-04-20 11:45:34 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 15GiB
                capacity: 15GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 15GiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: EXT4 volume
             product: WDC WD10EARX-00N
             vendor: Linux
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 1.0
             serial: 8638dbe0-fdc5-4941-9a5f-aaaad09bebf3
             size: 931GiB
             capabilities: journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
             configuration: ansiversion=5 created=2011-12-07 01:39:49 filesystem=ext4 label=Mark Backup Disk lastmountpoint=/media/mark/Mark Backup Disk modified=2014-04-20 11:23:08 mounted=2014-04-20 10:35:43 sectorsize=4096 state=clean
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7280S
             vendor: Optiarc
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:1.4
       logical name: wlan0
       serial: c0:4a:00:16:c5:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu ip=192.168.1.106 multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by bapoumba on 2014-04-20
Probably this : [https://bugs.freedesktop.org/show_bug.cgi?id=71031](https://bugs.freedesktop.org/show_bug.cgi?id=71031)

Tried to find the latest one, applies to all Linux. I have not found one on Launchpad (but may be I have not looked close engough, just used a search engine), may be you could file a bug : [https://help.ubuntu.com/community/ReportingBugs#Hardware_driver_bugs_.28e.g._sound.2C_Linux_kernel.2C_X.Org.2C_and_Nvidia_.2BAC8_AMD_proprietary_drivers.29](https://help.ubuntu.com/community/ReportingBugs#Hardware_driver_bugs_.28e.g._sound.2C_Linux_kernel.2C_X.Org.2C_and_Nvidia_.2BAC8_AMD_proprietary_drivers.29)

---

### Post by Peter_Waller on 2014-04-22
I've encountered this too, and now I have a non-bootable system.

I installed a fresh 14.04, and it booted the first time. Then I installed nvidia-current because the desktop was extremely janky to the point of being unusable. When I rebooted, I got this error message and a blank screen.

Any hints on how to make my system bootable again? I guess I just have to go through the rigmarole of livecd booting, chrooting and removing nvidia-current, or building a patched kernel..

---

### Post by Peter_Waller on 2014-04-22
I've removed nvidia-current and now the system us usable via a VT, but not via X11. I just get a blank screen. It appears from the log that X11 is using the intel chip on the motherboard rather than my nvidia video card, however connecting a monitor to the motherboard gives the same blank screen.

So I'm without a functioning desktop environment.

---

### Post by bapoumba on 2014-04-22
I'd advise you start a new thread in the Multimedia and Video forum with this later issue.

---

### Post by vandendriessche-pierre on 2014-06-25
[COLOR=#4b0082]Hello,

I have a similar error : 

- running ubuntu LTS 14.04 without nvidia drivers
- when i type CTRL+ALT+F1, it does prompt the error :
                      [     15.148348]   [drm:i915_stolen_to_physical] *ERROR* conflict detected with stolen region:[0xcba00000  -  0xcfa00000]
- when i type CTRL+ALT+F7, it go back to my ubuntu GUI correctly.


Here is my configuration : 
Ubuntu LTS 14.04
my nvidia drivers are not yet installed (that's why i tried to ctrl+alt+f1)
my screen is connected to my nvidia geforce GTX560.

for the person who see nothing on the screen, try to change screen connexion and plug in to the integrated hdmi output of the mother-board.

I think it's a incompatibility between mother's board integrated intel graphic and NVIDIA Geforce GTX 560 PCIe/SSE2.
The configuration's files are perhaps inconsistent.

I will try to install nvidia drivers so i will come back to report.

here is the "sudo lshw" command : 
[/COLOR]
Code : 
```
pvdd-z68xp-ud3            
    description: Desktop Computer
    product: Z68XP-UD3 ()
    vendor: wortmann
    serial: R2870579
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-50E5495561FB
  *-core
       description: Motherboard
       product: Z68XP-UD3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F6 WG
          date: 09/27/2011
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2600 CPU
          slot: Socket 1155
          size: 1900MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 8MiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 19
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM 1333 MHz (0,8 ns)
             physical id: 0
             slot: A0
             size: 4GiB
             width: 2180 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0,8 ns)
             physical id: 1
             slot: A1
             size: 4GiB
             width: 2180 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:f6000000-f9ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: GF114 [GeForce GTX 560]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f6000000-f7ffffff memory:e0000000-e7ffffff memory:ec000000-efffffff ioport:cf00(size=128) memory:e8000000-e807ffff
           *-multimedia
                description: Audio device
                product: GF114 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f9ffc000-f9ffffff
        *-display
             description: Display controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=i915 latency=0
             resources: irq:47 memory:fb400000-fb7fffff memory:d0000000-dfffffff ioport:ff00(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:46 memory:fbfff000-fbfff00f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:fbffe000-fbffe3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:fbff4000-fbff7fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:2000(size=4096) memory:cfa00000-cfbfffff ioport:cfc00000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:b000(size=4096) memory:fbc00000-fbcfffff
           *-pci
                description: PCI bridge
                product: Integrated Technology Express, Inc.
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 10
                width: 32 bits
                clock: 33MHz
                capabilities: pci pciexpress pm normal_decode bus_master cap_list
                resources: ioport:b000(size=4096) memory:fbc00000-fbcfffff
              *-network
                   description: Ethernet interface
                   product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
                   vendor: Realtek Semiconductor Co., Ltd.
                   physical id: 0
                   bus info: pci@0000:04:00.0
                   logical name: eth1
                   version: 10
                   serial: 80:1f:02:22:bb:37
                   size: 10Mbit/s
                   capacity: 100Mbit/s
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                   configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                   resources: irq:19 ioport:bc00(size=256) memory:fbcff000-fbcff0ff
              *-firewire
                   description: FireWire (IEEE 1394)
                   product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                   vendor: VIA Technologies, Inc.
                   physical id: 2
                   bus info: pci@0000:04:02.0
                   version: c0
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm ohci bus_master cap_list
                   configuration: driver=firewire_ohci latency=32 maxlatency=32
                   resources: irq:17 memory:fbcfe000-fbcfe7ff ioport:bf00(size=128)
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:fbb00000-fbbfffff
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:41 memory:fbbf8000-fbbfffff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:fba00000-fbafffff
           *-usb
                description: USB controller
                product: EJ168 USB 3.0 Host Controller
                vendor: Etron Technology, Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:42 memory:fbaf8000-fbafffff
        *-pci:5
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) ioport:fbe00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 06
                serial: 50:e5:49:55:61:fb
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.1.16 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:43 ioport:ee00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff
        *-pci:6
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:d000(size=4096) memory:fbd00000-fbdfffff ioport:cfe00000(size=1048576)
           *-storage
                description: SATA controller
                product: 88SE9172 SATA 6Gb/s Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:45 ioport:df00(size=8) ioport:de00(size=4) ioport:dd00(size=8) ioport:dc00(size=4) ioport:db00(size=16) memory:fbdff000-fbdff1ff memory:cfe00000-cfe0ffff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fbffd000-fbffd3ff
        *-pci:7
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode cap_list
        *-isa
             description: ISA bridge
             product: Z68 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:fe00(size=8) ioport:fd00(size=4) ioport:fc00(size=8) ioport:fb00(size=4) ioport:fa00(size=32) memory:fbffc000-fbffc7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fbffb000-fbffb0ff ioport:500(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: OCZ-SOLID3
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2.15
             serial: OCZ-ORXU3NZHQ90TZUSJ
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=03102ca3
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 6e1d1775-7371-7e47-93fe-0a4243a446d6
                size: 55GiB
                capacity: 55GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-11-22 09:22:13 filesystem=ntfs state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST2000DL003-9VT1
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: CC3C
             serial: 5YD5PZD9
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=d0ea2897
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/pvdd/CC942B13942AFF96
                version: 3.1
                serial: 0046da3d-c4a6-944c-be3c-29477ed95ffa
                size: 1843GiB
                capacity: 1843GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-11-22 20:51:45 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: 8a89dc71-bd99-4b4c-9a13-e3276237fd50
                size: 19GiB
                capacity: 19GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-02-12 09:51:08 filesystem=ntfs label=Not Protected Yet state=clean
     *-scsi:2
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD20EARX-00P
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdc
             version: 51.0
             serial: WD-WCAZAL564567
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0003aa7f
           *-volume:0
                description: Extended partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdc1
                size: 15GiB
                capacity: 15GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdc5
                   capacity: 15GiB
                   capabilities: nofs
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sdc2
                logical name: /
                version: 1.0
                serial: c6cd9e46-c992-4de6-ab35-c7a72b28e5f7
                size: 1847GiB
                capacity: 1847GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-07-26 18:55:54 filesystem=ext4 lastmountpoint=/ modified=2014-06-24 21:05:47 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-06-24 21:05:47 state=mounted
     *-scsi:3
          physical id: 5
          bus info: usb@2:1.1
          logical name: scsi8
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: STORAGE DEVICE
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@8:0.0.0
             logical name: /dev/sdd
             version: 0207
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdd
     *-scsi:4
          physical id: 6
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: iHAS122
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: ZL0F
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc


```

---

