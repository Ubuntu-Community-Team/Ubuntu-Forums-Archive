---
title: "GRUB/BIOS help"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by idealistic on 2014-05-02
Hi,

I need some guidance about how to boot from a USB live installation device to do an upgrade (my installation manager seems not to be able to do it).
I created the USB with Unetbootin, but how do I get to the BIOS menu ??
I tried all the different keys like C F12 F11 option, alt but nothing seems to work and I don't get any message on the screen indicating me what I should do.

Is there a way I can configure grub or something to *automatically* all the time start with the BIOS menu or at least change the order of the booting ?

Also, I'm not sure whether this is normal or not but I couldn't find any file named menu.lst in the /boot/grub/ file.

Here's the lshw :

```
laptop                   description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1982MiB
     *-cpu
          product: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:90380000-903fffff ioport:20e0(size=8) memory:80000000-8fffffff(prefetchable) memory:90400000-9043ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:90300000-9037ffff
        *-generic UNCLAIMED
             description: Performance counters
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:90444000-90444fff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:90440000-90443fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:90200000-902fffff memory:90500000-906fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 88E8053 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 22
                serial: 00:19:e3:46:d9:c7
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes
                resources: irq:26 memory:90200000-90203fff ioport:1000(size=256) memory:90500000-9051ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:90100000-901fffff memory:90700000-908fffff(prefetchable)
           *-network
                description: Wireless interface
                product: AR5008 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:1c:b3:b4:e6:5e
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k ip=192.168.128.204 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:17 memory:90100000-9010ffff
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:2080(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:2060(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:2040(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:2020(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:90445400-904457ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: memory:90000000-900fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323
                vendor: Agere Systems
                physical id: 3
                bus info: pci@0000:03:03.0
                version: 61
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=248 maxlatency=24 mingnt=12
                resources: irq:19 memory:90000000-90000fff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:20b0(size=16)
           *-cdrom
                description: DVD reader
                product: CD-RW  CW-8221
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: GA0J
                serial: [MATSHITACD-RW  CW-8221  GA0JPP  06/14/06MA
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:20c8(size=8) ioport:20ec(size=4) ioport:20c0(size=8) ioport:20e8(size=4) ioport:20a0(size=16) memory:90445000-904453ff
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:efa0(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage



```

Thanks,

---

### Post by Bucky Ball on 2014-05-02
To get to the BIOS, try delete. Also, the key to press to get to the BIOS will be easily found if you do a search for your machine make and model or look in the computer's manual. 

When you say upgrade, do you mean an upgrade of the entire system, say from 12.04 to 14.04? You don't give much detail (specifically the make and model of your machine and which release you are using). 

And no, BIOS comes before grub, grub has nothing to do with it so can't be set to boot the BIOS. Are you hitting the key at the correct time (immediately after the BIOS screen at boot, just mash it).

---

### Post by idealistic on 2014-05-02
Ok, sorry for being so basic, but could you give me a few commands that would allow me to tell you the right informations ?

And yes, I want to upgrade from 10,04 to 12,04 LTS.

---

### Post by fantab on 2014-05-02
You are upgrading from and 'end of life version [eol]' to a supported version.
You need to read this: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

On serious note I recommend that you install 12.04 clean and fresh. There have been several major changes between 10.04 and 12.04, (the latest version is 14.04).
And these can cause prblems, esp. since you will be upgrading from an 'eol' version for which there is no 'support', really.

So it will be a good idea to do a clean install of 12.04 rather than upgrade.

Back up all your Important DATA first.

---

### Post by idealistic on 2014-05-02
Hi, yes I'm trying to do a clean install from a USB, since the update/upgrade manager is not working any more (I can't install any program, dependancy problems appear all the time)

---

### Post by mörgæs on 2014-05-02
- and it will be even better to do a fresh install of 14.04.

---

### Post by oldfred on 2014-05-02
Each brand is a little different.

 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

It says 32 bit on computer but you have a Core2 T7200 which is a 64 bit chip?

If flash drive is not bootable, BIOS usually will not even show it.

---

