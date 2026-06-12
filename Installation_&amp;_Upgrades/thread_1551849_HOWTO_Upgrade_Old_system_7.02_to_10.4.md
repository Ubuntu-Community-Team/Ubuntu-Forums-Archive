---
title: "HOWTO Upgrade Old system 7.02 to 10.4"
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by w2vy on 2010-08-12
The 7 series is too old to have support, I am told that 7.10 is available,
but of course if I try an update I find they are offline.

I have the 10.4 Live CD and it hangs after:

> init: ureadahead-other main process (n) terminated with status 4
init: ureadahead-other main process (n+1) terminated with status 4

* Setting sensors limits

I added boot options:

> nomodeset irqpoll rhgb

My system is dual boot with XP running grub (too old for grub2)

I have no problem wiping the system
(was not booted in ubuntu for 839 days, so what could I need?)

tom

---

### Post by uRock on 2010-08-13
What are your system specs?

---

### Post by w2vy on 2010-08-13
> **uRock said:**
> What are your system specs?

eMachines T1120
> CPU: Intel Celeron Processor 1.20GHz (w/256KB)
Operating System: Genuine Microsoft Windows XP Home Edition
Chipset: Intel 810e chipset
Memory: 512MB SDRAM (PC133)
Hard Drive: 40GB HDD
Optical Drive: Built-in 16x Max. CD-RW Drive; 3.5&#8243; 1.44MB FDD
Video: Intel Direct AGP 3D (810e shared)
Sound: AC ’97 Audio
Modem: 56K ITU v.92-ready Fax/Modem
Peripherals: Keyboard, Mouse, Stereo Speakers
Ports/Other: 3 USB ports (1 on front), 1 Serial, 1 Parallel, 2 PS/2, Audio In & Out; 1 Midi/Game on front, Mic-In & Head Phone jack on front

This may be of more interest:

> tom@w2vy:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:0e.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:0e.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
tom@w2vy:~$ 


> /dev/sda1             40957684  25597448  15360236  63% /media/sda1
/dev/sda2             56214080  27186292  29027788  49% /media/sda2
/dev/sda3               101105     10049     85835  11% /media/sda3
/dev/sda5             36702396   2008464  32799472   6% /media/sda5
/dev/sda6             20161172   3481328  15655704  19% /

sda1 ntfs (XP partition)
sda2 vfat shared data between xp and ubuntu
sda3-6 are ext3

System is 7.04 not 7.02

anything else of interest?

tom

---

### Post by Rubi1200 on 2010-08-13
You have an Intel chipset Intel 810e; see here for more details:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

You need to boot the CD with the i915.modeset=1 parameter:

