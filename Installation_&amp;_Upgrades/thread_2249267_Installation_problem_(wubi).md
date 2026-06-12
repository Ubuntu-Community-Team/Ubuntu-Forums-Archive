---
title: "Installation problem (wubi)"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by Ifch0o1 on 2014-10-20
Hello. I have the following problem:
I tried to install lubuntu at normal way and I had this error: * Stopping CPU interrupts balancing daemon. [ OK ]. I research for some solution and I founded two things. 1-Deactivate installation slider and 2-Install with nomodeset. I don't know how to deactivate the slider. I researched how to install it with nomodeset and miracle, installation reached 'calc files for skip copying' and then 'copying files...'. I don't know how long it takes by default, but after 1-2 minutes the screen changed and the UI started.

Here is the problem. Sorry if I not explaning it fully correct but now I using windows for posting this thread because lubuntu is hard to use in this state.
When the UI started i get ubuntu crash message. ~"Ubuntu crashed if you experiencing this problem reboot."
Some info about this error: 
**Execution path**: usr/bin/ubiquiti-dm, **Package**: ubiquiti 2.10.16, **Title**: ubiquiti-dm crashed with *ValueError()* in command-line error.. literal in *int()* base 10: *"*   (the same exeption is thrown in stack trace) 
**Uniquiti-dm**: Here was a long text, but i attention on some lines here. It starting with X.org server or something. and below I see some errors:
(EE) cannot find module "nvidia"
(EE) cannot find module "nv"
this errors are repeated again.

More info:
The mouse leave permanent trails (big rectangles). Until the content is re-rendered the trails didn't vanish. Mouse pointer showing the arrow and loading circle simultaneously. Sometimes they are at different places at the screen, but it moving together. The system have other graphical issues.

I see in sympatic package manager I have some kind of nouveau nvidia drivers installed. When I try to install Nvidia 17x or 96, I get an error: fix damaged pakage first (or something).

The interesting thing is that when I reboot the OS with or without nomodeset, Installation starting again and it says something like: The root.dsk or some file like this is existing and cannot be installed. Reinstall to fix this problem. So when i installing lubuntu, it's starting the first time with the ubuntu crash. If I reboot, the installation starts again and cannot be continued.

System spec:
AMD Sempron 2400+
1GB Ram DDR1
Nvidia GeForce 6200 (128MB) AGP
IDE HDD
VIA KT880 chipset on Gigabyte board.

Trying to install Lubuntu 12.04 under windows XP with Wubi 12.04 on NTFS partition (fresh formatted).

Ok, I tried installing with "safe graphics mode" and installation do the same thing but with different resolution - copying files... (after it reaches ~20%) screen stopped responding, no desktop showed, no "start menu" (I dunno how it is called on linux). But the OS is started. I can run the browser and terminal from the right click menu on the desktop. The cursor is at "loading state" [FONT=tahoma][COLOR=#000000]perennially, but no trails leaved. Now I can use the browser and terminal, it's work fine, but I cannot use the OS at all.[/COLOR][/FONT]

---

### Post by mörgæs on 2014-10-21
Are you able to run any kind of Buntu in a live boot? 
If so please execute ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Ifch0o1 on 2014-10-21
> **mörgæs said:**
> Are you able to run any kind of Buntu in a live boot? 
If so please execute ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

I started lubuntu in Demo Mode this time, It's working fine. Here I execute this command. The file contents:
```

    computer    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1
  *-core
       description: Motherboard
       product: GA-7VT880
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F3
          date: 07/05/2005
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm)
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1670MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back
     *-memory
          description: System Memory
          physical id: 1c
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             physical id: 0
             slot: A0
             size: 256MiB
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM 400 MHz (2.5 ns)
             physical id: 1
             slot: A1
             size: 256MiB
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM 400 MHz (2.5 ns)
             physical id: 2
             slot: A2
             size: 256MiB
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM 400 MHz (2.5 ns)
             physical id: 3
             slot: A3
             size: 256MiB
             clock: 400MHz (2.5ns)
     *-pci:0
          description: Host bridge
          product: KT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:f0000000-f7ffffff
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:f8000000-faffffff memory:e0000000-efffffff
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:16 memory:f8000000-f8ffffff memory:e0000000-efffffff memory:f9000000-f9ffffff memory:fa000000-fa01ffff
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:d000(size=16)
           *-disk
                description: ATA Disk
                product: ST380011A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.01
                serial: [REMOVED]
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=17d917d8
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/F29C80139C7FD119
                   version: 3.1
                   serial: [REMOVED]
                   size: 21GiB
                   capacity: 21GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2014-05-17 03:17:08 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 52GiB
                   capacity: 52GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /isodevice
                      capacity: 52GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d400(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:dc00(size=32)
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:e000(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:fb000000-fb0000ff
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:22 ioport:e400(size=256)
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 13
             bus info: pci@0000:00:13.0
             logical name: eth0
             version: 10
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
             resources: irq:18 ioport:e800(size=256) memory:fb001000-fb0010ff
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
             vendor: VIA Technologies, Inc.
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 46
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=32
             resources: irq:16 memory:fb002000-fb0027ff ioport:ec00(size=128)
     *-pci:1
          description: Host bridge
          product: KT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: KT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: KT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: KT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: KT880 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz

```

I am able to execute this while installation running I think. I didn't fully understand what you mean with "live boot".

---

### Post by mörgæs on 2014-10-21
Wubi is a dead-end street and Lubuntu 12.04 is out of support. I suggest a real dual boot with Lubuntu 14.04.1 in stead.

The hardware is going to work fine but without SSE2. More info in the link in my signature.

---

