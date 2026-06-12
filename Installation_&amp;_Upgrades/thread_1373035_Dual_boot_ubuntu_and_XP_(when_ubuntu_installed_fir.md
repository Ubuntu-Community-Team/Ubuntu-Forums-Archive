---
title: "Dual boot ubuntu and XP (when ubuntu installed first)"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by jp071 on 2010-01-05
Hello, Anybody could know about the error. in this case, root is (hd0,6).

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 [COLOR=Red]Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested[/COLOR]

grub>

I need your valuable help. Thanks.

---

### Post by presence1960 on 2010-01-05
> **jp071 said:**
> Hello, Anybody could know about the error. in this case, root is (hd0,6).

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 [COLOR=Red]Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested[/COLOR]

grub>

I need your valuable help. Thanks.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by jp071 on 2010-01-05
Hello presence1960,
Thanks for your post. 
Could you make me more clear about the line "Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text."

---

### Post by kansasnoob on 2010-01-05
> **jp071 said:**
> Hello presence1960,
Thanks for your post. 
Could you make me more clear about the line "Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text."

Did you find the RESULTS.txt on your desktop (or possibly in the Downloads folder)?

If so just double click it and it will open in Gedit, then just right click anywhere within the file and click on "select all", then right click again and click on "copy".

Navigate back to the forum reply box and click on the # at the top (when you mouse-over it will show "wrap [CODE] tags ......."), then you'll see the CODE tags appear in the text area of the reply box, so just right click and select paste. That should dump the text you copied from gedit into the code tags.

Alternatively you can right click the RESULTS.txt and select "compress" which will create a tar.gz, then you can click on the paper clip at the top of the forum reply box (shows Attachments on mouse-over), browse to the RESULTS.txt.tar.gz, upload it, then click on the paper clip again to attach it here.

---

### Post by MichealH on 2010-01-05
I suggest putting in your live cd and installing Grub again

---

### Post by presence1960 on 2010-01-05
> **jp071 said:**
> Hello presence1960,
Thanks for your post. 
Could you make me more clear about the line "Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text."

kansasnoob answered that for you. Without the info requested I am loathe to give you commands to reinstall GRUB. I need to see your setup and boot process so I know I give you the correct commands.

---

### Post by jp071 on 2010-01-07
Hello, Here is the contents of results.txt file:

```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda3 starts at sector 146806784.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c45c84d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    99,635,129    99,635,067   7 HPFS/NTFS
/dev/sda2          99,635,254   309,325,823   209,690,570   f W95 Ext d (LBA)
/dev/sda5          99,635,256   107,635,499     8,000,244  82 Linux swap / Solaris
/dev/sda6         107,635,563   138,881,924    31,246,362  83 Linux
/dev/sda7         138,881,988   146,801,969     7,919,982  83 Linux
/dev/sda8         230,694,912   309,325,823    78,630,912   7 HPFS/NTFS
/dev/sda3         146,806,784   230,692,863    83,886,080   7 HPFS/NTFS
/dev/sda4         309,325,824   312,578,047     3,252,224   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x73696d20

Partition  Boot         Start           End          Size  Id System

/dev/sdb1     ? 1,919,230,059 6,204,919,772 4,285,689,714   a OS/2 Boot Manager
/dev/sdb2     ?   544,829,025 1,089,655,755   544,826,731  65 Novell Netware 386
/dev/sdb4       2,885,681,152 2,885,734,080        52,929   0 Empty

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb1 overlaps with /dev/sdb4
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb4 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

sda1: UUID="F4883A5D883A1F14" TYPE="ntfs" 
sda5: UUID="442781ed-e398-4cd0-9beb-4b1b20de95a1" TYPE="swap" 
sda6: UUID="e842567d-65f3-4e61-a719-71c99e7a503d" SEC_TYPE="ext2" TYPE="ext3" 
sda7: UUID="c675e39e-4eb0-4c36-82e8-73ab8b91aa24" SEC_TYPE="ext2" TYPE="ext3" 
sda8: UUID="FA00CF5E00CF208D" LABEL="Others" TYPE="ntfs" 
sda3: UUID="94BC612ABC610856" LABEL="Software" TYPE="ntfs" 
sda4: UUID="F29CE0FF9CE0BF6B" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb on /media/PERVEZ type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
default        10

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
# kopt=root=UUID=e842567d-65f3-4e61-a719-71c99e7a503d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e842567d-65f3-4e61-a719-71c99e7a503d

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        e842567d-65f3-4e61-a719-71c99e7a503d
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=e842567d-65f3-4e61-a719-71c99e7a503d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        e842567d-65f3-4e61-a719-71c99e7a503d
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=e842567d-65f3-4e61-a719-71c99e7a503d ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        e842567d-65f3-4e61-a719-71c99e7a503d
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=e842567d-65f3-4e61-a719-71c99e7a503d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        e842567d-65f3-4e61-a719-71c99e7a503d
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=e842567d-65f3-4e61-a719-71c99e7a503d ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        e842567d-65f3-4e61-a719-71c99e7a503d
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e842567d-65f3-4e61-a719-71c99e7a503d ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        e842567d-65f3-4e61-a719-71c99e7a503d
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=e842567d-65f3-4e61-a719-71c99e7a503d ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        e842567d-65f3-4e61-a719-71c99e7a503d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e842567d-65f3-4e61-a719-71c99e7a503d ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        e842567d-65f3-4e61-a719-71c99e7a503d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e842567d-65f3-4e61-a719-71c99e7a503d ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        e842567d-65f3-4e61-a719-71c99e7a503d
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
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=e842567d-65f3-4e61-a719-71c99e7a503d /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=c675e39e-4eb0-4c36-82e8-73ab8b91aa24 /home           ext3    relatime        0       2
# swap was on /dev/sda7 during installation
UUID=442781ed-e398-4cd0-9beb-4b1b20de95a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  70.8GB: boot/grub/menu.lst
  70.8GB: boot/grub/stage2
  70.8GB: boot/initrd.img-2.6.28-11-generic
  70.8GB: boot/initrd.img-2.6.31-14-generic
  70.9GB: boot/initrd.img-2.6.31-15-generic
  70.9GB: boot/initrd.img-2.6.31-16-generic
  70.8GB: boot/vmlinuz-2.6.28-11-generic
  70.8GB: boot/vmlinuz-2.6.31-14-generic
  70.8GB: boot/vmlinuz-2.6.31-15-generic
  70.8GB: boot/vmlinuz-2.6.31-16-generic
  70.9GB: initrd.img
  70.9GB: initrd.img.old
  70.8GB: vmlinuz
  70.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 ee 01  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 40 3c 00 09 0f 00 00  00 00 00 00 02 00 00 00  |.@<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 4c 3a f6 60 4e  4f 20 4e 41 4d 45 20 20  |..)L:.`NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 42 4f  |..............BO|
000001b0  4f 54 4d 47 52 20 69 73  20 6d 69 73 73 69 6e 67  |OTMGR is missing|
000001c0  ff 0d 0a 44 69 73 6b 20  65 72 72 6f 72 ff 0d 0a  |...Disk error...|
000001d0  50 72 65 73 73 20 61 6e  79 20 6b 65 79 20 74 6f  |Press any key to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  00 ac c1 ce 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory

```

---

### Post by presence1960 on 2010-01-07
Boot your Live CD  & choose "try ubuntu without any changes...", when the desktop loads open a terminal and do this:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,5)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd0,5)", 
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

You should be good to go.

---

### Post by jp071 on 2010-01-08
I already did these steps. 

But it shown fail message. The message i already posted in my very first post.

Actually my computer had dual boot with xp and ubuntu. i had some virus problem in xp, so that i reinstalled xp. After that i could not recover my ubuntu boot loader.

Will i reinstall ubuntu or any other ways to recover ubuntu.

Thanks.

---

### Post by presence1960 on 2010-01-08
> **jp071 said:**
> I already did these steps. 

But it shown fail message. The message i already posted in my very first post.

Actually my computer had dual boot with xp and ubuntu. i had some virus problem in xp, so that i reinstalled xp. After that i could not recover my ubuntu boot loader.

Will i reinstall ubuntu or any other ways to recover ubuntu.

Thanks.

No you did not do what I posted! You skipped the step "root (hd0,5) and that is most likely why it failed. This is what you did:

```
grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

```

This is what I asked you to do- note the red which you did not do:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,5)".
Use whatever your computer spits out for the following lines.
[COLOR="Red"]3. Type "root (hd0,5)",[/COLOR]
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

---

### Post by jp071 on 2010-01-08
Hello presence1960, 
I have followed all steps that you wrote. If you will see my first post, i have mentioned "root is (hd0,6)". That means, i have used "root (hd0,6)" command.

i executed all steps once again. The results are:

```

grub> find /boot/grub/stage1
 (hd0,6)

grub> root (hd0,6)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 [COLOR=Black]Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,6)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested
[/COLOR]
grub>

