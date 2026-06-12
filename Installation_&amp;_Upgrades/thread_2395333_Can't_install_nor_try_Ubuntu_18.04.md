---
title: "Can't install nor try Ubuntu 18.04"
date: 2018-06-30
forum: Installation &amp; Upgrades
---

### Post by vvmm on 2018-06-30
Hello!
As I had some fan and graphic issues (fan started to run as I turned off the computer) I wanted to install Ubuntu 18.04. I burnt a live CD and verified it with MD5Sum but every time I try to launch it I don't have the usual Ubuntu menu, only GRUB one (without MEMTest on advanced option like ACPI), and F2 or F6 don't work. I was able to install 16.04 (which I had before) but I always have the fan issue after shutdown. With checkdisk no issues were found on the disks.
Theses are my ASUS PX753VD-GC081R features:

```
sudo lshw
d-gl753vd                 
    description: Ordinateur Bloc-notes
    produit: GL753VD
    fabriquant: ASUSTeK COMPUTER INC.
    version: 1.0
    numéro de série: H6N0CV054051235
    bits: 64 bits
    fonctionnalités: smbios-3.0 dmi-3.0 vsyscall32
    configuration: boot=normal chassis=notebook family=GL uuid=346888BC-3BE7-4A75-8B40-56D6AEA8480D
  *-core
       description: Carte mère
       produit: GL753VD
       fabriquant: ASUSTeK COMPUTER INC.
       identifiant matériel: 0
       version: 1.0
       numéro de série: BSN12345678901234567
       emplacement: Default string
     *-firmware
          description: BIOS
          fabriquant: American Megatrends Inc.
          identifiant matériel: 0
          version: GL753VD.302
          date: 03/06/2017
          taille: 64KiB
          capacité: 8128KiB
           fonctionnalités: pci upgrade shadowing cdboot bootselect  socketedrom edd int13floppy1200 int13floppy720 int13floppy2880  int5printscreen int14serial int17printer acpi usb biosbootspecification  uefi
     *-memory
          description: Mémoire Système
          identifiant matériel: 3d
          emplacement: Carte mère
          taille: 32GiB
        *-bank:0
             description: SODIMM Synchrone 2400 MHz (0,4 ns)
             produit: 76.D305G.D390B
             fabriquant: AMD
             identifiant matériel: 0
             numéro de série: 07417182
             emplacement: ChannelA-DIMM0
             taille: 16GiB
             bits: 64 bits
             horloge: 2400MHz (0.4ns)
        *-bank:1
              description: Project-Id-Version: @(#)  $Id$Report-Msgid-Bugs-To: POT-Creation-Date: 2009-10-08  14:02+0200PO-Revision-Date: 2017-11-09 20:09+0000Last-Translator: Lyonel  Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type:  text/plain; charset=UTF-8Content-Transfer-Encoding:  8bitX-Launchpad-Export-Date: 2017-12-10 10:57+0000X-Generator: Launchpad  (build 18511)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To:  POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2017-11-09  20:09+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team:  MIME-Version: 1.0Content-Type: text/plain;  charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date:  2017-12-10 10:57+0000X-Generator: Launchpad (build 18511) [vide]
             identifiant matériel: 1
             emplacement: ChannelA-DIMM1
        *-bank:2
             description: SODIMM Synchrone 2400 MHz (0,4 ns)
             produit: 76.D305G.D390B
             fabriquant: AMD
             identifiant matériel: 2
             numéro de série: 07417182
             emplacement: ChannelB-DIMM0
             taille: 16GiB
             bits: 64 bits
             horloge: 2400MHz (0.4ns)
        *-bank:3
              description: Project-Id-Version: @(#)  $Id$Report-Msgid-Bugs-To: POT-Creation-Date: 2009-10-08  14:02+0200PO-Revision-Date: 2017-11-09 20:09+0000Last-Translator: Lyonel  Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type:  text/plain; charset=UTF-8Content-Transfer-Encoding:  8bitX-Launchpad-Export-Date: 2017-12-10 10:57+0000X-Generator: Launchpad  (build 18511)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To:  POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2017-11-09  20:09+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team:  MIME-Version: 1.0Content-Type: text/plain;  charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date:  2017-12-10 10:57+0000X-Generator: Launchpad (build 18511) [vide]
             identifiant matériel: 3
             emplacement: ChannelB-DIMM1
     *-cache:0
          description: L1 cache
          identifiant matériel: 43
          emplacement: L1 Cache
          taille: 256KiB
          capacité: 256KiB
          fonctionnalités: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          identifiant matériel: 44
          emplacement: L2 Cache
          taille: 1MiB
          capacité: 1MiB
          fonctionnalités: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          identifiant matériel: 45
          emplacement: L3 Cache
          taille: 6MiB
          capacité: 6MiB
          fonctionnalités: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          produit: Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
          fabriquant: Intel Corp.
          identifiant matériel: 46
          information bus: cpu@0
          version: Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
          numéro de série: To Be Filled By O.E.M.
          emplacement: U3E1
          taille: 940MHz
          capacité: 4005MHz
          bits: 64 bits
          horloge: 100MHz
           fonctionnalités: x86-64 fpu fpu_exception wp vme de pse tsc msr  pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx  fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art  arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf  eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma  cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer  aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb invpcid_single  intel_pt ibrs ibpb stibp kaiser tpr_shadow vnmi flexpriority ept vpid  fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap  clflushopt xsaveopt xsavec xgetbv1 dtherm ida arat pln pts hwp  hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          produit: Intel Corporation
          fabriquant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 05
          bits: 32 bits
          horloge: 33MHz
        *-pci:0
             description: PCI bridge
             produit: Sky Lake PCIe Controller (x16)
             fabriquant: Intel Corporation
             identifiant matériel: 1
             information bus: pci@0000:00:01.0
             version: 05
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:122 portE/S:e000(taille=4096) mémoire:de000000-df0fffff portE/S:c0000000(taille=301989888)
           *-display NON-RÉCLAMÉ
                description: 3D controller
                produit: NVIDIA Corporation
                fabriquant: NVIDIA Corporation
                identifiant matériel: 0
                information bus: pci@0000:01:00.0
                version: a1
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                 ressources: mémoire:de000000-deffffff  mémoire:c0000000-cfffffff mémoire:d0000000-d1ffffff  portE/S:e000(taille=128) mémoire:df000000-df07ffff
        *-display
             description: VGA compatible controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 2
             information bus: pci@0000:00:02.0
             version: 04
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915_bpo latency=0
             ressources: irq:127 mémoire:dd000000-ddffffff mémoire:b0000000-bfffffff portE/S:f000(taille=64)
        *-generic:0 NON-RÉCLAMÉ
             description: System peripheral
             produit: Sky Lake Gaussian Mixture Model
             fabriquant: Intel Corporation
             identifiant matériel: 8
             information bus: pci@0000:00:08.0
             version: 00
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: msi pm cap_list
             configuration: latency=0
             ressources: mémoire:df430000-df430fff
        *-usb
             description: USB controller
             produit: Sunrise Point-H USB 3.0 xHCI Controller
             fabriquant: Intel Corporation
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 31
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             ressources: irq:123 mémoire:df410000-df41ffff
           *-usbhost:0
                produit: xHCI Host Controller
                fabriquant: Linux 4.4.0-128-generic xhci-hcd
                identifiant matériel: 0
                information bus: usb@2
                nom logique: usb2
                version: 4.04
                fonctionnalités: usb-3.00
                configuration: driver=hub slots=8 speed=5000Mbit/s
           *-usbhost:1
                produit: xHCI Host Controller
                fabriquant: Linux 4.4.0-128-generic xhci-hcd
                identifiant matériel: 1
                information bus: usb@1
                nom logique: usb1
                version: 4.04
                fonctionnalités: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Clavier
                   produit: USB Receiver
                   fabriquant: Logitech
                   identifiant matériel: 1
                   information bus: usb@1:1
                   version: 12.01
                   fonctionnalités: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:1
                   description: Clavier
                   produit: ITE Device(8910)
                   fabriquant: ITE Tech. Inc.
                   identifiant matériel: 3
                   information bus: usb@1:3
                   version: 3.02
                   fonctionnalités: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: Interface sans fil Bluetooth
                   fabriquant: Intel Corp.
                   identifiant matériel: 9
                   information bus: usb@1:9
                   version: 0.01
                   fonctionnalités: bluetooth usb-2.01
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:3
                   description: Vidéo
                   produit: USB2.0 HD UVC WebCam
                   fabriquant: Azurewave
                   identifiant matériel: b
                   information bus: usb@1:b
                   version: 10.15
                   numéro de série: NULL
                   fonctionnalités: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-generic:1 NON-RÉCLAMÉ
             description: Signal processing controller
             produit: Sunrise Point-H Thermal subsystem
             fabriquant: Intel Corporation
             identifiant matériel: 14.2
             information bus: pci@0000:00:14.2
             version: 31
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi cap_list
             configuration: latency=0
             ressources: mémoire:df42f000-df42ffff
        *-generic:2
             description: Signal processing controller
             produit: Sunrise Point-H LPSS I2C Controller #0
             fabriquant: Intel Corporation
             identifiant matériel: 15
             information bus: pci@0000:00:15.0
             version: 31
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             ressources: irq:16 mémoire:df42e000-df42efff
        *-communication
             description: Communication controller
             produit: Sunrise Point-H CSME HECI #1
             fabriquant: Intel Corporation
             identifiant matériel: 16
             information bus: pci@0000:00:16.0
             version: 31
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             ressources: irq:128 mémoire:df42d000-df42dfff
        *-storage
             description: SATA controller
             produit: Sunrise Point-H SATA Controller [AHCI mode]
             fabriquant: Intel Corporation
             identifiant matériel: 17
             information bus: pci@0000:00:17.0
             version: 31
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
              ressources: irq:124 mémoire:df428000-df429fff  mémoire:df42c000-df42c0ff portE/S:f090(taille=8) portE/S:f080(taille=4)  portE/S:f060(taille=32) mémoire:df42b000-df42b7ff
        *-pci:1
             description: PCI bridge
             produit: Sunrise Point-H PCI Express Root Port #3
             fabriquant: Intel Corporation
             identifiant matériel: 1c
             information bus: pci@0000:00:1c.0
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:18 mémoire:df300000-df3fffff
           *-network
                description: Interface réseau sans fil
                produit: Wireless 7265
                fabriquant: Intel Corporation
                identifiant matériel: 0
                information bus: pci@0000:02:00.0
                nom logique: wlp2s0
                version: 59
                numéro de série: e4:42:a6:3b:1f:eb
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
                 configuration: broadcast=yes driver=iwlwifi  driverversion=4.4.0-128-generic firmware=17.352738.0 latency=0 link=no  multicast=yes wireless=IEEE 802.11abgn
                ressources: irq:129 mémoire:df300000-df301fff
        *-pci:2
             description: PCI bridge
             produit: Sunrise Point-H PCI Express Root Port #4
             fabriquant: Intel Corporation
             identifiant matériel: 1c.3
             information bus: pci@0000:00:1c.3
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:19 portE/S:d000(taille=4096) mémoire:df200000-df2fffff
           *-network
                description: Ethernet interface
                produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                fabriquant: Realtek Semiconductor Co., Ltd.
                identifiant matériel: 0
                information bus: pci@0000:03:00.0
                nom logique: enp3s0
                version: 15
                numéro de série: 10:7b:44:1c:9c:eb
                taille: 1Gbit/s
                capacité: 1Gbit/s
                bits: 64 bits
                horloge: 33MHz
                 fonctionnalités: pm msi pciexpress msix bus_master  cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt  1000bt-fd autonegotiation
                configuration:  autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI  duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.40 latency=0  link=yes multicast=yes port=MII speed=1Gbit/s
                ressources: irq:126 portE/S:d000(taille=256) mémoire:df204000-df204fff mémoire:df200000-df203fff
        *-pci:3
             description: PCI bridge
             produit: Sunrise Point-H PCI Express Root Port #7
             fabriquant: Intel Corporation
             identifiant matériel: 1c.6
             information bus: pci@0000:00:1c.6
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:18 mémoire:df100000-df1fffff
           *-generic
                description: Unassigned class
                produit: RTS5229 PCI Express Card Reader
                fabriquant: Realtek Semiconductor Co., Ltd.
                identifiant matériel: 0
                information bus: pci@0000:04:00.0
                version: 01
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                ressources: irq:125 mémoire:df100000-df100fff
        *-isa
             description: ISA bridge
             produit: Sunrise Point-H LPC Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 31
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa bus_master
             configuration: latency=0
        *-memory NON-RÉCLAMÉ
             description: Memory controller
             produit: Sunrise Point-H PMC
             fabriquant: Intel Corporation
             identifiant matériel: 1f.2
             information bus: pci@0000:00:1f.2
             version: 31
             bits: 32 bits
             horloge: 33MHz (30.3ns)
             configuration: latency=0
             ressources: mémoire:df424000-df427fff
        *-multimedia
             description: Audio device
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 1f.3
             information bus: pci@0000:00:1f.3
             version: 31
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             ressources: irq:16 mémoire:df420000-df423fff mémoire:df400000-df40ffff
        *-serial NON-RÉCLAMÉ
             description: SMBus
             produit: Sunrise Point-H SMBus
             fabriquant: Intel Corporation
             identifiant matériel: 1f.4
             information bus: pci@0000:00:1f.4
             version: 31
             bits: 64 bits
             horloge: 33MHz
             configuration: latency=0
             ressources: mémoire:df42a000-df42a0ff portE/S:f040(taille=32)
     *-scsi:0
          identifiant matériel: 1
          nom logique: scsi0
          fonctionnalités: emulated
        *-disk
             description: ATA Disk
             produit: Micron_1100_MTFD
             identifiant matériel: 0.0.0
             information bus: scsi@0:0.0.0
             nom logique: /dev/sda
             version: A020
             numéro de série: 164614A92FC1
             taille: 238GiB (256GB)
             fonctionnalités: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=c5d255c0-2f63-4194-98ff-67944954699d logicalsectorsize=512 sectorsize=512
           *-volume:0 NON-RÉCLAMÉ
                description: Windows FAT volume
                fabriquant: mkfs.fat
                identifiant matériel: 1
                information bus: scsi@0:0.0.0,1
                version: FAT32
                numéro de série: 7a1e-4d0b
                taille: 510MiB
                capacité: 511MiB
                fonctionnalités: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI System Partition
           *-volume:1
                description: Volume EXT4
                fabriquant: Linux
                identifiant matériel: 2
                information bus: scsi@0:0.0.0,2
                nom logique: /dev/sda2
                nom logique: /
                version: 1.0
                numéro de série: 959b1f35-32de-4f0f-ae9a-c8e92d01e046
                taille: 206GiB
                 fonctionnalités: journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                 configuration: created=2018-06-22 21:01:54  filesystem=ext4 lastmountpoint=/ modified=2018-06-24 14:42:08  mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,data=ordered  mounted=2018-06-24 14:42:08 state=mounted
           *-volume:2
                description: Linux swap volume
                fabriquant: Linux
                identifiant matériel: 3
                information bus: scsi@0:0.0.0,3
                nom logique: /dev/sda3
                version: 1
                numéro de série: f97a089f-37d5-4349-81ad-d465d62b568a
                taille: 31GiB
                capacité: 31GiB
                fonctionnalités: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          identifiant matériel: 2
          nom logique: scsi1
          fonctionnalités: emulated
        *-disk
             description: ATA Disk
             produit: ST1000LM035-1RK1
             fabriquant: Seagate
             identifiant matériel: 0.0.0
             information bus: scsi@1:0.0.0
             nom logique: /dev/sdb
             version: SDM1
             numéro de série: WDE8QQNR
             taille: 931GiB (1TB)
             fonctionnalités: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=89814643-0d91-42b5-b41c-d59e434c8d83 logicalsectorsize=512 sectorsize=4096
           *-volume
                description: Volume EXT4
                fabriquant: Linux
                identifiant matériel: 1
                information bus: scsi@1:0.0.0,1
                nom logique: /dev/sdb1
                nom logique: /media/d/3bb45031-d6e9-42c0-b103-d389ed816fff
                version: 1.0
                numéro de série: 3bb45031-d6e9-42c0-b103-d389ed816fff
                taille: 931GiB
                 fonctionnalités: journaled extended_attributes  large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                 configuration: created=2018-06-24 07:53:19  filesystem=ext4 modified=2018-06-24 14:44:23 mount.fstype=ext4  mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2018-06-24  14:44:23 name=Basic data partition state=mounted
     *-scsi:2
          identifiant matériel: 3
          nom logique: scsi2
          fonctionnalités: emulated
        *-cdrom
             description: DVD-RAM writer
             produit: DVDRAM GUE1N
             fabriquant: HL-DT-ST
             identifiant matériel: 0.0.0
             information bus: scsi@2:0.0.0
             nom logique: /dev/cdrom
             nom logique: /dev/cdrw
             nom logique: /dev/dvd
             nom logique: /dev/dvdrw
             nom logique: /dev/sr0
             nom logique: /media/d/Ubuntu 18.04 LTS amd64
             version: AS00
             fonctionnalités: removable audio cd-r cd-rw dvd dvd-r dvd-ram
              configuration: ansiversion=5 mount.fstype=iso9660  mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500  state=mounted status=nodisc
  *-power NON-RÉCLAMÉ
       description: To Be Filled By O.E.M.
       produit: To Be Filled By O.E.M.
       fabriquant: To Be Filled By O.E.M.
       identifiant matériel: 1
       version: To Be Filled By O.E.M.
       numéro de série: To Be Filled By O.E.M.
       capacité: 32768mWh
```

