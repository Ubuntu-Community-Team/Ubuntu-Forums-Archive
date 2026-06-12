---
title: "After creating dual boot, windows XP works only after soft restart"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by msharelick on 2010-05-26
Hello:

I have recently created a dual boot system with Windows XP and Ubuntu 9.05.  I tried ubuntu 10 but for various reasons  I found the installation to be more difficult. 

I have two hard drives.  I installed Windows XP on the first one, followed by Ubuntu on the second one.  I installed Windows first. 

When I perform a hard reboot (as in turn the machine off and on, or turn it on for the first time), after selecting Windows XP from the GRUB list, windows xp will not start.  I get either a blinking dash, the text "Startup..." or a blank screen. 

Under the same conditions, if I choose Ubuntu, Ubuntu boots normally. 

After a soft reboot from Ubuntu, and selection of Windows XP, Windows XP boots up about 50% of the time. 

This is on a fresh install of this system. 

Please advise. 

Thanks

Matthew Harelick

---

### Post by darkod on 2010-05-26
Follow these instructions and post the content of your results file in CODE tags as specified. It will show us more info about the boot process.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by msharelick on 2010-05-29
```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e3a2e39

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   491,524,739   491,524,677   7 HPFS/NTFS
/dev/sda2         491,524,740   976,751,999   485,227,260   f W95 Ext d (LBA)
/dev/sda5         491,524,803   976,751,999   485,227,197   e W95 FAT16 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00023499

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   957,875,624   957,875,562  83 Linux
/dev/sdb2         957,875,625   976,768,064    18,892,440   5 Extended
/dev/sdb5         957,875,688   976,768,064    18,892,377  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1640971A4096FFA3                       ntfs                                     
/dev/sdb1        29e33691-9470-4292-ac20-990c0dd788f9   ext3                                     
/dev/sdb5        fe7c60f7-2f8d-4c10-a845-25ae3053bea7   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=29e33691-9470-4292-ac20-990c0dd788f9

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		29e33691-9470-4292-ac20-990c0dd788f9
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		29e33691-9470-4292-ac20-990c0dd788f9
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		29e33691-9470-4292-ac20-990c0dd788f9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		29e33691-9470-4292-ac20-990c0dd788f9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=29e33691-9470-4292-ac20-990c0dd788f9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		29e33691-9470-4292-ac20-990c0dd788f9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=29e33691-9470-4292-ac20-990c0dd788f9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=fe7c60f7-2f8d-4c10-a845-25ae3053bea7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 273.5GB: boot/grub/menu.lst
 273.4GB: boot/grub/stage2
 273.4GB: boot/initrd.img-2.6.28-11-generic
 273.4GB: boot/initrd.img-2.6.28-18-generic
 273.4GB: boot/vmlinuz-2.6.28-11-generic
 273.4GB: boot/vmlinuz-2.6.28-18-generic
 273.4GB: initrd.img
 273.4GB: initrd.img.old
 273.4GB: vmlinuz
 273.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  05 33 f6 46 eb 02 33 f6  8b 45 14 6a 60 89 7d f4  |.3.F..3..E.j`.}.|
