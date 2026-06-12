---
title: "Upgrade From 13.10 to 14.04.1LT"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by tomsubt on 2014-09-17
Hello  I just got a notice that I could upgrade to 14.04.1LT  so I tried to upgrade
and a message came up after awhile, stating something about my graphic card
and if I continue to upgrade my pc will run slow etc. Do  I want to continue with
the upgrade and I said No.
Since I wiped out windows the pc, how do I bring up all the statics of this pc, so 
I can post it here and maybe someone will tell me what is wrong?
and how I can upgrade without the pc going slower? Thanks

PS:  Its an HP a1010n desktop if that helps!

---

### Post by deadflowr on 2014-09-17
Robustly,
```
sudo lshw
```
Should give you enough info.
You can copy and paste it in a post, use code tags, please.

---

### Post by tomsubt on 2014-09-17
Ok, this is what came up, why cant I install 14.04.1LT?  Thanks>>>>

```
tomsubt-ps563aa-aba-a1010n
    description: Desktop Computer
    product: PS563AA-ABA a1010n ()
    vendor: HP Pavilion 061
    version: 0nB1211RE101GUPPY00
    serial: CNH5130CS7 NA520
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=A0A33D88-919D-D911-AF7B-CDDACCDAA865
  *-core
       description: Motherboard
       product: Guppy
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 1.03
       serial: MB-1234567890
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.04
          date: 01/26/2005
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: PGA 478
          size: 2933MHz
          capacity: 3066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back unified
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 1536MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:d0000000-dfffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0000000-e7ffffff memory:e8100000-e817ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d400(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:e8180000-e81803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:e8000000-e80fffff
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: LSI Corporation
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=14 mingnt=252
                resources: memory:e8000000-e80000ff ioport:c000(size=8) ioport:c400(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: d
                bus info: pci@0000:01:0d.0
                logical name: eth0
                version: 10
                serial: 00:11:d8:9b:dc:52
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:17 ioport:c800(size=256) memory:e8001000-e80010ff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:60000000-600003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:e8181000-e81811ff memory:e8182000-e81820ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3160021A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 8.11
             serial: 5JS3LNSX
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=3b893b89
           *-volume:0
                description: Extended partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                size: 143GiB
                capacity: 143GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1526MiB
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 140GiB
                   capabilities: bootable
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux swap / Solaris partition
                   physical id: 7
                   logical name: /dev/sda7
                   capacity: 1523MiB
                   capabilities: nofs
           *-volume:1
                description: EXT3 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 1.0
                serial: 76cc3563-0ef6-4c14-8d0a-249ba221bc50
                size: 5677MiB
                capacity: 5677MiB
                capabilities: primary journaled extended_attributes large_files ext3 ext2 initialized
                configuration: created=2014-03-25 04:39:55 filesystem=ext3 modified=2014-03-26 07:55:28 mounted=2014-03-26 07:54:42 state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom:0
             description: DVD writer
             product: DVDRW SOHW-1633S
             vendor: LITE-ON
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: BPSA
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: SCSI CD-ROM
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/cdrom1
             logical name: /dev/sr1
             capabilities: audio
             configuration: status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@4:1
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
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:13:49:91:a5:24
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=3.8.0-44-generic firmware=4725 ip=192.168.1.4 link=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by tomsubt on 2014-09-17
What are Code tags and how to use them? Thanks

---

### Post by deadflowr on 2014-09-17
> **tomsubt said:**
> What are Code tags and how to use them? Thanks

Good enough explanation here
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by tomsubt on 2014-09-17
Ok Thanks for the code tag info.  Now can anyone tell me why i get message when

trying to upgrade to 14.04  and can I install it? Thanks

---

### Post by grahammechanical on 2014-09-17
That "something about the graphic card" message would have been useful to know. So, you are using Ubuntu 13.10 but are you using it with Unity? Was the message a warning that the video driver could not be upgraded? Or something like that? 

Ubuntu 14.04 has a fall back open source video driver called llvmpipe that does run the desktop kind of slow but it gets us to a desktop and from there we can install the proprietary video driver. Was the message about llvmpipe?

Regards.

---

### Post by tomsubt on 2014-09-18
I dont know if using unity or not how do I tell?

Also I am upgrading it again to see exactly what the error message said and will let you guys know

when done! Thanks

---

### Post by tomsubt on 2014-09-18
Ok, Here is exactly what it says.. "Your Graphics hardware may not be fully supported in 14.04, running
the Unity Desktop eviroment is not fully supported, you may end up with a very slow enviroment
after the upgrade.
Our Advise is to keep the LTS version now, for more information go to 

[http://wiki.ubuntu.com/x/bugs/updatemanagerwarningforunity3D](http://wiki.ubuntu.com/x/bugs/updatemanagerwarningforunity3D).

Do you still want to upgrade Yes or No?????????

What do you guys think, I can do????

---

