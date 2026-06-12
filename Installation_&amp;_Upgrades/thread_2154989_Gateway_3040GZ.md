---
title: "Gateway 3040GZ"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by SuzanneL on 2013-06-16
Ubuntu and Aloha,

    I have a Gateway laptop I bought in 2005.  I don't know the model, but the 

Ubuntu 10.10 System Monitor says:

Hardware:
   Memory: 463.8 MiB
   Process Intel(R) Celeron(R) M Processor 1.5 GHz

System Status
   Available disk space 48.7 GiB

Until yesterday it had WinXP on it that didn't work well, and I thought  some hidden viruses, because it would not always boot and when it did  boot, the wifi wouldn't work.   Installing Ubuntu on a friend's old 2002  Dell laptop, whose WinXP's networking had been destroyed by viruses,  had restored all functionality so splendidly for him (you couldn't pay  him to go back to Windows now), that I had hopes for my own laptop.

Well, 2005 was too old for this Gateway laptop to recognize the USB boot  stick, and I didn't have any blank DVD's laying around, so I installed  from the old Ubuntu 10.10 Live CD I had, figuring I'd upgrade later.  It  installed beautifully, the Ubuntu 10.10 runs fine except that the first  time it booted natively it flashed a black msg screen at me that I  needed to install some wifi driver, but that disappeared so fast I  couldn't read it, and of course it won't show it to me again.  So of  course the wifi still doesn't work.  

I am speaking to you now tethered through my smart phone.  Attempts to  upgrade Ubuntu through the tether have failed, as I must upgrade to  Ubuntu 11 before I can upgrade to Ubuntu 12, but of course Ubuntu 11  itself is so old it has been removed from the servers.   So I got in the  car and out into the blazing Phoenix 101 degree Fahrenheit heat and  bought some blank DVD's, plunked one into the much hated Win8 (now you  see it now you don't shell game of an operating system) across the room  and made the Ubuntu 12.04 Live DVD.

I put it in the Gateway laptop, and it cooked a while, showed me the  new-fangled black bar across the top, and then crashed and never  returned.  I tried it multiple times, and apparently the Ubuntu 10.10  was not touched, as I am still able to boot to it, and am talking to you  on it.  You can see a screenshot of it the crashed 12.04 install  attempt here -- [http://bluecoffeecat.com/Ubuntu-install-crash.jpg](http://bluecoffeecat.com/Ubuntu-install-crash.jpg)     (Sorry it's 2.8 MB for one ol' screenshot, but GIMP will not install  for Linux anywhere but from the Software Center, and of course, GIMP for  10.10 has been removed from the servers.   I am caught in a Catch 22.)

Even if my wifi is dead - I'll buy a USB wifi adapter if I have to since  I know the tethering works - but should I bother retrying the 12.04  install?  Was this a hardware error?  Or perhaps a bad burn of the LIve  DVD?

Thanks for any suggestions,

Suzanne


[ATTACH=CONFIG]243882[/ATTACH]

---

### Post by ahallubuntu on 2013-06-16
~

---

### Post by mörgæs on 2013-06-16
Hi, welcome to the fora.

Here's some more on the PAE problem and solutions:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by SuzanneL on 2013-06-17
Wow, thank you for the quick responses!  I see I have some educating  myself to do to figure out which one I should try.  My ultimate goal is  to run Synthesia (Dance Dance Revolution for piano keyboard) on Wine on  it, on a big screen TV.   And maybe stream a few movies :-)

I will come back and let you know how it goes.

Thank you again.

---

### Post by mörgæs on 2013-06-17
You're welcome.

Second thought: After all I'm not convinced that PAE is the problem. Please run

```
sudo lshw > lshw.txt
```

and post lshw.txt in CODE tags.

---

### Post by SuzanneL on 2013-06-18
I've done some reading now, so I'm begining to have an idea of the purposes of the different flavors, and ultimately figured I would just follow the links from this thread to complete the installation but I have not yet done so due to life's busy-ness.    But here is the result of the lshw. Yes, it did really contain unprintable characters :confused:    At the moment I have it hard-wired into the router (as the tethering would cut off any time somebody rang my phone).  I do see near the bottom of the lshw what appears to be an indicator that the wifi is indeed "DISABLED".  Besides the Ubuntu question, would you happen to know how to re-enable the wifi networking?

Thank you for looking at this.

