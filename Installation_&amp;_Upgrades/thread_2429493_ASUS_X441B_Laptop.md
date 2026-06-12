---
title: "ASUS X441B Laptop"
date: 2019-10-18
forum: Installation &amp; Upgrades
---

### Post by president-6 on 2019-10-18
Any advice or information on installing Ubuntu (most recent version) on my ASUS X441B laptop would be great. Been a few years since I have had the pleasure of running Ubuntu. I couldn't find much material on it. Currently running Windows 10.

---

### Post by mörgæs on 2019-10-19
Hi, welcome to the fora.

How does it work in a live boot of 19.10? 

While you are there please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags. 

The output will show people (who know more about the issue than me) the hardware details.

---

### Post by president-6 on 2019-10-19
I haven't installed it yet. That is why I was inquiring, beforehand, to see if anyone else had and whether there were any type of issues I might be able to preemptively address such as the need for downloading or compiling items in case things like the wireless drivers do not work.

---

### Post by mörgæs on 2019-10-20
I wasn't suggesting installing but doing a live boot.

---

### Post by president-6 on 2019-10-21
Ah, thanks! Will do and then I will post here.

```
ubuntu@ubuntu:~$ sudo lshw
ubuntu                     
    description: Notebook
    product: X441BA
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: JCN0CV023637496
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: boot=normal chassis=notebook family=X uuid=5D1519B2-175C-4CAA-98BE-B84356DC6820
  *-core
       description: Motherboard
       product: X441BA
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: N0CV1849MB0016088
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: X441BA.308
          date: 07/03/2019
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-cache:0
          description: L1 cache
          physical id: 4
          slot: L1 CACHE
          size: 160KiB
          capacity: 160KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 5
          slot: L2 CACHE
          size: 1MiB
          capacity: 1MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR4 [empty]
             product: A1_PartNum0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerialNum0
             slot: DIMM 0
             width: 64 bits
        *-bank:1
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
             product: M471A5143EB1-CRC
             vendor: Samsung
             physical id: 1
             serial: 00000000
             slot: DIMM 1
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-cpu
          description: CPU
          product: AMD A6-9225 RADEON R4, 5 COMPUTE CORES 2C+3G
          vendor: Advanced Micro Devices [AMD]
          physical id: 2e
          bus info: cpu@0
          version: AMD A6-9225 RADEON R4, 5 COMPUTE CORES 2C+3G
          slot: P0
          size: 2275MHz
          capacity: 2600MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp constant_tsc rep_good acc_power nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm perfctr_core perfctr_nb bpext ptsc mwaitx cpb hw_pstate ssbd ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 xsaveopt arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov cpufreq
          configuration: cores=2 enabledcores=2 threads=2
     *-pci:0
          description: Host bridge
          product: Family 15h (Models 60h-6fh) Processor Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic:0 UNCLAIMED
             description: IOMMU
             product: Family 15h (Models 60h-6fh) I/O Memory Management Unit
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-display
             description: VGA compatible controller
             product: Stoney [Radeon R2/R3/R4/R5 Graphics]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: ea
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=amdgpu latency=0
             resources: irq:35 memory:e8000000-efffffff memory:f0000000-f07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Advanced Micro Devices, Inc. [AMD/ATI]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:37 memory:feb64000-feb67fff
        *-pci:0
             description: PCI bridge
             product: Family 15h (Models 60h-6fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:e000(size=4096) memory:fea00000-feafffff
           *-network
                description: Wireless interface
                product: RTL8723BE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 00
                serial: 00:f4:8d:31:e2:1c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8723be driverversion=5.0.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:39 ioport:e000(size=256) memory:fea00000-fea03fff
        *-pci:1
             description: PCI bridge
             product: Family 15h (Models 60h-6fh) Processor Root Port
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:d000(size=4096) memory:fe900000-fe9fffff ioport:f0800000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL810xE PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 07
                serial: 04:92:26:12:ff:95
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:32 ioport:d000(size=256) memory:fe900000-fe900fff memory:f0800000-f0803fff
        *-generic:1 UNCLAIMED
             description: Encryption controller
             product: Advanced Micro Devices, Inc. [AMD]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msix ht pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0900000-f091ffff memory:fe800000-fe8fffff memory:feb70000-feb70fff memory:feb6a000-feb6bfff
        *-multimedia:1
             description: Computer telephony device
             product: Family 15h (Models 60h-6fh) Audio Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 9.2
             bus info: pci@0000:00:09.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:38 memory:feb60000-feb63fff
        *-usb:0
             description: USB controller
             product: FCH USB XHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 20
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi msix pciexpress xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:18 memory:feb68000-feb69fff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.0.0-23-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb
                   description: Mass storage device
                   product: Cruzer
                   vendor: SanDisk
                   physical id: 1
                   bus info: usb@2:1
                   logical name: scsi1
                   version: 1.00
                   serial: 20053550310C7A736B7A
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=200mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      product: Cruzer
                      vendor: SanDisk
                      physical id: 0.0.0
                      bus info: scsi@1:0.0.0
                      logical name: /dev/sdb
                      version: 1.02
                      size: 3815MiB (4GB)
                      capabilities: removable
                      configuration: ansiversion=2 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sdb
                         size: 3815MiB (4GB)
                         capabilities: partitioned partitioned:dos
                         configuration: signature=0f124be0
                       *-volume
                            description: Windows FAT volume
                            vendor: SYSLINUX
                            physical id: 1
                            logical name: /dev/sdb1
                            logical name: /cdrom
                            version: FAT32
                            serial: 18c4-b5f4
                            size: 3812MiB
                            capacity: 3814MiB
                            capabilities: primary bootable fat initialized
                            configuration: FATs=2 filesystem=fat label=UBUNTU 18_0 mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.0.0-23-generic xhci-hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 5.00
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
        *-storage
             description: SATA controller
             product: FCH SATA Controller [AHCI mode]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 4b
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=32
             resources: irq:19 ioport:f140(size=8) ioport:f130(size=4) ioport:f120(size=8) ioport:f110(size=4) ioport:f100(size=16) memory:feb6e000-feb6e3ff
        *-usb:1
             description: USB controller
             product: FCH USB EHCI Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 49
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:18 memory:feb6d000-feb6d0ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 5.0.0-23-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Advanced Micro Devices, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.18
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: 2.4G RF Keyboard & Mouse
                      vendor: MOSART Semi.
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 2.03
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Bluetooth wireless interface
                      product: Bluetooth Radio
                      vendor: Realtek
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 2.00
                      serial: 00e04c000001
                      capabilities: bluetooth usb-2.10
                      configuration: driver=btusb maxpower=500mA speed=12Mbit/s
                 *-usb:2
                      description: Video
                      product: USB2.0 VGA UVC WebCam
                      vendor: Azurewave
                      physical id: 4
                      bus info: usb@1:1.4
                      version: 16.08
                      serial: 0x0001
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 4b
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
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
        *-generic:2
             description: SD Host controller
             product: FCH SD Flash Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.7
             bus info: pci@0000:00:14.7
             version: 01
             width: 64 bits
             clock: 66MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=sdhci-pci latency=39
             resources: irq:16 memory:feb6c000-feb6c0ff
     *-pci:1
          description: Host bridge
          product: Family 15h (Models 60h-6fh) Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 15h (Models 60h-6fh) Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:03.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:09.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:9
          description: Host bridge
          product: Advanced Micro Devices, Inc. [AMD]
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500LM030-1RK17
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: SDM1
             serial: WL1PBRL2
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=8a4b8b08-ba6a-4b07-b64a-06e0e9749423 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: FAT32
                serial: 446c-7668
                size: 255MiB
                capacity: 259MiB
                capabilities: boot precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat label=SYSTEM name=EFI system partition
           *-volume:1
                description: reserved partition
                vendor: Windows
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                serial: d8f0a25f-642d-46f0-b84b-d0eafa0e6894
                capacity: 15MiB
                capabilities: nofs precious readonly hidden nomount
                configuration: name=Microsoft reserved partition
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: bcf1b119-eb89-a94d-831c-d13403bdb5ee
                size: 464GiB
                capacity: 464GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2018-12-06 10:21:21 filesystem=ntfs label=OS modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 3220-5e24
                size: 787MiB
                capacity: 799MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2018-12-06 10:26:18 filesystem=ntfs label=RECOVERY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
```

