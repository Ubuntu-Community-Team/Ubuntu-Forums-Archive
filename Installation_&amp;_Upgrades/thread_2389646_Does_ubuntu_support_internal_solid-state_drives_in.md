---
title: "Does ubuntu support internal solid-state drives in RAID (Intel RST) mode"
date: 2018-04-19
forum: Installation &amp; Upgrades
---

### Post by merocom on 2018-04-19
hello everyone,

My lapto is ASUS ROG G701VIK gamming with OS Windows 10 preinstalled on M.2 NVMe SSD RAID0 
My Bios set SATA Controller to : intel SRT premium ( No more option such as AHCI )
issues:
 - During ubuntu installation doesn't detected my SSD
 - If i break RAID to separate SSD also not detected SSd

Please any advises for resolve 
Thanks

---

### Post by oldfred on 2018-04-19
See these which are also RAID 0.
Note that RAID 0 is not recommended.

And if you break the RAID 0 you will lose all data on both drives as it alternates to make system fast. With hard drives it was alternate tracks, not sure exactly how RAID 0 works with SSDs.

Really old Sony
 Sony Vaio  - EFI dualboot Ubuntu 12.04 and Windows 8 in Raid 0 
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/) 
Asus
[http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04) 
      Acer Aspire S7 can't install ubuntu - UltraBook erased RAID 0 meta-data
[URL="http://ubuntuforums.org/showthread.php?t=2121187"]http://ubuntuforums.org/showthread.php?t=2121187
[/URL]MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815) 

It used to be that the desktop installer would not even recognize any type of RAID. Back with 12.04 there was an alternative desktop installer that included RAID & LVM drivers. When discontinued, they said to use 12.04 and upgrade and eventually they would update the standard installer to include RAID & LVM. Now the desktop installer will install LVM and sees RAID, but will not install grub.
You may be able to use the server installer that has RAID drivers and add desktop of choice. I also saw someone posted that Lubuntu still has an alternative installer.

[URL="http://ubuntuforums.org/showthread.php?t=2121187"]
[/URL]

---

### Post by merocom on 2018-04-22
Nothing happened, i'm feeling bored with my laptop

---

