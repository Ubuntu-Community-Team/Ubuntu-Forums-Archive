---
title: "Lost my grub and now starved of Ubuntu!"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by robhem on 2010-02-18
Hi, 

I am unable to boot and am getting grub error 17. 
This happened after I used GParted to format a partition that I thought was not being used. Here's the story: 

I originally had one hard drive which was dual boot WinXP and Ubuntu. 
I added a second hard drive and installed Ubuntu on it. I remember having some problems with grub and I think I added a chainloader so one copy of grub was then loading another. I think my old installation of Ubuntu must have had its own grub which was loaded at boot up and then loaded grub on my new installation of Ubuntu. Anyway, this worked ok and i could boot into WinXP on my old drive or Ubuntu on my new drive. Until... I was wanting to reclaim the disk space taken up by the old installation of Ubuntu. I forgot all about the grub thing and formatted the whole partition. Now I can not boot at all. 

Not knowing too much about these things, I'm guessing that if I could replace the grub files on the newly formatted partition and configure it to chainload the grub on my current installation then things would be back where they were. However, maybe there is a more elegant solution with the MBR loading directly grub on my current installation instead? Please could anyone direct me on this? 

I have the following information by running the useful boot info script: 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 68790393.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 186337998.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda9 starts at sector 195350463.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda10 starts at sector 204362928.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda11 starts at sector 222789483.
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf4e81b2c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    68,790,329    68,790,267   c W95 FAT32 (LBA)
/dev/sda2          68,790,330   976,768,064   907,977,735   f W95 Ext d (LBA)
/dev/sda5          68,790,393   103,603,184    34,812,792   c W95 FAT32 (LBA)
/dev/sda6         103,603,248   184,297,679    80,694,432  83 Linux
/dev/sda7         184,297,743   186,337,934     2,040,192  82 Linux swap / Solaris
/dev/sda8         186,337,998   195,350,399     9,012,402   b W95 FAT32
/dev/sda9         195,350,463   204,362,864     9,012,402   b W95 FAT32
/dev/sda10        204,362,928   222,789,419    18,426,492   b W95 FAT32
/dev/sda11        222,789,483   243,272,294    20,482,812   b W95 FAT32
/dev/sda12        243,272,358   265,795,424    22,523,067  83 Linux
/dev/sda13        265,795,488   307,066,409    41,270,922  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd08ed08e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,965,749    40,965,687   c W95 FAT32 (LBA)
/dev/sdb2          40,965,750   156,296,384   115,330,635   f W95 Ext d (LBA)
/dev/sdb5          40,965,813    75,778,604    34,812,792   c W95 FAT32 (LBA)
/dev/sdb6          98,221,473   107,394,524     9,173,052   b W95 FAT32
/dev/sdb7         107,394,588   116,567,639     9,173,052   b W95 FAT32
/dev/sdb8         116,567,703   125,740,754     9,173,052   b W95 FAT32
/dev/sdb9         125,740,818   144,086,984    18,346,167   b W95 FAT32
/dev/sdb10        144,087,048   156,296,384    12,209,337   b W95 FAT32
/dev/sdb11         75,778,668    98,221,409    22,442,742  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       8A01-AF02                              vfat       VFAT6                         
/dev/sda11       8A64-9DE0                              vfat       VFAT7                         
/dev/sda12       285a12da-0e0b-4e39-97b7-4d2f40de516f   ext2       EXT2                          
/dev/sda13       810caac1-6e16-4892-97ca-d9f88e3101f1   ext2       VBOX1                         
/dev/sda1        CDEE-430D                              vfat       XPBKUP                        
/dev/sda5        8768-85F3                              vfat       ROBSPC                        
/dev/sda6        371a3473-99fe-461e-9e2a-1bdb02b63378   ext2       UBUNTU                        
/dev/sda7        a9915c9f-3eb1-4f52-a2f7-600c91774b3c   swap       SWAP                          
/dev/sda8        88DE-7D74                              vfat       MP3                           
/dev/sda9        8966-FDD0                              vfat       VFAT5                         
/dev/sdb10       5FAC-0C0D                              vfat       _PICTURES                     
/dev/sdb11       40edcddc-6005-45bf-aff5-33510e12f699   ext2       _EXT2                         
/dev/sdb1        A041-6752                              vfat       _WINXP                        
/dev/sdb5        9C37-A7DE                              vfat       _GTA4                         
/dev/sdb6        78DD-5E93                              vfat       _DOWNLOADS                    
/dev/sdb7        1B69-13D5                              vfat       _VFAT1                        
/dev/sdb8        C574-9EDF                              vfat       _VFAT2                        
/dev/sdb9        9881-2474                              vfat       _COD                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