```

Thanks for your post.

---

### Post by presence1960 on 2010-01-08
something is not right then because you have a menu.lst in sda6. Menu.lst is legacy GRUB 0.97.

In legacy GRUB the partition numbering starts at 0 thus sda1 = (hd0,0), sda2 = (hd0,1) then sda6 = (hd0,5)

Edit: I can see you made a mess of your partition table because your fstab says / was originally on sda8, your script output says it is on sda6. Swap has changed from sda7 to sda5. Here is the fstab from your script output:
```

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Red"]# / was on /dev/sda8 during installation
UUID=e842567d-65f3-4e61-a719-71c99e7a503d /               ext3    relatime,errors=remount-ro 0       1[/COLOR]
# /home was on /dev/sda9 during installation
UUID=c675e39e-4eb0-4c36-82e8-73ab8b91aa24 /home           ext3    relatime        0       2
[COLOR="Red"]# swap was on /dev/sda7 during installation
UUID=442781ed-e398-4cd0-9beb-4b1b20de95a1 none            swap    sw              0       0[/COLOR]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

It would appear you didn't just install windows to an existing partition but rather moved/deleted some partitions also.

---

### Post by Jackyboy86 on 2010-01-08
> **presence1960 said:**
> something is not right then because you have a menu.lst in sda6. Menu.lst is legacy GRUB 0.97.

