---
title: "Cannot install any Linux, it hangs at partition formatting"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by infocom on 2008-09-23
Hi

I have been trying to get Ubuntu to work for a long time. It was installed but kept hanging. So I thought I would re-install it. But now it hangs on Partition Formatting, particularly the ext3 part. 

So I thought i would try other Linux's. I tried Suse and Debian, and both also hang during partition formatting. Actually, Suse got past that but then had an error on almost every package install. 

So I wonder if its a hardware issue. Would anyone be able to advise on this? If it is hardware how do I find out what? 

Thanks

---

### Post by Pumalite on 2008-09-23
Boot your Live CD and post:
sudo lshw

---

### Post by infocom on 2008-09-23
Here you go, thanks:-

```

ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Desktop Computer
    product: NF61S-M2A
    vendor: BIOSTAR Group
    version: 1.0
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=0 uuid=00E04D50-DCEC-FFFF-FFFF-FFFFFFFFFFFF
  *-core
       description: Motherboard
       product: NF61S-M2A
       vendor: BIOSTAR Group
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (08/15/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3500+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 Processor 3500+
          slot: Socket M2
          size: 2200MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up rep_good pni cx16 lahf_lm svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: IEEE 1394 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: 8
             bus info: pci@0000:01:08.0
             version: 46
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S202H
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /cdrom
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /cdrom
                configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:e0:4d:50:dc:ec
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: ATA Disk
             product: ExcelStor Techno
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: P21O
             serial: PVE101Q394W9RB
             size: 76GiB (82GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=00041b89
           *-volume:0
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                capacity: 73GiB
                capabilities: primary bootable
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 3239MiB
                capacity: 3239MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3239MiB
                   capabilities: nofs
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-display UNCLAIMED
          description: VGA compatible controller
          product: GeForce 6100 nForce 405
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: latency=0
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:11:50:b0:df:24
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g

```

---

### Post by Pumalite on 2008-09-23
???
 *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0

 *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0

*-display UNCLAIMED
          description: VGA compatible controller
          product: GeForce 6100 nForce 405
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: latency=0


The kernel is not recognizing some or your memory and the video controller.

---

### Post by infocom on 2008-09-23
oh right. does that mean its incompatible hardware or something? would that be the motherboard, or RAM? strange how it worked before and occasioanlly hung, and the live cd works. Isnt RAM needed for those? Perhaps it half works.
thanks

---

### Post by Pumalite on 2008-09-23
It ha me puzzled too. Take a look inside. Make sure your sticks of RAM are well set.

---

### Post by infocom on 2008-09-23
they seemed slotted in securely, so removed them and put them back in and I get the same output as above.

---

### Post by Pumalite on 2008-09-23
Next culprit is your display. You might need to boot with some boot parameters. Start with the most common:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) 
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x317 vga=788 vga=789 vga=791
To be used one at the time or in different combinations

---

### Post by infocom on 2008-09-24
Hmm, I decided that might take ages for now. By display do you mean just the monitor or the graphics card too? I have swapped to another monitor to see. 

But I decided to run memtest86 on the Ubuntu CD. I am getting VAST amounts of red lines. So I suppose that means there is a problem with memory. Maybe I will try inserting different sticks, but this a brand new PC from the shop, although I did assemble it myself.

Thanks

---

### Post by infocom on 2008-09-24
SOLVED!
It was a memory issue. I ran memtest86 on both sticks separately. One just streamed red errors, the other was fine. So using just the good stick Ubuntu installed just fine.

Thanks for your help, it was indeed a memory stick issue.

---

### Post by Pumalite on 2008-09-24
I'm glad you got it running. Good luck!

---

