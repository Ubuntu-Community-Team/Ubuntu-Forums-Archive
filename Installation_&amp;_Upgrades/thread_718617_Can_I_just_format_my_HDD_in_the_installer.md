---
title: "Can I just format my HDD in the installer"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by ADBD on 2008-03-08
I have zenwalk linux like this:
fdisk on ubuntu:
Device Boot Start End Blocks Id System
/dev/sda1 * 1 510 4096574+ 83 Linux
/dev/sda2 511 638 1028160 82 Linus swap/Solaris
/dev/sda3 639 30401 239071297+ 83 Linux

So can I just format the whole HDD on ubuntu installation and install ubuntu on it with no problems? I only have one HDD and I don't want dual-boot, just ubuntu

---

### Post by Pumalite on 2008-03-08
Install Ubuntu. Use 'Guided>Use Entire Disk'

---

### Post by ADBD on 2008-03-08
ok, thanks
I'm gonna try this now then. let's hope it works :)

---

### Post by ADBD on 2008-03-08
It shows:

The partition tables of the following devices are changed:
 SCSI3 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #1 of SCSI3 (0,0,0) (sda) as ext3
 partition #5 of SCSI3 (0,0,0) (sda) as swap

On "Ready to install" That looks a bit weird to me, I don't have 5 partitions? And why isn't making three partitions for /, /home and swap?

---

### Post by Pumalite on 2008-03-08
That's normal. Go ahead. You'll be OK.

---

### Post by ADBD on 2008-03-08
ok, thanks. just wanted to make sure

---

### Post by Pumalite on 2008-03-08
Good luck.

---

### Post by ADBD on 2008-03-08
> **Pumalite said:**
> Good luck.

wow that was the fastest installation ever :) seems to be working

---

### Post by prshah on 2008-03-08
On any HDD, you can have only 4 primary partitions.

If you need more, you can create an extended partition and create logical drives (partitions) within that.