### Post by merocom on 2018-04-22
this link for laptop System76 : [https://system76.com/laptops/bonobo](https://system76.com/laptops/bonobo). same my laptop specification specially M.2 PCI/SSD and hold Linux ????

---

### Post by merocom on 2018-04-22
```
root@ubuntu:/home/ubuntu# lshw
ubuntu                      
    description: Notebook
    product: G701VIK
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: H7N0CY00J82330E
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=G uuid=892253C4-E7A4-4CE0-9B50-E33CD57B2F60
  *-core
       description: Motherboard
       product: G701VIK
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: N0CY1719MB0024174
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: G701VIK.305
          date: 05/09/2017
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 8
          slot: System board or motherboard
          size: 64GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: 76.D305G.D060B
             vendor: AMD
             physical id: 0
             serial: 00717072
             slot: ChannelA-DIMM0
             size: 16GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: 76.D305G.D060B
             vendor: AMD
             physical id: 1
             serial: 00717072
             slot: ChannelA-DIMM1
             size: 16GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:2
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: 76.D305G.D060B
             vendor: AMD
             physical id: 2
             serial: 00717072
             slot: ChannelB-DIMM0
             size: 16GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:3
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: 76.D305G.D060B
             vendor: AMD
             physical id: 3
             serial: 00517083
             slot: ChannelB-DIMM1
             size: 16GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-cache:0
          description: L1 cache
          physical id: e
          slot: L1 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: f
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 10
          slot: L3 Cache
          size: 8MiB
          capacity: 8MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-7820HK CPU @ 2.90GHz
          vendor: Intel Corp.
          physical id: 11
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-7820HK CPU @ 2.90GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 3558MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Skylake PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:e000(size=4096) memory:eb000000-ec0fffff ioport:a0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GP104M [GeForce GTX 1080 Mobile]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:126 memory:eb000000-ebffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:e000(size=128) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Sunrise Point-H USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:124 memory:ec390000-ec39ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.15.0-13-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: ROG SICA
                   vendor: ASUS
                   physical id: 1
                   bus info: usb@1:1
                   version: 34.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Video
                   product: USB2.0 HD UVC WebCam
                   vendor: 04081-0009510017021009551
                   physical id: 4
                   bus info: usb@1:4
                   version: 0.02
                   serial: 200901010001
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Mass storage device
                   product: USB DISK
                   vendor: SMI Corporation
                   physical id: 5
                   bus info: usb@1:5
                   logical name: scsi16
                   version: 11.00
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: USB DISK
                      vendor: SMI
                      physical id: 0.0.0
                      bus info: scsi@16:0.0.0
                      logical name: /dev/sda
                      version: 1100
                      serial: AA00000000000489
                      size: 7680MiB (8053MB)
                      capabilities: removable
                      configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sda
                         size: 7680MiB (8053MB)
                         capabilities: partitioned partitioned:dos
                         configuration: signature=00016973
                       *-volume
                            description: Windows FAT volume
                            vendor: SYSLINUX
                            physical id: 1
                            logical name: /dev/sda1
                            logical name: /cdrom
                            version: FAT32
                            serial: d85b-bc32
                            size: 7676MiB
                            capacity: 7679MiB
                            capabilities: primary bootable fat initialized
                            configuration: FATs=2 filesystem=fat label=UBUNTU 18_0 mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
              *-usb:3
                   description: Keyboard
                   product: ROG MacroKey
                   vendor: ASASTeK COMPUTER INC.
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.03
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:4
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 9
                   bus info: usb@1:9
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.15.0-13-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-3.00
                configuration: driver=hub slots=10 speed=5000Mbit/s
        *-generic:0
             description: Signal processing controller
             product: Sunrise Point-H Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:ec3b5000-ec3b5fff
        *-generic:1
             description: Signal processing controller
             product: Sunrise Point-H Serial IO I2C Controller #0
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:16 memory:ec3b4000-ec3b4fff
        *-generic:2
             description: Signal processing controller
             product: Sunrise Point-H Serial IO I2C Controller #1
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:17 memory:ec3b3000-ec3b3fff
        *-communication
             description: Communication controller
             product: Sunrise Point-H CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:127 memory:ec3b2000-ec3b2fff
        *-storage
             description: RAID bus controller
             product: SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: storage msix pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:16 memory:ec3a0000-ec3a7fff memory:ec3b1000-ec3b10ff ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:ec300000-ec37ffff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:121 memory:ec200000-ec2fffff
           *-network
                description: Wireless interface
                product: Wireless 8260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 3a
                serial: cc:2f:71:3c:3a:f2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-13-generic firmware=34.0.1 ip=192.168.254.27 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:128 memory:ec200000-ec201fff
        *-pci:3
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:d000(size=4096) memory:ec100000-ec1fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 10
                serial: 70:4d:7b:46:c0:79
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:125 ioport:d000(size=256) memory:ec104000-ec104fff memory:ec100000-ec103fff
        *-pci:4
             description: PCI bridge
             product: Sunrise Point-H PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:2000(size=4096) memory:bc000000-ea0fffff ioport:2fb0000000(size=1241513984)
        *-isa
             description: ISA bridge
             product: Sunrise Point-H LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-H PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 31
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: latency=0
             resources: memory:ec3ac000-ec3affff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:129 memory:ec3a8000-ec3abfff memory:ec380000-ec38ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-H SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 31
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:ec3b0000-ec3b00ff ioport:f000(size=32)
```

---

### Post by oldfred on 2018-04-22
You also have nVidia and need nomodeset boot parameter.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

But with your RAID 0 you may need to use the Server installer and then add desktop of your choice.

---

### Post by merocom on 2018-04-23
ubuntu@ubuntu:~$ lspci -n
00:00.0 0600: 8086:5910 (rev 05)
00:01.0 0604: 8086:1901 (rev 05)
00:14.0 0c03: 8086:a12f (rev 31)
00:14.2 1180: 8086:a131 (rev 31)
00:15.0 1180: 8086:a160 (rev 31)
00:15.1 1180: 8086:a161 (rev 31)
00:16.0 0780: 8086:a13a (rev 31)
00:17.0 0104: 8086:2822 (rev 31)
00:1c.0 0604: 8086:a110 (rev f1)
00:1c.2 0604: 8086:a112 (rev f1)
00:1c.3 0604: 8086:a113 (rev f1)
00:1c.4 0604: 8086:a114 (rev f1)
00:1f.0 0601: 8086:a154 (rev 31)
00:1f.2 0580: 8086:a121 (rev 31)
00:1f.3 0403: 8086:a171 (rev 31)
00:1f.4 0c05: 8086:a123 (rev 31)
01:00.0 0300: 10de:1be0 (rev a1)
03:00.0 0280: 8086:24f3 (rev 3a)
04:00.0 0200: 10ec:8168 (rev 10)
ubuntu@ubuntu:~$

---

### Post by merocom on 2018-04-23
PCI ID	Works?	Vendor	Device	Driver	Kernel
80865910					
80861901		Intel Corporation	Sky Lake PCIe Controller (x16)		
8086a12f		Intel Corporation	Sunrise Point-H USB 3.0 xHCI Controller		
8086a131		Intel Corporation	Sunrise Point-H Thermal subsystem		
8086a160		Intel Corporation	Sunrise Point-H LPSS I2C Controller #0		
8086a161		Intel Corporation	Sunrise Point-H LPSS I2C Controller #1		
8086a13a		Intel Corporation	Sunrise Point-H CSME HECI #1		
80862822	Yes	Intel Corporation	SATA Controller [RAID mode]	ahci	v2.6.25-
8086a110		Intel Corporation	Sunrise Point-H PCI Express Root Port #1		
8086a112		Intel Corporation	Sunrise Point-H PCI Express Root Port #3		
8086a113		Intel Corporation	Sunrise Point-H PCI Express Root Port #4		
8086a114		Intel Corporation	Sunrise Point-H PCI Express Root Port #5		
8086a154		Intel Corporation	Sunrise Point-H LPC Controller		
8086a121		Intel Corporation	Sunrise Point-H PMC		
8086a171					
8086a123		Intel Corporation	Sunrise Point-H SMBus		
10de1be0					
808624f3		Intel Corporation	Wireless 8260		
10ec8168	Yes	Realtek Semiconductor Co., Ltd.	RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller	r8169

---

### Post by oldfred on 2018-04-24
Have you tried server installer & nomodeset boot parameter?

---

### Post by mörgæs on 2018-04-26
> **oldfred said:**
> 
I also saw someone posted that Lubuntu still has an alternative installer.[URL="http://ubuntuforums.org/showthread.php?t=2121187"]
[/URL]

Could have been me. I recommend the alternate ISO as a general first attempt if the standard ISO causes problems.

[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

