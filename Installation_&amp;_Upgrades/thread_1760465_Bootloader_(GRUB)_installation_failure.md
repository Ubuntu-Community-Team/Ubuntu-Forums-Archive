---
title: "Bootloader (GRUB) installation failure"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by susenj on 2011-05-16
I had an 80gb hard disk running dualboot XP and Ubuntu. Later i managed  to add another 500gb hard disk already having 5 partitions (which was  earlier running XP). I made this new hd as master making older one as  slave. Now, I wanted to get my older grub back, but since it was on  slave's partition, i couldn't reinstall it, then i deleted the old linux  partition from 80gb drive and wanted to have a clean install of ubuntu  on my new hd removing Xp from over there. I used a Ubuntu 10.04 live CD  to install it. I erased the Xp partition, and tried instaling ubuntu on  the same. But, finally it gave a fatal error: 
 **"grub bootloader installation failed"**
1)Continue and try manual installation later.
2)Abort the installation
3)Install grub somewhere else.
 
I tried last point and gave each of my partition's name where it could  install, but unfortunately, it couldn't take any of those (neither the  master's partition nor slave's). This msg continue to appear. Ultimately  i had to use option 1, that led to grub failure after restart and i am  not able to reinstall grub now.
 
I tried installing the same on the last partition of the master, but still the same issue. i am stuck[IMG]http://www.linuxforums.org/forum/images/smilies/icon_sad.gif[/IMG]
 
Any helps around!
 
TIA.

---

### Post by garvinrick4 on 2011-05-17
If in fact you have Ubuntu on the master drive or lets call it sda then you can install grub there.
Put in your install Cd and choose Try Ubuntu and run this in a terminal and post here:
```
sudo fdisk -l
``` (lower case L)
Leave the Ubuntu live cd in and have your internet connection working so we can fetch
a grub and install it from repository's.

---

### Post by susenj on 2011-05-17
Thanks garvinrick4!
here is the output you wanted:

ubuntu@ubuntu:~$ sudo fdisk -l
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d7667f4
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        5099    40949685    f  W95 Ext'd (LBA)
/dev/sda2   *        5100       19122   112639747+   7  HPFS/NTFS
/dev/sda3           19123       33145   112639747+   7  HPFS/NTFS
/dev/sda4           33146       48641   124471620    7  HPFS/NTFS
/dev/sda5               2        5099    40949653+   7  HPFS/NTFS
 
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf532f532
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sdb2            1913        9667    62292007    f  W95 Ext'd (LBA)
/dev/sdb5            1913        3442    12289693+   7  HPFS/NTFS
/dev/sdb6            3443        4972    12289693+   b  W95 FAT32
/dev/sdb7            4973        6502    12289693+   b  W95 FAT32
/dev/sdb8            6503        8414    15358108+   b  W95 FAT32
/dev/sdb9            8415        9667    10064691   83  Linux
ubuntu@ubuntu:~$

---

### Post by garvinrick4 on 2011-05-17
this will install grub to sdb drive where Ubuntu is. As long as your install went fine this
will boot you. 
```

#In live Cd using Try UBuntu copy and paste these in a terminal one by one.

[CODE]sudo mount /dev/sdb9 /mnt
``` ```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
```  ```
sudo chroot /mnt
``` ```
grub-install /dev/sdb 
``````
update-grub
``````
exit
``` ```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
``` ```
sudo umount /mnt
``` ```
sudo reboot
```Will put all windows install in menuentrys when you boot off of drive sdb (80 gig)
All will boot.

When you boot off of sda (500 gig) only Windows will boot.[/code]#This code using grub files in install and not fetching from repositories.
If any trouble post back.

---

### Post by susenj on 2011-05-17
```
grub-install /dev/sdb 
```

Doing this, gave the following result: 

root@ubuntu:/# grub-install /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
/dev/sda9: Not found or not a block device.

:confused: After this..i didn't go further.

---

### Post by Rubi1200 on 2011-05-17
Hi,

which drive is currently set in BIOS as first boot device?

Please run this script and post the results here so we can take a closer look at your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by garvinrick4 on 2011-05-17
If in fact you did mount /dev/sdb9 as in code and not /dev/sda9
Use the last 3 commands to unmount.
Go back to Live Cd and give rubi1200 the bootscript:
Seems the drive is still being seen as sda when it is sdb now most likely if you ran right code.
We know / was installed at sda9 and now is sdb9 because of swapping drives around.
Hopefully it will be an easy fix. Boot script takes a minute or two to run.

---

### Post by susenj on 2011-05-18
Thanks for the reply!

> Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


Here is the content requied.:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /etc/fstab

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /NTBOOTDD.SYS

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sdb6 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb6 starts at sector 55295793. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sdb7 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb7 starts at sector 79875243. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sdb8 starts 
                       at sector 63. But according to the info from fdisk, 
                       sdb8 starts at sector 104454693. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files:        /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1         781,418,494   976,773,119   195,354,626   5 Extended
