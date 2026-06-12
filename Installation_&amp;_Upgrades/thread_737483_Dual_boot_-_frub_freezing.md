---
title: "Dual boot - frub freezing"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by george182 on 2008-03-27
Hi, im new here!
Anyway, im having a problem in grub
I started with an original partition on my hard drive for windows xp. 
This worked fine until i decided to upgrade to linux (dapper drake) hoping for a single hard drive with two separate bootable OSs.
However at the moment, when the GRUB menu appears, I have the choice for both OSs, but only the linux one works(perfectly!).
But when i select windows, it freezes.
I tried typing the folowing into the GRUB command:

rootnoverify (hd0,0)
makeactive
chainloader +1
boot

and with makeactive and chainloader +1 the other way around as i saw written somewhere.
This also results in grub freezing
Please help!

---

### Post by Pumalite on 2008-03-27
Post:
sudo fdisk -lu

---

### Post by george182 on 2008-03-27
Sorry! here:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   565600454   282800196    7  HPFS/NTFS
/dev/sda2       565600455   775345094   104872320   83  Linux
/dev/sda3       775345095   781417664     3036285    5  Extended
/dev/sda5       775345158   781417664     3036253+  82  Linux swap / Solaris

---

### Post by diablo75 on 2008-03-27
Type this in:

```
sudo gedit /boot/grub/menu.lst
```

And paste the contents of that menu.lst file in here for us please.

---

### Post by Pumalite on 2008-03-27
Post:
gksudo gedit /boot/grub/menu.lst

---

### Post by george182 on 2008-03-27
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-51-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-51-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-51-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-51-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
makeactive
chainloader	+1

---

### Post by Pumalite on 2008-03-27
Change this:
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedafault
chainloader +1
To this:
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by diablo75 on 2008-03-27
[QUOTE=george182;4599553

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
makeactive
chainloader	+1[/QUOTE]

My menu.lst has this:

# This entry was added by username for a non-linux OS
# on /dev/sda3
title        Microsoft Windows XP Home Edition
root        (hd0,2)
***savedefault***
makeactive
chainloader    +1

I don't know if that savedefault matters...you might try inserting it in like mine has, save, and try again.

---

### Post by george182 on 2008-03-27
Nope. It still freezes

It says when it is selected: (from memory)

booting 'microsoft windows xp'

rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

_   <<< flashing


and freezes at this point. Any help?

---

### Post by Pumalite on 2008-03-27
Post:
lshw
Also get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Post screen shot.

---

### Post by george182 on 2008-03-27
georges-desktop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1010MB
     *-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.11.1
          size: 2100MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci:0
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: f0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          resources: iomemory:f0000000-f7ffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: GeForce 6200
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia
                resources: iomemory:f8000000-f8ffffff iomemory:e0000000-efffffff iomemory:f9000000-f9ffffff irq:185
        *-network:0 DISABLED
             description: Wireless interface
             product: BCM4306 802.11b/g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 8
             bus info: pci@00:08.0
             logical name: eth1
             version: 03
             serial: 00:11:50:3f:9a:fe
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical wireless
             configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
             resources: iomemory:fb000000-fb001fff irq:185
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@00:0f.0
             logical name: scsi0
             logical name: scsi1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list scsi-host
             configuration: driver=sata_via
             resources: ioport:e100-e107 ioport:e700-e703 ioport:e800-e807 ioport:e900-e903 ioport:e000-e00f ioport:d000-d0ff irq:169
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:e200-e20f irq:169
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom:0
                   product: LITE-ON LTR-48246S
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 698MB
                   capabilities: packet
              *-cdrom:1
                   product: HL-DT-ST DVDRAM GSA-4167B
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 2426MB
                   capabilities: packet
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e300-e31f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-51-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e400-e41f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-51-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e500-e51f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-51-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:e600-e61f irq:177
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-51-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:fb002000-fb0020ff irq:177
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-51-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-isa UNCLAIMED
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio
             resources: ioport:d400-d4ff irq:201
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 78
             serial: 00:19:db:44:f1:d1
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine ip=192.168.2.4 multicast=yes
             resources: ioport:dc00-dcff iomemory:fb003000-fb0030ff irq:193
     *-pci:1
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz

---

### Post by george182 on 2008-03-29
Heres a link to a screenshot of gparted:

[http://img440.imageshack.us/img440/8653/screenshotwp5.png](http://img440.imageshack.us/img440/8653/screenshotwp5.png)

---

### Post by Pumalite on 2008-03-29
I see no 'recovery' partition at the beginning, Windows is in sda1, it has the boot flag, all in order. The only thing strange that I see is that you have Ubuntu and /swap under two different 'extended' partitions, but you tell me Ubuntu is fine. I can't fight with success. I don't know what to tell you. Someone wiser will come up with the right answer.

---