---

### Post by president-6 on 2019-10-21
I copy and pasted the lshw into an email. I will do the sanitize here in a mn

---

### Post by mörgæs on 2019-10-22
I don't see anything in the lshw output which could cause problems for Ubuntu 19.10 but it might be better to wait for someone better versed in Asus than me to notice the thread.

How much did you test the system in the live boot?

---

### Post by president-6 on 2019-10-22
I ran 18.03 LTS. Pushed obviously Terminal. Spun up Firefox. That had always been the thing, back in the day, getting the wireless to work out of the box. No issues. Was able to screenshot, run LibreOffice, etc. no issues. To me, and I am an old timer, if the wireless works, anything else can be fixed within reason. ;)

Thanks, BTW, to everyone whom replies in. I will keep a rolling journal in this thread to give others updates!

---

### Post by mörgæs on 2019-10-23
Yes, please let us know how it proceeds. It might help other users.

---

### Post by president-6 on 2019-11-01
Happy to report that I am running a dual boot without any issues. There may be something in the background I don't know about, but compared to several years back, EVERYTHING is working out of the box --- printer, wireless, etc.

If anyone needs specific info to publish to clear this model, let me know.

Thanks!

---

### Post by mörgæs on 2019-11-01
Thanks, please mark the thread solved using Thread Tools.

---

