---
title: "Black screen while installing Ubuntu 12.04"
date: 2013-09-24
forum: Installation &amp; Upgrades
---

### Post by cyrilm2 on 2013-09-24
Hello,
I'm currently trying to reinstall ubuntu 12.04 LTS but as soon as i select the " Install ubuntu " line  i got a black screen.

There are actually 3 OS on this computer : Debian 6.0.0.7 (starting and working fine), Windows 7 (starting and working fine), and Ubuntu 12.04 ( not starting so i want to reinstall it)
It's a pretty recent computer ( a few month old)

Here is what i did to work around the problem :


[LIST]
[*]Change monitor
[*]boot for CD
[*]Boot from USB
[LIST]
[*]ubuntu-12.04.3-desktop-amd64.iso
[*]ubuntu-12.04.3-alternate-amd64.iso
[/LIST]

[*]Setting [FONT=Ubuntu Mono]option [/FONT]
[LIST]
[*][FONT=Ubuntu Mono]&#8203;[/FONT][FONT=Ubuntu Mono]"nomodset"[/FONT]
[*][FONT=Ubuntu Mono]"acpi = off " and "[/FONT][FONT=Ubuntu Mono]nolapic"[/FONT]
[*][FONT=Ubuntu Mono]"acpi = off " and  "[/FONT][FONT=Ubuntu Mono]nolapic" and "[/FONT][FONT=Ubuntu Mono]nomodset"[/FONT]
[/LIST]
[/LIST]
[FONT=Ubuntu Mono]
[/FONT]Thanks in advance

---

### Post by mörgæs on 2013-09-24
HI, welcome to the fora.

Please begin with a complete hardware description.

---

### Post by cyrilm2 on 2013-09-25
Hello,
Thanks,

The result of "lshw -html" is to big for the upload manager so i put it here :


