---
title: "Dell Dimension 4600, Kernel Won't Load"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by majasticmoose on 2014-09-21
I have a interesting problem that I have never experienced before. I am trying to convert my old Dell Dimension 4600 into a server using Ubuntu Server 14.04. Every time I try to boot my computer hangs at a blank screen. I have tried USB booting Ubuntu Server, Ubuntu 14.04 and 7.04, Mint, antiX, wattOS, Crunchbang, Arch, and Debian and tried CD boot of Ubuntu Server all with the computer hanging.

 The only OS that loads is Damn Small Linux, but X server won't start. And Puppy loads and runs perfectly. I don't know what separates these OSes from the others. I am beginning to think its the graphics card which I think is a nVidia GeForce FX 5200.

I'm stuck. I've tried to set up the server in DSL and Puppy but keep on running into walls and I need Ubuntu Server. 

Thanks for the help guys,
Andrew Mello


Dell Dimension 4600
Intel Pentium 4 with HT 32-bit
1 GB of RAM

---

### Post by mörgæs on 2014-09-22
Using any Linux distro please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by majasticmoose on 2014-09-22
```
computer
    description: Mini Tower Computer
    product: Dimension 4600
    vendor: Dell Computer Corporation
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-3500-1030-8035-B4C04F383331
  *-core
       description: Motherboard
       vendor: Dell Computer Corp.
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A02 (05/07/2003)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2400MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 2
             slot: CHANNEL A DIMM 1
             size: 128MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 3
             slot: CHANNEL B DIMM 1
             size: 128MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-efffffff(prefetchable)
        *-pci:0
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:fd000000-feafffff memory:f0000000-f7ffffff(prefetchable)
           *-display UNCLAIMED
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:fd000000-fdffffff memory:f0000000-f7ffffff(prefetchable) memory:fea00000-fea1ffff(prefetchable)
        *-usb:0
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:ff80(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.21.7 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:1
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:ff60(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.21.7 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:2
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:9 ioport:ff40(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.21.7 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:3
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:ff20(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.21.7 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Microsoft 5-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@4:1
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1
                   description: Keyboard
                   product: Microsoft Wireless Optical Desktop
                   vendor: Microsoft
                   physical id: 2
                   bus info: usb@4:2
                   version: 0.41
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:4
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:7 memory:ffa80800-ffa80bff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.21.7 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480.0MB/s
              *-usb
                   description: Mass storage device
                   product: STORE N GO
                   vendor: Verbatim
                   physical id: 2
                   bus info: usb@5:2
                   logical name: scsi2
                   version: 11.00
                   serial: [REMOVED]
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=500mA speed=480.0MB/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sda
                      size: 3824MiB (4009MB)
                      capabilities: partitioned partitioned:dos
                      configuration: signature=0ab91d83
                    *-volume
                         description: Windows FAT volume
                         vendor: SYSLINUX
                         physical id: 1
                         bus info: scsi@2:0.0.0,1
                         logical name: /dev/sda1
                         logical name: /initrd/mnt/dev_save
                         version: FAT32
                         serial: [REMOVED]
                         size: 3821MiB
                         capacity: 3823MiB
                         capabilities: primary bootable fat initialized
                         configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 state=mounted
        *-pci:1
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:fcf00000-fcffffff
           *-communication
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=serial latency=64
                resources: irq:3 memory:fcffe000-fcffefff ioport:df30(size=16)
           *-network
                description: Ethernet interface
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=[REMOVED] latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
                resources: irq:10 memory:fcfff000-fcffffff ioport:df40(size=64)
        *-isa
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=0
             resources: irq:9 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:febffc00-febfffff
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: WDC WD800BB-75CAA0
                   vendor: Western Digital
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 16.06V16
                   serial: [REMOVED]
                   size: 74GiB (80GB)
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: mode=udma5 signature=9dc96e9e smart=on
                 *-volume:0
                      description: Windows FAT volume
                      vendor: Dell 4.1
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      version: FAT16
                      serial: [REMOVED]
                      size: 31MiB
                      capacity: 956MiB
                      capabilities: primary nofs fat initialized
                      configuration: FATs=2 filesystem=fat label=DellUtility
                 *-volume:1
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      version: 1.0
                      serial: [REMOVED]
                      size: 9538MiB
                      capacity: 9538MiB
                      capabilities: primary bootable journaled large_files ext3 ext2 initialized
                      configuration: created=2014-09-21 22:22:44 filesystem=ext3 modified=2014-09-22 23:40:06 mounted=2014-09-22 23:40:05 state=clean
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: CD-R/CD-RW writer
                   product: SONY CD-RW CRX216E
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: PD01
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                   configuration: mode=udma2 status=nodisc
        *-ide:1
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:9 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16)
        *-serial
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:5 ioport:eda0(size=32)
        *-multimedia
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:5 ioport:ee00(size=256) ioport:edc0(size=64) memory:febffa00-febffbff memory:febff900-febff9ff
```

---

### Post by mörgæs on 2014-09-22
It's a somewhat strange output. Was it created with Ubuntu 7.04? 

I don't see any Nvidia graphics card but if you have a spare card please try to put it in. 

If we forget about installing for a while are you able to run a live Lubuntu 14.04.1? Best is to test with as few USB devices as possible attached.

---

### Post by majasticmoose on 2014-09-22
The output was created in Puppy Linux as that's the only distro that will run. It's a ported version of lshw (lshw doesn't come with Puppy). I can't get any of the OSes listed in the first post to even run live. I dropped GRUB into commandline and it load the kernel, loads initrd, then I type boot and it hangs. This happens every time. I tried Xubuntu (didn't work) and I'll try Lubuntu tonight. My roommate has a brand new custom built gaming computer that I may borrow his graphics card for. It will most certainly be overkill.

The Dell does have a graphics card (its in the AGP slot) and no integrated graphics.

Andrew

---

### Post by majasticmoose on 2014-09-22
Tried Lubuntu on CD and USB. When the CD attempts to boot, there is a blank screen for about 10 secs as the CD drive is spinning, then it goes to HDD boot. 

On USB boot the syslinux bootloader loads and when I select the Live Lubuntu or Install the menu drops and there is just a blank screen and the LED indicator on the USB blinks for a couple minutes then stops so I assume its hanging.

To make things weirder, I couldn't get my CD drive to boot my Windows 7 CD and I tried both drives I have installed. Also graphical GRUB hangs and doesn't load, but normal GRUB does load. This made me think it was my graphics card. But I've tried downloading the alternative text installers and it doesn't work.

I thank you for helping me. I am trying everything and putting in 6 hours a day, every day this weekend. My roommate and I sat down and made a list of possible causes and we narrowed it down to: extremely improbable motherboard/CPU failure where it still works but some specific task causes hang, weird BIOS problem, and black magic.

Andrew

---

### Post by majasticmoose on 2014-09-22
Also if you think it would help I can record a video of the booting

---

### Post by matt_symes on 2014-09-23
Hi

Can you boot the LiveCD if you change the grub command line options to use the vesa driver ? (vga=)

What about booting with the nomodeset option ?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Kind regards

---

### Post by mörgæs on 2014-09-23
Your BIOS is A02, which might explain your problems. Before testing more distros I would upgrade to the latest, which is [A12]("http://www.dell.com/support/home/us/en/19/product-support/product/dimension-4600/drivers").

---

