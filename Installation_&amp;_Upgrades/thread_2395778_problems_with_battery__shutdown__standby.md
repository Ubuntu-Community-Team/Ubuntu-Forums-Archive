---
title: "problems with battery // shutdown // standby"
date: 2018-07-06
forum: Installation &amp; Upgrades
---

### Post by sitefan on 2018-07-06
Hello everybody.

I've installed Ubuntu on my computer and I've some problems. I've tried the french forum but no answers

 I can't have any indications about the level of charge of the battery of my computer.

When I shut down my computer, everything stops, I got a black screen, but the computer is still turned on. Same problem with the stand by ! 

Here's what I send to the french community :

```
lshw
ATTENTION: ce programme devrait être lancé en tant que super-utilisateur.
stefan-aspire-e5-573g       
    description: Computer
    bits: 64 bits
    fonctionnalités: smp vsyscall32
  *-core
       description: Motherboard
       identifiant matériel: 0
     *-memory
          description: Mémoire système
          identifiant matériel: 0
          taille: 7891MiB
     *-cpu
          produit: Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz
          fabriquant: Intel Corp.
          identifiant matériel: 1
          information bus: cpu@0
          taille: 1179MHz
          capacité: 3GHz
          bits: 64 bits
          fonctionnalités: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap intel_pt xsaveopt dtherm ida arat pln pts cpufreq
     *-pci
          description: Host bridge
          produit: Broadwell-U Host Bridge -OPI
          fabriquant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 09
          bits: 32 bits
          horloge: 33MHz
          configuration: driver=bdw_uncore
          ressources: irq:0
        *-display
             description: VGA compatible controller
             produit: HD Graphics 5500
             fabriquant: Intel Corporation
             identifiant matériel: 2
             information bus: pci@0000:00:02.0
             version: 09
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             ressources: irq:50 mémoire:c2000000-c2ffffff mémoire:d0000000-dfffffff portE/S:5000(taille=64) mémoire:c0000-dffff
        *-multimedia:0
             description: Audio device
             produit: Broadwell-U Audio Controller
             fabriquant: Intel Corporation
             identifiant matériel: 3
             information bus: pci@0000:00:03.0
             version: 09
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             ressources: irq:53 mémoire:c4510000-c4513fff
        *-usb:0
             description: USB controller
             produit: Wildcat Point-LP USB xHCI Controller
             fabriquant: Intel Corporation
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 03
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             ressources: irq:46 mémoire:c4500000-c450ffff
        *-communication
             description: Communication controller
             produit: Wildcat Point-LP MEI Controller #1
             fabriquant: Intel Corporation
             identifiant matériel: 16
             information bus: pci@0000:00:16.0
             version: 03
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: bus_master cap_list
             configuration: driver=mei_me latency=0
             ressources: irq:51 mémoire:c451b000-c451b01f
        *-multimedia:1
             description: Audio device
             produit: Wildcat Point-LP High Definition Audio Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1b
             information bus: pci@0000:00:1b.0
             version: 03
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: bus_master cap_list
             configuration: driver=snd_hda_intel latency=64
             ressources: irq:52 mémoire:c4514000-c4517fff
        *-pci:0
             description: PCI bridge
             produit: Wildcat Point-LP PCI Express Root Port #1
             fabriquant: Intel Corporation
             identifiant matériel: 1c
             information bus: pci@0000:00:1c.0
             version: e3
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:42 portE/S:2000(taille=4096) mémoire:a0000000-a01fffff portE/S:260000000(taille=2097152)
        *-pci:1
             description: PCI bridge
             produit: Wildcat Point-LP PCI Express Root Port #3
             fabriquant: Intel Corporation
             identifiant matériel: 1c.2
             information bus: pci@0000:00:1c.2
             version: e3
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:43 portE/S:4000(taille=4096) mémoire:c4400000-c44fffff
           *-network
                description: Ethernet interface
                produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                fabriquant: Realtek Semiconductor Co., Ltd.
                identifiant matériel: 0
                information bus: pci@0000:02:00.0
                nom logique: enp2s0
                version: 15
                numéro de série: 2c:60:0c:f7:e1:c3
                taille: 10Mbit/s
                capacité: 1Gbit/s
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                ressources: irq:48 portE/S:4000(taille=256) mémoire:c4404000-c4404fff mémoire:c4400000-c4403fff
        *-pci:2
             description: PCI bridge
             produit: Wildcat Point-LP PCI Express Root Port #4
             fabriquant: Intel Corporation
             identifiant matériel: 1c.3
             information bus: pci@0000:00:1c.3
             version: e3
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:44 mémoire:c4200000-c43fffff
           *-network
                description: Interface réseau sans fil
                produit: QCA9377 802.11ac Wireless Network Adapter
                fabriquant: Qualcomm Atheros
                identifiant matériel: 0
                information bus: pci@0000:03:00.0
                nom logique: wlp3s0
                version: 30
                numéro de série: 30:52:cb:24:10:cd
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=4.15.0-23-generic firmware=WLAN.TF.1.0-00002-QCATFSWPZ-5 ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                ressources: irq:54 mémoire:c4200000-c43fffff
        *-pci:3
             description: PCI bridge
             produit: Wildcat Point-LP PCI Express Root Port #5
             fabriquant: Intel Corporation
             identifiant matériel: 1c.4
             information bus: pci@0000:00:1c.4
             version: e3
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:45 portE/S:3000(taille=4096) mémoire:c3000000-c40fffff portE/S:b0000000(taille=301989888)
           *-display
                description: 3D controller
                produit: GK208M [GeForce 920M]
                fabriquant: NVIDIA Corporation
                identifiant matériel: 0
                information bus: pci@0000:04:00.0
                version: a1
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: bus_master cap_list rom
                configuration: driver=nouveau latency=0
                ressources: irq:49 mémoire:c3000000-c3ffffff mémoire:b0000000-bfffffff mémoire:c0000000-c1ffffff portE/S:3000(taille=128) mémoire:c4000000-c407ffff
        *-usb:1 NON-RÉCLAMÉ
             description: USB controller
             produit: Wildcat Point-LP USB EHCI Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1d
             information bus: pci@0000:00:1d.0
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: ehci cap_list
             configuration: latency=0
             ressources: mémoire:c4519000-c45193ff
        *-isa
             description: ISA bridge
             produit: Wildcat Point-LP LPC Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 03
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             ressources: irq:0
        *-storage
             description: SATA controller
             produit: Wildcat Point-LP SATA Controller [AHCI Mode]
             fabriquant: Intel Corporation
             identifiant matériel: 1f.2
             information bus: pci@0000:00:1f.2
             version: 03
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             ressources: irq:47 portE/S:5088(taille=8) portE/S:5094(taille=4) portE/S:5080(taille=8) portE/S:5090(taille=4) portE/S:5060(taille=32) mémoire:c4518000-c45187ff
        *-serial NON-RÉCLAMÉ
             description: SMBus
             produit: Wildcat Point-LP SMBus Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1f.3
             information bus: pci@0000:00:1f.3
             version: 03
             bits: 64 bits
             horloge: 33MHz
             configuration: latency=0
             ressources: mémoire:c451a000-c451a0ff portE/S:5040(taille=32)
     *-scsi
          identifiant matériel: 2
          nom logique: scsi1
          fonctionnalités: emulated
        *-cdrom
             description: DVD-RAM writer
             produit: DVD A  DA8A6SH
             fabriquant: Slimtype
             identifiant matériel: 0.0.0
             information bus: scsi@1:0.0.0
             nom logique: /dev/cdrom
             nom logique: /dev/cdrw
             nom logique: /dev/dvd
             nom logique: /dev/dvdrw
             nom logique: /dev/sr0
             version: GA11
             fonctionnalités: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
ATTENTION: les informations sont potentiellement incomplètes ou erronées, vous devriez lancer ce programme en tant que super-utilisateur.

```

thank you !

---

### Post by sitefan on 2018-07-10
anybody ?

---