tmpfs            /                        tmpfs      (rw)
/dev/sr0         /mnt/cdrom               iso9660    (ro,relatime,mode=0644)
/dev/loop0       /mnt/livecd              squashfs   (ro,relatime)


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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,5)

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
title         Ubuntu 9.04, kernel 2.6.28-18-generic
root         (hd1,5)
kernel         /boot/vmlinuz-2.6.28-18-generic root=/dev/sda6 ro quiet splash 
initrd         /boot/initrd.img-2.6.28-18-generic
quiet

title         Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root         (hd1,5)
kernel         /boot/vmlinuz-2.6.28-18-generic root=/dev/sda6 ro single
initrd         /boot/initrd.img-2.6.28-18-generic

title         Ubuntu 9.04, kernel 2.6.28-17-generic
root         (hd1,5)
kernel         /boot/vmlinuz-2.6.28-17-generic root=/dev/sda6 ro quiet splash 
initrd         /boot/initrd.img-2.6.28-17-generic
quiet

title         Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
root         (hd1,5)
kernel         /boot/vmlinuz-2.6.28-17-generic root=/dev/sda6 ro single
initrd         /boot/initrd.img-2.6.28-17-generic

title         Ubuntu 9.04, kernel 2.6.28-16-generic
root         (hd1,5)
kernel         /boot/vmlinuz-2.6.28-16-generic root=/dev/sda6 ro quiet splash 
initrd         /boot/initrd.img-2.6.28-16-generic
quiet

