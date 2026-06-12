---
title: "Ubuntu 19.10 installation on Lenovo T460p runs into &quot;no working ini found&quot;"
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by thedoughnutlife on 2020-04-15
I am trying to get Ubuntu 19.10 running as the only System on my Lenovo T460p. The installation process goes as follows:
[LIST=1]
[*]Install Ubuntu 
[*]German keyboard layout 
[*]connecting to my wifi (tried without as well) 
[*]normal installation (tried minimal as well), Download updates while installing Ubuntu (tried without as well), install third-party software for (...) (tried without as well) 
[*]erase disk and install Ubuntu (without any of the options) (also tried to partition manually like here: [https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352) without the optional partitions for /boot, /tmp, /var) 
[*]after the installation is done the system wants a restart. 
[*]On boot it runs into a grey screen. 
[*]If i kill it and restart the system starts GNU GRUB version 2.04. 
[*]When I choose Ubuntu here the system runs into "(...) end Kernel panic - not syncing: No working init found. Try passing init= option to kernel. See Linux (...)" 
[/LIST]

I have tried to start with the "nomodeset" option, that doesn't do it.
I have been trying to look for different solutions but nothing has looked promising so far.
Could anyone please help me resolve this issue?

---

### Post by mörgæs on 2020-04-15
Hi, welcome to the fora.

Are you able to run a live boot?

---

### Post by thedoughnutlife on 2020-04-15
Hi,
thank you.

I still have the boot-stick and can "try out Ubuntu" just fine.

The last couple of times that I did, it threw an error "Oh no! Something has gone wrong. A problem has occurred and the system can't recover. Please log out and try again." Then I click "Log Out", it goes to the usual Ubtuntu login-screen with a "Live session user". I can click it and it will load and work just fine from there (from what I can tell).

---

### Post by mörgæs on 2020-04-15
In a live boot please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags. It will show all about the hardware.

---

