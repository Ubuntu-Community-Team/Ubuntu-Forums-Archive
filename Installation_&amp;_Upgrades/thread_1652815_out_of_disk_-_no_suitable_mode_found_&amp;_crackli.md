---
title: "out of disk - no suitable mode found &amp; crackling audio"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by Infrid on 2010-12-25
hi,
I have just installed xubuntu 10.10 on a old pc, and i get some strange problem after the installation.

the first time, after the computer boot I got a nice "grub rescue" prompt. I have tried to reinstall grub using the live cd (mountin and chroot) and even erase the mbr with DD

the disk was not in good shape anyway so and I changed it.

Width the new disk I installed a new system, but this time, after the boot I get

```
out of disk
no suitable mode found
```after that I get the login screen and a I can use the computer.

I’m beginning to get worried, why I get *out of disk*? I'm going to install windows xp for a few essential tools but I can't do this until this problem is solved... 

is the* suitable mode* error related to the screen resolution of grub at startup?

here the output of *lshw *and *fdisk -l*

```
                                                                     
occhietto
    description: Desktop Computer
    product: 00000000000000000000000
    vendor: Packard Bell NEC
    version: P851003506
    serial: 200201010000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=C4B58CCD-BECF-D711-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-6786
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: V1.0 (06/26/2003)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 2GHz
          capacity: 4GHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:c0000000-cfffffff
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
             resources: memory:d2000000-d4ffffff memory:d0000000-d1ffffff
           *-display
                description: VGA compatible controller
                product: MGA G400/G450
                vendor: Matrox Graphics, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
                configuration: driver=matrox_w1 latency=32 maxlatency=32 mingnt=16
                resources: irq:16 memory:d0000000-d1ffffff memory:d2000000-d2003fff memory:d3000000-d37fffff memory:d2010000-d201ffff
        *-multimedia:0
             description: Multimedia audio controller
             product: ES1371 [AudioPCI-97]
             vendor: Ensoniq
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ENS1371 latency=32 maxlatency=128 mingnt=12
             resources: irq:17 ioport:d000(size=64)
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d400(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:dc00(size=32)
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:d5000000-d50000ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e000(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG SP0802N
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: TK20
                serial: S00JJ40XB42388
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0001158a
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: 5fb00015-d004-4344-9121-0ae09d51bc89
                   size: 94MiB
                   capacity: 94MiB
                   capabilities: primary bootable journaled extended_attributes recover ext3 ext2 initialized
                   configuration: created=2010-12-24 15:44:48 filesystem=ext3 modified=2010-12-25 15:42:46 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,commit=5,barrier=0,data=ordered mounted=2010-12-25 15:42:46 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1952MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 62GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=5,barrier=0,data=ordered state=mounted
                 *-logicalvolume:2
                      description: HPFS/NTFS partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 10000MiB
           *-cdrom:0
                description: DVD reader
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio dvd
                configuration: status=nodisc
           *-cdrom:1
                description: DVD-RAM writer
                product: DVDRAM GSA-4167B
                vendor: HL-DT-ST
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: DL11
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-multimedia:1
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: irq:22 ioport:e400(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: irq:22 ioport:e800(size=256)
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: 00:0c:76:37:ab:6f
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.105 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:23 ioport:ec00(size=256) memory:d5001000-d50010ff

```sorry is in Italian, I'm going to translate it
```
Disco /dev/sda: 80.1 GB, 80060424192 byte
255 testine, 63 settori/tracce, 9733 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x0001158a

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
La partizione 1 non termina al limite del cilindro.
/dev/sda2              13        9734    78085121    5  Esteso
/dev/sda5              13         262     1998848   82  Linux swap / Solaris
/dev/sda6             262        8459    65844224   83  Linux
/dev/sda7            8459        9734    10240000    7  HPFS/NTFS

```in english

```

Disk /dev/sda: 80.1 GB, 80060424192 byte
255 heads, 63 sectors, 9733 cylinders
Unit = cylinders of 16065 * 512 = 8225280 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
disk ID: 0x0001158a

Device    Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
The partition 1 doesn't end at the cylinder's limit
/dev/sda2              13        9734    78085121    5  Extended
/dev/sda5              13         262     1998848   82  Linux swap / Solaris
/dev/sda6             262        8459    65844224   83  Linux
/dev/sda7            8459        9734    10240000    7  HPFS/NTFS

```The other big problem is related to the audio, it's just crackling when i play a video and I seek the file. When I get some audio notification from emesene the audio is crackling too. The music plying is disturbed, I can't get a clean listening. I have tried to drop audio volume but nothing changed so much.

I hope you will help me

Many thanks 
Infrid

:)

---

### Post by Infrid on 2010-12-27
any idea?

---

### Post by Infrid on 2010-12-28
audio fixed, was a mixer problem.

---