/dev/sda5         781,418,496   976,773,119   195,354,624  83 Linux
/dev/sda2    *     81,915,435   307,194,929   225,279,495   7 NTFS / exFAT / HPFS
/dev/sda3         307,194,930   532,474,424   225,279,495   7 NTFS / exFAT / HPFS
/dev/sda4         532,474,425   781,417,664   248,943,240   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    30,716,279    30,716,217   7 NTFS / exFAT / HPFS
/dev/sdb2          30,716,341   155,300,354   124,584,014   f W95 Extended (LBA)
/dev/sdb5          30,716,343    55,295,729    24,579,387   7 NTFS / exFAT / HPFS
/dev/sdb6          55,295,793    79,875,179    24,579,387   b W95 FAT32
/dev/sdb7          79,875,243   104,454,629    24,579,387   b W95 FAT32
/dev/sdb8         104,454,693   135,170,909    30,716,217   b W95 FAT32
/dev/sdb9         135,170,973   155,300,354    20,129,382  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        C620EABE20EAB519                       ntfs       3Local
/dev/sda3        4E8CCB0F8CCAF08F                       ntfs       1Local
/dev/sda4        0890D40A90D4005C                       ntfs       2Local
/dev/sda5        4ccc0dae-cf61-4eff-9c7f-be3c34ee1952   ext3       
/dev/sdb1        C47084E47084DE94                       ntfs       N
/dev/sdb5        88902F80902F743A                       ntfs       N
/dev/sdb6        10EE-1175                              vfat       NMY_EDUCATA
/dev/sdb7        80F6-3524                              vfat       NLEISURE
/dev/sdb8        60FD-9F1D                              vfat       NLIFE ROCKZ
/dev/sdb9        472b114a-7fca-4c82-a1f7-901044f6cd67   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext3    errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 460.912467957 = 494.900994048  boot/vmlinuz-2.6.32-21-generic                 2
 460.912467957 = 494.900994048  vmlinuz                                        2

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb9/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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

#A splash image for the menu
splashimage=(hd0,8)/boot/grub/splashimages/Mac4Lin_GRUB3_v1.0.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=472b114a-7fca-4c82-a1f7-901044f6cd67 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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
# howmany=1

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=472b114a-7fca-4c82-a1f7-901044f6cd67 ro quiet splash vga=792
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,8)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=472b114a-7fca-4c82-a1f7-901044f6cd67 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,8)
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

--------------------------------------------------------------------------------

=============================== sdb9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=472b114a-7fca-4c82-a1f7-901044f6cd67 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=f1a5438d-815e-4652-a283-66c673c6638a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

--------------------------------------------------------------------------------

=================== sdb9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  72.720194340 = 78.082714112   boot/grub/core.img                             4
  72.633520603 = 77.989648896   boot/grub/menu.lst                             1
  72.636862278 = 77.993236992   boot/grub/stage2                               7
  72.507025242 = 77.853825536   boot/initrd.img-2.6.24-24-generic             11
  73.723055363 = 79.159527936   boot/initrd.img-2.6.24-24-generic.bak         28
  73.698648930 = 79.133321728   boot/initrd.img-2.6.27-14-generic             13
  72.572939396 = 77.924600320   boot/initrd.img-2.6.28-11-generic              5
  72.742624760 = 78.106798592   boot/vmlinuz-2.6.24-24-generic                 3
  72.176226139 = 77.498632704   boot/vmlinuz-2.6.27-14-generic                 2
  72.858786106 = 78.231525888   boot/vmlinuz-2.6.28-11-generic                39
  72.572939396 = 77.924600320   initrd.img                                     5
  73.698648930 = 79.133321728   initrd.img.old                                13
  72.858786106 = 78.231525888   vmlinuz                                       39
  72.176226139 = 77.498632704   vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  4b 2f 63 6c 69 65 6e 74  2f 69 6e 74 65 67 72 61  |K/client/integra|
