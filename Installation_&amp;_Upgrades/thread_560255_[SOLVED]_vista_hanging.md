---
title: "[SOLVED] vista hanging"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by taylordgordon on 2007-09-26
hello!  I just installed ubuntu for the first time, and I really enjoy it.  

[I have been searching the forums for hours, and I can't seem to find this problem, so I am hoping someone here will be kind enough to help! :):]

The problem is, I still need some windows applications for work, so I still need Vista.   And when I tried to boot Vista up, I click on it in GRUB, and then the vista green bar thing appears as normal.  however, after about 10-15 seconds, it goes black and then to a BSOD, which says something about 'system volume on disk is corrupt.  chkdsk error # 0x1f'  I have tried the windows dvd repair functions, but they failed and i can't even get that dvd to recognize the volume (it sees my external HD at C: in the command prompt for some reason)  

fdisk describes the vista volume system as "SFS", whereas gparted sees it as ntfs, the way it should be i think.

my vista installation worked fine before.  some info: i was running dynamic disks in vista, and deleted about 25gigs for the ubuntu installation.  my vista install was a 32 bit system, and my linux is 64bit (i have a core2duo processor). I formatted it, everything was fine.  Then installed ubuntu, and ran across this problem the first time I tried to reboot and use vista.


I've attached a screenshot of gparted and of the output of fdisk -l
(in gparted, i noticed that sda1 (vista) has a 'first sector' of 63, not sure if that is relevant)

this is the vista line from menu.lst:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by pbcartwright on 2007-09-26
I have a DELL, so I also have a hidden restore partition. This makes my setup a bit different from yours. Here is my menu.lst entry for windows:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows XP Media Center Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1


----------------------------
when you boot ubuntu, can you mount your windows partition??
if not you might want to try to mount it using ntfs-3g:
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

and make sure you didn't corrupt the partition or remove files...

---

### Post by taylordgordon on 2007-09-26
Hi, 

I am able to mount the vista drive in ubuntu, and it seems like all the files are there.

Does anyone have any ideas?  

Thanks for the help

---

### Post by taylordgordon on 2007-09-26
Also, if I change the grub file to hd0,1 i get the GRUB message: Error 13: Invalid or unsupported executable format.  I take that to mean that vista is on hd0,0 but it just won't work?

---

### Post by Pumalite on 2007-09-26
From the Terminal, post:
sudo fdisk -lu
cat /boot/grub/menu.lst
blkid

---

### Post by taylordgordon on 2007-09-26
Here are the results:

fdisk -lu:
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   121344637    60672287+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       189502740   195366464     2931862+  82  Linux swap / Solaris
/dev/sda3       121355010   144777779    11711385   83  Linux
/dev/sda4       144777780   189502739    22362480   83  Linux

Partition table entries are not in disk order


blkid:
/dev/sda1: TYPE="ntfs" 
/dev/sda2: UUID="376bea54-a02a-4ec4-9cab-5fecada25028" TYPE="swap" 
/dev/sda3: UUID="957375ad-bd83-41a1-a5c3-645d01dbc61d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="9c4ffcce-758f-4042-be60-1d774c4652e6" SEC_TYPE="ext2" TYPE="ext3" 


menu.lst:
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=957375ad-bd83-41a1-a5c3-645d01dbc61d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=957375ad-bd83-41a1-a5c3-645d01dbc61d ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=957375ad-bd83-41a1-a5c3-645d01dbc61d ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=957375ad-bd83-41a1-a5c3-645d01dbc61d ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=957375ad-bd83-41a1-a5c3-645d01dbc61d ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by Pumalite on 2007-09-26
First backup:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back. then,

gksudo gedit /boot/grub/menu.lst

Change the 'root' line of the Windows entry from (hd0,1) to (hd0,0)
Save, exit and reboot. Cross your fingers.

---

### Post by taylordgordon on 2007-09-26
thanks for the help, but it still won't work!  same problem!

Is there anything else I can try?

---

### Post by Pumalite on 2007-09-26
Post:
cat /etc/fstab
(so I can compare UUID's)

---

### Post by taylordgordon on 2007-09-26
Thanks!

taylor@tpad:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=957375ad-bd83-41a1-a5c3-645d01dbc61d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=9c4ffcce-758f-4042-be60-1d774c4652e6 /home           ext3    defaults        0       2
# /dev/sda1
UUID=6C60DD4D60DD1F20 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=376bea54-a02a-4ec4-9cab-5fecada25028 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
taylor@tpad:~$

---

### Post by Pumalite on 2007-09-26
I checked you UUID's and they are all OK. The only thing I can think as a problem now is this:

/dev/sda1 * 63 121344637 60672287+ 42 SFS
Partition 1 does not end on cylinder boundary.

Why doesn't it say NTFS and there is the thing of not ending on cylinder boundary.

I suggest you get rescuescd and do all tests on that partition: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
[http://www.sysresccd.org/Online-Manual-EN](http://www.sysresccd.org/Online-Manual-EN)
(run fsck)
Report back.

---

### Post by Pumalite on 2007-09-26
Also post:
lshw

---

### Post by taylordgordon on 2007-09-26
here is the output, i am downloading the cd now and will post back soon.  Thanks!

tpad                      
    description: Notebook
    product: 2613CTO
    vendor: LENOVO
    version: ThinkPad T60p
    serial: xxxxxxxx
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: administrator_password=enabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=disabled power-on_password=enabled uuid=AA8BFC81-47D8-11CB-8BE5-C0B25BDC9CC8
  *-core
       description: Motherboard
       product: 2613CTO
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: VF0P76C61SB
       slot: Internal L2 Cache
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 79ETD6WW (2.16 ) (07/13/2007)
          size: 128KB
          capacity: 1984KB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: Intel(R) Core(TM)2 CPU
          slot: None
          size: 1GHz
          capacity: 2GHz
          width: 64 bits
          clock: 167MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KB
             capacity: 64KB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 4MB
             capacity: 4MB
             capabilities: burst internal write-back unified
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal L1 Cache
          size: 64KB
          capacity: 64KB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 2GB
          capacity: 2GB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 1GB
             width: 64 bits
        *-bank:1
             description: SODIMM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 1GB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0
                resources: iomemory:d0000000-dfffffff ioport:2000-20ff iomemory:ee100000-ee10ffff irq:16
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:ee400000-ee403fff irq:17
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:ee000000-ee01ffff ioport:3000-301f irq:16
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@03:00.0
                logical name: eth0
                version: 02
                serial: 00:18:de:ca:5e:8f
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
                resources: iomemory:edf00000-edf00fff irq:17
        *-pci:3
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:4
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1800-181f irq:16
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1820-183f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1840-185f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:1860-187f irq:19
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Bluetooth wireless interface
                   product: BCM2045B
                   vendor: Broadcom Corp
                   physical id: 1
                   bus info: usb@5:1
                   version: 1.00
                   capabilities: bluetooth usb-2.00
                   configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
              *-usb:1 UNCLAIMED
                   description: Generic USB device
                   product: Biometric Coprocessor
                   vendor: STMicroelectronics
                   physical id: 2
                   bus info: usb@5:2
                   version: 0.01
                   capabilities: usb-1.00
                   configuration: maxpower=100mA speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: iomemory:ee404000-ee4043ff irq:19
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@15:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:e4300000-e4300fff irq:16
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:1880-188f irq:16
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-842
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RB01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi2
             logical name: scsi3
             logical name: scsi4
             logical name: scsi5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list emulated scsi-host
             configuration: driver=ahci latency=0
             resources: ioport:18c8-18cf ioport:18ac-18af ioport:18c0-18c7 ioport:18a8-18ab ioport:18b0-18bf iomemory:ee404400-ee4047ff irq:16
           *-disk
                description: SCSI Disk
                product: HTS721010G9SA00
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: MCZI
                serial: MPCZN7Y0H7RKEL
                size: 93GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: SFS partition
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 57GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 2863MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 11GB
                   capabilities: primary
              *-volume:3
                   description: Linux filesystem partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 21GB
                   capabilities: primary
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0-18ff irq:11

---

### Post by taylordgordon on 2007-09-27
Excellent news!  :)

I am writing this from Vista...  

Using the RescueCD, and against my own better judgement, I used one of the utilities "testdisk" to analyze the partition tables, and then rewrite them.  rebooting, of course GRUB had been wiped out, but I thought the table might be what Vista needed to repair itself.  It wasn't, so back in the repair disk I clicked the fixmbr option in "testdisk", then again tried to load Vista, to no avail.  However, I reran the Vista repair disk and this time it was able to repair everything.

Now, I am going to add Ubuntu to the BCD and use it to access both systems.  I think this will be fine.  

Thanks to the UbuntuForums.org community, and in particularly Pumalite, for helping me through this!  

As I will be keeping my linux system because I was able to get this to work, you all have officially gained another Linux-convert! 

Thanks again!  
:)
Taylor:guitar:

---