00000010  89 7d fc 89 38 e8 6b 6c  f9 ff 3b c7 74 0f ff 75  |.}..8.kl..;.t..u|
00000020  0c 8b c8 e8 a9 4f 04 00  89 45 20 eb 03 89 7d 20  |.....O...E ...} |
00000030  39 7d 20 75 0a bf 0d fc  ff ff e9 97 02 00 00 8b  |9} u............|
00000040  4d 20 53 e8 a8 17 04 00  8b 4d 20 e8 92 58 04 00  |M S......M ..X..|
00000050  8b f8 bb bd f9 ff ff 3b  fb 75 0f 8b 4d 20 6a 01  |.......;.u..M j.|
00000060  e8 16 f8 ff ff 33 ff 89  7d 20 85 ff 0f 8c 47 02  |.....3..} ....G.|
00000070  00 00 85 f6 74 5c 6a 60  e8 08 6c f9 ff 85 c0 74  |....t\j`..l....t|
00000080  12 8b 4d f8 ff 71 1c 8b  c8 e8 43 4f 04 00 89 45  |..M..q....CO...E|
00000090  fc eb 04 83 65 fc 00 8b  75 fc 85 f6 75 0a bf 0d  |....e...u...u...|
000000a0  fc ff ff e9 11 02 00 00  8b ce e8 41 17 04 00 8b  |...........A....|
000000b0  ce e8 2c 58 04 00 8b f8  3b fb 75 0e 6a 01 8b ce  |..,X....;.u.j...|
000000c0  e8 b6 f7 ff ff 33 ff 89  7d fc 85 ff 0f 8c e7 01  |.....3..}.......|
000000d0  00 00 8b 75 1c 66 81 fe  00 01 0f 82 aa 00 00 00  |...u.f..........|
000000e0  83 7d 20 00 75 18 eb 4d  8b 4d 20 e8 f2 57 04 00  |.} .u..M.M ..W..|
000000f0  8b f8 3b fb 74 30 85 ff  0f 8c bb 01 00 00 ff 75  |..;.t0.........u|
00000100  f8 56 e8 d7 f4 ff ff 8b  4d 20 50 56 e8 66 4f 04  |.V......M PV.fO.|
00000110  00 8b 4d 20 50 e8 ff 4e  04 00 50 e8 3c f5 ff ff  |..M P..N..P.<...|
00000120  85 c0 7d 11 eb c2 8b 4d  20 6a 01 e8 4b f7 ff ff  |..}....M j..K...|
00000130  33 ff 89 7d 20 83 7d fc  00 75 18 eb 4d 8b 4d fc  |3..} .}..u..M.M.|
00000140  e8 9d 57 04 00 8b f8 3b  fb 74 30 85 ff 0f 8c 66  |..W....;.t0....f|
00000150  01 00 00 ff 75 f8 56 e8  82 f4 ff ff 8b 4d fc 50  |....u.V......M.P|
00000160  56 e8 11 4f 04 00 8b 4d  fc 50 e8 aa 4e 04 00 50  |V..O...M.P..N..P|
00000170  e8 e7 f4 ff ff 85 c0 7d  11 eb c2 8b 4d fc 6a 01  |.......}....M.j.|
00000180  e8 f6 f6 ff ff 33 ff 89  7d fc 33 f6 39 75 fc 89  |.....3..}.3.9u..|
00000190  75 0c 74 0b 8b 75 fc 33  db 43 89 5d 0c eb 03 8b  |u.t..u.3.C.]....|
000001a0  5d 10 33 c0 39 45 20 74  2b ff 45 0c 8b 75 20 83  |].3.9E t+.E..u .|
000001b0  cb ff 83 7d 0c 02 75 1c  8b 4d fc 89 45 e8 00 fe  |...}..u..M..E...|
000001c0  ff ff 0e fe ff ff 3f 00  00 00 bd fa eb 1c 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by msharelick on 2010-05-29
While the failure mostly occurs with Windows, it just occurred with Ubuntu.  I had to hard restart my computer twice before I was able to get into the Ubuntu partition. 

Thanks


Matthew Harelick

---

### Post by darkod on 2010-05-29
You have the grub1 bootloader on the windows disk. I don't know if that creates the problem, but it will boot faster if it's on the same disk as ubuntu.

Boot into your ubuntu, and to install grub1 also on the MBR of the ubuntu disk, just do in terminal:

sudo grub
setup (hd1)
quit

After that restart and go into BIOS, and switch the order of the hdds, to make the ubuntu disk first boot choice. They are both 500GB so it's a bit difficult to tell, but just switch the current order in the hdd boot order.

---

### Post by kansasnoob on 2010-05-29
I'm curious if both drives are SATA, IDE, or a combination of the two?

If both IDE do they share the same cable?

If the latter is true you may have to change some jumper settings on one or both of the drives.

---

### Post by darkod on 2010-05-29
> **kansasnoob said:**
> I'm curious if both drives are SATA, IDE, or a combination of the two?

If both IDE do they share the same cable?

If the latter is true you may have to change some jumper settings on one or both of the drives.

Wasn't IDE dropped long before 500GB capacity? Now it looks as if IDE was used ages ago. :)

---

### Post by kansasnoob on 2010-05-29
> **darkod said:**
> Wasn't IDE dropped long before 500GB capacity? Now it looks as if IDE was used ages ago. :)

I'm not sure, I think the largest IDE I've seen was 250GB.

If I have a thought I just blurt it out :tongue:

---

### Post by kansasnoob on 2010-05-29
I see WD still makes them:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014+1035907789+1036007800+103530113&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=14&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014+1035907789+1036007800+103530113&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=14&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

A lot more expensive than SATA.

---

### Post by darkod on 2010-05-29
> **kansasnoob said:**
> I see WD still makes them:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014+1035907789+1036007800+103530113&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=14&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014+1035907789+1036007800+103530113&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=14&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

A lot more expensive than SATA.

And not even ATA133, but ATA100. :)

They're probably not new, just resealed. :) Anyway, it seems 500GB IDE disk really exists.

---

### Post by msharelick on 2010-05-29
Hi:

When I do a setup(hd1) it says Error: 27 Unrecognized command.  

When I do a setup (hd1) it says invalid device 

How do I install grub on the second drive?

Thanks

---

### Post by darkod on 2010-05-29
> **msharelick said:**
> Hi:

When I do a setup(hd1) it says Error: 27 Unrecognized command.  

How do I install grub on the second drive?

Thanks

Did you first do sudo grub?

And the command prompt should change into

grub>

I think...

---

### Post by msharelick on 2010-05-29
Should I not be using IDE?

---

### Post by darkod on 2010-05-29
> **msharelick said:**
> Should I not be using IDE?

It's OK using IDE disks, but sometimes a combination of both SATA and IDE disks in your system creates issues. That's why kansas asked if you have IDE disks, SATA disks or a mix.

I guess because you have two 500GB disks that they are SATA.

Did you make sure you executed sudo grub before trying the setup (hd1)?

---

### Post by oldfred on 2010-05-29
I think Darko forgot the root command. It has been so long for old grub, I had to dig back into old notes.

In terminal
  sudo grub
  find grub/stage1
or
  find /boot/grub/stage1
  root (hd1,x)    <-- this must point to location of 'stage1', else see nb:
  setup (hd1)     <-- installs grub IPL to MBR of first hard drive. Prefered method.
  quit

---

### Post by darkod on 2010-05-29
> **oldfred said:**
> I think Darko forgot the root command. It has been so long for old grub, I had to dig back into old notes.

In terminal
  sudo grub
  find grub/stage1
or
  find /boot/grub/stage1
  root (hd1,x)    <-- this must point to location of 'stage1', else see nb:
  setup (hd1)     <-- installs grub IPL to MBR of first hard drive. Prefered method.
  quit

The OP can still boot into ubuntu, although it doesn't work every time. I was typing under assumption you are already inside your ubuntu.

Do you still need to specify root?

Similar for grub2 you can do only sudo grub-install /dev/sda without the --root-directory parameter.

---

### Post by confused57 on 2010-05-29
> **oldfred said:**
> I think Darko forgot the root command. It has been so long for old grub, I had to dig back into old notes.

In terminal
  sudo grub
  find grub/stage1
or
  find /boot/grub/stage1
  root (hd1,x)    <-- this must point to location of 'stage1', else see nb:
  setup (hd1)     <-- installs grub IPL to MBR of first hard drive. Prefered method.
  quit

Your instructions should work, using the 9.04 live cd(or in Ubuntu install) as described in this tutorial:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Set bios to boot first to sdb.

Then the OP could add an entry to menu.lst to boot Windows from grub:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