00000010  74 69 6f 6e 2f 52 65 67  69 73 74 72 61 74 69 6f  |tion/Registratio|
00000020  6e 01 00 2a 6f 72 61 63  6c 65 2f 73 79 73 6d 61  |n..*oracle/sysma|
00000030  6e 2f 65 6d 53 44 4b 2f  63 6f 6d 6d 6f 6e 2f 6e  |n/emSDK/common/n|
00000040  6c 73 2f 49 6d 61 67 65  42 75 6e 64 6c 65 01 00  |ls/ImageBundle..|
00000050  2c 6f 72 61 63 6c 65 2f  73 79 73 6d 61 6e 2f 65  |,oracle/sysman/e|
00000060  6d 53 44 4b 2f 63 6f 6d  6d 6f 6e 2f 6e 6c 73 2f  |mSDK/common/nls/|
00000070  4d 65 73 73 61 67 65 42  75 6e 64 6c 65 01 00 20  |MessageBundle.. |
00000080  6f 72 61 63 6c 65 2f 73  79 73 6d 61 6e 2f 72 65  |oracle/sysman/re|
00000090  73 6f 75 72 63 65 73 2f  56 74 61 49 6d 67 49 44  |sources/VtaImgID|
000000a0  01 00 20 6f 72 61 63 6c  65 2f 73 79 73 6d 61 6e  |.. oracle/sysman|
000000b0  2f 72 65 73 6f 75 72 63  65 73 2f 56 74 63 49 6d  |/resources/VtcIm|
000000c0  67 49 44 01 00 20 6f 72  61 63 6c 65 2f 73 79 73  |gID.. oracle/sys|
000000d0  6d 61 6e 2f 72 65 73 6f  75 72 63 65 73 2f 56 74  |man/resources/Vt|
000000e0  63 4d 73 67 49 44 01 00  28 6f 72 61 63 6c 65 2f  |cMsgID..(oracle/|
000000f0  73 79 73 6d 61 6e 2f 76  74 63 43 6f 6e 73 6f 6c  |sysman/vtcConsol|
00000100  65 2f 56 74 63 44 69 73  70 6c 61 79 50 72 6f 78  |e/VtcDisplayProx|
00000110  79 01 00 1a 6f 72 61 63  6c 65 2f 73 79 73 6d 61  |y...oracle/sysma|
00000120  6e 2f 76 78 78 2f 56 78  78 54 79 70 65 73 01 00  |n/vxx/VxxTypes..|
00000130  16 6f 72 61 63 6c 65 5f  73 79 73 6d 61 6e 5f 64  |.oracle_sysman_d|
00000140  61 74 61 62 61 73 65 01  00 19 6f 72 61 63 6c 65  |atabase...oracle|
00000150  5f 73 79 73 6d 61 6e 5f  64 62 63 6f 6e 6e 65 63  |_sysman_dbconnec|
00000160  74 65 64 01 00 13 6f 72  61 63 6c 65 5f 73 79 73  |ted...oracle_sys|
00000170  6d 61 6e 5f 67 72 6f 75  70 01 00 16 6f 72 61 63  |man_group...orac|
00000180  6c 65 5f 73 79 73 6d 61  6e 5f 6c 69 73 74 65 6e  |le_sysman_listen|
00000190  65 72 01 00 12 6f 72 61  63 6c 65 5f 73 79 73 6d  |er...oracle_sysm|
000001a0  61 6e 5f 6e 6f 64 65 01  00 14 6f 72 61 63 6c 65  |an_node...oracle|
000001b0  5f 73 79 73 6d 61 6e 5f  70 61 67 69 6e 67 00 01  |_sysman_paging..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 3b 0d 77 01 00 fe  |..........;.w...|
000001d0  ff ff 05 fe ff ff 3d 0d  77 01 7a 0d 77 01 00 00  |......=.w.z.w...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by garvinrick4 on 2011-05-18
*** Read last statement before this***
#Windows boot files in both drives mbr (master boot record) Need to have linux's grub.
#Every partition in fstab is off the drives were switched so sda are now sdb's and sdb's are now sda's in every fstab.
In the 500 gig drive now sda there is a linux install (sda5) of 10.04 but does not have boot files.
In the 80 gig drive in sdb9 there is a linux install of 9.04 with grub-legacy. (grub was grub2 in 9.10 version of linux and up).
Lets just see if we can put grub files in sda5 before we go any farther with this.(You had trouble with this at install)
Put in a Live CD (Ubuntu Cd and choose Try Ubuntu and open a terminal) Use your 10.04 cd.
Make sure internet working in Live Cd (get online with firefox and make sure working)
Copy and paste these one at a time.
                          ```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 
``````
apt-get install grub-common grub-pc
``````
dpkg --configure -a
``````
exit
```                               ```
  sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```#All we are doing here is seeing if we can put grub files in linux install of sda (500 gig drive now). And running the dpkg --configure -a to see if any dependency or other problems in installation. (just checking to see if boot files will install)
#Now run the bootscript again and see if we got them in there post bootscript just like before.
*** You have to know this is an absolute mess really no operating systems available. Two, Linux one on each. Partitions containing
all sorts of old boot files even I believe some from Windows 2000. This is just an effort to get sda5 running and delete all other partitions on 500 gig drive.
If nothing on sda5 as I believe better to just format whole drive and reinstall.
80 gig drive do you have anything of value on 9.04 install of Linux?
Lets stick with this, getting you bootable is a challenge, same users with boot problems always the same your drives are a bit special if you get my drift.

---

