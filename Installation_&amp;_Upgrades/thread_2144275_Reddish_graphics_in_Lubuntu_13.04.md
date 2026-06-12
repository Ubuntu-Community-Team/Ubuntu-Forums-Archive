---
title: "Reddish graphics in Lubuntu 13.04"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by Pablo W on 2013-05-11
Dear Forum,
I have installed Lubuntu 13.04 from scratch in an old IBM Think Centre desktop PC. Everything works well, except for the graphics. All looks kind of red: video, pictures, desktop... I mean, all. I guess there is an issue with the graphics card, which was running without problems under XP.

Here are the details of my graphics card:

```
*-display               
       descripción: VGA compatible controller
       producto: 82865G Integrated Graphics Controller
       fabricante: Intel Corporation
       id físico: 2
       información del bus: pci@0000:00:02.0
       versión: 02
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm vga_controller bus_master cap_list rom
       configuración: driver=i915 latency=0
       recursos: irq:16 memoria:f0000000-f7ffffff memoria:e8000000-e807ffff ioport:1800(size=8)
```

Regarding the rest of the PC, the specifics are as follows:
```
   descripción: Equipo de escritorio
    producto: 818845S
    fabricante: IBM
    serie: L1TG1VM
    anchura: 32 bits
    capacidades: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuración: administrator_password=disabled boot=oem-specific chassis=desktop cpus=1 keyboard_password=enabled power-on_password=disabled uuid=4665212B-947B-2812-B798-27DE078FCE6A
  *-core
       descripción: Placa base
       producto: IBM
       fabricante: IBM
       id físico: 0
     *-firmware
          descripción: BIOS
          fabricante: IBM
          id físico: 0
          versión: 2AKT49ASP
          date: 03/21/2005
          tamaño: 110KiB
          capacidad: 448KiB
          capacidades: pci pnp apm upgrade shadowing escd cdboot edd acpi usb agp ls120boot smartbattery biosbootspecification
     *-cpu:0
          descripción: CPU
          producto: Intel(R) Pentium(R) 4 CPU 3.00GHz
          fabricante: Intel Corp.
          id físico: 4
          información del bus: cpu@0
          versión: 15.4.1
          serie: 0000-0F41-0000-0000-0000-0000
          ranura: WMT478/NWD
          tamaño: 3GHz
          capacidad: 3400MHz
          anchura: 32 bits
          reloj: 100MHz
          capacidades: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuración: id=0
        *-cache
             descripción: L2 caché
             id físico: 6
             ranura: L2 Cache
             tamaño: 1MiB
             capacidades: burst internal write-back
        *-logicalcpu:0
             descripción: CPU lógica
             id físico: 0.1
             anchura: 32 bits
             capacidades: logical
        *-logicalcpu:1
             descripción: CPU lógica
             id físico: 0.2
             anchura: 32 bits
             capacidades: logical
     *-memory
          descripción: Memoria de sistema
          id físico: 22
          ranura: Placa de sistema o placa base
          tamaño: 512MiB
        *-bank:0
             descripción: DIMM DDR Síncrono
             id físico: 0
             ranura: J4
             tamaño: 512MiB
             anchura: 64 bits
        *-bank:1
             descripción: DIMM DDR Síncrono [vacío]
             id físico: 1
             ranura: J5
        *-bank:2
             descripción: DIMM DDR Síncrono [vacío]
             id físico: 2
             ranura: J15
        *-bank:3
             descripción: DIMM DDR Síncrono [vacío]
             id físico: 3
             ranura: J16
     *-cpu:1
          producto: Intel(R) Pentium(R) 4 CPU 3.00GHz
          fabricante: Intel Corp.
          id físico: 1
          información del bus: cpu@1
          versión: 15.4.1
          serie: 0000-0F41-0000-0000-0000-0000
          tamaño: 3GHz
          anchura: 32 bits
          capacidades: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuración: id=0
        *-logicalcpu:0
             descripción: CPU lógica
             id físico: 0.1
             anchura: 32 bits
             capacidades: logical
        *-logicalcpu:1
             descripción: CPU lógica
             id físico: 0.2
             anchura: 32 bits
             capacidades: logical
     *-pci
          descripción: Host bridge
          producto: 82865G/PE/P DRAM Controller/Host-Hub Interface
          fabricante: Intel Corporation
          id físico: 100
          información del bus: pci@0000:00:00.0
          versión: 02
          anchura: 32 bits
          reloj: 33MHz
          configuración: driver=agpgart-intel
          recursos: irq:0 memoria:ec000000-efffffff
        *-display
             descripción: VGA compatible controller
             producto: 82865G Integrated Graphics Controller
             fabricante: Intel Corporation
             id físico: 2
             información del bus: pci@0000:00:02.0
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm vga_controller bus_master cap_list rom
             configuración: driver=i915 latency=0
             recursos: irq:16 memoria:f0000000-f7ffffff memoria:e8000000-e807ffff ioport:1800(size=8)
        *-generic NO RECLAMADO
             descripción: System peripheral
             producto: 82865G/PE/P Processor to I/O Memory Interface
             fabricante: Intel Corporation
             id físico: 6
             información del bus: pci@0000:00:06.0
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             configuración: latency=0
             recursos: memoria:fecf0000-fecf0fff
        *-usb:0
             descripción: USB controller
             producto: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             fabricante: Intel Corporation
             id físico: 1d
             información del bus: pci@0000:00:1d.0
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             capacidades: uhci bus_master
             configuración: driver=uhci_hcd latency=0
             recursos: irq:16 ioport:1820(size=32)
        *-usb:1
             descripción: USB controller
             producto: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             fabricante: Intel Corporation
             id físico: 1d.1
             información del bus: pci@0000:00:1d.1
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             capacidades: uhci bus_master
             configuración: driver=uhci_hcd latency=0
             recursos: irq:19 ioport:1840(size=32)
        *-usb:2
             descripción: USB controller
             producto: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             fabricante: Intel Corporation
             id físico: 1d.2
             información del bus: pci@0000:00:1d.2
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             capacidades: uhci bus_master
             configuración: driver=uhci_hcd latency=0
             recursos: irq:18 ioport:1860(size=32)
        *-usb:3
             descripción: USB controller
             producto: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             fabricante: Intel Corporation
             id físico: 1d.3
             información del bus: pci@0000:00:1d.3
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             capacidades: uhci bus_master
             configuración: driver=uhci_hcd latency=0
             recursos: irq:16 ioport:1880(size=32)
        *-usb:4
             descripción: USB controller
             producto: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             fabricante: Intel Corporation
             id físico: 1d.7
             información del bus: pci@0000:00:1d.7
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm debug ehci bus_master cap_list
             configuración: driver=ehci-pci latency=0
             recursos: irq:23 memoria:e8080000-e80803ff
        *-pci
             descripción: PCI bridge
             producto: 82801 PCI Bridge
             fabricante: Intel Corporation
             id físico: 1e
             información del bus: pci@0000:00:1e.0
             versión: c2
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pci normal_decode bus_master
             recursos: ioport:2000(size=4096) memoria:e8100000-e81fffff
           *-network
                descripción: Ethernet interface
                producto: 82541EI Gigabit Ethernet Controller
                fabricante: Intel Corporation
                id físico: b
                información del bus: pci@0000:03:0b.0
                nombre lógico: eth0
                versión: 00
                serie: 00:11:25:f3:71:2a
                tamaño: 100Mbit/s
                capacidad: 1Gbit/s
                anchura: 32 bits
                reloj: 66MHz
                capacidades: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuración: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=192.168.1.102 latency=52 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
                recursos: irq:16 memoria:e8100000-e811ffff ioport:2000(size=64)
        *-isa
             descripción: ISA bridge
             producto: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             fabricante: Intel Corporation
             id físico: 1f
             información del bus: pci@0000:00:1f.0
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             capacidades: isa bus_master
             configuración: driver=lpc_ich latency=0
             recursos: irq:0
        *-ide
             descripción: IDE interface
             producto: 82801EB/ER (ICH5/ICH5R) IDE Controller
             fabricante: Intel Corporation
             id físico: 1f.1
             información del bus: pci@0000:00:1f.1
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             capacidades: ide bus_master
             configuración: driver=ata_piix latency=0
             recursos: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memoria:20000000-200003ff
        *-serial NO RECLAMADO
             descripción: SMBus
             producto: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             fabricante: Intel Corporation
             id físico: 1f.3
             información del bus: pci@0000:00:1f.3
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             configuración: latency=0
             recursos: ioport:18a0(size=32)
        *-multimedia
             descripción: Multimedia audio controller
             producto: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             fabricante: Intel Corporation
             id físico: 1f.5
             información del bus: pci@0000:00:1f.5
             versión: 02
             anchura: 32 bits
             reloj: 33MHz
             capacidades: pm bus_master cap_list
             configuración: driver=snd_intel8x0 latency=0
             recursos: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memoria:e8080c00-e8080dff memoria:e8080800-e80808ff
     *-scsi:0
          id físico: 2
          nombre lógico: scsi0
          capacidades: emulated
        *-disk
             descripción: ATA Disk
             producto: ST380011A
             fabricante: Seagate
             id físico: 0.0.0
             información del bus: scsi@0:0.0.0
             nombre lógico: /dev/sda
             versión: 8.10
             serie: 4JV48QZM
             tamaño: 74GiB (80GB)
             capacidades: partitioned partitioned:dos
             configuración: ansiversion=5 sectorsize=512 signature=000d6376
           *-volume:0
                descripción: partición EXT4
                fabricante: Linux
                id físico: 1
                información del bus: scsi@0:0.0.0,1
                nombre lógico: /dev/sda1
                nombre lógico: /
                versión: 1.0
                serie: 848757f4-d07b-4069-9fa3-4f74eaf6cba5
                tamaño: 74GiB
                capacidad: 74GiB
                capacidades: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuración: created=2013-05-05 15:39:48 filesystem=ext4 lastmountpoint=/ modified=2013-05-11 14:31:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-05-11 14:31:51 state=mounted
           *-volume:1
                descripción: Extended partition
                id físico: 2
                información del bus: scsi@0:0.0.0,2
                nombre lógico: /dev/sda2
                tamaño: 501MiB
                capacidad: 501MiB
                capacidades: primary extended partitioned partitioned:extended
              *-logicalvolume
                   descripción: Linux swap / Solaris partition
                   id físico: 5
                   nombre lógico: /dev/sda5
                   capacidad: 501MiB
                   capacidades: nofs
     *-scsi:1
          id físico: 3
          nombre lógico: scsi1
          capacidades: emulated
        *-cdrom
             descripción: DVD reader
             producto: CDW/DVD TS-H492A
             fabricante: TSSTcorp
             id físico: 0.0.0
             información del bus: scsi@1:0.0.0
             nombre lógico: /dev/cdrom
             nombre lógico: /dev/cdrw
             nombre lógico: /dev/dvd
             nombre lógico: /dev/sr0
             versión: TB02
             capacidades: removable audio cd-r cd-rw dvd
             configuración: ansiversion=5 status=nodisc
     *-scsi:2
          id físico: 5
          información del bus: usb@1:8
          nombre lógico: scsi2
          capacidades: emulated scsi-host
          configuración: driver=usb-storage
        *-disk
             descripción: SCSI Disk
             producto: 2500BEV External
             fabricante: WD
             id físico: 0.0.0
             información del bus: scsi@2:0.0.0
             nombre lógico: /dev/sdb
             versión: 1.05
             serie: WD-WXE908P98594
             tamaño: 232GiB (250GB)
             capacidades: partitioned partitioned:dos
             configuración: ansiversion=4 sectorsize=512 signature=44fdfe06
           *-volume
                descripción: Windows FAT volumen
                fabricante: MSWIN4.1
                id físico: 1
                información del bus: scsi@2:0.0.0,1
                nombre lógico: /dev/sdb1
                nombre lógico: /media/cristina/My Passport
                versión: FAT32
                serie: ab3c-e9a0
                tamaño: 232GiB
                capacidad: 232GiB
                capacidades: primary fat initialized
                configuración: FATs=2 filesystem=fat label=My Passport mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-remoteaccess NO RECLAMADO
       fabricante: Intel
       id físico: 1
       capacidades: inbound
```

Any clues? Being an Ubuntu user/fan since 2008 I'm still not an expert, so please be patient on me.

As a separate issue, despite having the restricted extras option clicked during install, flash won't work on either Chrome or Firefox.

---

