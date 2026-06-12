---
title: "Restoring to a working state after new Driver"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Parrothead74 on 2008-06-28
Hello. I want to install the video driver that Ubuntu Gutsy has been bugging me about and am a little anxious. When I had Hardy on this little laptop, I just couldn't get anything to allow my little Mobility Radeon 9000 IGP to give my 3D hardware acceleration. Now that I've downgraded OS's, things are working beautifully. The driver that the OS wants to install is "xserver-xorg-video-intel" Now it could just be my ignorance, but I can't see how an Intel driver will serve an ATI chipset. But if for some reason this driver is just what I need, is there a way to go back if issues arrive? And is there a way someone could describe it for and experienced Windows user who knows very little of Linux? 

Thanks! 
Dave.

---

### Post by Pumalite on 2008-06-28
Do you have an Intel chipset in your motherboard?
[http://packages.ubuntu.com/gutsy/xserver-xorg-video-intel](http://packages.ubuntu.com/gutsy/xserver-xorg-video-intel)

---

### Post by Parrothead74 on 2008-06-28
I thought it was an ATI chipset. The Laptop is a Toshiba A75-S206. I know ATI does the driver thing, but they do dabble in mobo chipsets as well.

---

### Post by Pumalite on 2008-06-28
We can find out; post:
lshw

---

### Post by Parrothead74 on 2008-06-29
Here we go:

WARNING: you should run this program as super-user.
yoshi                     
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 383MB
     *-cpu
          product: Mobile Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          size: 2800MHz
          capacity: 2800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor ds_cpl est tm2 cid xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: RS300 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-ati latency=64 module=ati_agp
        *-pci:0
             description: PCI bridge
             product: Radeon 9100 IGP AGP Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: RS300M AGP [Radeon Mobility 9100IGP]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=66 mingnt=8
        *-usb:0
             description: USB Controller
             product: OHCI USB Controller #1
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: OHCI USB Controller #2
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: EHCI USB Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SMBus
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 18
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: Dual Channel Bus Master PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: WDC WD2500BEVE-00WZT0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 232GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: TOSHIBA DVD-ROM SD-R2512
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-isa
             description: ISA bridge
             product: ATI Technologies Inc
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
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Wireless interface
                product: AR5212/AR5213 Multiprotocol MAC/baseband processor
                vendor: Atheros Communications, Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: wifi0
                version: 01
                serial: 00:90:96:b7:33:a2
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.105 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:02:3f:d4:d6:33
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
        *-multimedia
             description: Multimedia audio controller
             product: IXP150 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2 module=snd_atiixp
        *-communication
             description: Modem
             product: IXP AC'97 Modem
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: generic bus_master
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2 module=snd_atiixp_modem

Thanks!

---

### Post by Pumalite on 2008-06-29
The only Intel thing here is your CPU. My advise is to still upgrade.

---

