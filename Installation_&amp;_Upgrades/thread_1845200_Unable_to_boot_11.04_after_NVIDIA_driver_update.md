---
title: "Unable to boot 11.04 after NVIDIA driver update"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by beithon on 2011-09-16
When I boot I get a purple screen, with nothing appearing on it. If I do a hard shut down, it will work. I've tried starting GRUB, but no dice. Also, my external VGA is no longer recognized. Any idea what's going on? I've tried both sets of possible NVIDIA drivers, but neither seems to make a difference. I'm currently on version 173. I'm running this on a Lenovo T61. Help please!!

Thank you !

---

### Post by Hakunka-Matata on 2011-09-16
> **beithon said:**
> When I boot I get a purple screen, with nothing appearing on it. If I do a hard shut down, it will work. [COLOR=Red]I've tried starting GRUB[/COLOR], but no dice. Also, my external VGA is no longer recognized. Any idea what's going on? I've tried both sets of possible NVIDIA drivers, but neither seems to make a difference. I'm currently on version 173. I'm running this on a Lenovo T61. Help please!!

Thank you !


Welcome to the forums;


[LIST]
[*] What Release Ubuntu are you using now?
[LIST]
[*].
[/LIST]
 
[*][COLOR=Red]starting grub?[/COLOR]
[LIST]
[*][COLOR=Red].[/COLOR]
[/LIST]
 
[*][COLOR=Black]please post output of:[/COLOR]
[/LIST]
```
uname -a
sudo fdisk -lu
sudo lshw >t61hw
gedit t61hw
```
[LIST]
[*]# open and copy entire text of T61-Len.txt,
[*]# paste into new reply inside code tags #icon,
[*]```
 
```
[/LIST]

---

### Post by beithon on 2011-09-16
I'm running 11.04. This is what I got for an output with those commands:
andrea@kavula:~$uname-a
Linux kavula 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux
andrea@kavula:~$ sudo fdisk -lu
[sudo] password for andrea: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070661

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2          501758   234440703   116969473    5  Extended
/dev/sda5          501760   234440703   116969472   83  Linux

Disk /dev/dm-0: 119.8 GB, 119775686656 bytes
255 heads, 63 sectors/track, 14561 cylinders, total 233936888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 114.9 GB, 114861015040 bytes
255 heads, 63 sectors/track, 13964 cylinders, total 224337920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table
#icon
Disk /dev/dm-2: 4911 MB, 4911529984 bytes
255 heads, 63 sectors/track, 597 cylinders, total 9592832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

