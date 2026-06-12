---
title: "3D acceleration on Radeon Xpress 200M (aka 1150)"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by dan-du on 2014-02-03
I would want to play Half Life 2 on my laptop (Ubuntu 14.04) and I get a "Could not find required OpenGL entry point 'glColorMaskIndexedEXT'" message when I try to open it (it works fine on windows 7)
Here is a lshw:
```
computer    description: Ordinateur Transportable
    produit: Inspiron 1501 ()
    fabriquant: Dell Inc.
    version: Not Specified
    numéro de série: [REMOVED]
    bits: 64 bits
    fonctionnalités: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=oem-specific chassis=portable uuid=[REMOVED]
  *-core
       description: Carte mère
       produit: 0UW744
       fabriquant: Dell Inc.
       identifiant matériel: 0
       numéro de série: [REMOVED]
     *-firmware
          description: BIOS
          fabriquant: Dell Inc.
          identifiant matériel: 1
          version: 2.6.3
          date: 12/07/2007
          taille: 105KiB
          capacité: 960KiB
          fonctionnalités: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          produit: Mobile AMD Sempron(tm) Processor 3600+
          fabriquant: Advanced Micro Devices [AMD]
          identifiant matériel: 5
          information bus: cpu@0
          version: Engineering Sample
          emplacement: Socket M2/S1G1
          taille: 2GHz
          capacité: 4GHz
          bits: 64 bits
          horloge: 200MHz
          fonctionnalités: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_lm extapic cr8_legacy cpufreq
        *-cache
             description: L2 cache
             identifiant matériel: 6
             emplacement: L2 Cache
             taille: 256KiB
             capacité: 1MiB
             fonctionnalités: synchronous internal write-back
     *-memory
          description: Mémoire Système
          identifiant matériel: 19
          emplacement: Carte mère
          taille: 3GiB
        *-bank:0
             description: DIMM DRAM Synchrone
             identifiant matériel: 0
             emplacement: DIMM_A
             taille: 1GiB
             bits: 64 bits
        *-bank:1
             description: DIMM DRAM Synchrone
             identifiant matériel: 1
             emplacement: DIMM_B
             taille: 2GiB
             bits: 64 bits
     *-pci:0
          description: Host bridge
          produit: RS480/RS482/RS485 Host Bridge
          fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 10
          bits: 32 bits
          horloge: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             produit: RC4xx/RS4xx PCI Bridge [int gfx]
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 1
             information bus: pci@0000:00:01.0
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: pci ht normal_decode bus_master cap_list
             ressources: portE/S:9000(taille=4096) mémoire:c0100000-c01fffff portE/S:c8000000(taille=134217728)
           *-display
                description: VGA compatible controller
                produit: RS482M [Mobility Radeon Xpress 200]
                fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
                identifiant matériel: 5
                information bus: pci@0000:01:05.0
                version: 00
                bits: 32 bits
                horloge: 66MHz
                fonctionnalités: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                ressources: irq:17 mémoire:c8000000-cfffffff portE/S:9000(taille=256) mémoire:c0100000-c010ffff mémoire:c0120000-c013ffff
        *-pci:1
             description: PCI bridge
             produit: RC4xx/RS4xx PCI Express Port 2
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 5
             information bus: pci@0000:00:05.0
             version: 00
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm pciexpress msi ht normal_decode cap_list
             configuration: driver=pcieport
             ressources: irq:0 portE/S:2000(taille=4096) mémoire:b0000000-b01fffff portE/S:b0200000(taille=2097152)
        *-pci:2
             description: PCI bridge
             produit: RC4xx/RS4xx PCI Express Port 3
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 6
             information bus: pci@0000:00:06.0
             version: 00
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:0 portE/S:3000(taille=4096) mémoire:c0200000-c02fffff portE/S:b0400000(taille=2097152)
           *-network
                description: Network controller
                produit: BCM4311 802.11b/g WLAN
                fabriquant: Broadcom Corporation
                identifiant matériel: 0
                information bus: pci@0000:05:00.0
                version: 01
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                ressources: irq:18 mémoire:c0200000-c0203fff
        *-storage
             description: SATA controller
             produit: SB600 Non-Raid-5 SATA
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 12
             information bus: pci@0000:00:12.0
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             ressources: irq:22 portE/S:8438(taille=8) portE/S:8454(taille=4) portE/S:8430(taille=8) portE/S:8450(taille=4) portE/S:8400(taille=16) mémoire:c0004000-c00043ff
        *-usb:0
             description: USB controller
             produit: SB600 USB (OHCI0)
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 13
             information bus: pci@0000:00:13.0
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: ohci bus_master
             configuration: driver=ohci-pci latency=64
             ressources: irq:16 mémoire:c0005000-c0005fff
        *-usb:1
             description: USB controller
             produit: SB600 USB (OHCI1)
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 13.1
             information bus: pci@0000:00:13.1
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: ohci bus_master
             configuration: driver=ohci-pci latency=64
             ressources: irq:17 mémoire:c0006000-c0006fff
        *-usb:2
             description: USB controller
             produit: SB600 USB (OHCI2)
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 13.2
             information bus: pci@0000:00:13.2
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: ohci bus_master
             configuration: driver=ohci-pci latency=64
             ressources: irq:18 mémoire:c0007000-c0007fff
        *-usb:3
             description: USB controller
             produit: SB600 USB (OHCI3)
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 13.3
             information bus: pci@0000:00:13.3
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: ohci bus_master
             configuration: driver=ohci-pci latency=64
             ressources: irq:17 mémoire:c0008000-c0008fff
        *-usb:4
             description: USB controller
             produit: SB600 USB (OHCI4)
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 13.4
             information bus: pci@0000:00:13.4
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: ohci bus_master
             configuration: driver=ohci-pci latency=64
             ressources: irq:18 mémoire:c0009000-c0009fff
        *-usb:5
             description: USB controller
             produit: SB600 USB Controller (EHCI)
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 13.5
             information bus: pci@0000:00:13.5
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=64
             ressources: irq:19 mémoire:c0004400-c00044ff
        *-serial
             description: SMBus
             produit: SBx00 SMBus Controller
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 14
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: ht cap_list
             configuration: driver=piix4_smbus latency=0
             ressources: irq:0 portE/S:8410(taille=16)
        *-ide
             description: IDE interface
             produit: SB600 IDE
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 14.1
             information bus: pci@0000:00:14.1
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: ide bus_master
             configuration: driver=pata_atiixp latency=64
             ressources: irq:16 portE/S:1f0(taille=8) portE/S:3f6 portE/S:170(taille=8) portE/S:376 portE/S:8420(taille=16)
        *-multimedia
             description: Audio device
             produit: SBx00 Azalia (Intel HDA)
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 14.2
             information bus: pci@0000:00:14.2
             version: 00
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             ressources: irq:16 mémoire:c0000000-c0003fff
        *-isa
             description: ISA bridge
             produit: SB600 PCI to LPC Bridge
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 14.3
             information bus: pci@0000:00:14.3
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             produit: SBx00 PCI to PCI Bridge
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             identifiant matériel: 14.4
             information bus: pci@0000:00:14.4
             version: 00
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: pci subtractive_decode bus_master
             ressources: mémoire:c0300000-c03fffff
           *-network
                description: Ethernet interface
                produit: BCM4401-B0 100Base-TX
                fabriquant: Broadcom Corporation
                identifiant matériel: 0
                information bus: pci@0000:08:00.0
                nom logique: eth0
                version: 02
                numéro de série: [REMOVED]
                taille: 10Mbit/s
                capacité: 100Mbit/s
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
                ressources: irq:21 mémoire:c0300000-c0301fff
           *-generic:0
                description: SD Host controller
                produit: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                fabriquant: Ricoh Co Ltd
                identifiant matériel: 1
                information bus: pci@0000:08:01.0
                version: 19
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                ressources: irq:20 mémoire:c0302800-c03028ff
           *-generic:1
                description: System peripheral
                produit: R5C843 MMC Host Controller
                fabriquant: Ricoh Co Ltd
                identifiant matériel: 1.1
                information bus: pci@0000:08:01.1
                version: 01
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                ressources: irq:20 mémoire:c0302c00-c0302cff
     *-pci:1
          description: Host bridge
          produit: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 101
          information bus: pci@0000:00:18.0
          version: 00
          bits: 32 bits
          horloge: 33MHz
     *-pci:2
          description: Host bridge
          produit: K8 [Athlon64/Opteron] Address Map
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 102
          information bus: pci@0000:00:18.1
          version: 00
          bits: 32 bits
          horloge: 33MHz
     *-pci:3
          description: Host bridge
          produit: K8 [Athlon64/Opteron] DRAM Controller
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 103
          information bus: pci@0000:00:18.2
          version: 00
          bits: 32 bits
          horloge: 33MHz
     *-pci:4
          description: Host bridge
          produit: K8 [Athlon64/Opteron] Miscellaneous Control
          fabriquant: Advanced Micro Devices, Inc. [AMD]
          identifiant matériel: 104
          information bus: pci@0000:00:18.3
          version: 00
          bits: 32 bits
          horloge: 33MHz
          configuration: driver=k8temp
          ressources: irq:0
     *-scsi:0
          identifiant matériel: 0
          nom logique: scsi0
          fonctionnalités: emulated
        *-disk
             description: ATA Disk
             produit: WDC WD1200BEVS-2
             fabriquant: Western Digital
             identifiant matériel: 0.0.0
             information bus: scsi@0:0.0.0
             nom logique: /dev/sda
             version: 01.0
             numéro de série: [REMOVED]
             taille: 111GiB (120GB)
             fonctionnalités: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=304ee47a
           *-volume:0
                description: Windows NTFS volume
                identifiant matériel: 1
                information bus: scsi@0:0.0.0,1
                nom logique: /dev/sda1
                version: 3.1
                numéro de série: [REMOVED]
                taille: 98MiB
                capacité: 100MiB
                fonctionnalités: primary ntfs initialized
                configuration: clustersize=4096 created=2013-12-28 09:15:10 filesystem=ntfs label=Réservé au système state=clean
           *-volume:1
                description: Windows NTFS volume
                identifiant matériel: 2
                information bus: scsi@0:0.0.0,2
                nom logique: /dev/sda2
                nom logique: /media/dan/0EB43A25B43A0FA7
                version: 3.1
                numéro de série: [REMOVED]
                taille: 73GiB
                capacité: 73GiB
                fonctionnalités: primary ntfs initialized
                configuration: clustersize=4096 created=2013-12-28 09:15:12 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
           *-volume:2
                description: Extended partition
                identifiant matériel: 3
                information bus: scsi@0:0.0.0,3
                nom logique: /dev/sda3
                taille: 18GiB
                capacité: 18GiB
                fonctionnalités: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   identifiant matériel: 5
                   nom logique: /dev/sda5
                   nom logique: /
                   capacité: 15GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   identifiant matériel: 6
                   nom logique: /dev/sda6
                   capacité: 2940MiB
                   fonctionnalités: bootable nofs
           *-volume:3
                description: Volume EXT4
                fabriquant: Linux
                identifiant matériel: 4
                information bus: scsi@0:0.0.0,4
                nom logique: /dev/sda4
                nom logique: /media/dan/Steam
                version: 1.0
                numéro de série: [REMOVED]
                taille: 19GiB
                capacité: 19GiB
                fonctionnalités: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-02-02 22:19:01 filesystem=ext4 label=Steam modified=2014-02-02 22:19:01 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered state=mounted
     *-scsi:1
          identifiant matériel: 2
          nom logique: scsi4
          fonctionnalités: emulated
        *-cdrom
             description: DVD writer
             produit: DVD+-RW AD-5560A
             fabriquant: Optiarc
             identifiant matériel: 0.0.0
             information bus: scsi@4:0.0.0
             nom logique: /dev/cdrom
             nom logique: /dev/sr0
             version: DD12
             fonctionnalités: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Interface réseau sans fil
       identifiant matériel: 1
       nom logique: wlan0
       numéro de série: [REMOVED]
       fonctionnalités: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.13.0-6-generic firmware=666.2 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bg
```
(if you want me to get an english version, tell me)

---

### Post by mastablasta on 2014-02-03
i can't see what chip it is but can you do the following:

> To see your OpenGL information, you can run the commands below. Make sure your OpenGL renderer string does not say "software rasterizer" or "llvmpipe" because that would mean you have no 3D hardware acceleration: 

```
sudo apt-get install mesa-utils
LIBGL_DEBUG=verbose glxinfo
```


i believe AMD dropped support for this chip in newer kernels and that opensource drivers might not provide opengl support for it. but just to be sure do the above.

---

### Post by dan-du on 2014-02-03
The command doesnt show anything useful, but the system details tells me its a Gallium 0.4 on ATI RS480 with Standard experience

---