Since the extended partition is usually the 4th one, even if you have only one primary partition, ubuntu creates a primary partition (/dev/sda1), a secondary partition (/dev/sda2, invisible since it's not usable as a drive) and an extended partition (/dev/sda5) which in your case is the swap.

A better partitioning scheme though; 

10gb linux/ext3, mount point "/" (root)
2Gb linux/swap
everything else linux/ext3, mount point "/home"

This will allow you to upgrade/change operating systems without affecting your files.

If you want to implement this WITHOUT reinstalling your OS, try using gparted from the live ubuntu CD. But remember to copy everything in the /home folder to somewhere else, then resize the "/" parition to 10Gb, create a new "/home" partition and copy everything back into the new "/home" partition.

But I would recommend a fresh install instead of this mucking about.

Note that there is nothing "wrong" about your current partition; the above way is just better.

Also if you have two hard disks, you can get better performance by pushing the swap partition on the other drive. 

And if you have three HDDs, you can create the "/home" partition on the 3rd disk for even better multitasking performance!

Cheers,
PRShah

---

### Post by ADBD on 2008-03-08
> **prshah said:**
> On any HDD, you can have only 4 primary partitions.

If you need more, you can create an extended partition and create logical drives (partitions) within that.

Since the extended partition is usually the 4th one, even if you have only one primary partition, ubuntu creates a primary partition (/dev/sda1), a secondary partition (/dev/sda2, invisible since it's not usable as a drive) and an extended partition (/dev/sda5) which in your case is the swap.

A better partitioning scheme though; 

10gb linux/ext3, mount point "/" (root)
2Gb linux/swap
everything else linux/ext3, mount point "/home"

This will allow you to upgrade/change operating systems without affecting your files.

If you want to implement this WITHOUT reinstalling your OS, try using gparted from the live ubuntu CD. But remember to copy everything in the /home folder to somewhere else, then resize the "/" parition to 10Gb, create a new "/home" partition and copy everything back into the new "/home" partition.

But I would recommend a fresh install instead of this mucking about.

Note that there is nothing "wrong" about your current partition; the above way is just better.

Also if you have two hard disks, you can get better performance by pushing the swap partition on the other drive. 

And if you have three HDDs, you can create the "/home" partition on the 3rd disk for even better multitasking performance!

Cheers,
PRShah

thanks :) I'll consider trying that (that's how I've had it before on other distro)

---

### Post by ADBD on 2008-03-08
There's 196 updates. Should I just install them all?

---

### Post by Pumalite on 2008-03-08
You live only once!

---

### Post by ADBD on 2008-03-08
lol

---

### Post by ADBD on 2008-03-08
after installing the updates i got this message two times and only got to login after the third boot:
BusyBox v.1.1.3(Debian 1,:1.1.1.3-5ebuntu7) Built-in shell(ash) 
Enter 'help' for a list of built-in commands
(unitramfs)

And when ever I typed a letter I got two letters instead. Normal?

---

### Post by Pumalite on 2008-03-08
Maybe you could get in reconfiguring your xserver:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa as the driver, then: startx
If not, install again and this time avoid the new kernels in the update list.

---

### Post by ADBD on 2008-03-08
joni@joni-desktop:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for joni:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080308224443
joni@joni-desktop:~$ sudo startx
xauth:  creating new authority file /home/joni/.serverauth.6262

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

joni@joni-desktop:~$

EDIT: before I did this I tried to get my dual monitors working. What happened was now I'm in low-resolution mode :/ I need 1680x1500 for my lcd and 1024xsomething for my crt. with the crt extending the lcd to the left

---

### Post by ADBD on 2008-03-08
meh, I think I'll reinstall

---

### Post by ADBD on 2008-03-08
I reinstalled and it does that even before updating

---

### Post by Pumalite on 2008-03-08
If you can boot a Live CD, post:
lshw

---

### Post by ADBD on 2008-03-08
I was able to login after about 7 boot tries :/ 
The good thing is I got dual-monitors to work with sudo nvidia-settins :)
Here:
joni-desktop              
    description: Desktop Computer
    product: OEM
    vendor: OEM
    version: OEM
    serial: OEM
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-00508D945493
  *-core
       description: Motherboard
       product: AB9/AB9RPO(Intel965+ICH8)
       vendor: [http://www.abit.com.tw/](http://www.abit.com.tw/)
       physical id: 0
       version: 1.x (BIOS:15)
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (08/16/2007)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Socket 775
          size: 1904MHz
          capacity: 4GHz
          width: 64 bits
          clock: 272MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MB
             capacity: 2MB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM Synchronous
             physical id: 0
             slot: C
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM Synchronous
             physical id: 1
             slot: C
             size: 512MB
             width: 64 bits
        *-bank:2
             description: DIMM Synchronous
             physical id: 2
             slot: C
             size: 512MB
             width: 64 bits
        *-bank:3
             description: DIMM Synchronous
             physical id: 3
             slot: C
             size: 512MB
             width: 64 bits
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
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G71 [GeForce 7900 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Contoller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
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
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 01
                serial: 00:50:8d:94:54:93
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=10MB/s
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0 module=ahci
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:04:00.1
                logical name: scsi6
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0 module=pata_jmicron
              *-cdrom
                   description: DVD-RAM writer
                   product: DVDRW LH-18A1H
                   vendor: LITE-ON
                   physical id: 0.1.0
                   bus info: scsi@6:0.1.0
                   logical name: /dev/cdrom
                   logical name: /dev/dvd
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: HL07
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=open
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 2
                bus info: pci@0000:05:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=68 maxlatency=4 mingnt=2 module=ohci1394
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
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: WDC WD2500KS-00M
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 02.0
                serial: WD-WCANK6015908
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 227GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 5930MB
                   capacity: 5930MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5930MB
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
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix

---

### Post by Pumalite on 2008-03-08
I can find only two suspects: your 965 chipset and your JMicron controller:
[http://www.google.com/search?hl=en&q=ubuntu+and+965+chipset&btnG=Google+Search](http://www.google.com/search?hl=en&q=ubuntu+and+965+chipset&btnG=Google+Search)
[http://www.google.com/search?hl=en&q=ubuntu+and+JMicron+controller&btnG=Google+Search](http://www.google.com/search?hl=en&q=ubuntu+and+JMicron+controller&btnG=Google+Search)

---

### Post by ADBD on 2008-03-08
thanks,
I read some of those links but didn't get any wiser about what to do...
this thread hasn't really stayed on topic, btw :/ sorry about that, maybe I shoud have started a new one

---

### Post by Pumalite on 2008-03-08
No problem. You can do that.

---

