---
title: "LL install problem"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by Rotler on 2011-04-12
Hi, all. I'm hoping that someone can help me with Ubuntu LL  install.  The problem appears to be the hard disk, since it's  not letting me wipe in terminal.

Using a Live CD for desktop after getting the "installation unrecoverable error. now launch desktop session" error.

Then in terminal, tried:
ubuntu@ubuntu:~$ dd if=/dev/zero of=/dev/hda bs=1M
dd: opening `/dev/hda': Permission denied
ubuntu@ubuntu:~$ 

Any thoughts?
Rotler

---

### Post by Dutch70 on 2011-04-12
Hi and welcome to UF

Try putting "sudo" in front of the command...
```
sudo dd if=/dev/zero of=/dev/hda bs=1M
```

What is Ubuntu LL?

.

---

### Post by Rotler on 2011-04-12
tried that, it let me wipe, but still can't install. any ideas?

---

### Post by Dutch70 on 2011-04-12
Yes, boot up a live cd/usb and click Try Ubuntu, or Ubuntu LL whatever that is.

On second thoughts, read this...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by Rotler on 2011-04-13
Hi, sorry, should have written Lucid Linux (instead of just LL).

I am booting from the Live CD! On other computers, I have had the option to try ubuntu or install, but on this set of hardware, I don't even get the option. After the five dots (alternating white and purple), the purple desktop background loads and I get the "unrecoverable error" etc. message.

Hardware info:
    description: Desktop Computer
    product: 8I945GZME-RH
    vendor: iQon.ie
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-0016E66ED7C3
  *-core
       description: Motherboard
       product: 8I945GZME-RH
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F7 IQ (01/04/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          slot: Socket 775
          size: 2400MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capabilities: synchronous internal write-back
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
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
        *-bank:2
             description: DIMM 533 MHz (1.9 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.4
          serial: 0000-0F64-0000-0000-0000-0000
          size: 2400MHz
          capacity: 2400MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:e5000000-e5003fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:1000(size=4096) memory:e0000000-e2ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G72 [GeForce 7300 LE]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:e0000000-e0ffffff memory:d0000000-dfffffff(prefetchable) memory:e1000000-e1ffffff memory:e2000000-e201ffff(prefetchable)
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:bc00(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b000(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:b400(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:b800(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e5004000-e50043ff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:a000(size=4096) memory:e3000000-e4ffffff memory:40000000-400fffff(prefetchable)
           *-network
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 13
                serial: 00:16:e6:6e:d7:c3
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.70 latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
                resources: irq:21 memory:e4000000-e4003fff ioport:a000(size=256) memory:40000000-4001ffff(prefetchable)
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
        *-ide
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD400BD-75JM
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAMA2575129
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0007fbb9
              *-volume
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1610MiB
                   capacity: 1610MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1610MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: SPD2412T
                vendor: PHILIPS
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: P1.3
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
     *-scsi
          physical id: 2
          bus info: usb@1:4
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde

---

### Post by Dutch70 on 2011-04-14
I really don't know,  you may want to try the minimal or alternate cd install, or possibly try Xubuntu or Lubuntu.

Best regards

---