title         Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root         (hd1,5)
kernel         /boot/vmlinuz-2.6.28-16-generic root=/dev/sda6 ro single
initrd         /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda6 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=/dev/sda6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root        (hd1,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=/dev/sda6 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, memtest86+
root        (hd1,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
/dev/sda6 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda7
/dev/sda7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  61.6GB: boot/grub/menu.lst
  61.1GB: boot/grub/stage2
  61.1GB: boot/initrd.img-2.6.27-7-generic
  61.2GB: boot/initrd.img-2.6.28-13-generic
  61.1GB: boot/initrd.img-2.6.28-14-generic
  61.1GB: boot/initrd.img-2.6.28-15-generic
  62.4GB: boot/initrd.img-2.6.28-16-generic
  62.0GB: boot/initrd.img-2.6.28-17-generic
  62.4GB: boot/initrd.img-2.6.28-18-generic
  61.1GB: boot/vmlinuz-2.6.27-7-generic
  61.1GB: boot/vmlinuz-2.6.28-13-generic
  61.1GB: boot/vmlinuz-2.6.28-14-generic
  61.1GB: boot/vmlinuz-2.6.28-15-generic
  62.3GB: boot/vmlinuz-2.6.28-16-generic
  62.3GB: boot/vmlinuz-2.6.28-17-generic
  62.3GB: boot/vmlinuz-2.6.28-18-generic
  62.4GB: initrd.img
  62.0GB: initrd.img.old
  62.3GB: vmlinuz
  62.3GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  2c 1b e8 f4 00 00 00 01  |........,.......|
000001c0  01 00 0c fe ff ff 3f 00  00 00 fb a7 19 04 00 fe  |......?.........|
000001d0  ff ff 0f fe ff ff 3a a8  19 04 07 a4 1e 36 00 00  |......:......6..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file


The partition /dev/sdb11 was where my old install of Ubuntu resided, which I formatted. 
I have WinXP installed on /dev/sdb1 and my current copy of Ubuntu on /dev/sda6. 
Please could anyone help? Many thanks. 

Regards, 
Rab

---

### Post by Satoru-san on 2010-02-18
WOW! That is a LOT of partitions!

I dont know exactly what is wrong but you can try reinstalling grub.

boot the CD

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sdaX /mnt/ubuntu
sudo chroot /mnt/ubuntu
grub-install /dev/sdaX

```

You might have to restore the MBR, I dont know how.

---

### Post by oldfred on 2010-02-18
You should reinstall grub but your menu.lst looks a little strange.
root         (hd1,5)
kernel         /boot/vmlinuz-2.6.28-16-generic root=[COLOR=DarkRed]/dev/sda6[/COLOR] ro single

root 1,5 is sdb6 where your install is
but root-/dev/sda6 is not.

I might just try editing the first entry and see if it works, then edit the rest or rename menu.lst to menu.lst.backup so an update-grub creates a new menu.lst.

Usually UUIDs are used to eliminate error 17.
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

---

### Post by robhem on 2010-02-19
> You should reinstall grub but your menu.lst looks a little strange.
root         (hd1,5)
kernel         /boot/vmlinuz-2.6.28-16-generic root=[COLOR=DarkRed]/dev/sda6[/COLOR] ro single

root 1,5 is sdb6 where your install is
but root-/dev/sda6 is not.

I might just try editing the first entry and see if it works, then edit the rest or rename menu.lst to menu.lst.backup so an update-grub creates a new menu.lst.The menu.lst you refer to was working ok for me. I think it would still work, as it has not changed. I think the problem is that when booting, another menu.lst was being referenced which had a chainloader that pointed to this one. I have accidentally wiped the first menu.lst and don't know how to replace it plus any other files that are needed. Better still, I would like to get the system to go directly to the menu.lst that I still have. I don't really understand how this works. But, I am reading up on it ;)

Rab

---

### Post by oldfred on 2010-02-19
If that worked it was because you booted from sdb6 but ran the system (root) from sda6 and now sda6 does not exist. You can also delete (suggest rename to backup) menu.lst and reinstall grub and it will create a new one.

---

### Post by robhem on 2010-02-19
I have now tried to fix this using the Super Grub Disk and by following various threads. I've tried swapping the boot order in BIOS. I've tried a grub-update. None of this fixed my issues entirely. But, I was able to get the grub boot menu up and boot into Ubuntu. It wouldn't boot my WinXP if I chose that option. I read somewhere that I should do update-grub and now I can not boot anything again! I do still get the menu list on screen, but now if I choose to boot Ubuntu I get the following message: 

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init. 
No init found. Try passing init= bootarg. 


Then I get a BusyBox ash shell and a prompt like 

(initramfs)_ 


I have run the boot info script again and have the following results.txt 


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97-os.1 is installed in the MBR of /dev/sdc and looks on the same 
    drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb5 starts at sector 68790393.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb8 starts at sector 186337998.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb9 starts at sector 195350463.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb10 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb10 starts at sector 204362928.
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb11 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb11 starts at sector 222789483.
    Operating System:  
    Boot files/dirs:   

sdb12: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb13: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd08ed08e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   c W95 FAT32 (LBA)
/dev/sda2          40,965,750   156,296,384   115,330,635   f W95 Ext d (LBA)
/dev/sda5          40,965,813    75,778,604    34,812,792   c W95 FAT32 (LBA)
/dev/sda6          98,221,473   107,394,524     9,173,052   b W95 FAT32
/dev/sda7         107,394,588   116,567,639     9,173,052   b W95 FAT32
/dev/sda8         116,567,703   125,740,754     9,173,052   b W95 FAT32
/dev/sda9         125,740,818   144,086,984    18,346,167   b W95 FAT32
/dev/sda10        144,087,048   156,296,384    12,209,337   b W95 FAT32
/dev/sda11         75,778,668    98,221,409    22,442,742  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf4e81b2c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    68,790,329    68,790,267   c W95 FAT32 (LBA)
/dev/sdb2          68,790,330   976,768,064   907,977,735   f W95 Ext d (LBA)
/dev/sdb5          68,790,393   103,603,184    34,812,792   c W95 FAT32 (LBA)
/dev/sdb6         103,603,248   184,297,679    80,694,432  83 Linux
/dev/sdb7         184,297,743   186,337,934     2,040,192  82 Linux swap / Solaris
/dev/sdb8         186,337,998   195,350,399     9,012,402   b W95 FAT32
/dev/sdb9         195,350,463   204,362,864     9,012,402   b W95 FAT32
/dev/sdb10        204,362,928   222,789,419    18,426,492   b W95 FAT32
/dev/sdb11        222,789,483   243,272,294    20,482,812   b W95 FAT32
/dev/sdb12        243,272,358   265,795,424    22,523,067  83 Linux
/dev/sdb13        265,795,488   307,066,409    41,270,922  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1015 MB, 1015808000 bytes
5 heads, 4 sectors/track, 99200 cylinders, total 1984000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ec43681

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            249     1,983,999     1,983,751   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       5FAC-0C0D                              vfat       _PICTURES                     
/dev/sda11       40edcddc-6005-45bf-aff5-33510e12f699   ext2       _EXT2                         
/dev/sda1        A041-6752                              vfat       _WINXP                        
/dev/sda5        9C37-A7DE                              vfat       _GTA4                         
/dev/sda6        78DD-5E93                              vfat       _DOWNLOADS                    
/dev/sda7        1B69-13D5                              vfat       _VFAT1                        
/dev/sda8        C574-9EDF                              vfat       _VFAT2                        
/dev/sda9        9881-2474                              vfat       _COD                          
/dev/sdb10       8A01-AF02                              vfat       VFAT6                         
/dev/sdb11       8A64-9DE0                              vfat       VFAT7                         
/dev/sdb12       285a12da-0e0b-4e39-97b7-4d2f40de516f   ext2       EXT2                          
/dev/sdb13       810caac1-6e16-4892-97ca-d9f88e3101f1   ext2       VBOX1                         
/dev/sdb1        CDEE-430D                              vfat       XPBKUP                        
/dev/sdb5        8768-85F3                              vfat       ROBSPC                        
/dev/sdb6        371a3473-99fe-461e-9e2a-1bdb02b63378   ext2       UBUNTU                        
/dev/sdb7        a9915c9f-3eb1-4f52-a2f7-600c91774b3c   swap       SWAP                          
/dev/sdb8        88DE-7D74                              vfat       MP3                           
/dev/sdb9        8966-FDD0                              vfat       VFAT5                         
/dev/sdc1        0000-0000                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=/dev/hda1 ro

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

title        Ubuntu 9.04, kernel 2.6.28-18-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-18-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-18-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-13-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-13-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        Windows XP
rootnoverify    (hd1,0)
makeactive
chainloader +1





=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
/dev/sda6 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda7
/dev/sda7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  61.1GB: boot/grub/menu.lst
  61.6GB: boot/grub/stage2
  61.1GB: boot/initrd.img-2.6.27-7-generic
  61.2GB: boot/initrd.img-2.6.28-13-generic
  61.1GB: boot/initrd.img-2.6.28-14-generic
  61.1GB: boot/initrd.img-2.6.28-15-generic
  62.4GB: boot/initrd.img-2.6.28-16-generic
  62.0GB: boot/initrd.img-2.6.28-17-generic
  62.4GB: boot/initrd.img-2.6.28-18-generic
  61.1GB: boot/vmlinuz-2.6.27-7-generic
  61.1GB: boot/vmlinuz-2.6.28-13-generic
  61.1GB: boot/vmlinuz-2.6.28-14-generic
  61.1GB: boot/vmlinuz-2.6.28-15-generic
  62.3GB: boot/vmlinuz-2.6.28-16-generic
  62.3GB: boot/vmlinuz-2.6.28-17-generic
  62.3GB: boot/vmlinuz-2.6.28-18-generic
  62.4GB: initrd.img
  62.0GB: initrd.img.old
  62.3GB: vmlinuz
  62.3GB: vmlinuz.old

=========================== sdc1/boot/grub/menu.lst: ===========================

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 2
timeout 2
setgrubdevice # This is compulsory
#gfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


title Inicio normal / Normal Boot 
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs

title Soporte de accesibilidad / Accesibility Support -->
configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/menu.lst

title Normal boot. Kernel is aware of Boot device
kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
initrd $(grub_device)/initramfs

title Normal boot. Selecting kernel and initrd files depending on grub_device
kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
initrd $(grub_device)/initramfs_$(grub_device_string)

title Selecthd test
configfile $(grub_device)/boot/grub/choose/selecthd.lst

title findp test
configfile $(grub_device)/boot/grub/choose/selectpart.lst
title set SGD variables and boot SGD

configfile $(grub_device)/boot/sgd/menu.lst

=================== sdc1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb fe 90 4d 53 44 4f 53  35 2e 30 00 02 20 01 00  |...MSDOS5.0.. ..|
00000010  02 00 02 00 00 f8 f3 00  3f 00 20 00 f9 00 00 00  |........?. .....|
00000020  07 45 1e 00 80 01 29 00  00 00 00 4e 4f 20 4e 41  |.E....)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 90 90  |ME    FAT16   ..|
00000040  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
*
000001f0  90 90 90 90 90 90 90 90  90 90 90 90 90 90 55 aa  |..............U.|
00000200


Please could anyone help me out of this mess? Many thanks! 

Rab

---

### Post by robhem on 2010-02-19
> **oldfred said:**
> If that worked it was because you booted from sdb6 but ran the system (root) from sda6 and now sda6 does not exist. You can also delete (suggest rename to backup) menu.lst and reinstall grub and it will create a new one.

OK. I will try this.

---

### Post by kansasnoob on 2010-02-19
Your Windows entry in the menu.lst appears to be wrong:

```
title Windows XP
rootnoverify **(hd1,0)**
makeactive
chainloader +1

```

Whereas Win is here:

> **sda1**: __________________________________________________ _______________________

File system: vfat
Boot sector type: Windows XP: Fat32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM


In legacy grub numbering sda1 = (hd0,0).

To edit use:

```
gksudo gedit /boot/grub/menu.lst
```

Be sure and click on Save!

---

### Post by robhem on 2010-02-20
> **kansasnoob said:**
> Your Windows entry in the menu.lst appears to be wrong:

```
title Windows XP
rootnoverify **(hd1,0)**
makeactive
chainloader +1

```Whereas Win is here:



In legacy grub numbering sda1 = (hd0,0).

To edit use:

```
gksudo gedit /boot/grub/menu.lst
```Be sure and click on Save!

Ok, I did as you said and changed the entry in menu.lst (on sdb6). Now when I try to boot, if I choose the Windows XP item from the list I get the following: 

Starting up ... 
This is not a bootable disk.  Please insert a bootable floppy and press any key to try again ... 

If I then press any key, I get the GRUB Error 17

Disabling the floppy drive in bios makes no difference. 

Rab

---

### Post by darkod on 2010-02-20
> **kansasnoob said:**
> Your Windows entry in the menu.lst appears to be wrong:

```
title Windows XP
rootnoverify **(hd1,0)**
makeactive
chainloader +1

```Whereas Win is here:



In legacy grub numbering sda1 = (hd0,0).

To edit use:

```
gksudo gedit /boot/grub/menu.lst
```Be sure and click on Save!

(hd1,0) was correct if you trust sdb6/boot/grub/menu.lst because according to that sdb6 is (hd0,5). So it seems sda is hd1, sdb is hd0 in device.map.

How do you recreate device.map in grub1 and is it needed at all depending which disk are you booting from?

PS. And don't use Super Grub, it will mess it up further. It seems only the reference hd0 hd1 got swapped somehow. Don't try too many things at same time, it can mess it up further.

Check your /boot/grub/device.map and it should be:

/dev/sda (hd1)
/dev/sdb (hd0)

Then also adjust the windows entry in /boot/grub/menu.lst as:
title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by darkod on 2010-02-20
Also make sure you are booting from the 500GB as first choice.

---

### Post by robhem on 2010-02-20
Hi Darkod, 

Thanks for the help. 
I did as you said. Now when I try to boot, I get the menu and if I choose Ubuntu I get the errors as before: 

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init. 
No init found. Try passing init= bootarg. 


Then I get a BusyBox ash shell and a prompt like 

(initramfs)_ 

If I choose Windows I get: 

Error 11: Unrecognized device string 
Press any key to continue ...

Pressing any key takes me back to the menu list of boot options. 

Regards, 
Rab

---

### Post by robhem on 2010-02-20
I notice that at the top of the boot info output it says: 

=> Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

Could this be part of the issue?

---

### Post by darkod on 2010-02-20
Did you check which drive is hd0 and which hd1 in /boot/grub/device.map?

---

### Post by robhem on 2010-02-20
> **darkod said:**
> Did you check which drive is hd0 and which hd1 in /boot/grub/device.map?

Yes. It just had one line: 

(hd0)  /dev/sda

So, I changed it like you said and then got the errors I reported earlier. 

Since then, I tried hitting 'c' to go to the grub prompt. I had a mess about entering various commands and found that I could boot into Ubuntu if I changed the lines in menu.lst to read: 

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-18-generic root=/dev/sda6 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

Changing root=/dev/sda1 to root=/dev/sda6 now enables me to boot Ubuntu ok. 
I just need to figure out how to get Windows XP to boot from the grub menu now. 
Any suggestions please? Many thanks. 

Rab

---

### Post by darkod on 2010-02-20
I just noticed in your /boot/grub/menu.lst all the ubuntu entries say:
root=[COLOR=Red]/dev/sda1
[/COLOR]
Change that to /dev/sdb6 and see if you can boot ubuntu at least. Sorry I missed it earlier.

I have to say all this is very weird. It's like your computer has switched /dev/sda to /dev/sdb, and the other way around. It's like looking at the opposite disk.

You said it started after you deleted a partition you thought wasn't used. I don't know what you had on it, but it's weird all this.

EDIT: I just saw your last post, hold on with this. I have to think about this. :)

---

### Post by robhem on 2010-02-20
Darkod, 

I guess we both spotted the root=/dev/sda6 thing at the same time ;)

Yes, I have been thinking it seems like sda and sdb have been switched. I wonder if this happened when I tried the Super GRUB Disk. I chose a few auto options from that utility and it didn't help at all. Probably because I didn't understand what I was doing and I made things worse. I won't use super grub disk again.

---

### Post by darkod on 2010-02-20
Try for windows with:

title Windows XP
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

If it doesn't work, also try switching the map commands. I rarely use them and I'm never sure which one should be first and which second. Or if it makes a difference at all.

---

### Post by robhem on 2010-02-20
> **darkod said:**
> Try for windows with:

title Windows XP
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1

If it doesn't work, also try switching the map commands. I rarely use them and I'm never sure which one should be first and which second. Or if it makes a difference at all.

I get this error whichever way I switch the map commands: 

Error 11: Unrecognized device string 

Pressing any key takes me back to the boot menu.

---

### Post by darkod on 2010-02-20
Can you run the script again and post the content of the results file to see the current status? When you paste the text and while it's still selected, hit the # button in the toolbar above when creating the post to put CODE tags around the text. It's much easier for reading.

---

### Post by robhem on 2010-02-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda5 starts at sector 68790393.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 186337998.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda9 starts at sector 195350463.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda10 starts at sector 204362928.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda11 starts at sector 222789483.
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf4e81b2c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    68,790,329    68,790,267   c W95 FAT32 (LBA)
/dev/sda2          68,790,330   976,768,064   907,977,735   f W95 Ext d (LBA)
/dev/sda5          68,790,393   103,603,184    34,812,792   c W95 FAT32 (LBA)
/dev/sda6         103,603,248   184,297,679    80,694,432  83 Linux
/dev/sda7         184,297,743   186,337,934     2,040,192  82 Linux swap / Solaris
/dev/sda8         186,337,998   195,350,399     9,012,402   b W95 FAT32
/dev/sda9         195,350,463   204,362,864     9,012,402   b W95 FAT32
/dev/sda10        204,362,928   222,789,419    18,426,492   b W95 FAT32
/dev/sda11        222,789,483   243,272,294    20,482,812   b W95 FAT32
/dev/sda12        243,272,358   265,795,424    22,523,067  83 Linux
/dev/sda13        265,795,488   307,066,409    41,270,922  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd08ed08e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,965,749    40,965,687   c W95 FAT32 (LBA)
/dev/sdb2          40,965,750   156,296,384   115,330,635   f W95 Ext d (LBA)
/dev/sdb5          40,965,813    75,778,604    34,812,792   c W95 FAT32 (LBA)
/dev/sdb6          98,221,473   107,394,524     9,173,052   b W95 FAT32
/dev/sdb7         107,394,588   116,567,639     9,173,052   b W95 FAT32
/dev/sdb8         116,567,703   125,740,754     9,173,052   b W95 FAT32
/dev/sdb9         125,740,818   144,086,984    18,346,167   b W95 FAT32
/dev/sdb10        144,087,048   156,296,384    12,209,337   b W95 FAT32
/dev/sdb11         75,778,668    98,221,409    22,442,742  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       8A01-AF02                              vfat       VFAT6                         
/dev/sda11       8A64-9DE0                              vfat       VFAT7                         
/dev/sda12       285a12da-0e0b-4e39-97b7-4d2f40de516f   ext2       EXT2                          
/dev/sda13       810caac1-6e16-4892-97ca-d9f88e3101f1   ext2       VBOX1                         
/dev/sda1        CDEE-430D                              vfat       XPBKUP                        
/dev/sda5        8768-85F3                              vfat       ROBSPC                        
/dev/sda6        371a3473-99fe-461e-9e2a-1bdb02b63378   ext2       UBUNTU                        
/dev/sda7        a9915c9f-3eb1-4f52-a2f7-600c91774b3c   swap       SWAP                          
/dev/sda8        88DE-7D74                              vfat       MP3                           
/dev/sda9        8966-FDD0                              vfat       VFAT5                         
/dev/sdb10       5FAC-0C0D                              vfat       _PICTURES                     
/dev/sdb11       40edcddc-6005-45bf-aff5-33510e12f699   ext2       _EXT2                         
/dev/sdb1        A041-6752                              vfat       _WINXP                        
/dev/sdb5        9C37-A7DE                              vfat       _GTA4                         
/dev/sdb6        78DD-5E93                              vfat       _DOWNLOADS                    
/dev/sdb7        1B69-13D5                              vfat       _VFAT1                        
/dev/sdb8        C574-9EDF                              vfat       _VFAT2                        
/dev/sdb9        9881-2474                              vfat       _COD                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext2       (rw,relatime,errors=remount-ro)


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
# kopt=root=/dev/hda1 ro

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

title        Ubuntu 9.04, kernel 2.6.28-18-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-18-generic root=/dev/sda6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-18-generic root=/dev/sda6 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-16-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-15-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-14-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-13-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-13-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

title        Windows XP
rootnoverify    (hd1,0)
map (hd1)(hd0)
map (hd0)(hd1)
makeactive
chainloader +1





=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
/dev/sda6 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda7
/dev/sda7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  61.6GB: boot/grub/menu.lst
  61.6GB: boot/grub/stage2
  61.1GB: boot/initrd.img-2.6.27-7-generic
  61.2GB: boot/initrd.img-2.6.28-13-generic
  61.1GB: boot/initrd.img-2.6.28-14-generic
  61.1GB: boot/initrd.img-2.6.28-15-generic
  62.4GB: boot/initrd.img-2.6.28-16-generic
  62.0GB: boot/initrd.img-2.6.28-17-generic
  62.4GB: boot/initrd.img-2.6.28-18-generic
  61.1GB: boot/vmlinuz-2.6.27-7-generic
  61.1GB: boot/vmlinuz-2.6.28-13-generic
  61.1GB: boot/vmlinuz-2.6.28-14-generic
  61.1GB: boot/vmlinuz-2.6.28-15-generic
  62.3GB: boot/vmlinuz-2.6.28-16-generic
  62.3GB: boot/vmlinuz-2.6.28-17-generic
  62.3GB: boot/vmlinuz-2.6.28-18-generic
  62.4GB: initrd.img
  62.0GB: initrd.img.old
  62.3GB: vmlinuz
  62.3GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

```

---

### Post by darkod on 2010-02-20
Hmmm... Now it looks better, and they seem to have switched places again. You notice /dev/sda is now the 500GB disk and in the last results it was /dev/sdb.

According to the latest results, what I told you to write in device.map is now wrong, so I wonder if we should adjust it. Hopefully it won't break down the ubuntu boot which at least is working.

Because now /boot/grub/device.map should be:

(hd0) /dev/sda
(hd1) /dev/sdb

You can see in the menu.lst it calls the ubuntu root (hd0,5) and on the other hand /dev/sda6. So, hd0 should be sda, and hd1 should be sdb.

Try that but keep your ubuntu cd at hand, you might need to boot into live desktop and return device.map to what it is right now if ubuntu stops booting. :)

---

### Post by meierfra. on 2010-02-20
> Because now /boot/grub/device.map should be:

(hd0) /dev/sda
(hd1) /dev/sdb

That is is the correct device.map, but  editing it won't make a difference, since its hardly ever used.  But if it's wrong, you should still fix it.

> map (hd1)(hd0)
map (hd0)(hd1)

You need a "space"  between "(hd1)" and "hd0" and between  "(hd0)" and "(hd1)":

```
map (hd1) (hd0)
map (hd0) (hd1)

```

---

### Post by robhem on 2010-02-20
> **meierfra. said:**
> That is is the correct device.map, but  editing it won't make a difference, since its hardly ever used.  But if it's wrong, you should still fix it.


You need a "space"  between "(hd1)" and "hd0" and between  "(hd0)" and "(hd1)":

```
map (hd1) (hd0)
map (hd0) (hd1)

```

That is the final piece of the puzzle. The space was indeed missing and was the cause of the error 11. 
I am now able to boot Ubuntu or Windows XP. 

Many thanks to everyone who replied, especially to darkod for your patience. Your help is much appreciated. Thanks also to meierfra who I believe is the author of the very useful boot info script and for the last reply. 

Cheers, 
Rab :)

---

### Post by darkod on 2010-02-20
Just to make sure you can't file a lawsuit against me, I had space in my commands. :P

Glad it's all working now. Thanks to meierfra for spotting it.

---

