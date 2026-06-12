---
title: "after install, ubuntu server can not run?"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by srobert on 2007-02-06
I am newbie,

after ubuntu server install, it can not run? 

stop at show "booting the kernel...."

why, Thanks.

---

### Post by apjone on 2007-02-06
Hi, welcome to Ubuntu Forums.

Which Version did you install ?
What CPU, RAM, GFX are you using ?

Post these and you will recieve more help

---

### Post by felixj on 2007-02-09
Hi.
I'm having the same problem. Trying to install Dapper-server-CD to an IBM t40 Notebook. Installation goes fine but when rebooting grub loads but then it stops at "Uncompressing Linux... Ok, booting the kernel." No further messages.

What I tried so far:
- I turned off the IBM-recovery-tool
- I tried to boot with acpi=off
no changes

Just to test the notebook I did an install of the edgy-desktop-cd. Everything worked nicely out of the box. I need to install dapper-server because i want to follow this howto to completely encrypt the system: [https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem). As you can see I'm stuck before it becomes even interesting.
Thanks, felixj

---

### Post by apjone on 2007-02-10
> **felixj said:**
> Hi.
I'm having the same problem. Trying to install Dapper-server-CD to an IBM t40 Notebook. Installation goes fine but when rebooting grub loads but then it stops at "Uncompressing Linux... Ok, booting the kernel." No further messages.

What I tried so far:
- I turned off the IBM-recovery-tool
- I tried to boot with acpi=off
no changes

Just to test the notebook I did an install of the edgy-desktop-cd. Everything worked nicely out of the box. I need to install dapper-server because i want to follow this howto to completely encrypt the system: [https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem). As you can see I'm stuck before it becomes even interesting.
Thanks, felixj

whats the cpu or the notebook?

---

### Post by felixj on 2007-02-10
As I wrote, it's an IBM T40:

```
lshw
WARNING: you should run this program as super-user.
rosa
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1011MB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1500MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.9.5
          size: 600MHz
          capacity: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: d0000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:d0000000-dfffffff
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon Mobility M7 LW [Radeon Mobility 7500]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e0000000-e7ffffff ioport:3000-30ff iomemory:c0100000-c010ffff irq:11
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1800-181f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:c0000000-c00003ff irq:11
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-26-386 ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   physical id: 3
                   bus info: usb@4:3
                   version: 1.00
                   capabilities: usb-2.00 scsi
                   configuration: driver=usb-storage maxpower=100mA speed=480.0MB/s
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:b0000000-b0000fff irq:11
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0.1
                bus info: pci@02:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:b1000000-b1000fff irq:5
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth0
                version: 81
                serial: 00:0d:60:3b:11:b5
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 ip=192.168.0.170 multicast=yes
                resources: iomemory:c0200000-c0200fff ioport:8000-803f irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1860-186f iomemory:50000000-500003ff irq:11
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: FUJITSU MHV2080AH
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 74GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: HL-DT-STDVD-ROM GDR8083N
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             resources: ioport:1880-189f irq:5
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH
             resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:c0000c00-c0000dff iomemory:c0000800-c00008ff irq:5
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             resources: ioport:2400-24ff ioport:2000-207f irq:5
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage

```

I couldn't solve this problem, so I used the Desktop-Installation-Disc, which worked nicely. Although I think it's a pain in the *** that you have to start the life-system to install to the harddisc. But that's just mho.

Anyway, the encryption howto works great.

Thanks for your reply,
felixj

---

### Post by apjone on 2007-02-12
thats odd the standerd server cd should work, you could always thry the alternate server install.

---

