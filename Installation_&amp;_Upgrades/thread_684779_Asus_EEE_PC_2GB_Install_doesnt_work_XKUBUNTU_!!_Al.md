---
title: "Asus EEE PC 2GB Install doesnt work X/K/UBUNTU !! Alt install cd or normal!"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Cheesycrap on 2008-02-01
Well im in quite a pickle here.

Ive tried, EEExubuntu , ubuntu normal, and even the dreaded kubuntu (no offence meant :P) all with no avail.  And EEExubuntu stored on a usb flash drive, just to check it wasnt just my usb cd drive.  Anyway, in the livecd install it disappears, around 73% of installing.  Yup, disappears, off the screen.  And im left with no error message on an ubuntu livecd desktop, yet again.  On the alternate install cd it gets to 85% where it freezes, the drive goes quiet and continues running however.  Again no error.  The 85% message says - Installing kernal  -  retrieving and installing linux - generic.
 
I dont think thats the exact message, but thats the gist of it.  Any suggestions would be great,

yours,

rob.

---

### Post by Cheesycrap on 2008-02-02
please, anyone?

---

### Post by Pumalite on 2008-02-02
post:
lshw

---

### Post by Cheesycrap on 2008-02-03
ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Notebook
    product: 700
    vendor: ASUSTeK Computer INC.
    version: 0129
    serial: EeePC-1234567890
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5
    configuration: boot=normal chassis=notebook uuid=0021CAB6-4BFE-D581-2585-001E8CB8BBE7
  *-core
       description: Motherboard
       product: 700
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 2.30G
       serial: EeePC-0123456789
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0129 (11/19/2007)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor          800MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: Intel CPU
          size: 630MHz
          capacity: 900MHz
          width: 32 bits
          clock: 70MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KB
             capacity: 32KB
             capabilities: internal write-back data
        *-cache:1 DISABLED
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             capabilities: internal
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 512MB
        *-bank
             description: DIMM Synchronous 400 MHz (2.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L2 100 Mbit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: a0
                serial: 00:1e:8c:b8:bb:e7
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.3 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wifi0
                version: 01
                serial: 00:15:af:6c:a8:b9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (svn r2756) ip=192.168.1.4 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: SILICONMOTION SM
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: n/a
                serial: 38265297438940999915
                size: 1907MB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 1764MB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 141MB
                   capacity: 141MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 141MB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@5:5
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: CardReader SD0
             vendor: USB2.0
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 0100
             size: 1946MB
             capabilities: removable
           *-disc
                physical id: 0
                logical name: /dev/sdb
                size: 1946MB
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Linux filesystem partition
                   physical id: 1
                   logical name: /dev/sdb1
                   capacity: 1945MB
                   capabilities: primary bootable

The cpu comes underclocked to save battery power.  That was taken from EEExubuntu booting live from the sd card.  Those partitions are from past failed installs.

---

### Post by Pumalite on 2008-02-03
How did you post 'lshw'?
This called my attention:

*-display:1 UNCLAIMED
description: Display controller
product: Mobile 915GM/GMS/910GML Express Graphics Controller
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 04
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=0

Seems like your graphics controller is not recognized by the kernel.

---

### Post by Cheesycrap on 2008-02-03
I opened up terminal and typed in lshw, it said it should be run from super user, so i typed sudo lshw just to be safe.  It seems odd that it should be the graphics card when so many other people have got their eeepc's running on ubuntu fine.

---

### Post by Cheesycrap on 2008-02-03
sorry, it appears lshw and sudolshw are different...

heres lshw

lsubuntu@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 503MB
     *-cpu
          product: Intel(R) Celeron(R) M processor          800MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.13.8
          size: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: L2 100 Mbit Ethernet Adapter
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: a0
                serial: 00:1e:8c:b8:bb:e7
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=ATL2 driverversion=1.0.40.3 firmware=L2 latency=0 module=atl2 multicast=yes
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wifi0
                version: 01
                serial: 00:15:af:6c:a8:b9
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.4 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FBM (ICH6M) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
ubuntu@ubuntu:~$


Also this display thing not being correctly identified, could that be the vga port?  I've heard that its not detected correctly.

---

### Post by Pumalite on 2008-02-03
This is a hardware problem and this is at the root of it: '*-display:1 UNCLAIMED'
Try to get a -386 kernel and see what happens.

---

### Post by Cheesycrap on 2008-02-03
Sorry, after some swift googling I've now discovered what a kernel is, but I really have no idea on how to get one and how to shove it into my little pc.  Thanks a lot for your help so far, but would you care to enlighten me?

Thanks again,

Rob.

---

### Post by kerry_s on 2008-02-03
i think your just running out of space and the install is dying out, you should not put a swap cause the eee uses a card as hard drive you want to lessen the writes. 

```
capacity: 1764MB
capabilities: primary bootable
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@1:0.0.0,2
logical name: /dev/sda2
size: 141MB
capacity: 141MB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 141MB
```

you should be using 1 partion for the whole setup, no swap. try your hand at a custom install-> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Cheesycrap on 2008-02-03
Ok, now it installed the system, thanks to not having a swap partition but GRUB failed to install.  As did LILO.. so I have a ubuntu installation I cant boot into, and other cds fail installing grub too...  Any ideas?

---

### Post by kerry_s on 2008-02-03
> **Cheesycrap said:**
> Ok, now it installed the system, thanks to not having a swap partition but GRUB failed to install.  As did LILO.. so I have a ubuntu installation I cant boot into, and other cds fail installing grub too...  Any ideas?

i think that's still part of your space issue ubuntu stock takes just about 2 gigs, you might not have the needed room for grub(/boot) folder. have you looked over the minimal install, i think you would have better luck with something like that, since it's custom you can work with in size limits.
also i was wondering is that the surfer model, i've heard nothing but bad about that model, plus i heard it's only running at 500+mhz, under clocked from the 800mhz cpu that's in it. if so you really need to think about using only low resource applications in your install or things will be to slow.

---

### Post by borisd on 2008-02-06
I have to report the same problem installing eeeXubuntu on an sd card. The installer disappears without notice about 70% into the installation. My card is 4GB sdhc, so space should not be the problem (btw, insufficient space should be detected by the installer and the user should be notified, dying out in the middle of the install without any feedback for the user is not very nice :) But I think we are having a different problem here. Any help is appreciated.

---

### Post by Cresho on 2008-02-06
YES!! WHO EVER SAID HE IS RUNNING OUT OF SPACE IS CORRECT!

I managed to get my friends ubuntu on his eee running just fine with all the bells and whistles installed.

I am going to post my information here!!!
First off, let me post some cool sites I found about ubuntu on eee
[http://www.youtube.com/watch?v=ru780Jfc1bQ&feature=related](http://www.youtube.com/watch?v=ru780Jfc1bQ&feature=related)
[http://www.youtube.com/watch?v=aM0pzdtCFzs&feature=related](http://www.youtube.com/watch?v=aM0pzdtCFzs&feature=related)
[http://www.youtube.com/watch?v=3VaerIGpO5Q](http://www.youtube.com/watch?v=3VaerIGpO5Q)


Secondly, after you decide. you need to download this one.
ubuntu-7.10-desktop-i386.iso from the ubuntu download sites.  It needs to be i386.

Thirdly.  after install, you will need to either use an external cd usb drive or create a ubuntu 1gb install usb flash drive to get the job done.

I will post the USB install version since many people can easily install from an external drive like cake.
-----------------------------------------
Instructions to create a bootable USB stick from any .ISO file, using Ubuntu.
This has been tested with the .ISO files for Eeexubuntu, Eeebuntu, Breeezy, and gOS.
It should work for any .ISO.

1) Install gparted using the Add/Remove option under Applications.

2) Open a terminal.

3) Install the syslinux package using:  sudo aptitude install syslinux

4) Download this script:  wget [http://zelut.org/projects/misc/isotostick.sh](http://zelut.org/projects/misc/isotostick.sh)

5) Make it executable with the command:  chmod u+x isotostick.sh

