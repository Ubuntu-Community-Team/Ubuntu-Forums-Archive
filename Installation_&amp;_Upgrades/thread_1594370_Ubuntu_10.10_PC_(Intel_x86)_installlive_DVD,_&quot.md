---
title: "Ubuntu 10.10 PC (Intel x86) install/live DVD, &quot;E: Failed to mount the cdrom&quot;"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by MIJ-VI on 2010-10-12
After downloading and md5sum-ing the official release of [Ubuntu 10.10 (Maverick Meerkat) PC (Intel x86) install/live DVD]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs/ubuntu/10.10/release/") (and testing the 4x speed burnt DVD) I tried two different installation methods in order to set up a dual-boot on my notebook:

- One while my non-GNU/Linux-supported Broadcom BCM4312 (it requires a restricted driver)-equipped Acer Aspire 5517-1536 was connected to the Internet via a Windows, Mac, and GNU/Linux-friendly [Wi-Fire]("http://www.hfield.com/the-wi-fire/platform-compatibility/"). This worked flawlessly.

- And an install without Internet access (which also worked flawlessly) with the aim of installing the Broadcom's restricted driver from the DVD via Synaptic Package Manager after the OS install. This part didn't work. Every time I tried to adding the DVD in S.P.M. (Edit-->Add CD-ROM...) an error would be displayed: "E: Failed to mount the cdrom".

Hopefully the above method, when performed with an [Ubuntu 10.10 (Maverick Meerkat) PC (Intel x86) desktop CD]("http://ubuntu.media.mit.edu/ubuntu-releases/maverick/"), will work for those whose notebooks are afflicted with Broadcom Wi-Fi cards.

```
john@5517:~$ sudo lshw
[sudo] password for john: 
5517                      
    description: Notebook
    product: Aspire 5517
    vendor: Acer
    version: V1.09
    serial: LXPGZ020320034805B1601
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: boot=normal chassis=notebook uuid=66626132-3538-3735-6466-705AB62286B6
  *-core
       description: Motherboard
       product: Aspire 5517
       vendor: Acer
       physical id: 0
       version: V1.09
       serial: LXPGZ020320034805B1601
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.09 (11/30/2009)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor TF-20
          vendor: Advanced Micro Devices [AMD]
          physical id: 20
          bus info: cpu@0
          version: 15.12.2
          serial: NotSupport
          slot: Socket S1G1
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0 DISABLED
             description: L1 cache
             physical id: 21
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal write-through unified
        *-cache:1
             description: L1 cache
             physical id: 22
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: HYMP112S64CP6-S6
             vendor: Unknown
             physical id: 0
             serial: AD000000000000000109534F82712C
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: HYMP112S64CP6-S6
             vendor: Unknown
             physical id: 1
             serial: AD000000000000000109534F62712D
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR2 [empty]
             physical id: 2
             slot: DIMM2
        *-bank:3
             description: DIMM DDR2 [empty]
             physical id: 3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (int gfx)
             vendor: Advanced Micro Devices [AMD]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:7000(size=4096) memory:92100000-922fffff ioport:80000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:18 memory:80000000-8fffffff ioport:7000(size=256) memory:92200000-9220ffff memory:92100000-921fffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 0)
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=16384) memory:91100000-920fffff ioport:90000000(size=16777216)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 01
                serial: c4:17:fe:67:f3:d9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.180 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:16 memory:91100000-91103fff
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:91000000-910fffff
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: c0
                serial: 70:5a:b6:22:86:b6
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:91000000-9103ffff ioport:2000(size=128)
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:42 ioport:8038(size=8) ioport:804c(size=4) ioport:8030(size=8) ioport:8048(size=4) ioport:8010(size=16) memory:92306000-923063ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXA0AB9W4750
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a4bb357c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 0b17d3bb-e9d2-4dfd-b5ce-b6b45f168681
                   size: 131GiB
                   capacity: 131GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-10-11 01:15:53 filesystem=ext4 lastmountpoint=/&#65533;&#65533;E&#65533;U&#65533;&#65533;xE&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;l!&#65533;xE&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;p&#65533;&#65533;&#65533;U&#65533;&#65533; &#65533;4&#65533;&#65533;&#65533;yo!&#65533;&#65533;d modified=2010-10-11 01:56:36 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-10-12 07:59:26 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 101GiB
                   capacity: 101GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 97GiB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4259MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7700S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/Ubuntu 10.10 i386
                version: 1.B0
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/Ubuntu 10.10 i386
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:92305000-92305fff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:92304000-92304fff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:92306400-923064ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:92300000-92303fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
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
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:1000(size=4096)
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
john@5517:~$ 

```

---

