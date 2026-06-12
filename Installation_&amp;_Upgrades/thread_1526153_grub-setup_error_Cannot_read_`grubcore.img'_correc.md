---
title: "grub-setup: error: Cannot read `/grub/core.img' correctly"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by sukumarreddy on 2010-07-07
[FONT=Tahoma][SIZE=2]Hi all,
   I got a problem in reinstating ubunru.

earlier i had installed Xp and then ubuntu. Now i had installed windows 7.When i am trying to reinstall the grub following error was came.
[SIZE=5][COLOR=Red]"[/COLOR][/SIZE]ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt/
%mounting disk drive
ubuntu@ubuntu:~$   sudo grub-install --root-directory=/mnt /dev/sda6
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.[/SIZE]
[/FONT][FONT=Tahoma][SIZE=4]**grub-setup: error: Cannot read `/grub/core.img' correctly**[/SIZE][/FONT][FONT=Tahoma][SIZE=5][COLOR=Red]"[/COLOR][/SIZE][/FONT]

Any reply will be appreciated.

---

### Post by oldfred on 2010-07-08
Your last command is not to install to the partition sda6 but the MBR of drive sda (no number). 

You can force grub2 to install to a partition but it is not considered reliable and you have to have another boot loader to chainload to it.

---

### Post by sukumarreddy on 2010-07-29
I got it.It installed successfully.  But after grub loading  it hags on grub shell.

---

### Post by sukumarreddy on 2010-07-29
I tried 2,3 times but no results

---

### Post by oldfred on 2010-07-29
Try posting this so we can see if something looks out of place:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by sukumarreddy on 2010-07-29
Here the RESULT.txt


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 458450451 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   163,830,869    81,915,435   7 HPFS/NTFS
/dev/sda3         163,830,870   369,302,219   205,471,350   7 HPFS/NTFS
/dev/sda4         369,302,220   625,137,344   255,835,125   5 Extended
/dev/sda5         369,302,283   373,286,339     3,984,057  82 Linux swap / Solaris
/dev/sda6         373,286,403   466,945,289    93,658,887  83 Linux
/dev/sda7         466,945,353   625,121,279   158,175,927   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     7,843,839     7,835,648   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 135     3,858,623     3,858,489   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BC1055CE1055906E                       ntfs                                     
/dev/sda2        A46810EC6810BECC                       ntfs       Softwares                     
/dev/sda3        E85419335419064A                       ntfs       Precious                      
/dev/sda5        e580c2f5-69c9-4733-aa3f-7335ea0ffaa7   swap                                     
/dev/sda6        daa5b96a-c32c-4091-b385-f7a1cfc1ba39   ext3                                     
/dev/sda7        CE74086F74085D19                       ntfs       Education                     
/dev/sdb1        4607-6C62                              vfat       SUKUMAR                       
/dev/sdc1        6561-3635                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc1        /media/6561-3635         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
# kopt=root=UUID=daa5b96a-c32c-4091-b385-f7a1cfc1ba39 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=daa5b96a-c32c-4091-b385-f7a1cfc1ba39

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

title        Ubuntu 9.10, kernel 2.6.31-21-generic
uuid        daa5b96a-c32c-4091-b385-f7a1cfc1ba39
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=daa5b96a-c32c-4091-b385-f7a1cfc1ba39 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid        daa5b96a-c32c-4091-b385-f7a1cfc1ba39
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=daa5b96a-c32c-4091-b385-f7a1cfc1ba39 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

#title        Ubuntu 9.10, kernel 2.6.31-20-generic
#uuid        daa5b96a-c32c-4091-b385-f7a1cfc1ba39
#kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=daa5b96a-c32c-4091-b385-f7a1cfc1ba39 ro quiet splash 
#initrd        /boot/initrd.img-2.6.31-20-generic
#quiet

#title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
#uuid        daa5b96a-c32c-4091-b385-f7a1cfc1ba39
#kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=daa5b96a-c32c-4091-b385-f7a1cfc1ba39 ro  single
#initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, memtest86+
uuid        daa5b96a-c32c-4091-b385-f7a1cfc1ba39
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows XP 
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=daa5b96a-c32c-4091-b385-f7a1cfc1ba39 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=B9F2-EA38 /windows vfat defaults,umask=007,gid=46 0 1
# Entry for /dev/sda5 :
UUID=e580c2f5-69c9-4733-aa3f-7335ea0ffaa7 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/Precious ntfs-3g defaults,locale=en_IN 0 0

=================== sda6: Location of files loaded by Grub: ===================


 234.7GB: boot/grub/core.img
 234.6GB: boot/grub/menu.lst
 196.6GB: boot/grub/stage2
 211.3GB: boot/initrd.img-2.6.31-20-generic
 211.3GB: boot/initrd.img-2.6.31-21-generic
 234.7GB: boot/vmlinuz-2.6.31-20-generic
 238.2GB: boot/vmlinuz-2.6.31-21-generic
 211.3GB: initrd.img
 211.3GB: initrd.img.old
 238.2GB: vmlinuz
 234.7GB: vmlinuz.old


```