6) Insert your USB stick, right click on it's icon, unmount it.

7) Start gparted. System=>Administration=>Partition Editor.

8) In the upper right of the window, select the USB stick.
    (/dev/sdX)

9) Make absolutly sure you have selected the correct device.
    Mistakes with gparted can be fatal, we don't want to destroy anything.

10) Delete the partition on the USB stick.

11) Create a Fat 16 or 32 primary partition on your USB stick.
      I tried it with an ext3 partition and it didn't work on the EeePC.

12) Click Apply.

13) Double check to make sure everything is right, click Apply.

14) Right click on the new partition, select Manage Flags, check boot, click Close.

15) Remember the device name of the partition on your USB stick.
    (/dev/sdX1)

16) Close gparted.

17) Run the script, it requires two arguments, the .ISO file and the USB device.
    Run this command:  sudo ./isotostick.sh /path/to/your.iso /dev/sdX1

18) Make sure its bootable with syslinux:  sudo syslinux /dev/sdX1
-----------------------------------------

fourthly, installing ubuntu is important!!!!! do this and do not use ext3.  also, make sure you read up on the fstab info in this section or you will never be able to mount usb sticks at all.

pop in usb drive and hit escape till you can choose usb boot





Following are notes to install Ubuntu 7.10 Gutsy on an Asus Eee PC. These notes and scripts are derived from: [http://wiki.eeeuser.com/ubuntu](http://wiki.eeeuser.com/ubuntu)

The initial os install can be performed in quite a number of different ways. There are choices to be made with respect to installation media, drive partitioning schemes, file system types, and even the location of the resultant os components. Each of those choices comes with pros and cons.

The outline below is simply based upon my choices and attempts to reduce writes to the flash drive. For the time being, I will be using Ext2 for a filesystem, among other tricks. This comes at a price in that the file system is subject to potential data loss during power failure ( and other catastrophes ). I am willing to take this risk as the limitation of the eee's internal storage will likely dictate that I am keeping little of value on it in the first place.

I may change this approach as I learn more about the volume of writes that a journaling filesystem requires. If you feel more comfortable using a filesystem like Ext3, by all means, just substitute it at the appropriate place in this guide.

This guide now includes the new, interactive post-installer. This script will handle most post-installation fixes.


GUTSY INSTALL

* I have also changed the boot messaging from terse/splash screen to verbose. F2 > Boot > Boot Settings Configuration
Quick Boot [DISABLED]
Quiet Boot [DISABLED]

* Save changes and boot using the Ubuntu flash drive

* start up usb and install with first option

* Partition method: manual
- Delete all existing partitions
- Create one partition consuming the entire disc with the following specs:
Use as: Ext2 file system
Format the partition: yes, format it
Mount point: /
Mount options: noatime
Bootable flag: on
- Continue without defining a swap space

* Don't select any X screen resolutions

* Complete the install

* Reboot to the internal drive ( remove the USB external CD/DVD drive )

* Login

* Gutsy should come up with Compiz, max screen resolution ( 800x480 ) and functional ethernet

    *
      After completing this installation process, and rebooting your eee pc, your /etc/fstab file will have an incorrect entry for a cdrom drive. This is a problem, because it interferes with your ability to mount a usb drive (which will be assigned the same device name as the fictional cdrom drive). To remove the erroneous entry from your fstab file, open a terminal and

 sudo gedit /etc/fstab

and find the line that says

 /dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

and delete it (or comment it out). Hit save and close the text editor.

    *
      You will also have an entry in your /etc/apt/sources.list file for your LiveCD. Synaptic doesn't complain about it, but apt-get will, if this is a problem, open a terminal and

 sudo gedit /etc/apt/sources.list

and find the line that says

 deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

and delete it (or comment it out). Hit save and close the text editor.
-----------------------------------------


Fifthly, bugfixes.  Download from here the latest bugfixes for eee. and install the fixes.
[http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)
-----------------------------------------
If you have ethernet access, this part may help to fix the wifi problem.
sudo apt-get install build-essential
wget 'http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz'
tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make clean
make
sudo make install
reboot


for build essential, under adminstration and software sources, remove the cd rom check and make sure you are using the main repository with all checkmarks in ubuntu. reload after


do a search in synaptic for essential and install

-----------------------------------------
NOte!  if your having usb flash drive detection problems, remember to remove erroneous drives from the fstab.  Removing the line allowed my usb to normally detect my usb drives without any problems.


Sorry for the mess but I spent 4 hours making my friends work and these are just notes I copied and pasted in various text files which I can understand but I hope I got you guys in the right start!.

---

