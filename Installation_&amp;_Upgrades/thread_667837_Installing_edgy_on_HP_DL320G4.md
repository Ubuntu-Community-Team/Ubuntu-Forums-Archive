---
title: "Installing edgy on HP DL320G4"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Schleproque on 2008-01-14
Good Day, 

I am trying to install Edgy aka 6.10 from the server install CD on a HP DL320 G4. 

Right after the I am asked for which languages to use the screen turns blue with a white bar across the bottom.

Any help will be most appreciated.

Thanks,
Rodney

---

### Post by Pumalite on 2008-01-14
Do you have Raid enabled?

---

### Post by Schleproque on 2008-01-14
Yes, it is. Guess you are telling me that I should try it with the RAID disabled. :)

Will do.

---

### Post by Pumalite on 2008-01-15
It was just a question, but you hit the perfect answer.

---

### Post by Schleproque on 2008-01-15
Sadly it did not work. 

I was expecting the problem to be lack of driver support for the 82801GR/GH but it appears that many people have gotten the system to work. 

Still working.

---

### Post by Pumalite on 2008-01-15
If you are going to use the Raid Array after all, check Fake Raid How-to in Google.

---

### Post by Schleproque on 2008-01-15
I would do that but I can't even get the system to get that far. 

It goes to a blue screen with a white bar that I can enter text into.

Thanks,
Rodney

---

### Post by Pumalite on 2008-01-15
Have you read this?
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Schleproque on 2008-01-15
I had skimmed it and stopped when the system talked about having a live CD desktop which I can't get to.

I am going to try the alternative cd soon.

Thanks

---

### Post by Pumalite on 2008-01-15
Post:
lshw

---

### Post by Schleproque on 2008-01-16
The box is currently running RH el 4 but I would like to have it running Edgy. I have not been able to get edgy to install or start a live cd.

Here is the lslw:
    description: Rack Mount Chassis
    product: ProLiant DL320 G4
    vendor: HP
    serial: USE637NBVR
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=rackmount uuid=34313431-3035-5553-4536-33
374E425652
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: HP
          physical id: 0
          version: D20 (08/25/2006)
          size: 64KB
          capacity: 960KB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect int13fl
oppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial
int17printer int10video acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.10
          serial: 0000-0F4A-0000-0000-0000-0000
          slot: Proc 1
          size: 3GHz
          capacity: 3GHz
          width: 64 bits
          clock: 800MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic
 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86
-64 pni monitor ds_cpl est cid xtpr cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 710
             slot: Processor 1 Internal L1 Cache
             size: 16KB
             capacity: 32KB
             capabilities: burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 720
             slot: Processor 1 Internal L2 Cache
             size: 2MB
             capacity: 16MB
             capabilities: burst internal write-back
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 730
             slot: Processor 1 Internal L3 Cache
             capacity: 8MB
             capabilities: burst internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: DIMM 01
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous [empty]
             physical id: 1
             slot: DIMM 02
             width: 64 bits
        *-bank:2
             description: DIMM Synchronous [empty]
             physical id: 2
             slot: DIMM 03
             width: 64 bits
        *-bank:3
             description: DIMM Synchronous [empty]
             physical id: 3
             slot: DIMM 04
             width: 64 bits
     *-pci
          description: Host bridge
          product: E7230/3000/3010 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 81
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: E7230/3000/3010 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_li
st
           *-pci
                description: PCI bridge
                product: EPB PCI-Express to PCI-X Bridge
                vendor: Broadcom
                physical id: 0
                bus info: pci@0000:04:00.0
                version: b5
                width: 64 bits
                clock: 33MHz
                capabilities: pci pciexpress pcix pm normal_decode bus_master ca
p_list
                resources: iomemory:220001f10-220001f0f
              *-network:0
                   description: Ethernet interface
                   product: NetXtreme BCM5714 Gigabit Ethernet
                   vendor: Broadcom Corporation
                   physical id: 4
                   bus info: pci@0000:05:04.0
                   logical name: eth0
                   version: a3
                   serial: 00:18:71:e8:da:31
                   size: 1GB/s
                   capacity: 1GB/s
                   width: 64 bits
                   clock: 66MHz
                   capabilities: pcix pm vpd msi bus_master cap_list ethernet ph
