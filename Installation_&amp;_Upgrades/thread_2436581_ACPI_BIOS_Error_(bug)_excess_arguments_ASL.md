---
title: "ACPI BIOS Error (bug): ***excess arguments ASL"
date: 2020-02-09
forum: Installation &amp; Upgrades
---

### Post by michalkochman on 2020-02-09
Hi there.
This weekend, I made an attempt to upgrade old computer at my parents from... ubuntu 16.04 to 18.04 I think. Originally dual boot with Wvista (yeah, old notebook and not really used for a while). When things went sideways (powr outage during upgrade is rarelly a good thing)... long story short, I decided to completly wipe out everything on the disk and make clean istall of Ubuntu/lubuntu only. However, since it is a 32-bit architecture ntb, I ended up trying to install Ubuntu 16.04 from DVD (18.04 does not have a 32-bit ISO to install). The DVD won't boot, and I got an error
```
[0661911] ACPI BIOS Error (bug):\_[COLOR=#141414][FONT=inherit]SB.PCI0._OSC[/FONT][/COLOR]: Excess arguments - ASL declared 5, ACPI requires 4 (20181213/[COLOR=#141414][FONT=inherit]nsarguments-164) [/FONT][/COLOR]
```
even before I got to choose language and whether I want to "install" o "try" ubuntu. Ok, no big deal, I tried with Lubuntu 18.04 DVD. Same result. Got into some googling - this error seems to be widely discussed, however I was not able to find any solution for my case, everything I found was how to deal with it when system is already installed. I got workong backwards, I did try to install Ubuntu 14.10 (had that DVD on me for a long time) and upgrade from there to try solve this. Was not able to upgrade from there, even after editing [COLOR=#333333][FONT=UbuntuMono]sources.list [/FONT][/COLOR]to point to old-releases. After a long while trying, I went even more backwards - downloaded 14.04LTS, succesfully installed, initiated do-release-upgrade to 16.04. When it ("succesfully") ended and the computer was rebooting, it never booted. I only got "flashing" screen (from completely black to black with backlight on, I suppose). After pressing power button in this stage, I got the "ubuntu shutting down" screen (the one with logo and dots underneath it).I did try to change some settings in bios utility (fast boot enabled/disabled) and try with each described step in both states. I am really out of ideas.

Some info about the computer:
Acer Aspire 5720
Intel DualCore @ 1.5GHz (not my idea that one, originally it was higher. Bios obviously does not allow overclocking directly from the bios setup, so since I do not have working OS I have to work with this for now
BIOS setup: insydeh20 setup utility V1.45 rev3
currently with completely new and non functional ubuntu. No data to save ;). Plan is to use the computer only to check my emails and maybe social networks when I am at my parent's)

I won't probably have acces to this ntb for two weeks or so now, but man, it is bugging me. Any ideas what I can do next time to get it working with at least some linux distro (preferably lubuntu/ubuntu)? I got the feeling from my research that iti is problem of bios/linux kernel

---

### Post by mörgæs on 2020-02-09
Hi, welcome to the fora.

The 5720 is 64 bit. 
I would not recommend Ubuntu for this hardware but X/Lubuntu 19.10. No upgrades, only clean installs.

---

### Post by michalkochman on 2020-02-09
Thank you for your response
I am pretty sure the original Wvista (sold with the computer) was 32-bit. I have to admit I have not double checked whether the hardware is actually 32 or 64 and just ran with the information from Wvista (did not even occured to me that I could have 64bit computer with 32bit system isntalled directly from seller). 
I surely will prefer 18.04 (or 20.04) since they are LTS, but I will sure try to install the 64bit version next time I'll got my hands on that notebook.

---

### Post by mörgæs on 2020-02-09
I understand that you want to install 20.04 for its LTS status when it's ready but there is no point in selecting something that has already spent two of the three years of support. 

Anyway, post back when you get access to the computer and let's hear how it all goes.

---

### Post by michalkochman on 2020-02-22
OK, so the attempt to install 64bit versions ended... well, identically  to the 32bit ones. So, since I was unable to find my original  documentation of the laptop, I returned to the 32bit versions. I  sacrificed 20Gb of space to make my laptop dual-boot (i added another  14.04 to the "not-functional" 16.04). Then, I was able to selecet  "advanced options -> recovery mode" for my 16.04. It loaded the login  screen (that I considered a succes). However, when I tried to log in, I  only got a blank background. Even Ctrl-T for opening terminal did  nothing. So i switched to tty2 (or some of the other terminals without  graphics) and logged in there. I got a warning about some missing  dependency (apt-something missing in some python script, I think). I  tried to install that one, I got an error. so I ran apt-get -f.  Everything started to work in non-graphic terminal, tty7 still had the  same issue. I tried apt-get install gnome. When I tried to login to  gnome in tty7, I always got returned back to the loggin screen. So I ran  apt-get update, and apt-get upgrade upgrade from tty1. Gnome sessions  got working. Then upgraded (still via tty1, to be sure) from 16.04 to  18.04. When restarting to finish the upgrade, I got some ugly red error  msgs on booting. Have to admit, did study them. They said something in  the general mean of "cant start default welcome session to 18.04". So  once again I tried recovery mode - > back to normal boot. It seems it  did the trick, so far the computer seems operational (did not restarted  it since). I am really interested how the final 18.04->20.04 will go  when the time comes.

TL;DR: some dark magic with non-graphic ttyX and recover modes worked. 32bit system running.

edit: external monitor is not recognized when connected. When restarted with monitor already plugged-in, system will freeze on login and requires booting via recovery mode again to make it work. Ghost in the mashine, really...

---

### Post by mörgæs on 2020-02-22
Let's take the guesswork out of the process. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags. It will show all hardware details.

---

### Post by michalkochman on 2020-02-23
Will do, just once again probably in two or three weeks time.

---

### Post by michalkochman on 2020-03-07
```
computer
    description: Computer
    product: Aspire 5720 (None)
    vendor: Acer
    version: V1.45
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: cpus=1 family=None sku=None uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Nettiling
       vendor: Acer
       physical id: 0
       version: V1.45
       serial: [REMOVED]
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.45
          date: 11/10/2008
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             vendor: Kingston
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             vendor: Kingston
             physical id: 1
             serial: [REMOVED]
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz
          vendor: Intel Corp.
          physical id: 20
          bus info: cpu@0
          version: 6.15.13
          serial: [REMOVED]
          slot: uPGA-478
          size: 1496MHz
          capacity: 1500MHz
          width: 64 bits
          clock: 166MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts cpuid aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm pti dtherm cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: 21
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: asynchronous internal write-back unified
             configuration: level=2
        *-cache:1
             description: L1 cache
             physical id: 23
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
             configuration: level=1
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
     *-cache
          description: L1 cache
          physical id: 22
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
          configuration: level=1
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d4000000-d40fffff memory:c0000000-cfffffff ioport:5110(size=8) memory:c0000-dffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d8500000-d85fffff
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:50a0(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-88-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:5080(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-88-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:d8404400-d84047ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-88-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:25 memory:d8400000-d8403fff
        *-pci:0
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
             resources: irq:16 ioport:4000(size=4096) memory:d7400000-d83fffff ioport:d0000000(size=16777216)
        *-pci:1
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
             resources: irq:17 ioport:3000(size=4096) memory:d6400000-d73fffff ioport:d1000000(size=16777216)
        *-pci:2
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
             resources: irq:18 ioport:2000(size=4096) memory:d5300000-d63fffff ioport:d2000000(size=16777216)
           *-network
                description: Ethernet interface
                product: NetLink BCM5787M Gigabit Ethernet PCI Express
                vendor: Broadcom Inc. and subsidiaries
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5787m-v3.22 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:26 memory:d5300000-d530ffff
        *-pci:3
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
             resources: irq:19 ioport:1000(size=4096) memory:d4200000-d52fffff ioport:d3000000(size=16777216)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 02
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=4.15.0-88-generic firmware=15.32.2.9 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:24 memory:d4200000-d4200fff
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:5060(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-88-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5040(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-88-generic uhci_hcd
                physical id: 1
                bus info: usb@6
                logical name: usb6
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5020(size=32)
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 4.15.0-88-generic uhci_hcd
                physical id: 1
                bus info: usb@7
                logical name: usb7
                version: 4.15
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:d8404000-d84043ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-88-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb
                   description: Video
                   product: Acer Crystal Eye webcam
                   vendor: Acer, Inc
                   physical id: 4
                   bus info: usb@2:4
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:d4100000-d41fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:20 memory:d4100000-d41007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:07:00.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:22 memory:d4100b00-d4100bff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:07:00.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r592 latency=64
                resources: irq:22 memory:d4100900-d41009ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 0.3
                bus info: pci@0000:07:00.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:22 memory:d4100800-d41008ff
        *-isa
             description: ISA bridge
             product: 82801HM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide isa_compatibility_mode_controller__supports_both_channels_switched_to_pci_native_mode__supports_bus_mastering bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:50e0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm pci_native_mode_controller__supports_both_channels_switched_to_isa_compatibility_mode__supports_bus_mastering bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:50f8(size=8) ioport:511c(size=4) ioport:50f0(size=8) ioport:5118(size=4) ioport:50d0(size=16) ioport:50c0(size=16)
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
             resources: memory:d8404800-d84048ff ioport:5000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ-850S
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.61
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Hitachi HTS54161
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: C70P
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=00051ce6
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 131GiB
                capacity: 131GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2020-02-08 23:33:12 filesystem=ext4 lastmountpoint=/ modified=2020-03-07 12:18:15 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,stripe=32738,data=ordered mounted=2020-03-07 12:10:07 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 18GiB
                capacity: 18GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap volume
                   physical id: 5
                   logical name: /dev/sda5
                   version: 1
                   serial: [REMOVED]
                   size: 4085MiB
                   capacity: 4085MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-logicalvolume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 6
                   logical name: /dev/sda6
                   version: 1.0
                   serial: [REMOVED]
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2020-02-22 13:16:43 filesystem=ext4 lastmountpoint=/ modified=2020-02-22 13:48:55 mounted=2020-02-22 13:48:55 state=clean
  *-battery
       description: Lithium Ion Battery
       product: Li-ion(6cell)
       vendor: Sony
       physical id: 1
       serial: [REMOVED]
       slot: Internal Battery
       capacity: 51840mWh
       configuration: voltage=10,8V
```

---

### Post by mörgæs on 2020-03-09
You could try the *noacpi* boot option.

---

