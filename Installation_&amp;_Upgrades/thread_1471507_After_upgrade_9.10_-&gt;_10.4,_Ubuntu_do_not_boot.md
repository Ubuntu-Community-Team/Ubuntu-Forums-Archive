---
title: "After upgrade 9.10 -&gt; 10.4, Ubuntu do not boot"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by hogar_pg on 2010-05-03
After upgrading from 9.10 to 10.4 using Update Manager (as it took some time, it was mostly unattended), I can't boot. In GRUB, latest entry is:

```

Ubuntu 9.10, kernel 2.6.31-21-generic
```After selecting this entry, following message is displayed:

```

mounting none on /dev failed no such devicead91b5929e
chroot: cannot execute /etc/apparmor/ionitramfs
```After few seconds, booting resumes and it hangs with the message

```

Checking battery state...
```Adding in seconds:

```

[16.647853] sky eth0: Link is up and 100 Mbps, full duplex, flow control
[16.648039] ADDRCONF (NETDEC-CHANGE): eth0: link becomes ready
```Did as said in below post:

[http://ubuntuforums.org/showthread.php?p=9211458](http://ubuntuforums.org/showthread.php?p=9211458)

but got the message "File not found"

After checking /boot/ found no initrd.img-2.6.32.31-generic file.

Following files are present:

```

vmcoreinfo-2.6.32.31-generic
abi-2.6.32.31-generic
System.map-2.6.32.31-generic
config-2.6.32.31-generic
```Any ideas? Thanks!

---

### Post by hogar_pg on 2010-05-04
Anybody? My precious email is stuck with it :(

---

### Post by hogar_pg on 2010-05-06
I am still, hopelessly, stuck! Please help!

---

### Post by wilee-nilee on 2010-05-06
Since you have run some commands it may be best to have a closer look at your system, so post this boot script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tomski on 2010-05-06
similar problem but all i get is the grub rescue prompt & now have no idea what to type grrrrrrrrrrrrrrrrrrrrrrrrr
when is a ubuntu upgrade going to be smooth?

---

### Post by hogar_pg on 2010-05-06
As requested, output from boot script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   309,540,419   309,540,357  83 Linux
/dev/sdc2         309,540,420   321,669,494    12,129,075   5 Extended
/dev/sdc5         309,540,483   321,669,494    12,129,012  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,465,144,064 1,465,144,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0A4838984838848B                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        58E8A72FE8A709F8                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        56acaae8-6ee8-4381-a1c4-d9ad91b5929e   ext3                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        bc24d1e0-d410-4973-ac0f-e303f2e25556   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        fce7e09a-3dad-4e85-86a3-8263914a0a3d   ext3       Multimedia                    
/dev/sdd: PTTYPE="dos" 
/dev/sde         706E-5FC7                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde         /media/706E-5FC7         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdc1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=56acaae8-6ee8-4381-a1c4-d9ad91b5929e

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

title        Ubuntu 10.4
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.27-11-generic
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.10, memtest86+
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=bc24d1e0-d410-4973-ac0f-e303f2e25556 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=fce7e09a-3dad-4e85-86a3-8263914a0a3d /home/veselin/Multimedia/ ext3 defaults 0 0

=================== sdc1: Location of files loaded by Grub: ===================


  96.7GB: boot/grub/menu.lst
  20.1GB: boot/grub/stage2
  95.7GB: boot/initrd.img-2.6.27-11-generic
  95.6GB: boot/initrd.img-2.6.28-16-generic
  95.5GB: boot/initrd.img-2.6.31-14-generic
  95.5GB: boot/initrd.img-2.6.31-15-generic
  95.6GB: boot/initrd.img-2.6.31-16-generic
  95.6GB: boot/initrd.img-2.6.31-17-generic
  23.7GB: boot/initrd.img-2.6.31-19-generic
  95.6GB: boot/initrd.img-2.6.31-20-generic
  95.6GB: boot/initrd.img-2.6.31-21-generic
  95.6GB: boot/vmlinuz-2.6.27-11-generic
  95.6GB: boot/vmlinuz-2.6.28-16-generic
  95.6GB: boot/vmlinuz-2.6.31-14-generic
  95.6GB: boot/vmlinuz-2.6.31-15-generic
  95.6GB: boot/vmlinuz-2.6.31-16-generic
  95.6GB: boot/vmlinuz-2.6.31-17-generic
  23.6GB: boot/vmlinuz-2.6.31-19-generic
  24.1GB: boot/vmlinuz-2.6.31-20-generic
  95.6GB: boot/vmlinuz-2.6.31-21-generic
  95.6GB: boot/vmlinuz-2.6.32-21-generic
  95.6GB: initrd.img
  95.6GB: initrd.img.old
  95.6GB: vmlinuz
  24.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.<.MSWIN4.1..@ .|
00000010  02 00 02 00 00 f8 00 01  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 40 3c 00 80 00 29 c7  5f 6e 70 4e 4f 20 4e 41  |.@<...)._npNO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|
00000200


```

This part of menu.lst was added by me, but selecting it results in "File not found" error message:

[FONT=monospace]```
[/FONT]
title        Ubuntu 10.4
uuid        56acaae8-6ee8-4381-a1c4-d9ad91b5929e
kernel        /boot/vmlinuz-2.6.32-21-generic  root=UUID=56acaae8-6ee8-4381-a1c4-d9ad91b5929e ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

```

---

### Post by wilee-nilee on 2010-05-06
bump

---

### Post by kansasnoob on 2010-05-07
This is going to take me a little bit, so please be patient. I started to look at this last night but I was just too tired. We will get you through this.

---

### Post by hogar_pg on 2010-05-07
Thanks! Waiting ... :D

---

### Post by kansasnoob on 2010-05-07
**Please take time to read this all, briefly browse all linked threads, and ask for clarification if something seems confusing before proceeding.**

Well first I see that Win XP is missing it's /boot.ini file so if you want to fix that with a Windows disc I'd do that first:

[http://support.microsoft.com/kb/330184](http://support.microsoft.com/kb/330184)

Or if you'd rather wait until we get Ubuntu booting Meierfra wrote an excellent how-to:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

Note: ignore the part about Win being in a logical partition, yours is NOT! And of course remember that your XP is on /dev/sda1. If you decide to postpone fixing XP until we get Ubuntu straightened out I'll be glad to explain more in detail if necessary.

But as far as Ubuntu it looks like you're correct about it missing it's /boot/initrd.img so obviously something failed in the upgrade process. It happens:

[http://ubuntuforums.org/showthread.php?t=1471183](http://ubuntuforums.org/showthread.php?t=1471183)

Of course no two situations are the same so we'll need to begin by trying some things in a chroot. Please take a few minutes to look at the following link to gain just a general understanding how that works:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

In your case we'll begin by booting an Ubuntu Live CD and from the Live Desktop first double check to be sure Ubuntu is on /dev/sdc1:

```
sudo fdisk -l
```

If that appears to be correct then proceed:

```
sudo mount /dev/sdc1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

Now another double check, run:

```
lsb_release -a
```

That should show an output like:

> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid


We just want to be sure we mounted the right partition, if that looks right then proceed:

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

```
apt-get autoclean
```

```
apt-get clean
```

```
apt-get update
```

```
apt-get dist-upgrade
```

Note: if either 'update' or 'dist-upgrade' spits a bunch of errors we need to do some more troubleshooting so I'll need to see the full terminal output! Some potentially helpful commands to resolve package management issues:

```
apt-get -f install
```

```
apt-get autoremove
```

```
dpkg --configure -a
```

Of course without seeing the terminal output I can only guess, but you can check the status of 'boot/initrd.img' by running:

```
ls /boot
```

Example:

```
lance@lance-desktop:~$ ls /boot
abi-2.6.32-22-generic         memtest86+.bin
config-2.6.32-22-generic      System.map-2.6.32-22-generic
grub                          vmcoreinfo-2.6.32-22-generic
initrd.img-2.6.32-22-generic  vmlinuz-2.6.32-22-generic

```

If you do seem to get the Lucid initrd.img you could then just try:

```
update-grub
```

Note: your manual edits to the automagic section of the menu.lst may have to be removed or you could get 'update-grub' to generate a new menu.lst by renaming the menu.lst like:

```
mv /boot/grub/menu.lst /boot/grub/menu.lst_OLD
```

Then when you run 'update-grub' it should ask you if you want to generate a menu.lst. Of course then you'd have to add Windows again.

I'd personally recommend upgrading to grub2 but let's see if we can get Ubuntu booting first.

Anyway, anytime you want to exit the chroot and unmount run:

```
exit
``` 

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

---

### Post by kansasnoob on 2010-05-07
> **hogar_pg said:**
> Thanks! Waiting ... :D

Sorry to be so slow, I'm getting old ;)

I will keep checking back throughout the day.

---

### Post by hogar_pg on 2010-05-07
Hey, thanks a million!!!!

I followed your code line by line until following code:

```
dpkg-divert --local --rename --add /sbin/initctl
```

when I got a message stating that there is an error and that I must type following to have it sorted out automatically:

```
sudo dpkg --configure -a
```

after typing that, installer obviously continued upgrade where it stopped. After some 20-ish minutes, I got prompt back again. After that I just rebooted Live CD and booted from HDD. Got GRUB, selected entry "Ubuntu 10.4" that I made and everything was up and running with not a glitch!

So, Ubuntu is up and running. What I can/have to do with WinXP? I can boot it and use, but I keep getting error message that boot.ini is missing!

THANKS AGAIN!

---

### Post by kansasnoob on 2010-05-07
> **hogar_pg said:**
> Hey, thanks a million!!!!

I followed your code line by line until following code:

```
dpkg-divert --local --rename --add /sbin/initctl
```

when I got a message stating that there is an error and that I must type following to have it sorted out automatically:

```
sudo dpkg --configure -a
```

after typing that, installer obviously continued upgrade where it stopped. After some 20-ish minutes, I got prompt back again. After that I just rebooted Live CD and booted from HDD. Got GRUB, selected entry "Ubuntu 10.4" that I made and everything was up and running with not a glitch!

So, Ubuntu is up and running. What I can/have to do with WinXP? I can boot it and use, but I keep getting error message that boot.ini is missing!

THANKS AGAIN!

I'm glad you're at least partly sorted out, a silly question though, "did you really type those long commands?" In the future just copy-n-paste, that's one of the advantages of putting them in code tags. A double-click highlights the text, a right click copies, and another right click pastes.

One thing about your menu.lst though. The section that you edited is the "automagic" section and any edits to it usually end up stopping future kernel updates from "automagically" being applied so you should at least try removing those edits, running "sudo update-grub", and seeing if the menu.lst updates normally.

As far as the /boot.ini problem I included two links previously. You can fix it the Windows way (probably simplest):

[http://support.microsoft.com/kb/330184](http://support.microsoft.com/kb/330184)

Here's another link to the Windows way:

[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

Or Meierfra's Ubuntu method (a bit more complicated):

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

If you use Meierfra's method just remember you windows is on /dev/sda1.

If you have the Windows disc that would probably be the easiest way to go since Windows is on a different drive.

---

### Post by hogar_pg on 2010-05-08
> **kansasnoob said:**
> I'm glad you're at least partly sorted out, a silly question though, "did you really type those long commands?" In the future just copy-n-paste, that's one of the advantages of putting them in code tags. A double-click highlights the text, a right click copies, and another right click pastes.

One thing about your menu.lst though. The section that you edited is the "automagic" section and any edits to it usually end up stopping future kernel updates from "automagically" being applied so you should at least try removing those edits, running "sudo update-grub", and seeing if the menu.lst updates normally.

As far as the /boot.ini problem I included two links previously. You can fix it the Windows way (probably simplest):

[http://support.microsoft.com/kb/330184](http://support.microsoft.com/kb/330184)

Here's another link to the Windows way:

[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

Or Meierfra's Ubuntu method (a bit more complicated):

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

If you use Meierfra's method just remember you windows is on /dev/sda1.

If you have the Windows disc that would probably be the easiest way to go since Windows is on a different drive.


Off course I was copy/pasting :)

Thanks for Win tip, now it is booting without error message on missing boot.ini.

Well, this issue is solved! Thanks both of you!

---

