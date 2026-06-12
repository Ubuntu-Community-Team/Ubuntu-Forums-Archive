---
title: "Can't stop gnome-system-monitor"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by olipoh1 on 2010-09-26
Hi everybody (and sorry for my english),

since a few days (maybe one week and after an automatic upgrade), I could see a strange behavior of gnome-system-monitor.

After a boot, everything is normal. But if I log-out, and then log-in again, the problem begins. Impossible to close the gnome-system-monitor window (by clicking on the window upper-right close button). I have to terminate the process. And this process takes about 50% of CPU. In the same time, a dbus-deamon process takes the other 50%. When I terminate gnome-system-monitor process, the CPU use drops down to 6%.

I use ubuntu 10.04 64 bits.

Any idea ?
Thanks a lot.

---

### Post by sikander3786 on 2010-09-26
> 
But if I log-out, and then log-in again, the problem begins. Impossible to close the gnome-system-monitor window (by clicking on the window upper-right close button).

Hi and welcome to the forums. :-)

What do you mean by that statement? Does gnome-system-monitor start automatically after you login? Or you start it to see which program is eating up the processor and then you are unable to close it?

gnome-system-monitor uses a lot of resources to display the system status so in some cases it might eat up some processor power. What are your system specs?

---

### Post by olipoh1 on 2010-09-26
Does gnome-system-monitor start automatically after I login? No.
Or I start it to see which program is eating up the processor and then I'm unable to close it? Yes but only when I login after I logged out, with dbus-deamon eating the processor to.

lshw (is that what you wanted to see ?) :

```
 *-core
       description: Motherboard
       product: P5B
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0701 (10/02/2006)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) D CPU 2.80GHz
          serial: To Be Filled By O.E.M.
          slot: Socket 775
          size: 2400MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back
     *-memory
          description: System Memory
          physical id: 40
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 667 MHz (1.5 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:9000(size=4096) memory:fa800000-fe8fffff ioport:bfe00000(size=536870912)
           *-display
                description: VGA compatible controller
                product: G73 [GeForce 7600 GT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:c0000000-cfffffff(prefetchable) memory:fc000000-fcffffff ioport:9c00(size=128) memory:fe8e0000-fe8fffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:dc00(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:e000(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:febffc00-febfffff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:febf8000-febfbfff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:1000(size=4096) memory:80000000-803fffff ioport:dfe00000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:b000(size=4096) memory:fea00000-feafffff memory:80400000-805fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 00:18:f3:08:8f:bf
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:28 ioport:b800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:a000(size=4096) memory:fe900000-fe9fffff memory:80600000-807fffff(prefetchable)
           *-storage
                description: SATA controller
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:16 memory:fe9fe000-fe9fffff memory:fe9e0000-fe9effff(prefetchable)
           *-ide
                description: IDE interface
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                logical name: scsi4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0
                resources: irq:17 ioport:ac00(size=8) ioport:a880(size=4) ioport:a800(size=8) ioport:a480(size=4) ioport:a400(size=16)
              *-cdrom:0
                   description: CD-R/CD-RW writer
                   physical id: 0.0.0
                   bus info: scsi@4:0.0.0
                   logical name: /dev/cdrom2
                   logical name: /dev/cdrw2
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   capabilities: audio cd-r cd-rw
                   configuration: status=nodisc
              *-cdrom:1
                   description: DVD reader
                   product: DVD-ROM SD-M1712
                   vendor: TOSHIBA
                   physical id: 0.1.0
                   bus info: scsi@4:0.1.0
                   logical name: /dev/cdrom
                   logical name: /dev/dvd
                   logical name: /dev/scd1
                   logical name: /dev/sr1
                   version: 1004
                   capabilities: removable audio dvd
                   configuration: ansiversion=5 status=ready
                 *-medium
                      physical id: 0
                      logical name: /dev/cdrom
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d480(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d800(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d880(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:febff800-febffbff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
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
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) ioport:e080(size=16)
           *-disk:0
                description: ATA Disk
                product: Hitachi HDP72505
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: GM4O
                serial: GEC534RF2MD75E
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f51200c7
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/Data-1
                   logical name: /export/Musique
                   logical name: /export/Vidéos
                   version: 1.0
                   serial: 52b38472-a319-4576-9644-04a9181532ad
                   size: 465GiB
                   capacity: 465GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-02-26 09:02:54 filesystem=ext4 label=Data-1 lastmountpoint=/media/Data-18=&#65533;C&#65533;&#65533;&#65533;3i&#65533;0(=&#65533;C&#65533;&#65533;&#65533;O`!&#65533;&#65533;&#65533;@"&#65533;9&#65533;&#65533;&#65533;&#65533;W,&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-09-26 20:52:54 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noexec,relatime,barrier=1,data=ordered mounted=2010-09-26 20:52:54 state=mounted
           *-disk:1
                description: ATA Disk
                product: Hitachi HDP72505
                vendor: Hitachi
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: GM4O
                serial: GEC534RJ104UHE
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8d43cef3
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media/Data-2
                   version: 1.0
                   serial: 4f71a875-f37a-47b0-a591-811335e8d25f
                   size: 364GiB
                   capacity: 364GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-02-26 18:22:47 filesystem=ext4 label=Data-2 lastmountpoint=/media/Data-28&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;6&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;@.&#65533;,&#65533;&#65533;&#65533;&#65533;&#65533; modified=2010-09-26 20:52:54 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noexec,relatime,barrier=1,data=ordered mounted=2010-09-26 20:52:54 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sdb3
                   size: 100GiB
                   capacity: 100GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      logical name: /
                      logical name: /export/home
                      capacity: 96GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sdb6
                      capacity: 4251MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:80800000-808000ff ioport:400(size=32)
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=16) ioport:c800(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG SP2504C
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdc
                version: VT10
                serial: S09QJ1HLC30359
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=61a161a1
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdc1
                   logical name: /media/Data-3
                   version: 1.0
                   serial: beb51717-b955-4c53-99f4-ec64951284ff
                   size: 232GiB
                   capacity: 232GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-02-26 20:10:30 filesystem=ext4 label=Data-3 modified=2010-09-26 20:52:54 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noexec,relatime,barrier=1,data=ordered mounted=2010-09-26 20:52:54 state=mounted

```

thank you anyway for your help.

---

### Post by sikander3786 on 2010-09-26
Processor, RAM or Graphics bottlenecks shouldn't be a problem with your specs.

That dbus-daemon can cause problems due to Samba. Do you use Samba? If not, you can remove it and see if it helps.

---

### Post by olipoh1 on 2010-09-27
Thank you again for your help.

I uninstalled samba, and nothing changed. But something is strange. In gnome-system-monitor, gnome-system-monitor itself appears as a running process (42% CPU), and dbus-deamon is "sleeping" (48% !!!!).

I tried to launch gnome-system-monitor as root (sudo gnome-system-monitor in a terminal), and it works fine. Dbus-deamon eats 0% and I can close the monitor. I tried to login as another user. Same problem. Only root works fine.

And when I launch gnome-system-monitor in a terminal, There is this message : ** (gnome-system-monitor:14174): WARNING **: SELinux was found but is not enabled.

Where to look now ?

---

### Post by olipoh1 on 2010-09-27
any idea ?

---