```
lspci -vnn | egrep 'VGA|3D'
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:591b] (rev 04) (prog-if 00 [VGA controller])
01:00.0 3D controller [0302]: NVIDIA Corporation Device [10de:1c8d] (rev a1)
```

```
lshw -c display | grep driver
ATTENTION: ce programme devrait être lancé en tant que super-utilisateur.
       configuration: driver=i915_bpo latency=0

```

```
sudo dpkg -l nvidia-*
Souhait=inconnU/Installé/suppRimé/Purgé/H=à garder
| État=Non/Installé/fichier-Config/dépaqUeté/échec-conFig/H=semi-installé/W=attend-traitement-déclenchements
|/ Err?=(aucune)/besoin Réinstallation (État,Err: majuscule=mauvais)
||/ Nom            Version      Architecture Description
+++-==============-============-============-=================================
un  nvidia-common  <aucune>     <aucune>     (aucune description n'est disponi
un  nvidia-prime   <aucune>     <aucune>     (aucune description n'est disponi

```

```
dkms status 

``` this one doesn't work.

Theses are the errors i have every time I turn on the computer:
```
ACPI Error : [prio] Namespace lockup failure, AE_ALREADY_EXISTS (2017Q831/dswload-378)
ACPI Exception : AE_ALREADY_EXISTS, Duringname lockup/catalog (20170631/psoibject-252)
ACPI Exception : AE_ALREADY_EXISTS, ( SSD : Sata Tab1) while loading table (20170631/tbkfload-228)
ACPI Error : 1 table load failures, 10 succesful (20170631/tbtxt load-246)
``` 

And in the following pictures you can see the mess I have as I try to install/Try without installing:
1) [http://tinypic.com/r/10wpqmw/9](http://tinypic.com/r/10wpqmw/9)
2) [http://tinypic.com/r/2wrddft/9](http://tinypic.com/r/2wrddft/9)
3) [http://tinypic.com/r/2vmtsvt/9](http://tinypic.com/r/2vmtsvt/9)
4) [http://tinypic.com/r/1y0bpf/9](http://tinypic.com/r/1y0bpf/9)
5) [http://tinypic.com/r/242idlh/9](http://tinypic.com/r/242idlh/9)


I asked for help on italian and french forums but theirs solutions didn't work for me, I hope you can help me! Thank you!

EDIT: I also have some issues with the keyboard, I made the reconfig , still sometimes ubuntu doesn't recognize it :/

---