### Post by thedoughnutlife on 2020-04-15
```

computer
    description: Notebook
    product: 20FW003PMS (LENOVO_MT_20FW_BU_Think_FM_ThinkPad T460p)
    vendor: LENOVO
    version: ThinkPad T460p
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: administrator_password=disabled chassis=notebook family=ThinkPad T460p power-on_password=disabled sku=LENOVO_MT_20FW_BU_Think_FM_ThinkPad T460p uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 20FW003PMS
       vendor: LENOVO
       physical id: 0
       version: SDK0J40697 WIN
       serial: [REMOVED]
       slot: Not Available
     *-cache:0
          description: L1 cache
          physical id: 2
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 3
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: 4
          slot: L2 Cache
          size: 1MiB
          capacity: 1MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 5
          slot: L3 Cache
          size: 8MiB
          capacity: 8MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-6820HQ CPU @ 2.70GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-6820HQ CPU @ 2.70GHz
          serial: [REMOVED]
          slot: U3E1
          size: 3362MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 32GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: CMSO16GX4M1A2133C15
             vendor: AMI
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM0
             size: 16GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: CMSO16GX4M1A2133C15
             vendor: AMI
             physical id: 2
             serial: [REMOVED]
             slot: ChannelB-DIMM0
             size: 16GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:3
             description: [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: d
          version: R07ET63W (2.03 )
          date: 03/15/2016
          size: 128KiB
          capacity: 16MiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification uefi
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122
        *-pci:1
             description: PCI bridge
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x4)
             vendor: Intel Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:d000(size=4096) memory:f1000000-f1ffffff ioport:c0000000(size=301989888)
           *-display
                description: 3D controller
                product: GM108M [GeForce 940MX]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nouveau latency=0
                resources: irq:131 memory:f1000000-f1ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:d000(size=128)
        *-display
             description: VGA compatible controller
             product: HD Graphics 530
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:130 memory:f0000000-f0ffffff memory:e0000000-efffffff ioport:e000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:126 memory:f2220000-f222ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.3.0-18-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.03
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Intenso Rainbow Line
                   vendor: ALCOR
                   physical id: 4
                   bus info: usb@1:4
                   logical name: scsi4
                   version: 1.00
                   serial: [REMOVED]
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Rainbow Line
                      vendor: Intenso
                      physical id: 0.0.0
                      bus info: scsi@4:0.0.0
                      logical name: /dev/sdb
                      version: 8.07
                      serial: [REMOVED]
                      size: 14GiB (16GB)
                      capabilities: removable
                      configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdb
                         size: 14GiB (16GB)
                         capabilities: partitioned partitioned:dos
                         configuration: signature=001bec02
                       *-volume
                            description: Windows FAT volume
                            vendor: SYSLINUX
                            physical id: 1
                            logical name: /dev/sdb1
                            logical name: /cdrom
                            version: FAT32
                            serial: [REMOVED]
                            size: 14GiB
                            capacity: 14GiB
                            capabilities: primary bootable fat initialized
                            configuration: FATs=2 filesystem=fat label=UBUNTU 19_1 mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
              *-usb:1
                   description: Communication device
                   product: HUAWEI Mobile
                   vendor: Huawei Technologies Co., Ltd.
                   physical id: 5
                   bus info: usb@1:5
                   version: 1.02
                   serial: [REMOVED]
                   capabilities: usb-2.10 ethernet
                   configuration: driver=option maxpower=2mA speed=480Mbit/s
              *-usb:2 UNCLAIMED
                   description: Generic USB device
                   product: VFS7500 Touch Fingerprint Sensor
                   vendor: Validity Sensors, Inc.
                   physical id: 6
                   bus info: usb@1:6
                   version: 1.64
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=12Mbit/s
              *-usb:3
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 7
                   bus info: usb@1:7
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:4
                   description: Video
                   product: Integrated Camera
                   vendor: Chicony Electronics Co.,Ltd.
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.09
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:5 UNCLAIMED
                   description: Smart card reader
                   product: EMV Smartcard Reader
                   vendor: Generic
                   physical id: 9
                   bus info: usb@1:9
                   version: 1.20
                   capabilities: usb-2.01
                   configuration: maxpower=50mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.3.0-18-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.03
                capabilities: usb-3.00
                configuration: driver=hub slots=8 speed=5000Mbit/s
        *-generic
             description: Signal processing controller
             product: 100 Series/C230 Series Chipset Family Thermal Subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:f224a000-f224afff
        *-communication:0
             description: Communication controller
             product: 100 Series/C230 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:132 memory:f224b000-f224bfff
        *-communication:1
             description: Serial controller
             product: 100 Series/C230 Series Chipset Family KT Redirection
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: msi pm 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:19 ioport:e080(size=8) memory:f224f000-f224ffff
        *-sata
             description: SATA controller
             product: HM170/QM170 Chipset SATA Controller [AHCI Mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             logical name: scsi0
             version: 31
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:127 memory:f2248000-f2249fff memory:f224e000-f224e0ff ioport:e088(size=8) ioport:e090(size=4) ioport:e060(size=32) memory:f224c000-f224c7ff
           *-disk
                description: ATA Disk
                product: SAMSUNG MZ7LN512
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 1L6Q
                serial: [REMOVED]
                size: 476GiB (512GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=37c284ed
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: [REMOVED]
                   size: 487MiB
                   capacity: 487MiB
                   capabilities: primary bootable nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 476GiB
                   capacity: 476GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 5
                      logical name: /dev/sda5
                      version: 1.0
                      serial: [REMOVED]
                      size: 18GiB
                      capacity: 18GiB
                      capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                      configuration: created=2020-04-15 10:03:05 filesystem=ext4 lastmountpoint=/target modified=2020-04-15 10:13:46 mounted=2020-04-15 10:03:10 state=clean
                 *-logicalvolume:1
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 6
                      logical name: /dev/sda6
                      version: 1.0
                      serial: [REMOVED]
                      size: 457GiB
                      capacity: 457GiB
                      capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                      configuration: created=2020-04-15 10:03:06 filesystem=ext4 lastmountpoint=/home modified=2020-04-15 10:13:45 mounted=2020-04-15 10:03:10 state=clean
        *-pci:2
             description: PCI bridge
             product: 100 Series/C230 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:f2100000-f21fffff
           *-network
                description: Wireless interface
                product: Wireless 8260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 3a
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-18-generic firmware=36.77d01142.0 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:134 memory:f2100000-f2101fff
        *-pci:3
             description: PCI bridge
             product: 100 Series/C230 Series Chipset Family PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 memory:f2000000-f20fffff
           *-generic
                description: Unassigned class
                product: RTS522A PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:129 memory:f2000000-f2000fff
        *-isa
             description: ISA bridge
             product: QM170 Chipset LPC/eSPI Controller
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
             product: 100 Series/C230 Series Chipset Family Power Management Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 31
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:f2244000-f2247fff
        *-multimedia
             description: Audio device
             product: 100 Series/C230 Series Chipset Family HD Audio Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:133 memory:f2240000-f2243fff memory:f2230000-f223ffff
        *-serial
             description: SMBus
             product: 100 Series/C230 Series Chipset Family SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 31
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:16 memory:f224d000-f224d0ff ioport:efa0(size=32)
        *-network
             description: Ethernet interface
             product: Ethernet Connection (2) I219-LM
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 31
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.8-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:128 memory:f2200000-f221ffff
     *-pnp00:00
          product: PnP device PNP0c01
          physical id: 0
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0b00
          physical id: 8
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:03
          product: PnP device LEN0071
          physical id: 9
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:04
          product: PnP device LEN2018
          physical id: a
          capabilities: pnp
          configuration: driver=i8042 aux
     *-pnp00:05
          product: PnP device PNP0c02
          physical id: b
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0c02
          physical id: c
          capabilities: pnp
          configuration: driver=system
  *-battery
       product: 45N1777
       vendor: SANYO
       physical id: 1
       slot: Front
       capacity: 71280mWh
       configuration: voltage=10.8V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       bus info: usb@1:5
       logical name: wwp0s20f0u5c2
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=no multicast=yes

```

---

### Post by mörgæs on 2020-04-15
You could upgrade the UEFI firmware.
[https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t460p/downloads/ds112077](https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t460p/downloads/ds112077)

---

### Post by thedoughnutlife on 2020-04-16
Installed latest BIOS version from Lenovo website. Then fresh installation of Ubuntu. Unaltered outcome.

---

### Post by mörgæs on 2020-04-16
Next test: 
Try to install the [minimal ISO]("http://cdimage.ubuntu.com/netboot/19.10/") using a wired internet connection and then add a GUI later. There is some advice in the *old hardware* link below (though this hardware is not old, I know).

If this does not work I suggest that you try other boot options than nomodeset.

---