```

 cat  lshw.txt
<computer name>
    description: Notebook
    product: 3040GZ
    vendor: Gateway
    version: Rev 1.0
    serial: <serial number>
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific  chassis=notebook frontpanel_password=unknown keyboard_password=unknown  power-on_password=disabled uuid=804D084D-7E64-0010-8467-0E0E00001808
  *-core
       description: Motherboard
       vendor: Gateway
       physical id: 0
       version: 4210
       serial: V56HM5I0071FHCB00X
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: W320.F08 (06/06/2005)
          size: 98KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce  cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe  nx up bts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 512MiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous [empty]
             physical id: 1
             slot: M2
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:20000000-23ffffff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:e020b000-e020bfff  ioport:3000(size=256) ioport:3400(size=256) memory:20000000-23ffffff  memory:28000000-2bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 7.2
                bus info: pci@0000:02:07.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=3
                resources: irq:19 memory:e020a000-e020a7ff memory:e0200000-e0203fff
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 7.3
                bus info: pci@0000:02:07.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:19 memory:e0204000-e0205fff
           *-network:0
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial: 00:03:25:1d:d8:ac
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes  driver=b44 driverversion=2.0 duplex=full ip=192.168.1.111 latency=32  link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: irq:17 memory:e0206000-e0207fff
           *-network:1
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=32
                resources: irq:17 memory:e0208000-e0209fff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6  ioport:170(size=8) ioport:376 ioport:1810(size=16)  memory:24000000-240003ff
           *-disk
                description: ATA Disk
                product: IC25N060ATMR04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MO3O
                serial: MRG31YKCKYUSJH
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000db741
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 854138dd-6e9b-428c-b3f1-14c2a202bec7
                   size: 54GiB
                   capacity: 54GiB
                   capabilities: primary bootable journaled  extended_attributes large_files huge_files dir_nlink recover extents  ext4 ext2 initialized
                   configuration: created=1988-01-10 09:44:22  filesystem=ext4 lastmountpoint=/&#521;7XS&#65533;`t&#65533;&#1792;;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;l!&#65533;`t&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;*{&#65533;*{&#65533;XS&#65533;  &#65533;4&#65533;&#65533;&#65533;yo!&#65533;&#65533;d modified=2013-06-16 07:12:32 mount.fstype=ext4  mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered  mounted=2013-06-17 22:28:18 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1498MiB
                   capacity: 1498MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1498MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4243N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.01
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:fd:78:2a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43  driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes  wireless=IEEE 802.11bg
$


```

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by mörgæs on 2013-06-18
As I imagined there's no PAE problem on your computer, but you are low on RAM.

Forget everything posted about PAE and old Buntu releases. I would recommend a fresh install of Lubuntu 13.04 (including all updates) with wired internet access; when that works we can focus on the wirefree card.

---

### Post by SuzanneL on 2013-07-05
Hi mörgæs, Thank you for the advise.  I have come back after a couple of weeks and installed Lubuntu.  It seems to work most of the time, and there are only a few browser add-ons I miss (like Flash, to watch YouTube).  I cannot find a version of Flash that will install.  I also found where I could download a non-open source driver for my wifi receiver, but my Lubuntu crashed entirely when I tried to install it.  Below is a screenshot of that crash, and a re-run of the sudu lshw.

I have since had a couple of more random crashes. Is there anything more I can do, or am I likely to live with random crashes from now on?

Thank you for any advise,

Suzanne



[IMG]http://sunwebhost.com/Lubuntu-crash.jpg[/IMG]
 

```
gateway-laptop
    description: Notebook
    product: 3040GZ
    vendor: Gateway
    version: Rev 1.0
    serial: N6456 210 27068
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=804D084D-7E64-0010-8467-0E0E00001808
  *-core
       description: Motherboard
       vendor: Gateway
       physical id: 0
       version: 4210
       serial: V56HM5I0071FHCB00X
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: W320.F08
          date: 06/06/2005
          size: 98KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U1
          size: 1500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx bts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 512MiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous [empty]
             physical id: 1
             slot: M2
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:20000000-23ffffff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:19 memory:28000000-28000fff ioport:3000(size=256) ioport:3400(size=256) memory:20000000-23ffffff memory:2c000000-2fffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 7.2
                bus info: pci@0000:02:07.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=3
                resources: irq:19 memory:e020a000-e020a7ff memory:e0200000-e0203fff
           *-storage
                description: Mass storage controller
                product: PCIxx21 Integrated FlashMedia Controller
                vendor: Texas Instruments
                physical id: 7.3
                bus info: pci@0000:02:07.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm bus_master cap_list
                configuration: driver=tifm_7xx1 latency=57 maxlatency=4 mingnt=7
                resources: irq:19 memory:e0204000-e0205fff
           *-network:0
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 01
                serial: 00:03:25:1d:d8:ac
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:17 memory:e0206000-e0207fff
           *-network:1
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=32
                resources: irq:17 memory:e0208000-e0209fff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:24000000-240003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: IC25N060ATMR04-0
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MO3O
             serial: MRG31YKCKYUSJH
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000db741
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 854138dd-6e9b-428c-b3f1-14c2a202bec7
                size: 54GiB
                capacity: 54GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=1988-01-10 09:44:22 filesystem=ext4 lastmountpoint=/ modified=2013-07-05 14:37:03 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-07-05 14:37:03 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1498MiB
                capacity: 1498MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1498MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: RW/DVD GCC-4243N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 1.01
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlan0
       serial: f8:d1:11:12:f1:83
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.8.0-26-generic firmware=0.29 ip=192.168.1.244 link=yes multicast=yes wireless=IEEE 802.11bgn


```

---

### Post by mörgæs on 2013-07-06
Have you applied all updates using wired internet connection?
Was it also unstable before you tried to add drivers?
If you run MEMTEST from the boot menu for (at least) a couple of hours, do you see any indication of bad memory sticks?

---