ysical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                   configuration: autonegotiation=on broadcast=yes driver=bcm570
0 driverversion=8.3.17c duplex=full firmware=5714-v3.24 ip=66.77.140.11 latency=
64 link=yes mingnt=64 multicast=yes port=twisted pair speed=1GB/s
              *-network:1
                   description: Ethernet interface
                   product: NetXtreme BCM5714 Gigabit Ethernet
                   vendor: Broadcom Corporation
                   physical id: 4.1
                   bus info: pci@0000:05:04.1
                   logical name: eth1
                   version: a3
                   serial: 00:18:71:e8:da:32
                   size: 1GB/s
                   capacity: 1GB/s
                   width: 64 bits
                   clock: 66MHz
                   capabilities: pcix pm vpd msi bus_master cap_list ethernet ph
ysical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                   configuration: autonegotiation=on broadcast=yes driver=bcm570
0 driverversion=8.3.17c duplex=full firmware=5714-v3.24 ip=172.16.0.9 latency=64
 link=yes mingnt=64 multicast=yes port=twisted pair speed=1GB/s
              *-pci
                   description: PCI bridge
                   product: BCM5785 [HT1000] PCI/PCI-X Bridge
                   vendor: Broadcom
                   physical id: 8
                   bus info: pci@0000:05:08.0
                   version: b4
                   width: 32 bits
                   clock: 66MHz
                   capabilities: pci pcix normal_decode bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_li
st
        *-pci:2
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_li
st
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: latency=0
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.9-22.ELsmp uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: latency=0
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.9-22.ELsmp uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: latency=0
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.9-22.ELsmp uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: latency=0
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.9-22.ELsmp uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: latency=0
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.9-22.ELsmp ehci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: ES1000
                vendor: ATI Technologies Inc
                physical id: 3
                bus info: pci@0000:01:03.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm vga bus_master cap_list
                configuration: latency=64 mingnt=8
           *-system:0 UNCLAIMED
                description: System peripheral
                product: Integrated Lights Out Controller
                vendor: Compaq Computer Corporation
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Integrated Lights Out  Processor
                vendor: Compaq Computer Corporation
                physical id: 4.2
                bus info: pci@0000:01:04.2
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-usb
                description: USB Controller
                product: Hewlett-Packard Company
                vendor: Hewlett-Packard Company
                physical id: 4.4
                bus info: pci@0000:01:04.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm uhci bus_master cap_list
                configuration: latency=64
              *-usbhost
                   product: UHCI Host Controller
                   vendor: Linux 2.6.9-22.ELsmp uhci_hcd
                   physical id: 1
                   bus info: usb@5
                   logical name: usb5
                   version: 2.06
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
                 *-usb:0
                      description: Keyboard
                      product: Virtual Keyboard
                      vendor: HP
                      physical id: 1
                      bus info: usb@5:1
                      version: 0.01
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=0mA speed=12.0MB/s
                 *-usb:1
                      description: USB hub
                      product: Virtual Hub
                      vendor: HP
                      physical id: 2
                      bus info: usb@5:2
                      version: 0.01
                      capabilities: usb-1.10
                      configuration: driver=hub maxpower=0mA slots=7 speed=12.0M
B/s
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide UNCLAIMED
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: 82801GR/GH (ICH7 Family) SATA RAID Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list scsi-host
             configuration: driver=adpahci latency=0
           *-disk
                description: SCSI Disk
                product: RAID 1
                vendor: ADAPTEC
                physical id: 0.5.0
                bus info: scsi@0:0.5.0
                logical name: /dev/sda
                version: 1.0
                size: 232GB
                capabilities: partitioned partitioned:dos
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.5.0,1
                   logical name: /dev/sda1
                   capacity: 101MB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux LVM Physical Volume partition
                   physical id: 2
                   bus info: scsi@0:0.5.0,2
                   logical name: /dev/sda2
                   serial: QazOSX-5BL0-SeoM-NdLw-9Wix-UFE1-5pMwGo
                   size: 232GB
                   capacity: 232GB
                   capabilities: primary multi lvm2

---

### Post by Pumalite on 2008-01-16
If you post exact error of where you are getting stuck; we can help you better.

---

### Post by Schleproque on 2008-01-16
I put the install cd in the server and reboot the system. The installation menu appears and I select install system on local disk or what ever the equivalent is. The installation asks which language I want to use and what language my keyboard is. I answer these questions and then the screen goes blue except for a white bar along the bottom, any text I type appears in this box. The system sits in this state indefinitely.

Thanks,
Rodney

---

### Post by Pumalite on 2008-01-16
I'd burn a new CD at 4x or less after doing md5sum on iso. Use CD-R of good quality.

---

### Post by Schleproque on 2008-01-17
It made no difference.

Any other ideas?

Thanks,
Rodney

---

### Post by Pumalite on 2008-01-17
Try the CD in a different computer.

---

### Post by Schleproque on 2008-01-18
The problem is still there on the other machine.

I tried a 7.10 installation cd and it worked fine.

Thanks,
Rodney

---