---

### Post by oldfred on 2010-07-29
You have grub2 in the MBR and parts of grub & grub2 in the install.
/boot/grub/menu.lst /etc/fstab /boot/grub/core.img

You have menu.lst from grub legacy and core.img from grub2 but no grub.cfg.

You need to totally chroot into your system & uninstall both grub and grub2 (grub-pc) and install one or the other.

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
kansasnoob's change sda5 to correct partition - Yours should be sda6, which I have changed:
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Once chrooted into your system:

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

---

### Post by sukumarreddy on 2010-07-30
VVV Thanks for reply. Now my pc works fine.

---

### Post by Khan_77 on 2010-09-02
this is my Results.txt and i am also struggling to fix it can any body help

---

### Post by Khan_77 on 2010-09-02
this is my Results.txt and i am also struggling to fix it can any body help
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89338933

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   208,893,194   208,893,132   7 HPFS/NTFS
/dev/sda2         208,893,195   625,137,344   416,244,150   f W95 Ext d (LBA)
/dev/sda5         208,893,258   417,786,389   208,893,132   7 HPFS/NTFS
/dev/sda6         417,786,453   533,406,194   115,619,742  83 Linux
/dev/sda7         533,406,258   621,635,174    88,228,917  83 Linux
/dev/sda8         621,635,238   625,137,344     3,502,107  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c60f6

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,827,455     7,819,392   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AED829FFD829C705                       ntfs                                     
/dev/sda5        10C86248C8622C62                       ntfs       New Volume                    
/dev/sda6        0c33c34c-25ac-444b-8356-69d85a3f6ba5   ext3                                     
/dev/sda7        671dbc45-b13d-4b09-bd09-a29bf532785d   ext4                                     
/dev/sda8        7a28033c-3755-4077-8aaa-24e8b33abf1a   swap                                     
/dev/sdb1        E963-B2C5                              vfat       HP v100w                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/HP v100w          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6        /media/0c33c34c-25ac-444b-8356-69d85a3f6ba5 ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda1        /mnt                     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color yellow/light-gray white/light-gray

#A splash image for the menu
splashimage=/boot/grub/splashimages/106843-lambo-murcielago-00.xpm.gz

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
# kopt=root=UUID=0c33c34c-25ac-444b-8356-69d85a3f6ba5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0c33c34c-25ac-444b-8356-69d85a3f6ba5

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
# defoptions=quiet vga=769

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

