---
title: "Please Help Upgrade/Downgrade all_generic_ide=1"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by DLoc on 2010-01-05
First let me say I'm new to ubuntu. (Currently running 9.10 with cd-rom issues and other issues listed below)
Please let me know what logs etc... you need from me. I've been trying to do my "Research" before acting/ asking questions here. Now for my being an idiot so I need help story.
I have a compaq sr1803wm intel celeron d (maybe EM64T) with ATI intergrated graphics card Radeon Xpress 200 (whcih began my problems) displayed via s-video to TV.
I upgraded to ubuntu 9.10 hoping the graphics card would have drivers. (no)
Then I found out I needed the catalist drver 9.3 (not supported on either ubuntu 9.04 or 9.10 as it is now a legacy driver by ATi)
So I attempted to downgrade xserver so I could use the 9.3 graphics driver (didn't work)
Then I had the bright idea to just downgrade my operating system to ubuntu 8.10 (I got multiple I/O errors beginning with something like Buffer I/O error on device sr0, logical block which repeated until the live cd would freeze. So I went to google and typed the error in and the response I found was that at the install/boot options F6 you needed to add the line irqpoll generic_ide=1 as well as trying a other time with all_generic_ide=1 (different combos to tell the truth listed in bug reports solved) 
Again nothing. So I decided to try the 64 bit version 8.10 (EM64T) which didn't work.
Then I decided to go to 64bit 8.04, (can't remember if I needed to use any of the all_generic_ide=1 but I do not think so) And BINGO it opened the try ubuntu live cd. So I installed it. 
But after reboot the system went really slow. I couldn't even open terminal. So I installed ubuntu 9.04 again so I could burn the 32bit version and be happy to get my graphics card working etc... But I couldn't burn the image I thought I was doing something wrong at first and went back over the tutorials. Still burning cd's with nothing on them and finalized. I then upgraded back to 9.10 to make sure it would burn. Still it wouldn't burn the live cd. So I then realized I must have messed something up with the whole all_generic_ide=1 thing. I did lshw and it shows that now I have wlan0 instead of wifi0, Instead of having only pci and SMbus I now had Bus and IDE instead of PCI. Please help me fix this. I want to install ubuntu 8.04 and have the ability to write in my cd writer.:( :confused:

---

### Post by DLoc on 2010-01-05
ideas any one? Before entering all_generic_ide=1 as a install paramater my lshw did not show *ide0, *ide1, *ide2. How do I change this back to PCI? (factory settings on my hard drive and samsung cd-rom are set to cable select and in boot loader show up as both master)

---

### Post by DLoc on 2010-01-05
Ok so I've booted up the live cd of 8.04.3 LTS (I'll try install Using the intel boot parameter)
Here is the result of lshw and lspci and cat /etc/issue

ubuntu@ubuntu:~$ cat /etc/issue
Ubuntu 8.04.3 LTS \n \l

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
          size: 222MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc up pebs bts pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
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
             capabilities: pci normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=64 mingnt=8
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
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
             version: 80
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
             version: 80
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
             version: 82
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   product: HDS728080PLAT20
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 74GiB (80GB)
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   product: TSSTcorpCD-R/RW TS-H292C
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   logical name: /cdrom
                   capacity: 696MiB (730MB)
                   capabilities: packet
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
        *-multimedia
             description: Audio device
             product: IXP SB4x0 High Definition Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
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
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:15:f2:ea:e4:80
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.4 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-network:1
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: wifi0
                version: 01
                serial: 00:11:50:d4:ca:98
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW323
                vendor: Agere Systems
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=24 mingnt=12 module=ohci1394
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem
02:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
ubuntu@ubuntu:~$

---

### Post by DLoc on 2010-01-05
intel boot parametr did not help. still froze after logging in

---

### Post by DLoc on 2010-01-09
ok so I've finally found out the generic.all_generic_ide=1 changed my bios setup and I need to re-enable my native hd settings. I'm not sure exactly where it is in my pheonix bios. Any help is appriceated

---

### Post by lynnevan on 2010-01-09
Every bios I've ever seen has an option to reset defaults, usu near the end of the bios menu, or as part of the "save" options - "save settings and exit", "exit without saving", "set default options", etc.  Or maybe even at the bottom of all screens where it explains how to do thing, as in (maybe), F7 = default settings.

---

### Post by DLoc on 2010-01-09
So I tried the default settings in my bios. It's still showing a simular lshw but I'll try writing a cd before saying I can't get it to work.

---

### Post by DLoc on 2010-01-10
Ok, so I reinstalled grub and I think it's fixed now. (again need to try and burn a cd) but the ath0 eth0 and lo are back when I do ifconfig.

---

### Post by kansasnoob on 2010-01-10
If this is your total memory I don't think you'll get Ubuntu running at all well on that:

> *-memory
description: System memory
physical id: 0
size: 222MiB

> Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * **384 MB of system memory (RAM)**
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    *

      Sound card
    *

      A network or Internet connection

---

