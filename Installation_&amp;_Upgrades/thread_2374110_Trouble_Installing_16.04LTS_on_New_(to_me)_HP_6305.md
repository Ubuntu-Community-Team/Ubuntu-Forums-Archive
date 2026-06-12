---
title: "Trouble Installing 16.04LTS on New (to me) HP 6305"
date: 2017-10-12
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2017-10-12
Never had trouble installing Ubuntu before. Today I got a HP 6305 with Windows 10 pre-installed. The first thing I did was to install Ubuntu 16.04LT along side the Windows partition from a USB flash drive. It goes fine, gets to the 'reboot now' screen and reboots. When it comes up, it gets to the maroon colored screen where the ubuntu logo and progress dots are, but the logo and progress never comes up. I tried reinstalling, this time selecting the 'try before you buy' option and that boots up fine. Yet when I reboot, I am still stuck at the maroon / no logo screen. 

Any help/advice? Thanks.

-=[ EDIT ]=-

I looked at the sticky regarding this and I tried to boot to recovery mode. It gets as far as 

```
[240.365998] [<c0104087>] kernel_thread_helper +0x7/0x10
```

and then goes black and stays there. I know I tend to ramble, but there is just too much information in that sticky for me to follow. Again, any help would be greatly appreciated.

---

### Post by mörgæs on 2017-10-13
From the live boot please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by rebeltaz on 2017-10-13
Sure. Here ya go:

```

computer
    description: Low Profile Desktop Computer
    product: HP Compaq Pro 6305 SFF (D4D85UC#ABA)
    vendor: Hewlett-Packard
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=low-profile family=103C_53307F G=D frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=D4D85UC#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 1850
       vendor: Hewlett-Packard
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: K06 v02.57
          date: 08/16/2013
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot uefi
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: [empty]
             physical id: 0
             slot: XMM4
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             vendor: U
             physical id: 1
             serial: [REMOVED]
             slot: XMM3
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: [empty]
             physical id: 2
             slot: XMM2
        *-bank:3
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             vendor: U
             physical id: 3
             serial: [REMOVED]
             slot: XMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cache:0
          description: L1 cache
          physical id: 36
          slot: L1 CACHE
          size: 96KiB
          capacity: 96KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 37
          slot: L2 CACHE
          size: 1MiB
          capacity: 1MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: AMD A4-5300B APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 40
          bus info: cpu@0
          version: AMD A4-5300B APU with Radeon(tm) HD Graphics
          slot: P0
          size: 3400MHz
          capacity: 3400MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: Family 15h (Models 10h-1fh) I/O Memory Management Unit
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht bus_master cap_list
             configuration: latency=0
        *-display
             description: VGA compatible controller
             product: Trinity [Radeon HD 7480D]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:41 memory:d0000000-dfffffff ioport:f000(size=256) memory:ff700000-ff73ffff
        *-multimedia:0
             description: Audio device
             product: Trinity HDMI Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:ff744000-ff747fff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:ff74a000-ff74bfff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-31-generic xhci-hcd
                physical id: 0
                bus info: usb@7
                logical name: usb7
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-31-generic xhci-hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
        *-usb:1
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:17 memory:ff748000-ff749fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-31-generic xhci-hcd
                physical id: 0
                bus info: usb@9
                logical name: usb9
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=2 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-31-generic xhci-hcd
                physical id: 1
                bus info: usb@8
                logical name: usb8
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Hub
                   vendor: ATEN International Co., Ltd
                   physical id: 1
                   bus info: usb@8:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: USB NetVista Full Width Keyboard.
                      vendor: LITE-ON Technology
                      physical id: 1
                      bus info: usb@8:1.1
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=70mA speed=2Mbit/s
                 *-usb:1
                      description: Mouse
                      product: USB Optical Mouse
                      vendor: Logitech
                      physical id: 2
                      bus info: usb@8:1.2
                      version: 43.01
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:33 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:ff751000-ff7517ff
        *-usb:2
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:ff750000-ff750fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-31-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:ff74f000-ff74f0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-31-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
        *-usb:4
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:ff74e000-ff74efff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-31-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=5 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:17 memory:ff74d000-ff74d0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-31-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=5 speed=480Mbit/s
              *-usb
                   description: Mass storage device
                   product: TransMemory-Mx
                   vendor: TOSHIBA
                   physical id: 5
                   bus info: usb@2:5
                   logical name: scsi3
                   version: 1.10
                   serial: [REMOVED]
                   capabilities: usb-2.10 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=300mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@3:0.0.0
                      logical name: /dev/sdb
                      size: 29GiB (31GB)
                      capabilities: partitioned partitioned:dos
                      configuration: logicalsectorsize=512 sectorsize=512 signature=c3072e18
                    *-volume
                         description: Windows FAT volume
                         vendor: SYSLINUX
                         physical id: 1
                         bus info: scsi@3:0.0.0,1
                         logical name: /dev/sdb1
                         logical name: /cdrom
                         version: FAT32
                         serial: [REMOVED]
                         size: 29GiB
                         capacity: 29GiB
                         capabilities: primary bootable fat initialized
                         configuration: FATs=2 filesystem=fat label=123456789 mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia:1
             description: Audio device
             product: FCH Azalia Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:16 memory:ff740000-ff743fff
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: FCH PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
        *-usb:6
             description: USB controller
             product: FCH USB OHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=32
             resources: irq:18 memory:ff74c000-ff74cfff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.4.0-31-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.04
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-pci:1
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: Hudson PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:ff600000-ff6fffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5761 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: enp3s0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5761-v3.81 DASH v1.54.1.0 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:43 memory:ff610000-ff61ffff memory:ff600000-ff60ffff
     *-pci:1
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:5
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 15h (Models 10h-1fh) Processor Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD2500AAKX-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1H19
             serial: [REMOVED]
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=fdef45a9
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 348MiB
                capacity: 350MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2017-10-07 21:20:27 filesystem=ntfs label=System modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: [REMOVED]
                size: 27GiB
                capacity: 27GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2017-10-07 21:20:28 filesystem=ntfs label=Windows modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: [REMOVED]
                size: 14GiB
                capacity: 14GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2017-10-07 21:20:30 filesystem=ntfs label=Recovery image modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 189GiB
                capacity: 189GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3277MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 186GiB
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DH16AESH
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 3HH6
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-power UNCLAIMED
       product: High Efficiency
       physical id: 1
       capacity: 32768mWh

```

