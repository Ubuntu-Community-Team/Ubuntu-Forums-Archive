---
title: "Grub error 18???"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by srikar on 2008-03-01
Hey i again started getting this grub error 18.
I hav reinstalled the grub.And even i tried out super grub disk.But  again i am getting grub error??
What may be the problem???? :(

---

### Post by Pumalite on 2008-03-01
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by srikar on 2008-03-01
i've seen it before.Dint work.

---

### Post by Pumalite on 2008-03-01
If you can boot a Live CD, post:
sudo fdisk -lu
And after mounting your partition:
cat /boot/grub/menu.lst

---

### Post by srikar on 2008-03-01
```
srikar@gearup:~$ sudo fdisk -lu
[sudo] password for srikar:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca9fca9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS
/dev/sda2        61432560   312576704   125572072+   f  W95 Ext'd (LBA)
/dev/sda5        61432623   174080339    56323858+   7  HPFS/NTFS
/dev/sda6       174080403   286728119    56323858+   7  HPFS/NTFS
/dev/sda7       286728183   290728304     2000061   82  Linux swap / Solaris
/dev/sda8       290728368   312576704    10924168+  83  Linux

```

---

### Post by Pumalite on 2008-03-01
Where is menu.lst?

---

### Post by srikar on 2008-03-01
```
srikar@gearup:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=69dec955-adbf-457a-9a49-abc23b627aa5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=69dec955-adbf-457a-9a49-abc23b627aa5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,7)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=69dec955-adbf-457a-9a49-abc23b627aa5 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,7)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional by Srikar
root            (hd0,0)
savedefault
makeactive
chainloader     +1


```

---

### Post by Pumalite on 2008-03-01
Is this a clean install or an upgrade?.
Post:
lshw

---

### Post by srikar on 2008-03-01
**its a clean install.**

```
srikar@gearup:~$ sudo lshw
gearup                    
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=81B84010-A15C-11DA-B80C-000C6EFF7219
  *-core
       description: Motherboard
       product: D101GGC
       vendor: Intel Corporation
       physical id: 0
       version: AAD35788-305
       serial: BTGC60769246
     *-firmware
          description: BIOS
          vendor: Award BIOS for Intel
          physical id: 0
          version: GC11010N.86A.0313.2006.0915.1840 (09/15/2006)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) 4 CPU 3.00GHz
          slot: Socket 775
          size: 2800MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl est cid cx16 xtpr cpufreq
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 16KB
             capacity: 16KB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 2MB
             capacity: 2MB
             capabilities: synchronous internal write-back unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: d
             slot: L3 Cache
             capabilities: synchronous internal varies
     *-cpu:1 DISABLED
          description: CPU
          vendor: Null
          physical id: 5
          bus info: cpu@1
          version: Null
          slot: Socket 775
          size: 2800MHz
          capacity: 2800MHz
          capabilities: cpufreq
     *-cache:0 DISABLED
          description: L1 cache
          physical id: a
          slot: L1 Cache
          capabilities: synchronous internal data
     *-cache:1 DISABLED
          description: L2 cache
          physical id: c
          slot: L2 Cache
          capabilities: synchronous internal unified
     *-cache:2 DISABLED
          description: L3 cache
          physical id: e
          slot: L3 Cache
          capabilities: synchronous internal varies
     *-memory
          description: System Memory
          physical id: 32
          slot: System board or motherboard
          size: 1GB
          capacity: 1GB
        *-bank:0
             description: DIMM DDR 200 MHz (5.0 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GB
             width: 64 bits
             clock: 200MHz (5.0ns)
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
        *-ide:0
             description: IDE interface
             product: 437A Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: SCSI Disk
                product: ST3160815AS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 6RA45F1H
                size: 149GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 29GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 119GB
                   capacity: 119GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 53GB
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 53GB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 1953MB
                      capabilities: nofs
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 10GB
        *-ide:1
             description: IDE interface
             product: 4379 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=sata_sil latency=64 module=sata_sil
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 82
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:2
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD writer
                   product: TSSTcorpCD/DVDW SH-W162Z
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: TS00
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: mode=udma2 status=ready
                 *-disc
                      physical id: 0
                      logical name: /dev/hdd
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:16:76:33:c1:a4
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-multimedia
                description: Multimedia audio controller
                product: [SB Live! Value] EMU10k1X
                vendor: Creative Labs
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1X latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1x
srikar@gearup:~$ 
```

---

### Post by Pumalite on 2008-03-01
Have you updated your BIOS?

---

### Post by srikar on 2008-03-01
See i used kubuntu before.I got this grub problem then. So I

> re-installed grub ---> dint work
>did a fresh install(stupid way) ---> dint work
> tried super grub disk ---> dint work
>finally updated intel bios through floppy ---> dint work.
But after all these attempts i get grub error.

So now , i installed ubuntu 64 bit freshly.Still i get this grub error. What may be the problem??:(

---

### Post by Pumalite on 2008-03-01
I can only refer you back to this:

    18 : Selected cylinder exceeds maximum supported by BIOS
        This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

The error message (above)  from the GNU/GRUB manual dates back to the old days when new computers were just beginning to use hard disks that exceeded the 8.45 GB limit.  If you have an old computer that was made back in the late 1990's or earlier, this error message could be absolutely correct. Some computers made as late as 2001 report this error. There are even a few  newer computers that this applies to as well.
The 8.45 GB BIOS hard drive limit was reached when the CHS, (Cylinders, Sectors and Heads) system for plotting the co-ordinates of sectors in the hard disk reached the maximum number of sectors it could address.

Windows users were limited to 8.45 GB by its CHS addressing scheme, but that didn't stop larger hard disks from being invented and used.
A famous Linux method for utilizing larger hard disks than 8.45 GB was to create a separate /boot partition containing GRUB and the Linux kernel entirely within the 8.45 GB limit in the first hard disk.
Linux users could leave room for Windows to be installed within the 8.45 GB limit if they wanted to also have Windows.
As long as the Linux kernel was placed somewhere inside the limit, so the BIOS could 'see' it and boot it, the Linux kernel could manage a file system which was located outside the limit. This was possible because Linux was the first to use LBA addressing. Using LBA addressing means that to the Linux kernel, all the sectors in the hard disk are numbered from 0 to whatever number was necessary. Therefore the hard drive was seen more like a roll of film that could be any number of sectors long.   Linux wasn't restricted to only the first 1024 cylinders that the BIOS could 'see' with the old CHS addressing scheme.
Clever Linux users installed the Linux /root partition outside the limit and in that way they could then make use of much larger hard disks.
Historic Links:
[http://www.win.tue.nl/~aeb/linux/Large-Disk-5.html](http://www.win.tue.nl/~aeb/linux/Large-Disk-5.html)

Now, technology has also passed the 33.8 and 137 GB hard drive limits too, so bear these two in mind as well, when diagnosing error 18 faults.

The GRUB error 18 message could nowadays be referring to the 137 GB BIOS hard disk size limit. This occurs when a machine was made for an 80 or 120 GB hard disk, and someone fits a 137 GB+ hard disk in thier machine without checking if the BIOS supports it.
Windows XP will work because it gets a Microsoft update for coping with that, so the average user is blissfully unaware of the situation until they maybe install Linux on the second half of their hard disk, past the BIOS limit and get GRUB error 18.

Reduce the size of the Linux partition
One way of coping this problem which is reported to have worked for some people is to just try reducing the size of the Linux partition. (So it will be inside the limit). I have participated in one or two Ubuntu Web Forum threads where that seemed to solve the problem. A data partition can be used to fill the rest of the hard drive so it won't be wasted.
I have also read of three separate instances where users claimed that installing Linux '/' (root) on a logical partition instead of a primary partition cleared this problem up for them. (..."Go figure?"..!)

Making a separate /boot partition would probably still be the best answer even with a relatively modern computer if you think you might have the 137 GB hard drive limit.
In the following thread, Ioza had a system that wouldn't boot after and upgrade from Feisty to Gutsy. Here is the link, [http://ubuntuforums.org/showthread.php?t=582855](http://ubuntuforums.org/showthread.php?t=582855)
Apparently, an operating system that is partly inside the hard drive limit may boot for some time as long as the kernel happens to be located within the part of the disk that the BIOS can 'see'.
After an update, if a newer kernel  happens to be placed somewhere outside the limit, the operating system might suddenly become unable to boot (at least by the new kernel), and most users would find it difficult to understand the reason why not.
Here is a great explanation of how that might happen, also already linked to in the above link, [http://www.nabble.com/Grub-tf4291271.html#a12218543](http://www.nabble.com/Grub-tf4291271.html#a12218543)
That might also explain the real reason why resizing the Linux partition to a smaller size has helped some people cure GRUB error 18.  A separate /boot partition could have fixed that and allowed them to make better use of their hard disk.
Here's how to make a separate /boot partition: How to make a separate /boot partition.
Actually, as you will see, re-installing might be easier if it's a new install anyway.

BEFORE YOU DO ANYTHING, check your computer's BIOS date and settings in case your BIOS can be updated instead.

You can check the date of your computer's BIOS by going into 'setup' by pressing the appropriate key during the early stages of booting, something like this: Getting Product Information.

Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented.
2.11 GB or 4095 cylinder limit
3.26 GB or 6322 cylinder limit
4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)

You could check at your motherboard manufacturer's website, (find it with google), to see if there is a newer update for your machine's BIOS available. If so, you can download it and try 'flashing the BIOS'.  That has been reported to have solved this problem.

BIOS settings
If you don't think the BIOS date could be your problem, or there is no more modern BIOS flash available for your BIOS, then at least check and make sure your hard disk is being correctly detected and set up in the BIOS.
Quote:
" I had the same problem. Error 18 and After GRUB. The solution is in the bios.
Put the hard disk detection on auto and not on user. It did the trick for me."

 * Make sure LBA is enabled in your BIOS. If LBA is already enabled, try switching to 'normal' mode and see if that helps.
Remember, the old 8.0 GB limit was overcome when the old CHS (Cylinder, Heads, Sectors) method for dealing with hard disk addressing (disk geometry) was replaced by LBA (Logical Block Addressing). (Numbering each sector of the hard disk starting with the MBR and counting upwards).  

* Check your hard Disk Boot Priority in CMOS.
I am able to produce this error if I have operating systems installed in more than one hard disc in my computer and I either remove my first hard disk or switch the hard disk order around in my BIOS.  Therefore maybe it should be possible to cure this grub error for in some instances by reversing with the hard disc order in the BIOS. You can try, it might help or maybe not, but it's worth a try. I know you can certianly scramble things up that way, so notwithstanding Murphy's Law, it should be possible to unscramble things this way too.
 

 * Check your IDE hard drive cabling and jumper settings 
If your hard drives are connected to your motherboard by IDE cables that have black plugs, or all plugs of the same color then probably you have a non cable select IDE cable.
If you have non cable select IDE cables then you should make sure your first hard disk is jumpered as Master and your second hard disk is jumpered as Slave on your first cable, and the same thing on your second IDE cable, even if one or two of your drives are CD-ROM drives.

If your IDE cable has a blue plug connected to your motherboard and a black plug for the Master of first hard disk and a grey plug for the slave or second hard disk then you should make sure you have your jumpers all set to 'cable select' position.

There are stickers on all hard drives to tell you how to position these jumpers.

Make sure you have the blue plug plugged into the motherboard and the black plug plugged into the master and the grey plug if used, plugged into the slave drive. Please refrain from using the blue plug for a hard drive and a different plug for the motherboard even if cable length or spacial restrictions make this idea seem attractive. It isn't ! A longer IDE cable is very cheap, like about a dollar or so, and sometimes you can even get one thrown in for free with a reasonable purchase from a freindly computer store.

Ways that older Windows computers used to overcome BIOS/Hard drive limits
If you have an older Windows machine, the use of 'Disk Manager' (break the 528 mb IDE barrier!) software is a way for Windows users to utilize a hard disk larger than the machine's BIOS would normally support.

For a slightly more modern example, there is 'OnTrack Disk Manager' (for the 37 GB barrier).

Since those install in the first track of the hard disk, GRUB users should be aware of them in case GRUB's (optional) stage1_5, which installs in the first track of the hard disk, overwrites the disk managment software.  People who know they have software in the first track of their hard disk should consider using LiLo instead.

'On Track Disk Manager' (for the 137 GB limit).
I'm not sure because I can't see it mentioned anywhere in the documentation, but I believe these are still installed somewhere in first track of the hard disk, so if your old computer does have a disk manager, (not needed for Linux), you should be careful when installing GRUB because GRUB will want to install its optional stage1_5 to the first track as well.  I cannot see anywhere where they say it is compatable with Linux either.

As far as I know, the use of disk management software is quite rare these days. Anyway, you would not be likely to need if you install Linux in the second half of your hard disk.

The use of disk manager software might be another reason why a computer user might install Linux and then find that Linux doesn't boot in their computer. It's not GRUB or Linux's fault at all, it's because the user is unaware of the fact that their hard disk is larger than their BIOS can support.

---

### Post by srikar on 2008-03-01
I need an advice from grub specialists so that i fix it soon.I am getting irritated by this grub problem.Help me plzz.

---

### Post by srikar on 2008-03-01
ya i have seen it.I need a fixxxx.

---

### Post by dstew on 2008-03-01
To fix your boot problem you will need to create a **/boot** partition at the front of your drive and re-install Ubuntu. Make the /boot partition 100 Mb, format it ext3, and give it the mount point /boot when you re-install. See the very complete and interesting post by Pumalite. As disks have outpaced BIOS, the issue pops up from time to time. It means your disk is too big for your BIOS, which grub depends on to boot the kernel.

---

### Post by srikar on 2008-03-01
ya i will re-install now and create a boot partition.And tell u da result.

---

### Post by davmt on 2008-03-01
Don't mean to interfere but I have thesame problem. I have a Dell Inspiron Laptop 6400 (so I don't have options for setting hard disk to Auto/Normal Mode, setting cylinders,heads etc. and the Bios is the most updated). I installed Ubuntu and got the Grub error 18, so I resized the Windows XP NTFS partition so I have a 32mb boot ext 2 partition as the first partition of the drive. After having done this im still getting GRUB error 18 :(. Any suggestions guys?

My hard drive is 120GB large, and I'm using 95GB for windows and about 18GB for UBUNTU.

**UPDATE** Important that after affecting these changes, you have to re-install ubuntu.Now it works :)

---

### Post by srikar on 2008-03-02
hey i re-installed ubuntu again.

I made a separate boot partition 150 mb and re-installed grub in it.But still i get the error.How to fix this.When i get this grub error after several restarts i get grub loader, but this isn't good.So many restarts may spoil  the system.Any fix????

---

### Post by srikar on 2008-03-02
anybody there to help me out????

---

### Post by Herman on 2008-03-02
> I made a separate boot partition 150 mb and re-installed grub in it.But still i get the error.How to fix this.When i get this grub error after several restarts i get grub loader, but this isn't good.So many restarts may spoil the system.Any fix????:) Hello srikar,
The information you have already been given is correct,

You need to do more than just make a new partition and re-install GRUB in it, the most important thing is it has to have the Linux kernel in it. It is the Linux kernel that is most important for the BIOS to be able to reach here.

The easy way is to re-install like dstew said, and mount the new partition as /boot during the installation, , it worked for davmt. 
There is another way. You can copy the contents of your /boot directory to the new partition and then edit /etc/fstab to register it as your /boot partition. You will also need to edit /boot/grub/menu.lst, and re-install GRUB. 
Here is a link to a detailed how-to, but I think you will find it easier to just re-install, [How to make a separate /boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition").-contains the Linux kernel, initrd.img and GRUB files.

Good luck with it whatever you do,
Regards, Herman :)

---

### Post by srikar on 2008-03-02
Thanks for ur support.I will do that and post u the results.

---

### Post by dstew on 2008-03-02
> When i get this grub error after several restarts i get grub loader, but this isn't good.This behavior strongly implies that you have a hardware problem. Most often it will be a drive cable is going bad. If you can, try to get a different drive cable in there. 

A plain old software configuration error will usually behave the same way with every boot. However, if one of the wires in a drive ribbon cable is broken, you can get this on-and-off problem. If that is really your problem, reinstalling won't help. Try to get some new drive cables.

---

