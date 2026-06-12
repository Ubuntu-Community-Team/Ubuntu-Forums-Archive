---
title: "Super slow graphics on a fresh install. Inspiron 1501 Dell laptop."
date: 2016-02-02
forum: Installation &amp; Upgrades
---

### Post by sinnedam on 2016-02-02
I am a small step above a Linux newbie but far from an expert. I just installed a fresh copy of Ubuntu 15.10. I had a widely experienced issue of colorful bars filling the screen after booting to the disk during install. The fix mentioned online worked perfectly for that. Then I had the issue of the wireless card not working, and once again the fix I found worked. The problem I cannot fix is the graphics in the GUI are incredibly slow. A good 10 seconds to minimize a window or open a new one. It is like it is in slow motion. It acts like as if there isnt a video driver loaded, but im not sure how to determine that. I think it is an ATI chipset but when I go to about this computer the graphics are listed as Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)

Any help is appreciated.

---

### Post by kansasnoob on 2016-02-02
See if Additional Drivers are available:

[http://askubuntu.com/questions/47506/how-do-i-install-additional-drivers](http://askubuntu.com/questions/47506/how-do-i-install-additional-drivers)

---

### Post by kansasnoob on 2016-02-02
BTW, if proprietary drivers are available one will usually say it's been tested.

---

### Post by mörgæs on 2016-02-03
Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by sinnedam on 2016-02-03
> **mörgæs said:**
> Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Here you go 

```
computer
    description: Computer
    width: 64 bits
    capabilities: smbios-2.4 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1873MiB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-50
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall cpufreq
     *-pci:0
          description: Host bridge
          product: RS480/RS482/RS485 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD/ATI]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RC4xx/RS4xx PCI Bridge [int gfx]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:c0100000-c01fffff ioport:c8000000(size=134217728)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS482M [Mobility Radeon Xpress 200]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
        *-pci:1
             description: PCI bridge
             product: RC4xx/RS4xx PCI Express Port 2
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:2000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: RC4xx/RS4xx PCI Express Port 3
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:3000(size=4096) memory:c0200000-c02fffff ioport:80400000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:18 memory:c0200000-c0203fff
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8438(size=8) ioport:8454(size=4) ioport:8430(size=8) ioport:8450(size=4) ioport:8400(size=16) memory:c0004000-c00043ff
        *-usb:0
             description: USB controller
             product: SB600 USB (OHCI0)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:16 memory:c0005000-c0005fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-27-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: SB600 USB (OHCI1)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:c0006000-c0006fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-27-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: SB600 USB (OHCI2)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:c0007000-c0007fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-27-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             description: USB controller
             product: SB600 USB (OHCI3)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:17 memory:c0008000-c0008fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-27-generic ohci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: SB600 USB (OHCI4)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64
             resources: irq:18 memory:c0009000-c0009fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-27-generic ohci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: SB600 USB Controller (EHCI)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             resources: irq:19 memory:c0004400-c00044ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-27-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=10 speed=480Mbit/s
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8410(size=16) memory:c0004800-c0004bff
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8420(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             resources: irq:16 memory:c0000000-c0003fff
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: memory:c0300000-c03fffff
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:21 memory:c0300000-c0301fff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:08:01.0
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:20 memory:c0302000-c03020ff
           *-generic:1
                description: System peripheral
                product: R5C843 MMC Host Controller
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:08:01.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:20 memory:c0302400-c03024ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1200BEVS-7
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1G04
             serial: [REMOVED]
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=baf2582e
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 109GiB
                capacity: 109GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-02-01 15:46:34 filesystem=ext4 lastmountpoint=/ modified=2016-02-03 11:03:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-02-03 15:55:33 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1916MiB
                capacity: 1916MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1916MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi4
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD+-RW TS-L632D
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: DE04
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=4.2.0-27-generic firmware=666.2 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bg


```

---

### Post by Vladlenin5000 on 2016-02-03
Here's the problem:
```
*-display [COLOR=#ff0000]UNCLAIMED[/COLOR]
                description: VGA compatible controller
                product: [COLOR=#ff0000]RS482M [Mobility Radeon Xpress 200][/COLOR]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
```

An ancient Radeon graphics chip and on top of that no driver.
This chip was not very good when new, let alone in this day and age. So, even with the proper driver being loaded, standard Ubuntu is way too much for your hardware.

---

### Post by mörgæs on 2016-02-04
Yes, L/Xubuntu or Mate are better choices. 
The drivers you are using are the only ones available. Don't try to install other.

---

### Post by thosecars822 on 2016-12-10
Could this also be the reason of my slow computer and why the fan is 
I described this problem here:
[https://ubuntuforums.org/showthread.php?t=2344643](https://ubuntuforums.org/showthread.php?t=2344643)

I tried sudo lshw -sanitize
and I got this:
```

.......................................................
...........................................................
..........................................................

*-display
                Beschreibung: VGA compatible controller
                Produkt: RS482M [Mobility Radeon Xpress 200]
                Hersteller: Advanced Micro Devices, Inc. [AMD/ATI]
                Physische ID: 5
                Bus-Informationen: pci@0000:01:05.0
                Version: 00
                Breite: 32 bits
                Takt: 66MHz
                Fähigkeiten: pm vga_controller bus_master cap_list rom
                Konfiguration: driver=radeon latency=64 mingnt=8
                Ressourcen: irq:17 memory:c0000000-c7ffffff ioport:6000(Größe=256) memory:d4300000-d430ffff memory:d4320000-d433ffff
............................
..........................

```


Thanks

---

### Post by mörgæs on 2016-12-10
Yes, give it a fresh install of a light Buntu. Ubuntu is too heavy.

---

### Post by thosecars822 on 2016-12-10
I think I made a mistake. I found ubuntu 8.sth in this computer. Then I think I downloaded lubuntu 16.10 and I installed it. It was very slow and then I downloaded Lubuntu 14.04 just in case tht worked faster and without the fan on all the time. However that did not work either because it still runs extremely slow. I have not updated the operative system any more.
Currently I have this:
```


lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

```

I thought this is Lubuntu because that is what I downloaded but now I am confused because this lsb_release command says &#8222;Ubuntu&#8220; instead of &#8222;Lubuntu&#8220;.
Thanks

---

### Post by mörgæs on 2016-12-10
Lubuntu 14.04.5 and 16.10 are fairly similar with regards to processor workload. 

The Ubuntu name in the command output only means that the core system is Ubuntu. All systems in the Buntu family will show that. 

Have you cleaned the fan and heat sink for dust bunnies?

---

### Post by thosecars822 on 2016-12-10
I  did not do that because i thought that was not the problem considering the computer worked great with a live Linux distribution:without fan on all the time and much quicker.

---

### Post by mörgæs on 2016-12-11
So, the obvious next step is trying to install the distro which worked well in a live boot. 

It's risky to transfer observations from one distro to another. I clean every piece of hardware I get in for repairs no matter if it overheats or not.

---

### Post by thosecars822 on 2016-12-11
I have just found this:

[https://ubuntuforums.org/showthread.php?t=2323156](https://ubuntuforums.org/showthread.php?t=2323156)

They describe exactly each and all of the problems I have very accurately with both the same computer as me.

---

### Post by mörgæs on 2016-12-12
I think it's time to quit studying and begin experimenting. Install a number of promising distros and see if you notice any difference.

---

