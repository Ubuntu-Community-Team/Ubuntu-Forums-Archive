---
title: "Where's GRUB? New dual [install]..."
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-05-07
I've setup dual boot before, but this is new.

New 750G disk, put 8.04 LTS on partition 1, then put XP on FAT32 partition 2, and re-booted.

I expected XP to wipe GRUB, then restore GRUB, and link the XP into GRUB. But I booted, and got 'Disk Error'; Press any key to restart.

Then the process repeats.

Shouldn't XP have booted even?

---

### Post by garvinrick4 on 2010-05-07
> **Moozillaaa said:**
> I've setup dual boot before, but this is new.

New 750G disk, put 8.04 LTS on partition 1, then put XP on FAT32 partition 2, and re-booted.

I expected XP to wipe GRUB, then restore GRUB, and link the XP into GRUB. But I booted, and got 'Disk Error'; Press any key to restart.

Then the process repeats.

Shouldn't XP have booted even?Put your install cd in and use live cd. 
Run 
sudo fdisk -l
 
see what is where. Post here on this thread.

---

### Post by Moozillaaa on 2010-05-08
I got the GRUB back, but cannot boot into [COLOR=Red]Windows (in red)[/COLOR] The MAIN Ubuntu GRUBloader is NOW the SAME disk as [COLOR=Red]Windows[/COLOR] install

chucknb@chucknb-desktop:~$ sudo fdisk -l
[sudo] password for chucknb: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022288

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000afd18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006ca0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3735    30001356    c  W95 FAT32 (LBA)

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005a373

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       12748   102398278+  83  Linux
[B][COLOR=Red]/dev/sdd2   *       12749       19122    51199155    b  W95 FAT32
[/COLOR][/B]
Disk /dev/sdi: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df049

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *       50994      101986   409601272+   7  HPFS/NTFS
/dev/sdi2          101987      182401   645933487+   7  HPFS/NTFS
/dev/sdi3               1       50993   409601241    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38665b5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       12766   102537216    7  HPFS/NTFS
/dev/sdj2           12766       30402   141659488    7  HPFS/NTFS
/dev/sdj3           30402      121602   732561408    f  W95 Ext'd (LBA)
/dev/sdj5           30402       94143   512000000    7  HPFS/NTFS
/dev/sdj6           94144      121601   220556353+   7  HPFS/NTFS
chucknb@chucknb-desktop:~$

---

### Post by kansasnoob on 2010-05-08
Why install Windows second if everything is a clean install? Windows always likes to be first!

That said post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by garvinrick4 on 2010-05-08
You have grub in windows partition and boot only Linux? Not grub in sdd but sdd2.

When I need to get my Windows back I have always Code:

sudo grub-mkconfig && update-grub

You got a lot going on sda thru sdj or so. 
I usually just stay away from so system with so many HDD's
and do not get involved.

kansasnoob will most likely confirm your fix if you give him his boot script. Seen him around
and he is worth listening to.

---

### Post by Moozillaaa on 2010-05-08
Interesting script...

To help sort devices:

The 750 (sdd) will be the only internal device.
The 2 80's (sda, sdb), and the 30 (sdc), are coming OUT, after data migration to the 750.
The 1.5 tB (sdi) and the 1tB (sdj) are external file storage.



> 

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdi
 => No boot loader is installed in the MBR of /dev/sdj

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdd2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd2 starts at sector 204796620.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdi1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdj1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdj2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdj3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdj5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdj5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdj6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdj6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00022288

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   149,838,254   149,838,192  83 Linux
/dev/sda2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000afd18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders, total 60030432 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006ca0a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    60,002,774    60,002,712   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005a373

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   204,796,619   204,796,557  83 Linux
/dev/sdd2    *    204,796,620   307,194,929   102,398,310   b W95 FAT32


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000df049

Partition  Boot         Start           End          Size  Id System

/dev/sdi1    *    819,202,545 1,638,405,089   819,202,545   7 HPFS/NTFS
/dev/sdi2       1,638,405,090 2,930,272,064 1,291,866,975   7 HPFS/NTFS
/dev/sdi3                  63   819,202,544   819,202,482   7 HPFS/NTFS


