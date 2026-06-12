---
title: "Cannot install 10.04 Dell Optiplex 740 Nvidia"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by likuidkewl on 2010-04-09
Searched didn't see a thread, this computer hates Linux period. The only distro I can get to work is Mint, so I think this of coarse has something to with the Nvidia chipset drivers.


Boot progress - after splash fails to symptoms.
Symptoms - Black screen with blinking cursor, hard lockup only holding power button will reboot.

Troubleshooting in progress...
nomodeset is no help and removing quiet splash doesn't give any output to the screen at all only blinking cursor.

OS: 10.04 B2

---

### Post by dino99 on 2010-04-09
i dont know what video chipset your optiplex have, but i've to say that "nomodeset" is now outdated, 

so instead use i915.modeset=0 for example if the chipset is i915

search around with the chipset's name to add above

next step is to check if a bug-report have been filled yet, if not, into console:

ubuntu-bug video and explain what happen

---

### Post by likuidkewl on 2010-04-09
I am fairly certain it is not _just_ a video problem. When I say chipset I mean the north bridge/south bridge goodness.  

If I remember correctly Debian Testing stated after starting the installation process that the CD/DVD-rom drive would disappear...

I will have to look at it again.

I understand the concept of bug reporting, but I was looking to see if anyone else had similar issues before I went that route.

And there is no access to the console at all, get a nice little blinking cursor and nothing else.  Maybe Plymouth is crapping out who knows.

---

### Post by dino99 on 2010-04-09
when you says "cannot install", in fact as i understand, lucid is installed but fail with gdm/plymouth (ie black screen)

so the way is to try to boot in recovery mode with the minimum required & tweak xxxx.modeset=0  (xxxx is the chipset's name)

Lucid, by default dont need xorg.conf, so if yours have been made by an other release, its better to rename it or delete it.
Of course, nvidia-current, nvidia-common, nvidia-settings, nvidia-current-modaliases have to be installed.

an other way, if you have Mint installed or booting from cd/dvd, is to chroot: 

here is an example

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

---

### Post by likuidkewl on 2010-04-09
I don't run from Livecd's usually I install from Alternate cds most of the time.

This time I tried to use a Server edition first as I want to run some vm's using KVM or XEN this would get to the boot menu but when install was selected would stall.

This will be a clean install when it happens.

For clarification, I cannot boot _any_ Ubuntu 10.04 options from the cd's on said box but in a VM (VirtualBox-ose) they work fine.

---

### Post by likuidkewl on 2010-04-09
Here is some more information on this system:
```

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [GeForce 6150 LE] [10de:0241] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express [14e4:167a] (rev 02)
```

lshw:
```
linux01
    description: Desktop Computer
    product: OptiPlex 740
    vendor: Dell Inc
    serial: (REMOVED)
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=44454C4C-4B00-1047-8050-B7C04F374731
  *-core
       description: Motherboard
       product: 0RY469
       vendor: Dell Inc
       physical id: 0
       version: A01
       serial: ..(REMOVED)
     *-firmware
          description: BIOS
          vendor: Dell Inc
          physical id: 1
          version: 2.0.12 (01/22/2008)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 8
          bus info: cpu@0
          version: 15.3.3
          slot: Socket M2
          size: 2800MHz
          capacity: 3GHz
          width: 64 bits
          clock: 1GHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: e
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: f
             slot: Internal Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 2e
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: HYMP112U64CP8-Y5
             vendor: AD00000000000000
             physical id: 0
             serial: 0000302A
             slot: DIMM_4
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: HYMP112U64CP8-Y5
             vendor: AD00000000000000
             physical id: 1
             serial: 0000402F
             slot: DIMM_3
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: CT25664AA667.M16FJ
             vendor: 7F7F7F7F7F9B0000
             physical id: 2
             serial: 00000000
             slot: DIMM_2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: CT25664AA667.M16FJ
             vendor: 7F7F7F7F7F9B0000
             physical id: 3
             serial: 00000000
             slot: DIMM_1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 2
          bus info: cpu@1
          version: 15.3.3
          size: 2800MHz
          capacity: 2800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:24 ioport:a000(size=4096) memory:fd800000-fd8fffff ioport:fd700000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:25 ioport:8000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-network
             description: Ethernet interface
             product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             logical name: eth0
             version: 02
             serial: 00:1e:c9:3c:22:a5
             size: 100MB/s
             capacity: 1GB/s
             width: 64 bits
             clock: 33MHz
             capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5754-v3.15 ip=192.0.100.214 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
             resources: irq:27 memory:fdef0000-fdefffff
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:26 ioport:b000(size=4096) memory:fdc00000-fdcfffff ioport:fd900000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:16 memory:fc000000-fcffffff memory:e0000000-efffffff(prefetchable) memory:fb000000-fbffffff memory:c0000000-c001ffff(prefetchable)
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e000(size=16) memory:fe02d000-fe02dfff
        *-disk
             description: ATA Disk
             product: Hitachi HDS72161
             vendor: Hitachi
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: P22O
             serial: PVFC34ZHRH1U6B
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=20000000
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 65c6d2d6-7798-4794-bd82-a0126a595a39
                size: 142GiB
                capacity: 142GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2010-03-30 11:29:03 filesystem=ext4 lastmountpoint=/&#65533;+&#65533;&#65533;"&#65533;&#65533;&#65533;i&#65533;&#65533;)&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Y&#65533;&#65533;0&#65533;&#65533;0&#65533;&#65533;"&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;"&#65533;&#65533;&#65533;4&&#65533; modified=2010-03-30 11:41:08 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-04-09 12:41:07 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 6236MiB
                capacity: 6236MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 6236MiB
                   capabilities: nofs
        *-cdrom
             description: DVD reader
             product: CDRW/DVD GCCT10N
             vendor: HL-DT-ST
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /media/cdrom0
             version: A100
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/cdrom0
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:cc00(size=16) memory:fe02c000-fe02cfff
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
          resources: ioport:9000(size=4096) memory:fdb00000-fdbfffff memory:fda00000-fdafffff(prefetchable)
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:fe024000-fe027fff
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

---