[http://ubuntuforums.org/showpost.php?p=9239795&postcount=19](http://ubuntuforums.org/showpost.php?p=9239795&postcount=19)

---

### Post by w2vy on 2010-08-13
Not much changes with any different settings.

I do see an odd error while it is running:

> Buffer: I/O error, dev sr0, logical block 358116
[sr0] Unhandled sense code
[sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[sr0] Sense Key : Hardware Error [current]
[sr0] Add. Sense: Timeout on logical unit
[sr0] CDB: Read(10): 28 00 00 05 76 e4 00 00 10 00

It also happens on LBA 358114 and 358115

I assume it recovers, since it stops happening.

I am not sure where to go next.

In the category of 'it could not hurt' here is RESULTS.txt from bootinfoscript

Thanks,
tom
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 81915435.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora Core release 6 (Zod) 
                       Kernel on an
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 7.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   194,563,214   112,647,780   7 HPFS/NTFS
/dev/sda3         194,563,215   194,772,059       208,845  83 Linux
/dev/sda4         194,772,060   312,576,704   117,804,645   5 Extended
/dev/sda5         194,772,123   270,550,664    75,778,542  83 Linux
/dev/sda6         270,550,728   311,516,414    40,965,687  83 Linux
/dev/sda7         311,516,478   312,576,704     1,060,227  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1                                               ntfs                                     
/dev/sda2        4639-0D22                              vfat       data                          
/dev/sda3        d398a828-19d3-4bec-b789-a369cedfb2b5   ext3       /boot                         
/dev/sda5        3e7457f9-31f6-404a-9517-10a317460836   ext3       /                             
/dev/sda6        7c45dc44-efe9-49f9-af13-c44a85c494de   ext3                                     
/dev/sda7        e4540a55-0539-4a36-976b-98d3fb0d0e43   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda1        /media/sda1              ntfs       (rw,nls=utf8,umask=007,gid=46)
/dev/sda2        /media/sda2              vfat       (rw,utf8,umask=007,gid=46)
/dev/sda3        /media/sda3              ext3       (rw)
/dev/sda5        /media/sda5              ext3       (rw)
/dev/scd0        /media/cdrom0            iso9660    (ro,noexec,nosuid,nodev,user=tom)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=5

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=5

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn


============================= sda3/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/hda5
#          initrd /initrd-version.img
#boot=/dev/hda
default=0
timeout=5
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora Core (2.6.18-1.2798.fc6)
	root (hd0,2)
	kernel /vmlinuz-2.6.18-1.2798.fc6 ro root=LABEL=/ rhgb quiet
	initrd /initrd-2.6.18-1.2798.fc6.img
title Other
	rootnoverify (hd0,0)
	chainloader +1

=================== sda3: Location of files loaded by Grub: ===================


  99.6GB: grub/grub.conf
  99.6GB: grub/menu.lst
  99.6GB: grub/stage2
  99.6GB: initrd-2.6.18-1.2798.fc6.img
  99.6GB: vmlinuz-2.6.18-1.2798.fc6

=============================== sda5/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
LABEL=SWAP-hda7         swap                    swap    defaults        0 0

=========================== sda6/boot/grub/menu.lst: ===========================

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
default		6

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
# kopt=root=UUID=7c45dc44-efe9-49f9-af13-c44a85c494de ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7c45dc44-efe9-49f9-af13-c44a85c494de ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7c45dc44-efe9-49f9-af13-c44a85c494de ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7c45dc44-efe9-49f9-af13-c44a85c494de ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7c45dc44-efe9-49f9-af13-c44a85c494de ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Fedora Core (2.6.18-1.2798.fc6) (on /dev/sda5)
root		(hd0,2)
kernel		/vmlinuz-2.6.18-1.2798.fc6 ro root=LABEL=/ rhgb quiet 
initrd		/initrd-2.6.18-1.2798.fc6.img
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=7c45dc44-efe9-49f9-af13-c44a85c494de /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8AB40311B4030005 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4639-0D22  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=d398a828-19d3-4bec-b789-a369cedfb2b5 /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=3e7457f9-31f6-404a-9517-10a317460836 /media/sda5     ext3    defaults        0       2
# /dev/sda7
UUID=e4540a55-0539-4a36-976b-98d3fb0d0e43 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda6: Location of files loaded by Grub: ===================


 138.9GB: boot/grub/menu.lst
 138.8GB: boot/grub/stage2
 138.9GB: boot/initrd.img-2.6.20-15-generic
 138.8GB: boot/initrd.img-2.6.20-15-generic.bak
 138.9GB: boot/initrd.img-2.6.20-16-generic
 138.8GB: boot/initrd.img-2.6.20-16-generic.bak
 138.9GB: boot/vmlinuz-2.6.20-15-generic
 138.8GB: boot/vmlinuz-2.6.20-16-generic
 138.9GB: initrd.img
 138.9GB: initrd.img.old
 138.8GB: vmlinuz
 138.9GB: vmlinuz.old
```

---

### Post by mörgæs on 2010-08-14
Can you run a live 9.10?
If yes, have you tried installing it?

---

### Post by w2vy on 2010-08-14
> **mörgæs said:**
> Can you run a live 9.10?
If yes, have you tried installing it?

I tried it with various combinations of i915.modeset=1 and rhgb and nomodeset
with no luck... downloading 8.04.4 now

The RHGB is in my menu.lst already

It only costs a CD and may be an interesting data point...

tom

---

### Post by Rubi1200 on 2010-08-14
Considering your specs. you might want to think about trying a "lighter" version such as Xubuntu or Lubuntu. 
Another distro that comes to mind is Puppy Linux.

---

### Post by w2vy on 2010-08-14
> **Rubi1200 said:**
> Considering your specs. you might want to think about trying a "lighter" version such as Xubuntu or Lubuntu. 
Another distro that comes to mind is Puppy Linux.

Well 8.04.4 works in Live mode.

A lighter version sounds like a VERY good idea (512MB ram!)

tom

---

### Post by mörgæs on 2010-08-14
Then you could go for a minimal Ubuntu. I have good experience with these.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

It is a long thread, but worth reading.

---

### Post by w2vy on 2010-08-14
Well I tried Xubuntu 10.4 and it acted the same as Ubuntu 10.4.
No surprise since they are the same core.

Of course since 8.04.4 did boot, maybe I should have tried that version.

I would likely be able to upgrade to 9.02 and then to 10.4 but I would
also still have the same issue... but it may be easier to debug with a running system vs a Live CD.

Thoughts?
----
Ok, progress... Xubuntu 8.04.1 loaded and updated to 8.10

BAM now I have issues.. now to find the solution that many have already discovered...
I do have i915.modeset=1 already

windows manager comes up, see mouce cursor and background filled in... then it does

I should be able to find some problem in the logs.. since it is an installed version vs a Live CD

tom

---

### Post by w2vy on 2010-08-15
Well desktop appears, cursor is X and a ball, it almost starts spinning and then we crash...

Xorg.0.log

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux tom-desktop 2.6.27-17-generic #1 SMP Fri Mar 12 03:09:00 UTC 2010 i686
Build Date: 09 March 2009  10:48:54AM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 15 19:43:32 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI: (0@0:1:0) Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller rev 3, Mem @ 0xe4000000/0, 0xe0000000/0
(--) PCI:*(0@1:14:0) ATI Technologies Inc RV280 [Radeon 9200 PRO] rev 1, Mem @ 0xe8000000/0, 0xe0100000/0, I/O @ 0x00002800/0, BIOS @ 0x????????/131072
(--) PCI: (0@1:14:1) ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) rev 1, Mem @ 0xf0000000/0, 0xe0110000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610, ATI RV670,
	ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE, ATI Radeon HD 3470,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI FireMV 2450, ATI FireMV 2260,
	ATI FireMV 2260, ATI ATI Radeon HD 3600 Series,
	ATI ATI Radeon HD 3650 AGP, ATI ATI Radeon HD 3600 PRO,
	ATI ATI Radeon HD 3600 XT, ATI ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics
(II) Primary Device is: PCI 01@00:0e:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000e0100000: size 64KB
(II) RADEON(0): PCI bus 1 card 14 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon 9250 5960 (AGP)" (ChipID = 0x5960)
(--) RADEON(0): Linear framebuffer at 0x00000000e8000000
(II) RADEON(0): PCI card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:0e.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:0e.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.29.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2048x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 200.000000, mclk: 240.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=20000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-0x60, DACType-1, TMDSType-1, ConnectorType-1
(II) RADEON(0): Port1: DDCType-0x64, DACType-2, TMDSType-1, ConnectorType-2
(II) RADEON(0): Port5: DDCType-0x0, DACType-2, TMDSType-0, ConnectorType-5
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC PAL PAL-M NTSC-J 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- 0x64
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "NEC", prod id 24005
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x960"x85.0  149.43  1280 1376 1512 1744  960 961 964 1008 -hsync +vsync (85.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.59  1920 2064 2272 2624  1440 1441 1444 1490 -hsync +vsync (89.4 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: NEC  Model: 5dc5  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 26
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 37  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.629 redY: 0.330   greenX: 0.281 greenY: 0.600
(II) RADEON(0): blueX: 0.148 blueY: 0.068   whiteX: 0.283 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@87Hz (interlaced)
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #4: hsize: 1280  vsize 960  refresh: 85  vid: 22913
(II) RADEON(0): #5: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  356 x 267 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 55 V max: 160 Hz, H min: 31 H max: 96 kHz, PixClock max 240 MHz
(II) RADEON(0): Monitor name: AccuSync 90
(II) RADEON(0): Serial No: 2601426TA
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0038a3c55d01010101
(II) RADEON(0): 	1a0c01030c251b78ea2228a154489926
(II) RADEON(0): 	11484cffff80315945596159714f8159
(II) RADEON(0): 	8199a94fd140863d00c05100304040a0
(II) RADEON(0): 	1300640b1100001e000000fd0037a01f
(II) RADEON(0): 	6018000a202020202020000000fc0041
(II) RADEON(0): 	63637553796e632039300a20000000ff
(II) RADEON(0): 	003236303134323654410a20202000f0
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID vendor "NEC", prod id 24005
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "640x480"x85.0   35.71  640 672 736 832  480 481 484 505 -hsync +vsync (42.9 kHz)
(II) RADEON(0): Modeline "800x600"x85.0   56.55  800 840 928 1056  600 601 604 630 -hsync +vsync (53.5 kHz)
(II) RADEON(0): Modeline "1024x768"x85.0   94.39  1024 1088 1200 1376  768 769 772 807 -hsync +vsync (68.6 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) RADEON(0): Modeline "1280x960"x85.0  149.43  1280 1376 1512 1744  960 961 964 1008 -hsync +vsync (85.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x85.0  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -hsync +vsync (91.4 kHz)
(II) RADEON(0): Modeline "1600x1200"x75.0  205.99  1600 1720 1896 2192  1200 1201 1204 1253 -hsync +vsync (94.0 kHz)
(II) RADEON(0): Modeline "1920x1440"x60.0  234.59  1920 2064 2272 2624  1440 1441 1444 1490 -hsync +vsync (89.4 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: NEC  Model: 5dc5  Serial#: 16843009
(II) RADEON(0): Year: 2002  Week: 26
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite
(II) RADEON(0): Max Image Size [cm]: horiz.: 37  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.629 redY: 0.330   greenX: 0.281 greenY: 0.600
(II) RADEON(0): blueX: 0.148 blueY: 0.068   whiteX: 0.283 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@87Hz (interlaced)
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #4: hsize: 1280  vsize 960  refresh: 85  vid: 22913
(II) RADEON(0): #5: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #6: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #7: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 157.5 MHz   Image Size:  356 x 267 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) RADEON(0): Ranges: V min: 55 V max: 160 Hz, H min: 31 H max: 96 kHz, PixClock max 240 MHz
(II) RADEON(0): Monitor name: AccuSync 90
(II) RADEON(0): Serial No: 2601426TA
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0038a3c55d01010101
(II) RADEON(0): 	1a0c01030c251b78ea2228a154489926
(II) RADEON(0): 	11484cffff80315945596159714f8159
(II) RADEON(0): 	8199a94fd140863d00c05100304040a0
(II) RADEON(0): 	1300640b1100001e000000fd0037a01f
(II) RADEON(0): 	6018000a202020202020000000fc0041
(II) RADEON(0): 	63637553796e632039300a20000000ff
(II) RADEON(0): 	003236303134323654410a20202000f0
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "NEC", prod id 24005
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-0:ddc2" removed.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (370, 270) mm
(**) RADEON(0): DPI set to (115, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 4.1
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit e8000000 0 0
```

end of syslog

```
Aug 15 19:43:31 tom-desktop nm-system-settings:    SCPlugin-Ifupdown: init!
Aug 15 19:43:31 tom-desktop nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
Aug 15 19:43:31 tom-desktop nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
Aug 15 19:43:31 tom-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_04_5a_69_01_14, iface: eth0): not well known
Aug 15 19:43:31 tom-desktop nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_06_4f_81_1f_c2, iface: wlan0): not well known
Aug 15 19:43:31 tom-desktop nm-system-settings:    SCPlugin-Ifupdown: end _init.
Aug 15 19:43:31 tom-desktop nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Aug 15 19:43:31 tom-desktop nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Aug 15 19:43:31 tom-desktop nm-system-settings:    SCPlugin-Ifupdown: (163684640) ... get_connections.
Aug 15 19:43:31 tom-desktop nm-system-settings:    SCPlugin-Ifupdown: (163684640) ... get_connections (managed=false): return empty list.
Aug 15 19:43:31 tom-desktop nm-system-settings:    Ifupdown: get unmanaged devices count: 0
Aug 15 19:43:32 tom-desktop hal_lpadmin: hal_lpadmin triggered by usblp kernel module
Aug 15 19:43:32 tom-desktop hal_lpadmin: Using device ID from HAL database entry
Aug 15 19:43:32 tom-desktop hal_lpadmin: hal_lpadmin triggered by low-level USB device
Aug 15 19:43:32 tom-desktop hal_lpadmin: Polling device ID from the printer
Aug 15 19:43:32 tom-desktop hal_lpadmin: Device 001:007: /org/freedesktop/Hal/devices/usb_device_43d_7b_0487055_if0
Aug 15 19:43:32 tom-desktop hal_lpadmin: Stopping hal_lpadmin triggered by low-level USB device
Aug 15 19:43:32 tom-desktop hal_lpadmin: add
Aug 15 19:43:32 tom-desktop hal_lpadmin: URIs: ['usb://Lexmark%20/X1100%20Series', 'hal:///org/freedesktop/Hal/devices/usb_device_43d_7b_0487055_if0_printer_noserial']
Aug 15 19:43:32 tom-desktop hal_lpadmin: HPLIP Fax URIs: None
Aug 15 19:43:32 tom-desktop hal_lpadmin: Not adding printer: X1100_Series already exists
Aug 15 19:43:32 tom-desktop acpid: client connected from 4779[0:0]
Aug 15 19:43:32 tom-desktop anacron[4811]: Anacron 2.3 started on 2010-08-15
Aug 15 19:43:32 tom-desktop anacron[4811]: Normal exit (0 jobs run)
Aug 15 19:43:32 tom-desktop kernel: [   35.791911] pci 0000:01:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 15 19:43:33 tom-desktop kernel: [   36.250842] Linux agpgart interface v0.103
Aug 15 19:43:33 tom-desktop kernel: [   36.300766] [drm] Initialized drm 1.1.0 20060810
Aug 15 19:43:33 tom-desktop kernel: [   36.323863] [drm] Initialized radeon 1.29.0 20080528 on minor 0
Aug 15 19:43:33 tom-desktop /usr/sbin/cron[4869]: (CRON) INFO (pidfile fd = 3)
Aug 15 19:43:33 tom-desktop /usr/sbin/cron[4872]: (CRON) STARTUP (fork ok)
Aug 15 19:43:33 tom-desktop /usr/sbin/cron[4872]: (CRON) INFO (Running @reboot jobs)

```

End of /var/log/messages

```
Aug 15 19:43:27 tom-desktop kernel: [   20.872102] intel8x0_measure_ac97_clock: measured 54328 usecs
Aug 15 19:43:27 tom-desktop kernel: [   20.872179] intel8x0: clocking to 48000
Aug 15 19:43:27 tom-desktop kernel: [   25.419151] lp0: using parport0 (interrupt-driven).
Aug 15 19:43:27 tom-desktop kernel: [   25.668946] Adding 530104k swap on /dev/sda7.  Priority:-1 extents:1 across:530104k
Aug 15 19:43:27 tom-desktop kernel: [   26.086102] EXT3 FS on sda5, internal journal
Aug 15 19:43:27 tom-desktop kernel: [   27.252897] type=1505 audit(1281915804.188:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3794
Aug 15 19:43:27 tom-desktop kernel: [   27.254022] type=1505 audit(1281915804.188:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3794
Aug 15 19:43:27 tom-desktop kernel: [   27.443695] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 15 19:43:27 tom-desktop kernel: [   28.928319] ACPI: WMI: Mapper loaded
Aug 15 19:43:27 tom-desktop kernel: [   30.740633] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Aug 15 19:43:27 tom-desktop kernel: [   30.807984] apm: BIOS not found.
Aug 15 19:43:27 tom-desktop kernel: [   30.980702] ppdev: user-space parallel port driver
Aug 15 19:43:31 tom-desktop kernel: [   34.329719] Bluetooth: Core ver 2.13
Aug 15 19:43:31 tom-desktop kernel: [   34.333481] NET: Registered protocol family 31
Aug 15 19:43:31 tom-desktop kernel: [   34.333495] Bluetooth: HCI device and connection manager initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.333505] Bluetooth: HCI socket layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.421244] Bluetooth: L2CAP ver 2.11
Aug 15 19:43:31 tom-desktop kernel: [   34.421256] Bluetooth: L2CAP socket layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.483205] Bluetooth: RFCOMM socket layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.483984] Bluetooth: RFCOMM TTY layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.484001] Bluetooth: RFCOMM ver 1.10
Aug 15 19:43:31 tom-desktop kernel: [   34.502379] Bluetooth: SCO (Voice Link) ver 0.6
Aug 15 19:43:31 tom-desktop kernel: [   34.502402] Bluetooth: SCO socket layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.575509] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 15 19:43:31 tom-desktop kernel: [   34.575524] Bluetooth: BNEP filters: protocol multicast
Aug 15 19:43:31 tom-desktop kernel: [   34.655303] Bridge firewalling registered
Aug 15 19:43:32 tom-desktop kernel: [   35.791911] pci 0000:01:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 15 19:43:33 tom-desktop kernel: [   36.250842] Linux agpgart interface v0.103
Aug 15 19:43:33 tom-desktop kernel: [   36.300766] [drm] Initialized drm 1.1.0 20060810
Aug 15 19:43:33 tom-desktop kernel: [   36.323863] [drm] Initialized radeon 1.29.0 20080528 on minor 0

```

end of kern.log

```
Aug 15 19:43:27 tom-desktop kernel: [   20.201449] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 15 19:43:27 tom-desktop kernel: [   20.201568] Intel ICH 0000:00:1f.5: setting latency timer to 64
Aug 15 19:43:27 tom-desktop kernel: [   20.872102] intel8x0_measure_ac97_clock: measured 54328 usecs
Aug 15 19:43:27 tom-desktop kernel: [   20.872179] intel8x0: clocking to 48000
Aug 15 19:43:27 tom-desktop kernel: [   25.419151] lp0: using parport0 (interrupt-driven).
Aug 15 19:43:27 tom-desktop kernel: [   25.668946] Adding 530104k swap on /dev/sda7.  Priority:-1 extents:1 across:530104k
Aug 15 19:43:27 tom-desktop kernel: [   26.086102] EXT3 FS on sda5, internal journal
Aug 15 19:43:27 tom-desktop kernel: [   27.252897] type=1505 audit(1281915804.188:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3794
Aug 15 19:43:27 tom-desktop kernel: [   27.254022] type=1505 audit(1281915804.188:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3794
Aug 15 19:43:27 tom-desktop kernel: [   27.443695] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 15 19:43:27 tom-desktop kernel: [   28.928319] ACPI: WMI: Mapper loaded
Aug 15 19:43:27 tom-desktop kernel: [   30.740633] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Aug 15 19:43:27 tom-desktop kernel: [   30.807984] apm: BIOS not found.
Aug 15 19:43:27 tom-desktop kernel: [   30.980702] ppdev: user-space parallel port driver
Aug 15 19:43:31 tom-desktop kernel: [   34.329719] Bluetooth: Core ver 2.13
Aug 15 19:43:31 tom-desktop kernel: [   34.333481] NET: Registered protocol family 31
Aug 15 19:43:31 tom-desktop kernel: [   34.333495] Bluetooth: HCI device and connection manager initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.333505] Bluetooth: HCI socket layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.421244] Bluetooth: L2CAP ver 2.11
Aug 15 19:43:31 tom-desktop kernel: [   34.421256] Bluetooth: L2CAP socket layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.483205] Bluetooth: RFCOMM socket layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.483984] Bluetooth: RFCOMM TTY layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.484001] Bluetooth: RFCOMM ver 1.10
Aug 15 19:43:31 tom-desktop kernel: [   34.502379] Bluetooth: SCO (Voice Link) ver 0.6
Aug 15 19:43:31 tom-desktop kernel: [   34.502402] Bluetooth: SCO socket layer initialized
Aug 15 19:43:31 tom-desktop kernel: [   34.575509] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 15 19:43:31 tom-desktop kernel: [   34.575524] Bluetooth: BNEP filters: protocol multicast
Aug 15 19:43:31 tom-desktop kernel: [   34.655303] Bridge firewalling registered
Aug 15 19:43:32 tom-desktop kernel: [   35.791911] pci 0000:01:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 15 19:43:33 tom-desktop kernel: [   36.250842] Linux agpgart interface v0.103
Aug 15 19:43:33 tom-desktop kernel: [   36.300766] [drm] Initialized drm 1.1.0 20060810
Aug 15 19:43:33 tom-desktop kernel: [   36.323863] [drm] Initialized radeon 1.29.0 20080528 on minor 0


```

---

### Post by mörgæs on 2010-08-16
Best is forgetting everything about upgrades. They make more trouble than benefit.

Since you are doing a fresh install anyway, simply pick the one you want and install it.

---

### Post by w2vy on 2010-08-16
> **mörgæs said:**
> Best is forgetting everything about upgrades. They make more trouble than benefit.

Since you are doing a fresh install anyway, simply pick the one you want and install it.

Go check the first post of this thread...

I started with 10.4 Ubuntu with Live CD not working.

I now have a collection of Ubuntu 8.04.4, 9.10, 10.4
and Xubuntu 10.4 and 8.04.1

The only ones that work in Live Mode are 8.04.x

I am set up for triple boot, Windows XP, Ubuntu 7.04 and right now Xubuntu 8.04.1

I am wondering if I should try to go back to my Integrated video card and blacklist my ATI Card... I am not sure why I installed
it so many years ago... I am sure it was for Windows Games or something for the kids...

I'd like to keep it for now, since XP and 7.04 work fine with it.

tom

---

### Post by mörgæs on 2010-08-16
Sorry, I was not being precise. It was not my intention to make fun of your attempts.

Have you tried the alternative (text-based) installer?

---

### Post by w2vy on 2010-08-16
> **mörgæs said:**
> Sorry, I was not being precise. It was not my intention to make fun of your attempts.

Have you tried the alternative (text-based) installer?

I did not take it that way.

Well I could try loading a 10.4 version via text method, but I am not
sure how much more info I will be able to provide.

I have nothing to lose! (just some time)

The god? bad? news is that removing the ATI card and using the internal graphics did not change the symptoms much...

There may be an issue yet to be fixed...

I a neighbor had a x64 dual core 2ghz w/2gb system that did not work with
6.x and I held on to it and I ended up trying again with 8.x and it worked LOL

I heard that 10.7 is due out any, humm, ooops maybe that would be 10.8 (10.9 ? :lolflag:)

off to try xubuntu 10.4

tom

2 hours later

Downloaded the ALT CD (Go Figure the Live CD does it all, except Text install LOL)

Well in did install... but no video... I will debug that in the morning....

The 8.04.1 Xubuntu Lve CD will come in handy for that!

tom

---

### Post by w2vy on 2010-08-17
I want to say you guys put in a lot of time helping those of us with problems!

THANKS!!! :popcorn:

--

Ok I can log in the console (text mode)

So the system works, now to get X running

I did X -configure and X -config xorg.conf.new

It loads and seems to crash, well the keyboard ends up not working.

I say this because after the system sits for a while I try CTL-ALT-DEL and the system does not reboot.

Maybe I should enable sshd so I can log in from another system to watch log files... etc

xorg.0.log

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux tom-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=c2630ff5-b6b2-4068-9820-e98a7b319f57 ro i915.modeset=1
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 17 08:37:57 2010
(++) Using config file: "/home/tom/xorg.conf.new"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:0:1:0) 8086:7125:109f:7148 Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller rev 3, Mem @ 0xf8000000/67108864, 0xf4000000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:01:0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(==) intel(0): Depth 16, (==) framebuffer bpp 16
(==) intel(0): RGB weight 565
(==) intel(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 1024 kB
(II) intel(0): VESA VBE OEM: Intel(R) 810, Intel(R) 815 Chipset Video BIOS
(II) intel(0): VESA VBE OEM Software Rev: 36.56
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(R) 810, Intel(R) 815 Chipset
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level 2
(II) intel(0): VESA VBE DDC transfer in appr. 1 sec.
(II) intel(0): VESA VBE DDC read successfully
(II) intel(0): Manufacturer: NEC  Model: 5dc5  Serial#: 16843009
(II) intel(0): Year: 2002  Week: 26
(II) intel(0): EDID Version: 1.3
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) intel(0): Sync:  Separate  Composite
(II) intel(0): Max Image Size [cm]: horiz.: 37  vert.: 27
(II) intel(0): Gamma: 2.20
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.629 redY: 0.330   greenX: 0.281 greenY: 0.600
(II) intel(0): blueX: 0.148 blueY: 0.068   whiteX: 0.283 whiteY: 0.297
(II) intel(0): Supported established timings:
(II) intel(0): 720x400@70Hz
(II) intel(0): 720x400@88Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@67Hz
(II) intel(0): 640x480@72Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@56Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@72Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 832x624@75Hz
(II) intel(0): 1024x768@87Hz (interlaced)
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@70Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): 1280x1024@75Hz
(II) intel(0): 1152x864@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported standard timings:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #4: hsize: 1280  vsize 960  refresh: 85  vid: 22913
(II) intel(0): #5: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) intel(0): #6: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) intel(0): #7: hsize: 1920  vsize 1440  refresh: 60  vid: 16593
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 157.5 MHz   Image Size:  356 x 267 mm
(II) intel(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) intel(0): Ranges: V min: 55 V max: 160 Hz, H min: 31 H max: 96 kHz, PixClock max 240 MHz
(II) intel(0): Monitor name: AccuSync 90
(II) intel(0): Serial No: 2601426TA
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0038a3c55d01010101
(II) intel(0): 	1a0c01030c251b78ea2228a154489926
(II) intel(0): 	11484cffff80315945596159714f8159
(II) intel(0): 	8199a94fd140863d00c05100304040a0
(II) intel(0): 	1300640b1100001e000000fd0037a01f
(II) intel(0): 	6018000a202020202020000000fc0041
(II) intel(0): 	63637553796e632039300a20000000ff
(II) intel(0): 	003236303134323654410a20202000f0
(II) intel(0): EDID vendor "NEC", prod id 24005
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1280x960"x0.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(II) intel(0): Modeline "1600x1200"x0.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(II) intel(0): Modeline "1920x1440"x0.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 -hsync +vsync (90.0 kHz)
(--) intel(0): Chipset: "i810e"
(--) intel(0): Linear framebuffer at 0xF8000000
(--) intel(0): IO registers at addr 0xF4000000
(II) intel(0): Kernel reported 108544 total, 1 used
(II) intel(0): I810CheckAvailableMemory: 434172k available
(==) intel(0): Will alloc AGP framebuffer: 24576 kByte
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(II) intel(0): Monitor0: Using hsync range of 31.00-96.00 kHz
(II) intel(0): Monitor0: Using vrefresh range of 55.00-160.00 Hz
(II) intel(0): Monitor0: Using maximum pixel clock of 240.00 MHz
(II) intel(0): Estimated virtual size for aspect ratio 1.3704 is 1920x1440
(II) intel(0): Clock range:   9.50 to 163.00 MHz
(II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (unknown reason)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using driver mode "1024x768" (unknown reason)
(II) intel(0): Not using driver mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using driver mode "1920x1440" (bad mode clock/interlace/doublescan)
(WW) intel(0): Shrinking virtual size estimate from 1920x1440 to 1600x1200
(--) intel(0): Virtual size is 1600x1200 (pitch 1600)
(**) intel(0): *Default mode "1600x1200": 162.0 MHz, 75.0 kHz, 60.0 Hz
(II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(**) intel(0): *Default mode "1680x1050": 146.2 MHz, 65.3 kHz, 60.0 Hz
(II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(**) intel(0): *Default mode "1400x1050": 155.8 MHz, 81.5 kHz, 74.8 Hz
(II) intel(0): Modeline "1400x1050"x74.8  155.80  1400 1464 1784 1912  1050 1052 1064 1090 +hsync +vsync (81.5 kHz)
(**) intel(0): *Default mode "1400x1050": 145.1 MHz, 76.5 kHz, 70.0 Hz
(II) intel(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(**) intel(0): *Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
(II) intel(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(**) intel(0): *Driver mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(**) intel(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) intel(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) intel(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(**) intel(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) intel(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) intel(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
(II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) intel(0): *Driver mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(**) intel(0): *Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) intel(0): Modeline "1280x960"x85.0  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync (85.9 kHz)
(**) intel(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) intel(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) intel(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) intel(0): *Default mode "1152x864": 143.5 MHz, 91.5 kHz, 100.0 Hz
(II) intel(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 -hsync +vsync (91.5 kHz)
(**) intel(0): *Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) intel(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(**) intel(0): *Default mode "1152x864": 119.7 MHz, 77.1 kHz, 85.0 Hz
(II) intel(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(**) intel(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) intel(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) intel(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) intel(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) intel(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) intel(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) intel(0): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) intel(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) intel(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) intel(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) intel(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) intel(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) intel(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) intel(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) intel(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) intel(0): *Driver mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) intel(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) intel(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) intel(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) intel(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) intel(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) intel(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) intel(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) intel(0): *Driver mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) intel(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) intel(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) intel(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) intel(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) intel(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) intel(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) intel(0): *Driver mode "720x400": 35.5 MHz, 39.4 kHz, 87.8 Hz
(II) intel(0): Modeline "720x400"x87.8   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(**) intel(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) intel(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) intel(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) intel(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) intel(0): Display dimensions: (370, 270) mm
(**) intel(0): DPI set to (109, 112)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) intel(0): page flipping disabled
(II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:01.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 14, (OK)
drmOpenByBusid: drmOpenMinor returns 14
drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
(II) [drm] loaded kernel module for "i810" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer handle = 0xf8000000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [drm] Registers = 0xf4000000
(II) intel(0): [agp] dcacheHandle : 0x0
(II) intel(0): [agp] GART: no dcache memory found
(II) intel(0): [agp] Bound backbuffer memory
(II) intel(0): [agp] Bound depthbuffer memory
(II) intel(0): [agp] Bound System Texture Memory
(II) intel(0): [agp] GART: Allocated 4K for mouse cursor image
(II) intel(0): [agp] GART: Allocated 16K for ARGB mouse cursor image
(II) intel(0): Adding 384 scanlines for pixmap caching
(II) intel(0): Allocated Scratch Memory
(II) intel(0): [dri] Buffer map : d9b000
(II) intel(0): [drm] added 256 4096 byte DMA buffers
(II) intel(0): [drm] Init v1.4 interface.
(II) intel(0): [drm] dma control initialized, using IRQ -22
(II) intel(0): [dri] visual configs initialized.
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Setting dot clock to 162.0 MHz [ 0x19 0x6 0x10 ] [ 27 8 1 ]
(II) intel(0): chose watermark 0x22416000: (tab.freq 162.0)
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		20 128x128 slots
		4 256x256 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(**) intel(0): DPMS enabled
(II) intel(0): [DRI] installation complete
(II) intel(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 15, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:01.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 15, (OK)
drmOpenByBusid: drmOpenMinor returns 15
drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
(II) AIGLX: Loaded and initialized /usr/lib/dri/i810_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-A56E63F16102D5B0903F3FDBDC0FB5D20109AAF6.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Microsoft Basic Optical Mouse (/dev/input/event4)
(**) Microsoft Basic Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Microsoft Basic Optical Mouse: always reports core events
(**) Microsoft Basic Optical Mouse: Device: "/dev/input/event4"
(II) Microsoft Basic Optical Mouse: Found 3 mouse buttons
(II) Microsoft Basic Optical Mouse: Found scroll wheel(s)
(II) Microsoft Basic Optical Mouse: Found relative axes
(II) Microsoft Basic Optical Mouse: Found x and y relative axes
(II) Microsoft Basic Optical Mouse: Configuring as mouse
(**) Microsoft Basic Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Microsoft Basic Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Basic Optical Mouse" (type: MOUSE)
(II) Microsoft Basic Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Microsoft Basic Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_variant" "intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Microsoft Basic Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xe0732000 at 0xb78e1000
(II) intel(0): [drm] Closed DRM master.
 ddxSigGiveUp: Closing log

```

xorg.config.new

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "dbe"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  370   270	# mm
	Identifier   "Monitor0"
	VendorName   "NEC"
	ModelName    "AccuSync 90"
	HorizSync    31.0 - 96.0
	VertRefresh  55.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82810E DC-133 (CGC) Chipset Graphics Controller"
	BusID       "PCI:0:1:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

lsmod

```
Module                  Size  Used by
ipv6                  267780  8 
i810                   19968  2 
drm                    82452  3 i810
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
lp                     12324  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8712  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
ac                      6916  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
snd_intel8x0           35356  1 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_mpu401              9448  0 
snd_mpu401_uart         9728  1 snd_mpu401
snd_seq_dummy           4868  0 
container               5632  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_i810                5636  0 
snd                    56996  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                  9232  0 
intel_agp              25492  1 
i2c_algo_bit            7300  1 i2c_i810
parport_pc             36260  1 
shpchp                 34452  0 
iTCO_wdt               13092  0 
evdev                  13056  3 
agpgart                34760  3 drm,intel_agp
i2c_core               24832  2 i2c_i810,i2c_algo_bit
parport                37832  3 ppdev,lp,parport_pc
pci_hotplug            30880  1 shpchp
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
analog                 13600  0 
gameport               16008  1 analog
pcspkr                  4224  0 
battery                14212  0 
squashfs               49160  1 
loop                   18948  2 
unionfs                76752  1 
isofs                  36388  1 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
nls_iso8859_1           4992  1 
nls_cp437               6656  2 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
libusual               19108  1 usb_storage
usbhid                 31872  0 
hid                    38784  1 usbhid
sg                     36880  0 
sr_mod                 17956  1 
cdrom                  37408  1 sr_mod
sd_mod                 30720  5 
floppy                 59588  0 
tulip                  53536  0 
uhci_hcd               27024  0 
ata_piix               19588  3 
pata_acpi               8320  0 
ata_generic             8324  0 
usbcore               146028  5 usb_storage,libusual,usbhid,uhci_hcd
libata                159344  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 

```

lspci

```
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

```

messages

```
Aug 17 08:37:58 tom-desktop kernel: [  397.279990] [drm] Initialized drm 1.1.0 20060810
Aug 17 08:37:58 tom-desktop kernel: [  397.289779] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 08:37:58 tom-desktop kernel: [  397.294419] [drm] Initialized i810 1.4.0 20030605 for 0000:00:01.0 on minor 0
Aug 17 08:37:58 tom-desktop kernel: [  397.295402] mtrr: base(0xf8000000) is not aligned on a size(0x3aa000) boundary
Aug 17 08:37:58 tom-desktop kernel: [  397.459666] [drm] Using v1.4 init.
Aug 17 08:38:07 tom-desktop kernel: Kernel logging (proc) stopped.
Aug 17 08:38:07 tom-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="597" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

kern.log

```
Aug 17 08:37:58 tom-desktop kernel: [  397.279990] [drm] Initialized drm 1.1.0 20060810
Aug 17 08:37:58 tom-desktop kernel: [  397.289747]   alloc irq_desc for 16 on node -1
Aug 17 08:37:58 tom-desktop kernel: [  397.289757]   alloc kstat_irqs on node -1
Aug 17 08:37:58 tom-desktop kernel: [  397.289779] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 08:37:58 tom-desktop kernel: [  397.289790] pci 0000:00:01.0: setting latency timer to 64
Aug 17 08:37:58 tom-desktop kernel: [  397.294419] [drm] Initialized i810 1.4.0 20030605 for 0000:00:01.0 on minor 0
Aug 17 08:37:58 tom-desktop kernel: [  397.295402] mtrr: base(0xf8000000) is not aligned on a size(0x3aa000) boundary
Aug 17 08:37:58 tom-desktop kernel: [  397.459666] [drm] Using v1.4 init.
Aug 17 08:38:01 tom-desktop kernel: [  400.548019] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
Aug 17 08:38:01 tom-desktop kernel: [  400.548029] 	driver to use reclaim_buffers_idlelocked() instead.
Aug 17 08:38:01 tom-desktop kernel: [  400.548032] 	I will go on reclaiming the buffers anyway.
Aug 17 08:38:07 tom-desktop kernel: Kernel logging (proc) stopped.
```

syslog

```
Aug 17 08:37:57 tom-desktop acpid: client connected from 1206[0:0]
Aug 17 08:37:57 tom-desktop acpid: 1 client rule loaded
Aug 17 08:37:58 tom-desktop kernel: [  397.279990] [drm] Initialized drm 1.1.0 20060810
Aug 17 08:37:58 tom-desktop kernel: [  397.289747]   alloc irq_desc for 16 on node -1
Aug 17 08:37:58 tom-desktop kernel: [  397.289757]   alloc kstat_irqs on node -1
Aug 17 08:37:58 tom-desktop kernel: [  397.289779] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 17 08:37:58 tom-desktop kernel: [  397.289790] pci 0000:00:01.0: setting latency timer to 64
Aug 17 08:37:58 tom-desktop kernel: [  397.294419] [drm] Initialized i810 1.4.0 20030605 for 0000:00:01.0 on minor 0
Aug 17 08:37:58 tom-desktop kernel: [  397.295402] mtrr: base(0xf8000000) is not aligned on a size(0x3aa000) boundary
Aug 17 08:37:58 tom-desktop kernel: [  397.459666] [drm] Using v1.4 init.
Aug 17 08:38:01 tom-desktop kernel: [  400.548019] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
Aug 17 08:38:01 tom-desktop kernel: [  400.548029] 	driver to use reclaim_buffers_idlelocked() instead.
Aug 17 08:38:01 tom-desktop kernel: [  400.548032] 	I will go on reclaiming the buffers anyway.
Aug 17 08:38:07 tom-desktop kernel: Kernel logging (proc) stopped.
Aug 17 08:38:07 tom-desktop rsyslogd: [origin software="rsyslogd" swVersion="4
```

---

### Post by him610 on 2010-08-17
> A lighter version sounds like a VERY good idea (512MB ram!)

I have a T1115 with 384MB that I installed both Xubuntu and Lubuntu. Both distros run quite satisfactorily with no problems whatsover.

As someone once said, "Come on in, the water's fine."

---

### Post by w2vy on 2010-08-17
I was looking around and saw reference to doing CTRL-ALT-F7 (F1-6 too)

On F7 I see start up messages and one caught my eye

init: dbus pre-start process (511) terminated with a status 1

That does not look good...

Also 

sudo service dbus start

returns

start: Job failed to start

I am running a clean install of xubuntu 10.4 with all updates

tom

---