Drive: sdj ___________________ _____________________________________________________

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38665b5b

Partition  Boot         Start           End          Size  Id System

/dev/sdj1               2,048   205,076,479   205,074,432   7 HPFS/NTFS
/dev/sdj2         205,078,192   488,397,167   283,318,976   7 HPFS/NTFS
/dev/sdj3         488,398,848 1,953,521,663 1,465,122,816   f W95 Ext d (LBA)
/dev/sdj5         488,400,896 1,512,400,895 1,024,000,000   7 HPFS/NTFS
/dev/sdj6       1,512,407,358 1,953,520,064   441,112,707   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        654332b6-ba09-4f40-adbd-81d10e04db9f   ext3       Ubuntu                        
/dev/sda5        5aff062a-5f40-4ab9-84d9-32b503af07b9   swap                                     
/dev/sdb1        FC88BFD588BF8D20                       ntfs       NB 80                         
/dev/sdc1        9CEA-4B46                              vfat                                     
/dev/sdd1        828568e1-8bbb-45a1-a7ed-60244e9e9630   ext2                                     
/dev/sdd2        4BE4-C677                              vfat                                     
/dev/sdi1        5441B2FE6C26DD75                       ntfs       A400Or                        
/dev/sdi2        28428D5804AF1366                       ntfs       661Or                         
/dev/sdi3        7759BEB45DC8EB44                       ntfs       B400Or                        
/dev/sdj1        9E2ED0832ED0563D                       ntfs       1New VolumeOr                 
/dev/sdj2        F27EA5D47EA59241                       ntfs       2New VolumeOr                 
/dev/sdj5        0E782DD9782DBFF7                       ntfs       3New VolumeOr                 
/dev/sdj6        F8AA4679AA463502                       ntfs       4New VolumeOr                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdd1        /                        ext2       (rw,relatime,errors=remount-ro)
/dev/sdi3        /media/B400Or            fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdj6        /media/4New VolumeOr     fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdj2        /media/2New VolumeOr     fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdi2        /media/661Or             fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdj1        /media/1New VolumeOr     fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdj5        /media/3New VolumeOr     fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdi1        /media/A400Or            fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


=========================== sda1/boot/grub/menu.lst: ===========================

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title        XPPro
map             (hd0) (hd1)
map             (hd1) (hd0)
rootnoverify    (hd1,0)
chainloader    +1


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=654332b6-ba09-4f40-adbd-81d10e04db9f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sde5
UUID=5aff062a-5f40-4ab9-84d9-32b503af07b9 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  70.5GB: boot/grub/menu.lst
  70.0GB: boot/grub/stage2
  70.0GB: boot/initrd.img-2.6.24-26-generic
  70.5GB: boot/initrd.img-2.6.24-27-generic
  70.1GB: boot/initrd.img-2.6.24-27-generic.bak
  70.0GB: boot/vmlinuz-2.6.24-26-generic
  70.4GB: boot/vmlinuz-2.6.24-27-generic
  70.5GB: initrd.img
  70.0GB: initrd.img.old
  70.4GB: vmlinuz
  70.0GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