---

### Post by rebeltaz on 2017-10-13
I don't know if this means anything, but I tried booting into a text console again, and I noticed that it seemed to hang for about two minutes with five instances of

```
request_modprobe: runaway loop modprobe binfmt-464c
```

before moving on and finally hanging on the kernel_thread_helper line.

---

### Post by slickymaster on 2017-10-13
> **rebeltaz said:**
> 
```
request_modprobe: runaway loop modprobe binfmt-464c
```

That usually signals a mismatch between the word size of the kernel and the userspace modprobe (one is 32bit and one is 64bit) which means you are likely booting a 32-bit kernel with a 64-bit OS.

---

### Post by rebeltaz on 2017-10-13
> **slickymaster said:**
> That usually signals a mismatch between the word size of the kernel and the userspace modprobe (one is 32bit and one is 64bit) which means you are likely booting a 32-bit kernel with a 64-bit OS.

I am using a 64-bit version of 16.04, but does this line in lshw, listed under CPU, not indicate that the CPU is 64-bit?

```
    width: 64 bits 
```

---

### Post by rebeltaz on 2017-10-13
So... I haven't kept up with the advances in computer technology as of late, ever since it became cheaper to just buy a computer than build one for scratch. I didn't even know that computers had Electronic Fuel Injection now. (That's a joke, kid.) 

Anyway, I must have inadvertently turned off something related to UEFI when I was trying to get the computer to boot from a USB flash drive. Once I reset that, I was able to reinstall Ubuntu and now it boots fine. 

I do have another small problem, though. I no longer get a grub menu. It just boots directly into Linux without asking. What do I need to do to get the grub menu back?

---

### Post by mörgæs on 2017-10-14
Pushing Left Shift or Escape repeatedly during boot should give you the menu.

---

### Post by rebeltaz on 2017-10-14
> **mörgæs said:**
> Pushing Left Shift or Escape repeatedly during boot should give you the menu.

I was able to get the grub menu to come up with the left shift key, but the Windows partition is no longer listed. It was there before I re-enabled the UEFI boot options in the BIOS (?) settings, but LInux wouldn't boot. Now Linux will boot, but Windows is missing.

---

### Post by mörgæs on 2017-10-15
> **rebeltaz said:**
> Now Linux will boot, but Windows is missing.

Win-win. 

Now you can give Ubuntu a chance and see how it works. Windows is still there and if some day Ubuntu does not solve all your problems then it can be resurrected.

---

### Post by rebeltaz on 2017-10-15
> **mörgæs said:**
> Win-win. 

Now you can give Ubuntu a chance and see how it works. Windows is still there and if some day Ubuntu does not solve all your problems then it can be resurrected.

lol... I use Ubuntu EXCLUSIVELY on all of my systems. I just left the Windows OS with 35gb of space just in case I decided that I needed it for some reason in the future. I also purposely left the recovery partition, just in case. I've been running Ubuntu for about ten years now and I would NEVER look back to windows. However, I am the kind of person who hates it when something doesn't work like it should, hence my wanting to get the grub menu to show the windows system :)

---

### Post by mörgæs on 2017-10-15
> **rebeltaz said:**
> I've been running Ubuntu for about ten years now and I would NEVER look back to windows.

Sounds like me. 
Sorry, I can't help you here but I'm sure there are many users around with experience in dual boot settings.

---