In legacy GRUB the partition numbering starts at 0 thus sda1 = (hd0,0), sda2 = (hd0,1) then sda6 = (hd0,5)

I was just about to say - should it be hd 0,3 - as its the 4th device in the list. Or have I got the wrong end of the stick?

```

**(hd0,0)**/dev/sda1    *             63    99,635,129    99,635,067   7 HPFS/NTFS
**(hd0,1)**/dev/sda2          99,635,254   309,325,823   209,690,570   f W95 Ext d (LBA)
**(hd 0,2)**/dev/sda5          99,635,256   107,635,499     8,000,244  82 Linux swap / Solaris
**(hd0,3)**/dev/sda6         107,635,563   138,881,924    31,246,362  83 Linux
**(hd 0,4)**/dev/sda7         138,881,988   146,801,969     7,919,982  83 Linux
/dev/sda8         230,694,912   309,325,823    78,630,912   7 HPFS/NTFS
/dev/sda3         146,806,784   230,692,863    83,886,080   7 HPFS/NTFS
/dev/sda4         309,325,824   312,578,047     3,252,224   7 HPFS/NTFS
```


[edit]
Jeez, just seen the last edit. I'm gonna shut up now, we're out of my depth ;)

---

### Post by presence1960 on 2010-01-08
> **Jackyboy86 said:**
> I was just about to say - should it be hd 0,3 - as its the 4th device in the list. Or have I got the wrong end of the stick?

```

**(hd0,0)**/dev/sda1    *             63    99,635,129    99,635,067   7 HPFS/NTFS
**(hd0,1)**/dev/sda2          99,635,254   309,325,823   209,690,570   f W95 Ext d (LBA)
**(hd 0,2)**/dev/sda5          99,635,256   107,635,499     8,000,244  82 Linux swap / Solaris
**(hd0,3)**/dev/sda6         107,635,563   138,881,924    31,246,362  83 Linux
**(hd 0,4)**/dev/sda7         138,881,988   146,801,969     7,919,982  83 Linux
/dev/sda8         230,694,912   309,325,823    78,630,912   7 HPFS/NTFS
/dev/sda3         146,806,784   230,692,863    83,886,080   7 HPFS/NTFS
/dev/sda4         309,325,824   312,578,047     3,252,224   7 HPFS/NTFS
```


