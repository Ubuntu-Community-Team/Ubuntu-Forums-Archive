---
title: "New User -- Lenovo FLEX4-1130 bad eMMC Ubuntu 16.04LTS?"
date: 2018-03-25
forum: Installation &amp; Upgrades
---

### Post by mrpuzzl3 on 2018-03-25
Hi... I'm trying to resurrect a Lenovo FLEX4-1130 which has a bad eMMC (internal SSD, soldered on). So far:
1. Can boot Ubuntu from USB (Try Ubuntu) with UEFI DISABLED
2. Can't boot ANYTHING from UEFI (Black screen with not blinking cursor, top left)
3. Can run LIVE Ubuntu (Legacy Mode) flawlessly off any USB (yay! I like it!)
4. Can INSTALL from USB to OTHER USB, see GRUB (select anything boots to black screen)
5. Running boot-repair to make UEFI gives error (CAN'T FIX UEFI IN LEGACY MODE)

:( This computer was free, so I'm not OUT anything if I only have to keep using LIVE mode but I really want to be able to install and use Ubuntu with drivers, etc...

[http://paste.ubuntu.com/p/GrsQvyXmsY/](http://paste.ubuntu.com/p/GrsQvyXmsY/)

Thanks to anyone who's willing to help sort this ugly mess!

---

### Post by mörgæs on 2018-03-26
Hi, welcome to the fora.

If the eMMC is gone then your best option is to install from one USB stick to another (permanently attached) USB stick like you have tried in step 4. Did you install GRUB onto the USB stick?

---

### Post by mrpuzzl3 on 2018-03-26
I used the live usb to install 16.04lts(internet connected, download updates and install drivers) on to the other usb. Once the install completed, I shut off the laptop, removed the live usb and booted from the installed one. I see the screen to select Ubuntu or terminal, and I can edit commands. I changed quiet splash to nomodeset but I still boot to a black screen, no cursor, nothing.

---

### Post by mörgæs on 2018-03-26
Let's see the hardware details. From a live boot please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it into the command line, run it and post lshw.txt here in CODE tags.

---

### Post by mrpuzzl3 on 2018-03-26
```
 computer
    description: Notebook
    product: 80U3 (LENOVO_MT_80U3_BU_idea_FM_Lenovo ideapad FLEX 4-1130)
    vendor: LENOVO
    version: Lenovo ideapad FLEX 4-1130
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=notebook family=ideapad frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_80U3_BU_idea_FM_Lenovo ideapad FLEX 4-1130 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Sofia-F
       vendor: LENOVO
       physical id: 0
       version: SDK0J91204WIN
       serial: [REMOVED]
       slot: Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 2MCN23WW
          date: 09/27/2016
          size: 64KiB
          capacity: 3008KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU N3350 @ 1.10GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU N3350 @ 1.10GHz
          serial: [REMOVED]
          slot: U3E1
          size: 2361MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg cx16 xtpr pdcm sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave rdrand lahf_lm 3dnowprefetch intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust smep erms mpx rdseed smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts cpufreq
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
          physical id: 23
          slot: System board or motherboard
          size: 2GiB
        *-bank
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             vendor: 0000
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 2GiB
             width: 8 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0a
          width: 32 bits
          clock: 33MHz
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:24 memory:91410000-91417fff
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:370 memory:90000000-90ffffff memory:80000000-8fffffff ioport:2000(size=64) memory:c0000-dffff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:372 memory:91418000-9141bfff memory:91200000-912fffff
        *-communication:0
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:371 memory:91420000-91420fff
        *-communication:1 UNCLAIMED
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:91421000-91421fff
        *-communication:2 UNCLAIMED
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: f.2
             bus info: pci@0000:00:0f.2
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:91422000-91422fff
        *-generic:1 UNCLAIMED
             description: Unclassified device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:9141c000-9141dfff memory:91423000-91423fff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 0a
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:368 memory:9141e000-9141ffff memory:91430000-914300ff ioport:2080(size=8) ioport:2088(size=4) ioport:2060(size=32) memory:9142e000-9142e7ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: fa
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:120 memory:91000000-911fffff
           *-network
                description: Wireless interface
                product: Qualcomm Atheros
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 31
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=4.8.0-36-generic firmware=WLAN.TF.1.0-00267-1 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:373 memory:91000000-911fffff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: fa
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:121 ioport:1000(size=4096) memory:91300000-913fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 15
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:369 ioport:1000(size=256) memory:91304000-91304fff memory:91300000-91303fff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:122 memory:91400000-9140ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.8.0-36-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: USB 2.0 FD
                   vendor: PNY Technologies
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi1
                   version: 1.10
                   serial: [REMOVED]
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=300mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@1:0.0.0
                      logical name: /dev/sda
                      size: 29GiB (31GB)
                      capabilities: partitioned partitioned:dos
                      configuration: logicalsectorsize=512 sectorsize=512 signature=0790d2d7
                    *-volume
                         description: Windows FAT volume
                         vendor: SYSLINUX
                         physical id: 1
                         bus info: scsi@1:0.0.0,1
                         logical name: /dev/sda1
                         logical name: /cdrom
                         version: FAT32
                         serial: [REMOVED]
                         size: 29GiB
                         capacity: 29GiB
                         capabilities: primary bootable fat initialized
                         configuration: FATs=2 filesystem=fat label=LUBUNTU 16_ mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: Atheros Communications, Inc.
                   physical id: 5
                   bus info: usb@1:5
                   version: 0.01
                   capabilities: bluetooth usb-2.01
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: Video
                   product: EasyCamera
                   vendor: SunplusIT Inc
                   physical id: 6
                   bus info: usb@1:6
                   version: 53.09
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.8.0-36-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
                capabilities: usb-3.00
                configuration: driver=hub slots=7 speed=5000Mbit/s
        *-generic:2
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:27 memory:91424000-91424fff memory:91425000-91425fff
        *-generic:3
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:30 memory:91426000-91426fff memory:91427000-91427fff
        *-generic:4
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:31 memory:91428000-91428fff memory:91429000-91429fff
        *-generic:5
             description: SD Host controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=0
             resources: irq:3 memory:9142a000-9142afff memory:9142b000-9142bfff
        *-generic:6
             description: SD Host controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=0
             resources: irq:39 memory:9142c000-9142cfff memory:9142d000-9142dfff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: Broxton SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 0a
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:9142f000-9142f0ff ioport:2040(size=32)
  *-battery
       description: Lithium Ion Battery
       product: SR Real Battery
       vendor: Intel SR 1
       physical id: 1
       version: Date
       serial: [REMOVED]
       slot: I2C2
       configuration: voltage=3.8V
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: [REMOVED]
       capacity: 75mWh


```

---

### Post by mörgæs on 2018-03-27
The N3350 is a fairly new processor. Does it work differently with 17.10.1?

---

### Post by mrpuzzl3 on 2018-03-27
Nope. I originally started with 17.10 but switched to 16.04lts upon reading that it provided greater stability and support. 17.10 exhibits the same behavior.

---

### Post by mörgæs on 2018-03-28
Choosing a Buntu release is always a trade-off between stability and hardware support. It's difficult to get both.

Anyway, it didn't change anything here. Does this help?
[https://forums.lenovo.com/t5/Linux-Discussion/Installing-linux-via-usb-with-uefi-on-lenovo-flex-14/m-p/1393241#M5578](https://forums.lenovo.com/t5/Linux-Discussion/Installing-linux-via-usb-with-uefi-on-lenovo-flex-14/m-p/1393241#M5578)

---

### Post by mrpuzzl3 on 2018-03-29
No. BUT! Having BOTH USB sticks in at the same time allows me to boot into Ubuntu... Go figure?!? I tried using ```
 dd if=/dev/sda of=/dev/sdb bs=64K conv=noerror,sync 
``` and it seems to have copied my drive(Install location, SanDisk Cruzer) to my other USB (PNY) but I can only boot off of the original install drive (SanDisk Cruzer).  I'm able to get to boot screens on both USB drives, but it goes back to the original problem of booting to a black screen. As soon as the PNY AND the SanDisk are in place, and selecting the SanDisk as the boot device, I can get into Ubuntu. In fact, I'm in Ubuntu now using the problem computer to reply to this thread. What are my next steps to make it so that I don't need to have BOTH drives in place to be able to boot?

---

### Post by mörgæs on 2018-03-30
I don't have any further ideas. Isn't it an option to carry on with the system as it is, that is with two USB sticks attached?

---

