---
title: "Live cd (hardy) Won't Boot into Desktop!"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by symon1980 on 2008-06-17
Hi guys. There seems to be a problem for alot of people with 
the ubuntu hardy live cd, and the linux mint Elyssa live cd. I have 2 computers, and it worked on one of them, but not on the other pc, even though it had ubuntu/mint earlier version on it. 

There must be a slight bug with hardy when it encounters specific hardware.
You get into the login screen, it logs you into the desktop, and then boots you out back to the login screen again. And no cheats or tricks that i have found have worked. I've tried all the tricks in the book that i am aware of.
I've seen alot of people with this bug in the last couple days.

Anybody else had this problem?
Anybody know how to solve it?

---

### Post by Pumalite on 2008-06-17
What are your specs in the computer with difficulties?

---

### Post by symon1980 on 2008-06-18
ok, heres a full list :) its gonna be a lone one....

fleur@fleur-desktop:~$ sudo lshw
[sudo] password for fleur:
fleur-desktop             
    description: Desktop Computer
    product: EG214AA-ABG SR1620AN AN540
    vendor: Compaq Presario 061
    version: 0qm0411RE101AMETM00
    serial: AUB54007S9
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=80FFA1E8-45A4-1010-B331-F5041B19A0A3
  *-core
       description: Motherboard
       product: AMETHYST-M
       vendor: MSI
       physical id: 0
       version: 1.0
       slot: A3
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.47 (03/03/2006)
          size: 128KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Sempron(tm) Processor 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.15.0
          slot: Socket 939
          size: 1800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous internal write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.15.0
          slot: Socket 939
          size: 1800MHz
          capacity: 3GHz
          clock: 200MHz
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 256KB
             capacity: 256KB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 256MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 256MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2.5 ns) [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 64 bits
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
             capabilities: pci ht normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RS480 [Radeon Xpress 200G Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-ide:0
             description: IDE interface
             product: 4379 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: SCSI Disk
                product: WDC WD800JD-60LU
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 07.0
                serial: WD-WMAMD4645826
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 8001MB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 7632MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 59GB
                   capabilities: primary
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
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
             capabilities: msi ohci bus_master cap_list
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
             capabilities: pm msi ehci bus_master cap_list
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
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:1
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4120B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: A102
                   serial: K13472C1543
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2 status=nodisc
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
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: Agere Systems
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=14 mingnt=252
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:90:bd:4b
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
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
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: USB SD Reader
             vendor: Generic
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: USB CF Reader
             vendor: Generic
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             version: 1.01
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: USB SM Reader
             vendor: Generic
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
             version: 1.02
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: USB MS Reader
             vendor: Generic
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
             version: 1.03
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sde
fleur@fleur-desktop:~$

---

### Post by Sef on 2008-06-18
How about what's your ram, video, card, motherboard, and is the BIOS set to boot from the CD first?

---

### Post by symon1980 on 2008-06-18
i know its a long list, but its in there. thats the full list.
Radeon Xpress 200g series
description: Motherboard
product: AMETHYST-M
vendor: MSI
512 ram

and yes ofcoarse the bios is set to boot from cd. How do u think i get to the login screen :p :)

---

### Post by symon1980 on 2008-06-18
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/188660](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/188660)

apparently its a bug that happens to people with radeon Xpress series
graphics cards
arghhh.
hope this gets fixed soon
hardy has been out for a while now.

---

### Post by meindian523 on 2008-06-18
Um,I've a Radeon XPRess 200 and I didn't have any problem running the Live CD or installing.

---

### Post by Lesleyp on 2008-06-18
I'm also haveing problems loading the Live CD's of both Ubuntu 8.04, and Mint 5 . But I'm running with an Nvidia video card.

---

### Post by Lesleyp on 2008-06-18
Geetings all, a fuller response from my previous.

re Ubuntu 8.04 Live CD.

I insert disk and choose language.
The main menu opens and I can scroll through the options, butnone work. 
"Install" just freezez the screen. 
"Try" either siezes, or once the kernel starts loading but freezes at 7%. 
"Check for CD defects" does nothing.

My .iso came from my computer magazines DVD
I have verified the image integrity using checksum (winMd5Sum)
I have burned from .iso to 3 different disks using Nero image burner.
I have running the disks from both installed optical drives

I have previously had Ubuntu 7.04 and 7.10 installed and run them live in memory. Ditto for Linux Mint 4

My setup is as follows:-
Dual Boot with WinXP
Processor:  Pentium D Dual 940 core 3.2 Ghz
Mainboard: Intel DP965LT 
RAM 2GB Corsair Value Select PC - 5300
Video: XpertVision (nVIDIA) GeForce 6600 PCI-E 512 MB
Optical Drives: Samsung DVD-ROM - DDU1615; LG DVD RAM - HL-DT-ST DVDRA< GSA-H1oN
Hard Drives: 2 X Western Digital 250 KS Series

I also tried the Ubuntu derived Mint 5.
Went through the same proceedurs. After I load the disk it freezes at "loading please wait"

---

### Post by Pumalite on 2008-06-18
I'd ad vise the Alternate CD to all of you, bur you also might need to add some boot parameters in there too:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
Try the m0ost common ones first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=788
Alone or in different combinations, until you hit the right one.

---

