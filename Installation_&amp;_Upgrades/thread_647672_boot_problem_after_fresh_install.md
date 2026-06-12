---
title: "boot problem after fresh install"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by Angelbeast on 2007-12-22
Hello and thank you in advance for any help.

Let me give you a little history. I had previously installed the 64 bit version of feisty fawn. the 64 bit version to me was nothing but hedache so i finally decided to downgrde to the 32 bit version...now what was actually on my hard drive at the time i decided to downgrade was gutsy after the upgrade tothe next version...

so i format and do a fresh install of 32 bit gutsy...now i am having boot problems...
when i go to boot from the hard disk or the live cd i get the error:

cannot allocate resource region 7 bridge

and

cannot allocate resource region 8 bridge

booting from the hard disk it just hangs but booting to the live cd it does actually boot...is there any way to fix this?

---

### Post by Pumalite on 2007-12-22
From Live CD Terminal, post this:
sudo fdisk -lu
lshw

---

### Post by Angelbeast on 2007-12-22
> **Pumalite said:**
> From Live CD Terminal, post this:
sudo fdisk -lu
lshw

What does this do?

---

### Post by Angelbeast on 2007-12-22
ah okay...here's the output...


Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d6a1d69

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   150239879    75119908+  83  Linux
/dev/hda2       150239880   156296384     3028252+   5  Extended
/dev/hda5       150239943   156296384     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf998f998

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   156296384    78148161   83  Linux
ubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1010MB
     *-cpu
          product: AMD Turion(tm) 64 Mobile Technology ML-37
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.4.2
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MB
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=66 mingnt=8
        *-pci:1
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=0 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk:0
                   product: FUJITSU MHV2080AH
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 74GB
              *-disk:1
                   product: FUJITSU MHV2080AH
                   vendor: Fujitsu
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 74GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   product: PIONEER DVDRW DVR-K15
                   vendor: Pioneer
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 695MB
                   capabilities: packet
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0 DISABLED
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: eth1
                version: 02
                serial: 00:14:a5:1d:94:ad
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:06:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 4.2
                bus info: pci@0000:06:04.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 4.3
                bus info: pci@0000:06:04.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7 module=tifm_7xx1
           *-system
                description: Generic system peripheral
                product: PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
                vendor: Texas Instruments
                physical id: 4.4
                bus info: pci@0000:06:04.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 maxlatency=4 mingnt=7 module=sdhci
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 6
                bus info: pci@0000:06:06.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:bc:03:ad
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=69.14.108.108 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: generic bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2 module=snd_atiixp_modem
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
          configuration: driver=k8temp module=k8temp

---

### Post by Pumalite on 2007-12-22
If your Live CD is booting, it'll tell me everything I need to know to try to help you.

---

### Post by Pumalite on 2007-12-22
Try installing with the Alternate CD.

---

### Post by Angelbeast on 2007-12-22
> **Pumalite said:**
> Try installing with the Alternate CD.

How do i do that? All i have is the regular install cd.

---

### Post by Pumalite on 2007-12-22
Download it from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the sign 'Start Download'

---

### Post by Angelbeast on 2007-12-22
> **Pumalite said:**
> Download it from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the sign 'Start Download'

Okay it's downloading...I didn't know i could download nd save while using the live cd.

Now it says it uses a text based installer. Is that very complicated?

---

### Post by Angelbeast on 2007-12-22
hey wait..i hve the live cd running in the cd drive...i would need to take it out to burn this new one to disk...will the live cd version still run if i take it out?  *LOL*

---

### Post by Angelbeast on 2007-12-22
alright well i can't download it anyway...says i don't have enough disk space after it gets about half way done...

---

### Post by Angelbeast on 2007-12-22
> **Pumalite said:**
> Try installing with the Alternate CD.

what do i do now?

---