[edit]
Jeez, just seen the last edit. I'm gonna shut up now, we're out of my depth ;)

No, it goes by sdax where x determines the counting starting at 0. sda1 = (hd0,0), sda2 = (hd0,1) etc. Extended and Logical partitions follow that rule also- thus sda5 = (hd0,4), sda6 = (hd0,5)

Note this is for Legacy GRUB only. GRUB2 has eliminated the 0 for partition numbering. In GRUB2 sda1 = (hd0,1), sda2 = (hd0,2) sda5 = (hd0,5)

---

### Post by Jackyboy86 on 2010-01-08
> **presence1960 said:**
> No, it goes by sdax where x determines the counting starting at 0. sda1 = (hd0,0), sda2 = (hd0,1) etc. Extended and Logical partitions follow that rule also- thus sda5 = (hd0,4), sda6 = (hd0,5)

Note this is for Legacy GRUB only. GRUB2 has eliminated the 0 for partition numbering. In GRUB2 sda1 = (hd0,1), sda2 = (hd0,2) sda5 = (hd0,5)

Awesome. Thanks for clearing that up. I'm still trying learn GRUBs ways :D

---

### Post by presence1960 on 2010-01-08
> **Jackyboy86 said:**
> I was just about to say - should it be hd 0,3 - as its the 4th device in the list. Or have I got the wrong end of the stick?

```

**(hd0,0)**/dev/sda1    *             63    99,635,129    99,635,067   7 HPFS/NTFS
**(hd0,1)**/dev/sda2          99,635,254   309,325,823   209,690,570   f W95 Ext d (LBA)
**(hd 0,2)**/dev/sda5          99,635,256   107,635,499     8,000,244  82 Linux swap / Solaris
**(hd0,3)**/dev/sda6         107,635,563   138,881,924    31,246,362  83 Linux
**(hd 0,4)**/dev/sda7         138,881,988   146,801,969     7,919,982  83 Linux
/dev/sda8         230,694,912   309,325,823    78,630,912   7 HPFS/NTFS
/dev/sda3         146,806,784   230,692,863    83,886,080   7 HPFS/NTFS
/dev/sda4         309,325,824   312,578,047     3,252,224   7 HPFS/NTFS
```


[edit]
Jeez, just seen the last edit. I'm gonna shut up now, we're out of my depth ;)

You don't have to shut up. Participation will facilitate knowledge. Here is his current partition table as listed from the script output:

```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c45c84d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    99,635,129    99,635,067   7 HPFS/NTFS
/dev/sda2          99,635,254   309,325,823   209,690,570   f W95 Ext d (LBA)
/dev/sda5          99,635,256   107,635,499     8,000,244  82 Linux swap / Solaris
/dev/sda6         107,635,563   138,881,924    31,246,362  83 Linux
/dev/sda7         138,881,988   146,801,969     7,919,982  83 Linux
/dev/sda8         230,694,912   309,325,823    78,630,912   7 HPFS/NTFS
/dev/sda3         146,806,784   230,692,863    83,886,080   7 HPFS/NTFS
/dev/sda4         309,325,824   312,578,047     3,252,224   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3
```

sda1 is windows
sda2 is an extended partition which contains the logical partitions sda5 thru sda8
sda3 & sda4 are NTFS partitions (probably data/storage)

The reason sda5 thru sda8 are listed ahead of sda3 & sda4 in the partition table output is they are inside of sda2. But that does not move them up in the numbering for (hdx,y) The y designation is still determined by the Y in sdaY. Thus sda5 is still the 5th partition and is (hd0,4) in Legacy GRUB and (hd0,5) in GRUB2. Hope this clears that up in your mind.

---