avula
    description: Notebook
    version: ThinkPad T61
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 family=ThinkPad T61 frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=B258C601-49BD-11CB-B680-B509E400C54A
  *-core
       description: Motherboard
       product: 6459CTO
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: VF1Z489F1JP
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 7LETC4WW (2.24 )
          date: 08/15/2008
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          slot: None
          size: 2101MHz
          capacity: 2101MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: burst internal write-back unified
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
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          size: 2101MHz
          capacity: 2101MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:d4000000-d6ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G84M [Quadro NVS 140M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:d6000000-d6ffffff memory:e0000000-efffffff memory:d4000000-d5ffffff ioport:2000(size=128)
        *-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:21:86:94:ce:cb
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:46 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1860(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1880(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fe226c00-fe226fff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:49 memory:fe220000-fe223fff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:fc000000-fdffffff ioport:f8000000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:dc100000-df2fffff ioport:dfd00000(size=1048576)
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 61
                serial: 00:21:5c:88:4e:c5
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic firmware=228.61.2.24 ip=10.0.0.229 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:48 memory:df2fe000-df2fffff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:d8000000-d9ffffff ioport:dfa00000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:6000(size=4096) memory:d0000000-d1ffffff ioport:df700000(size=1048576)
        *-pci:5
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:7000(size=4096) memory:cc000000-cdffffff ioport:df400000(size=1048576)
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18a0(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:18c0(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18e0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:fe227000-fe2273ff
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:8000(size=16384) memory:f8100000-fbffffff ioport:f4000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:15:00.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b01716150-b0171614f irq:16 memory:f8100000-f8100fff ioport:8000(size=256) ioport:8400(size=256) memory:f4000000-f7ffffff memory:80000000-83ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:15:00.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:17 memory:f8101000-f81017ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:15:00.2
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:f8101800-f81018ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:15:00.4
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: memory:f8102000-f81020ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 0.5
                bus info: pci@0000:15:00.5
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:18 memory:f8102400-f81024ff
        *-isa
             description: ISA bridge
             product: 82801HBM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1830(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-U10N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:47 ioport:1c48(size=8) ioport:1c1c(size=4) ioport:1c40(size=8) ioport:1c18(size=4) ioport:1c20(size=32) memory:fe226000-fe2267ff
           *-disk
                description: ATA Disk
                product: HITACHI HTS54251
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: BB2Z
                serial: 080430BB6202WBE1X9LG
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00070661
              *-volume:0
                   description: Linux filesystem partition
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: a3eeb0ad-201c-4004-a4a4-60af7bace468
                   size: 243MiB
                   capacity: 243MiB
                   capabilities: primary bootable ext2 initialized
                   configuration: filesystem=ext2 modified=2011-09-16 12:30:29 mount.fstype=ext2 mount.options=rw,relatime,errors=continue mounted=2011-08-23 09:11:23 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 111GiB
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe227400-fe2274ff ioport:1c60(size=32)
  *-battery
       product: 92P1133
       vendor: Panasonic
       physical id: 1
       slot: Rear
       capacity: 84240mWh
       configuration: voltage=10.8V
#icon

---

### Post by Hakunka-Matata on 2011-09-16
> Disk /dev/dm-0: 119.8 GB, 119775686656 bytes
255 heads, 63 sectors/track, 14561 cylinders, total 233936888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 114.9 GB, 114861015040 bytes
255 heads, 63 sectors/track, 13964 cylinders, total 224337920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table
#icon
Disk /dev/dm-2: 4911 MB, 4911529984 bytes
255 heads, 63 sectors/track, 597 cylinders, total 9592832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
you have multiple disks on the machine (Disk /dev/dm-0, 1, & 2)  

post output of 
```
dmraid -r
```please

you may have to install dmraid - **sudo apt-get install dmraid**

---

### Post by beithon on 2011-09-16
This is what I got:

andrea@kavula:~$ sudo dmraid -r
no raid disks

---

### Post by beithon on 2011-09-16
Additional info: It seems I can surpass the purple screen by pushing Ctrl+Alt+F6 then Ctrl+Alt+F7. This doesn't really solve the problem. Still having external monitor issues. I've tried reverting drivers, etc. That seems to only exacerbate the problem. I'm now running nvidia 270 driver.

---

### Post by Hakunka-Matata on 2011-09-16
Is this a dual boot machine?, I see only linux partitions on sda?
Maybe a dumb question, but have you run the update manager recently?

---

### Post by MAFoElffen on 2011-09-16
> **beithon said:**
> Additional info: It seems I can surpass the purple screen by pushing Ctrl+Alt+F6 then Ctrl+Alt+F7. This doesn't really solve the problem. Still having external monitor issues. I've tried reverting drivers, etc. That seems to only exacerbate the problem. I'm now running nvidia 270 driver.
<<When posting logs and output, please press the "#" button in the posting tool bar to insert CODE TAGS, which will organise the selected "text" within a text box.>>

So you can probably get to tty1 thru tty6 using hotkeys-- but your X-Session is not booting.

What is your specific video card? The output of thids will show that:
```

lspci -v  | grep VGA

```Then post the /var/log/xorg.0.log.  That will show us what module the video driver is erring out on in the Xorg init.

Next post this file if present:/var/log/nvidia-installer.log  --  That log is generated in an NVidia driver install (of Nvidia's driver) and has additional info on if the driver was compiled correctly during the install for what kernel... and if the linux header files where present during the compile. (common error in the last 4 motnhs.)

Problem seems to be with the Xorg video driver files, but the above should narrow down what is going on with them.

Other info and refence in this sticky:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Get that part of it working first!  The external monitor we can work on after that-- through the xorg.conf.

---