E:\grldr=grldr="Start Linux"
=========================== sdd1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro quiet splash 
initrd        /boot/initrd.img-2.6.24-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro single 
initrd        /boot/initrd.img-2.6.24-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro quiet splash 
initrd        /boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro single 
initrd        /boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu 8.04.4 LTS, memtest86+ (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows XP Professional
root        (hd3,0)
savedefault
makeactive
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1


=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=5aff062a-5f40-4ab9-84d9-32b503af07b9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd1: Location of files loaded by Grub: ===================


  78.2GB: boot/grub/menu.lst
  57.5GB: boot/grub/stage2
  57.5GB: boot/initrd.img-2.6.24-26-generic
  81.4GB: boot/initrd.img-2.6.24-27-generic
  83.3GB: boot/initrd.img-2.6.24-27-generic.bak
  57.7GB: boot/vmlinuz-2.6.24-26-generic
  82.9GB: boot/vmlinuz-2.6.24-27-generic
  81.4GB: initrd.img
  57.5GB: initrd.img.old
  82.9GB: vmlinuz
  57.7GB: vmlinuz.old

================================ sdd2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\ = "Unidentified operating system on drive C." 
=======Devices which don't seem to have a corresponding hard drive==============

hdc hdd sde sdf sdg sdh 

---

### Post by wilee-nilee on 2010-05-08
If you edit the script to a scrolling reader it will be easier to read. Just open edit remove the code tags for quote and highlight the text hit # in tghe gui panel it will look better. ;)

---

### Post by kansasnoob on 2010-05-08
Just now getting a chance to look at this, I'll be back very soon.

---

### Post by kansasnoob on 2010-05-08
OK, what I see:

You have the following operating systems installed; Ubuntu 8.04.4 is on sda1, Windows XP is on sdc1, and another Ubuntu 8.04.4 is on sdd1.

Windows is installed in the MBR of /dev/sdc so, if your BIOS/cabling is set to boot sdc first, then only Win XP should boot.

Actually each OS is on a separate drive and each of those three drives mbr's is assigned to the OS on that drive.

The new drive appears to be sdd:

> Drive: sdd ___________________ __________________________________________________ ___

Disk /dev/sdd: **750.1 GB**, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005a373

Partition Boot Start End Size Id System

[B]/dev/sdd1 63 204,796,619 204,796,557 83 Linux
/dev/sdd2 * 204,796,620 307,194,929 102,398,310 b W95 FAT32[/B]

But the Info Script is not recognizing the Win OS:

> sdd2: __________________________________________________ _______________________

File system: vfat
Boot sector type: Windows XP: Fat32
Boot sector info: According to the info in the boot sector, sdd2 starts
at sector 0. But according to the info from fdisk,
sdd2 starts at sector 204796620.
Operating System:
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM


Notice the "Operating System" section is blank although a boot flag is set there and the Boot files/directories are complete. As I said previously Windows generally likes to be first on the drive!

There are also discrepancies in sdd1's menu.lst:

> title Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root (**[COLOR="Red"]hd0,0[/COLOR]**)
kernel /boot/vmlinuz-2.6.24-27-generic root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro quiet splash
initrd /boot/initrd.img-2.6.24-27-generic
quiet

> ## default grub root device
## e.g. groot=(**[COLOR="Red"]hd0,0[/COLOR]**)
# groot=(**[COLOR="Red"]hd0,0[/COLOR]**)

NOTE: sdd1 should = (hd3,0) but that part of the menu.lst is automagically generated **and should NOT be edited!** 

Even the Win XP portion of that is messed up:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/**[COLOR="Red"]sdd1[/COLOR]**
title Microsoft Windows XP Professional
root (**[COLOR="Red"]hd3,0[/COLOR]**)
savedefault
makeactive
[B][COLOR="Red"]map (hd0) (hd3)
map (hd3) (hd0)[/COLOR][/B]
chainloader +1

But XP is actually on sdd2, sort of - remember it doesn't appear properly in the Info Script.

The other XP is on sdc1.

Basically you have a mell of a hess! In my opinion since both the Hardy and XP on sdd are fresh installs I'd start over by wiping that drive and reinstalling. Only this time install XP first, then Ubuntu second!

I really wonder what your final goal here is? That's a lot of hard drives :lolflag:

2/80GB, 1/30GB, 1/750GB, 1/1TB, 1/1.5TB?

There are also a couple of boot flags set that needn't be:

> /dev/sda1 * 63 149,838,254 149,838,192 83 Linux

> /dev/sdb1 * 63 156,296,384 156,296,322 7 HPFS/NTFS

> /dev/sdi1 * 819,202,545 1,638,405,089 819,202,545 7 HPFS/NTFS

But that's not critical.

Another thing to consider is that Hardy is only supported for another 11 months.

---

### Post by Moozillaaa on 2010-05-08
Thanks - 

The 80's and the 30 are coming out after file migration. The 750 will be solo. The 1.5 and 1tB are external storage.

SOME of the discrepancies are because the 80's and the 30 are now on a PCI IDE controller card, and the 750 was put in on a SATA channel AFTERWARD.

I thought that the 'mapping' function for Windows on a slave disk install, would work also on a 'slave' partition install (partition 2).

---