[http://pastebin.ca/2458079](http://pastebin.ca/2458079)

---

### Post by mörgæs on 2013-09-25
Sorry, it's almost impossible to read.

Please post the result of lshw (as plain text, no HTML) here in CODE tags.

---

### Post by cyrilm2 on 2013-09-25
Here is it:
```

MyComputer
    description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: B75 Pro3-M
       vendor: ASRock
       physical id: 0
       serial: M80-2C007800221
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.60 (12/11/2012)
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cache:0
          description: L2 cache
          physical id: a
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-through unified
     *-cache:1
          description: L1 cache
          physical id: b
          slot: CPU Internal L1
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-through data
     *-cache:2
          description: L3 cache
          physical id: c
          slot: CPU Internal L3
          size: 6MiB
          capacity: 6MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [Empty]
             slot: ChannelA-DIMM0
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-8GBXL
             vendor: 04CD
             physical id: 3
             serial: 00000000
             slot: ChannelB-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3570 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: e
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3570 CPU @ 3.40GHz
          slot: CPUSocket
          size: 1600MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx f16c rdrand lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e8000000(size=167772160)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: latency=0
                resources: memory:f6000000-f6ffffff memory:e8000000-efffffff(prefetchable) memory:f0000000-f1ffffff(prefetchable) ioport:e000(size=128) memory:f7000000-f707ffff(prefetchable)
           *-multimedia UNCLAIMED
                description: Audio device
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f7080000-f7083fff
        *-usb:0
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:16 memory:f7200000-f720ffff
        *-communication UNCLAIMED
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f721b000-f721b00f
        *-usb:1
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f7218000-f72183ff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f7210000-f7213fff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:d000(size=4096) memory:f7100000-f71fffff
           *-storage
                description: SATA controller
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: scsi6
                logical name: scsi7
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list emulated
                configuration: driver=ahci latency=0
                resources: irq:30 ioport:d050(size=8) ioport:d040(size=4) ioport:d030(size=8) ioport:d020(size=4) ioport:d000(size=32) memory:f7100000-f71001ff
              *-disk
                   description: ATA Disk
                   product: ST1000DM003-1CH1
                   vendor: Seagate
                   physical id: 0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/sda
                   version: CC47
                   serial: Z1D4XR8M
                   size: 931GiB (1TB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=b3d6143d
                 *-volume:0
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: scsi@6:0.0.0,1
                      logical name: /dev/sda1
                      version: 3.1
                      serial: 0a41-ad00
                      size: 98MiB
                      capacity: 100MiB
                      capabilities: primary bootable ntfs initialized
                      configuration: clustersize=4096 created=2012-12-11 01:05:40 filesystem=ntfs label=Réservé au système state=clean
                 *-volume:1
                      description: Windows NTFS volume
                      physical id: 2
                      bus info: scsi@6:0.0.0,2
                      logical name: /dev/sda2
                      version: 3.1
                      serial: 08e77fc9-5266-3243-b44e-576c1f93de22
                      size: 245GiB
                      capacity: 245GiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=4096 created=2012-12-11 01:05:59 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
                 *-volume:2
                      description: EXT4 volume
                      vendor: Linux
                      physical id: 3
                      bus info: scsi@6:0.0.0,3
                      logical name: /dev/sda3
                      version: 1.0
                      serial: bdb7d699-7031-4f23-b1e7-4ebda8faaafd
                      size: 184GiB
                      capacity: 184GiB
                      capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                      configuration: created=2013-07-11 14:04:09 filesystem=ext4 lastmountpoint=/edia/bdb7d699-7031-4f23-b1e7-4ebda8faaafd modified=2013-09-24 11:20:58 mounted=2013-09-24 11:02:56 state=clean
                 *-volume:3
                      description: Extended partition
                      physical id: 4
                      bus info: scsi@6:0.0.0,4
                      logical name: /dev/sda4
                      size: 501GiB
                      capacity: 501GiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume:0
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/sda5
                         capacity: 14GiB
                         capabilities: nofs
                    *-logicalvolume:1
                         description: Linux filesystem partition
                         physical id: 6
                         logical name: /dev/sda6
                         logical name: /data
                         capacity: 186GiB
                         configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                    *-logicalvolume:2
                         description: Linux filesystem partition
                         physical id: 7
                         logical name: /dev/sda7
                         logical name: /
                         capacity: 300GiB
                         configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
              *-cdrom
                   description: DVD-RAM writer
                   product: DVDRAM GH24NS95
                   vendor: HL-DT-ST
                   physical id: 1
                   bus info: scsi@7:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: RN01
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=nodisc
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:c000(size=4096) ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 06
                serial: bc:5f:f4:90:1a:d0
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.36 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:28 ioport:c000(size=256) memory:f2104000-f2104fff(prefetchable) memory:f2100000-f2103fff(prefetchable)
        *-usb:2
             description: USB Controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7217000-f72173ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7216000-f72167ff
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7215000-f72150ff ioport:f000(size=32)

```

---

### Post by alec3 on 2013-09-25
I am having this problem as well with (only) debian 7.1 xfce installed

---

### Post by mörgæs on 2013-09-25
Which graphics card do you use? 
How does it work in a live boot of 13.10 (beta)?

---

### Post by irlanco on 2013-09-25
I have the same problem as the topic creator. I have a NVIDIA GTX780 and a UEFI motherboard. I'm a attempting to run ubuntu from a cd before I install it. I just get a black screen when I try to run Ubuntu. Any help would be appreciated.

---

### Post by cyrilm2 on 2013-09-25
It's a GT610 sl 1G d3 L
I didn't try with 13.10 because i do need 12.04 and because it worked once

---

### Post by mörgæs on 2013-09-26
Ok, you have made up your mind. This is for others who might read the thread: 

Expecting that a (relatively) old version of Buntu to work on the latest hardware is not realistic. Hardware support is improving in 13.04 and 13.10, and first step in troubleshooting should be trying the latest release(s).

---

### Post by cyrilm2 on 2013-09-26
Well we do use ubuntu 12.04 LTS to have this support, i do not understand how a beta version (13.10) can be more efficient than a LTS one's

I could try without my graphic card but it's more a workaround than a real solution.

---

### Post by cyrilm2 on 2013-09-27
I've just try without my graphic card and it didn't change anything.
(ubuntu 12.04 desktop = nothing, alernate = the first screen only)

---

### Post by chrisb009 on 2014-01-02
I'm having the same issue - black screen after selecting install Ubuntu. Not sure why an LTS release would be so difficult to install on older hardware. I have played around with mouse/keyboard combinations and it seems to install after playing for hours only to fail again during a re-installation. I have tested the entire system - no issues with RAM/Video/HD's/MB.

---

### Post by mörgæs on 2014-01-03
You are posting in a thread in which people are encouraged to a) try the latest release and b) provide a complete hardware description as seen with lshw, and in first post a selection of c) boot options were mentioned. 

Before posting please try these suggestions.

---

