---
title: "Nouveau or ubiquity problem on my machine (ubuntu alpha3"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ankspo71 on 2010-02-28
Hi,

I finally managed to get alpha 3 installed on my computer, but to do that I had to perform the upgrade (update-manager -d) over my 9.10 installation. I couldn't use a free partition like I was hoping.

The problem is, the live cd will only get as far as the cd's boot menu, and when I select either install or live cd, something shuts off my monitor and the power button blinks (no output to monitor I think). I tried this several times without setting special boot options, and several times with random boot options but I still can't get it too keep power to my monitor. Being that I have no display and the live cd is session only I have no log files or error messages to look at. If it is not the Nouveau drivers, then it might be ubiquity or xorg crashing my display.

It is not a problem with my monitor, because I am running Lucid alpha3 as we speak. Also, virtualbox has no problem running the iso image of Lucid-alpha3. I md5'ed the iso and it checks out fine. The problem is only booting the cd from my PC.

Does anybody know of a command or boot option to bypass the new Nouveau drivers, and let me use the earlier open source nvidia drivers?

(Nvidia 8400 GS)
Here's my other hardware:
```
james@James-Karmic:~$ sudo lshw
[sudo] password for james: 
james-karmic              
    description: Desktop Computer
    product: P4M90-M4
    vendor: BIOSTAR Group
    version: Ver:1.0
    serial: OEM
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00000000-0000-0000-3412-000078563412
  *-core
       description: Motherboard
       product: P4M90-M4
       vendor: BIOSTAR Group
       physical id: 0
       version: Ver:1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (12/12/2008)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 4GHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2
             physical id: 0
             slot: A0
             size: 2GiB
        *-bank:1
             description: DIMM DDR2 [empty]
             physical id: 1
             slot: A1
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:d8000000-dfffffff(prefetchable)
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
             resources: ioport:c000(size=4096) memory:fdc00000-fdcfffff memory:fdb00000-fdbfffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:b000(size=4096) memory:f8000000-fbffffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G98 [GeForce 8400 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:24 memory:fa000000-faffffff memory:c0000000-cfffffff(prefetchable) memory:f8000000-f9ffffff ioport:bc00(size=128) memory:fb000000-fb01ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:a000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
        *-ide:0
             description: IDE interface
             product: VIA Technologies, Inc.
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:21 ioport:fc00(size=8) ioport:f800(size=4) ioport:f400(size=8) ioport:f000(size=4) ioport:ec00(size=16) ioport:e800(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             logical name: scsi1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:e400(size=16)
           *-disk:0
                description: ATA Disk
                product: ST380215A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 9RXAWEV9
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009aa36
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: e40bc4f0-abe0-40c5-9459-7f7a76249837
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-02-25 15:02:07 filesystem=ext4 lastmountpoint=/&#65533;&#65533;8C&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;1&#65533;&#65533;x]&#65533;\&#65533;p&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;]&#65533;]&#65533;e^&#65533;&#65533;&#65533;p&#65533;%&#65533;&#65533;v modified=2010-02-25 15:19:15 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-02-27 23:47:10 state=mounted
           *-disk:1
                description: ATA Disk
                product: ST3120213A
                vendor: Seagate
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: 2AAA
                serial: 5LS24VQ3
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000e2393
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 1
                   serial: 7e1ae295-8f14-463c-8fc0-7aa9649a98ee
                   size: 4000MiB
                   capacity: 4000MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   logical name: /media/sdb2
                   version: 1.0
                   serial: fa6ea57d-1a87-4894-bc27-8a255b58a416
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-02-10 03:15:29 filesystem=ext4 lastmountpoint=/media/sdb2&#65533;&#65533;Àr&#65533;&#65533;HwB&#65533;[&#65533;&#65533;&#65533;&#65533;\&#65533;(B&#65533;(B&#65533;r&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;e^&#65533; modified=2010-02-27 23:47:11 mount.fstype=ext4 mount.options=rw,nosuid,nodev,noexec,relatime,barrier=1,data=ordered mounted=2010-02-27 23:47:11 state=mounted
           *-cdrom
                description: DVD-RAM writer
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:20 ioport:e000(size=32)
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:22 ioport:dc00(size=32)
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d800(size=32)
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:23 ioport:d400(size=32)
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:21 memory:fdfff000-fdfff0ff
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:e0:4d:bd:db:9f
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.2 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: irq:23 ioport:d000(size=256) memory:fdffe000-fdffe0ff
        *-pci:3
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:8
          description: Host bridge
          product: VT8237A Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 108
          bus info: pci@0000:00:13.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:bfffc000-bfffffff
james@James-Karmic:~$ 
```Thanks,

---

### Post by gnomeuser on 2010-02-28
This does sound like an issue that nouveau could cause. Can I ask you to report a bug "ubuntu-bug xserver-xorg-video-nouveau" should take care of collecting the information needed.

As for switching back to nv, you could simply remove the nouveau package I believe or you could add your own /etc/X11/xorg.conf file to enable the nv driver. 

Regardless this should work, let's fix it.

---

### Post by ankspo71 on 2010-02-28
> **gnomeuser said:**
> Can I ask you to report a bug "ubuntu-bug xserver-xorg-video-nouveau" should take care of collecting the information needed.
Regardless this should work, let's fix it.

Sure thing, I'll work on the bug report today ;)  I'll try to report the bug directly from the live cd first, and if I can't get that to work I'll do it from this installed version. I can see it is already installed by looking in Synaptic.
Thanks for the help.

---

### Post by ankspo71 on 2010-02-28
Hi again
The bug is now reported.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/529563](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/529563)
thanks

---

### Post by ankspo71 on 2010-03-01
Hello,

And now the problem is no longer an issue for me (see bug report above).
I had to try another daily build, the second one I've tried, and it works great.

Fixed :D

PS. I am currently running ubuntu desktop daily build 28-Feb-2010 32bit
(it was alpha3 and daily build 26-Feb-2010 that didn't work out for me)

---