title		Ubuntu 9.04, memtest86+
uuid		0c33c34c-25ac-444b-8356-69d85a3f6ba5
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


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=0c33c34c-25ac-444b-8356-69d85a3f6ba5 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=23cec361-1f84-41a2-b3e8-4c5870367e06 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 238.5GB: boot/grub/menu.lst
 238.4GB: boot/grub/stage2

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,8)
search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 671dbc45-b13d-4b09-bd09-a29bf532785d
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=671dbc45-b13d-4b09-bd09-a29bf532785d ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aed829ffd829c705
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 0c33c34c-25ac-444b-8356-69d85a3f6ba5
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=671dbc45-b13d-4b09-bd09-a29bf532785d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=7a28033c-3755-4077-8aaa-24e8b33abf1a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 273.9GB: boot/grub/core.img
 280.6GB: boot/grub/grub.cfg
 273.7GB: boot/initrd.img-2.6.31-14-generic
 273.4GB: boot/initrd.img-2.6.31-17-generic
 307.6GB: boot/initrd.img-2.6.31-19-generic
 301.0GB: boot/initrd.img-2.6.31-20-generic
 274.4GB: boot/initrd.img-2.6.31-21-generic
 312.0GB: boot/initrd.img-2.6.31-22-generic
 273.7GB: boot/vmlinuz-2.6.31-14-generic
 274.0GB: boot/vmlinuz-2.6.31-17-generic
 310.9GB: boot/vmlinuz-2.6.31-19-generic
 296.8GB: boot/vmlinuz-2.6.31-20-generic
 280.5GB: boot/vmlinuz-2.6.31-21-generic
 274.6GB: boot/vmlinuz-2.6.31-22-generic
 312.0GB: initrd.img
 274.4GB: initrd.img.old
 274.6GB: vmlinuz
 280.5GB: vmlinuz.old
```

> **Khan_77 said:**
> I am an idealist. I dont know where i am going but i am on my way

---

### Post by sukumarreddy on 2010-09-02
Have tried above commands

---

### Post by spicysur on 2010-10-16
Hi,

I installed windows 7 on top of Ubuntu 10.04 - lost the ability to boot into ubuntu in the process. I tired to recover the grub using the instructions provided at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). But I'm getting the following error:

grub-setup: error: Cannot read `/grub/core.img' correctly


I have also attached the RESULTS.txt for reference. Someone pls help.

Thx

---

### Post by drs305 on 2010-10-16
> **spicysur said:**
> Hi,

I installed windows 7 on top of Ubuntu 10.04 - lost the ability to boot into ubuntu in the process. I tired to recover the grub using the instructions provided at [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows). But I'm getting the following error:

grub-setup: error: Cannot read `/grub/core.img' correctly


I have also attached the RESULTS.txt for reference. Someone pls help.

Thx

If you can boot to an Ubuntu LiveCD, run these commands to mount your Ubuntu partition and install Grub2 to the MBR. Once you update Grub it should find your Windows OS and include it in the Grub menu on boot.

From the LiveCD desktop:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and it should show the Ubuntu OS. If it doesn't show the Windows OS, run:
```
sudo update-grub
```

---

### Post by spicysur on 2010-10-16
> **drs305 said:**
> If you can boot to an Ubuntu LiveCD, run these commands to mount your Ubuntu partition and install Grub2 to the MBR. Once you update Grub it should find your Windows OS and include it in the Grub menu on boot.

From the LiveCD desktop:
```
sudo mount /dev/sda5 /mnt
sudo grub-install /dev/sda
```Reboot and it should show the Ubuntu OS. If it doesn't show the Windows OS, run:
```
sudo update-grub
```


Hi, Thx for the reply..

I'm getting the following error when i run sudo grub-install /dev/sda

grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.


should it be /dev/sda5 instead of /dev/sda?

Thx again...

---

### Post by drs305 on 2010-10-16
> **spicysur said:**
> Hi, Thx for the reply..

I'm getting the following error when i run sudo grub-install /dev/sda 

grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.


should it be /dev/sda5 instead of /dev/sda?

Thx again...

Sorry, it's getting late. I've edited the previous post, adding the correct instruction. Do not put "sda5" on the second line.

---

### Post by spicysur on 2010-10-16
> **drs305 said:**
> Sorry, it's getting late. I've edited the previous post, adding the correct instruction. Do not put "sda5" on the second line.


Thanks.. That worked..

---

