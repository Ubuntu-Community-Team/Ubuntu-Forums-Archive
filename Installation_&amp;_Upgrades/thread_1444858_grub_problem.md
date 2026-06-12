---
title: "grub problem"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by m3asmi on 2010-04-01
Hi!
[SIZE=2]
I have a problem to restore grub after an installation of Windows
to restore my Ubuntu  I try this cmd :[/SIZE]

```

sudo /media/disk/usr/sbin/grub

grub> 
grub> find /boot/grub/stage1
 (hd0,5)
grub>root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... **[COLOR=Navy]failed[/COLOR]**

Error 12: Invalid device requested

grub> 

grub> quit

```but the problem exist too !
I try this:

```
ubuntu@ubuntu:~$ sudo grub-install hd0
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:/media/disk$ sudo sbin/grub-install hd0
Could not find device for /boot: Not found or not a block device.

```[SIZE=2]but the problem exist too ![/SIZE]

[SIZE=2]In Windows I see this message 
```
" it n' there does not have disc in the reading. Insert a disc in the reading \ Device \ Harddisk1 \ DR5"
[/SIZE]
```



My file /media/disk/boot/grub/menu.lst

```

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
# kopt=root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5f6f2a40-ccf8-4366-9391-73a218189182

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

uuid        5f6f2a40-ccf8-4366-9391-73a218189182
background 336633
foreground 66FF33
splashimage=(hd0,6)/boot/grub/splashimages/medine_moon_right_below.xpm.gz

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


```

---

### Post by oldfred on 2010-04-01
I think you need to chroot into system so paths are correct, change partition sda6 (hd0,5) if not correct:

sudo mount /dev/sda6 /mnt
for i in dev proc sys; do mount --bind /$i /mnt/$i; done
sudo chroot  /mnt
grub
at grub prompt:
root (hd0,5)
setup (hd0)
quit

---

### Post by m3asmi on 2010-04-02
> **oldfred said:**
> I think you need to chroot into system so paths are correct, change partition sda6 (hd0,5) if not correct:

sudo mount /dev/sda6 /mnt
for i in dev proc sys; do mount --bind /$i /mnt/$i; done
sudo chroot  /mnt
grub
at grub prompt:
root (hd0,5)
setup (hd0)
quit

Doesn't work ! :(

---

### Post by presence1960 on 2010-04-02
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by m3asmi on 2010-04-03
thiks for the help!

but I'm recovred my ubuntu whith :
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x1a347364

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2            4080       19456   123515752+   f  W95 Etendue (LBA)
/dev/sda3            6630       19456   103032846    7  HPFS/NTFS
/dev/sda5            4080        6379    18474687   83  Linux
/dev/sda6            6381        6629     2000061   82  Linux swap / Solaris

Disque /dev/sdf: 2011 Mo, 2011168768 octets
255 têtes, 63 secteurs/piste, 244 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x00048373


```& I tray this :

```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set at 19,457. 
There is nothing'incorrect with that, but it is bigger than 1024, 
and this could cause problems for some installations: 
1) software that is executed at boot time (eg, old versions of LILO) 
2) software and boot partition for other OS 
   (I.e., DOS FDISK, OS / 2 FDISK) 

Command (m for help): w 
The partition table has been altered! 

Calling ioctl () to reread the partition table. 

WARNING: rereading partition table failed with error 16: Device or resource busy. 
The kernel will continue to use the old table. 
The new table will be used at the next reboot. 
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk -l

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x1a347364

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2            4080       19456   123515752+   f  W95 Etendue (LBA)
/dev/sda3            6630       19456   103032846    7  HPFS/NTFS
/dev/sda5            4080        6379    18474687   83  Linux
/dev/sda6            6381        6629     2000061   82  Linux swap / Solaris

Disque /dev/sdf: 2011 Mo, 2011168768 octets
255 têtes, 63 secteurs/piste, 244 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x00048373

ubuntu@ubuntu:~$ 

```In the end I tray ```

grub> find /boot/grub/stage1
 (hd0,4)        #is changed  <= hd0,5  

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

```all is good!
 thinks for god my UBUNTU is recovred :)
****************************************

---

### Post by m3asmi on 2010-04-03
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

RESULTS.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Identifiant de disque : 0x1a347364

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    65,529,134    65,529,072   7 HPFS/NTFS
/dev/sda2          65,529,135   312,560,639   247,031,505   f W95 Ext d (LBA)
/dev/sda5          65,529,261   102,478,634    36,949,374  83 Linux
/dev/sda6         102,494,763   106,494,884     4,000,122  82 Linux swap / Solaris
/dev/sda3         106,494,948   312,560,639   206,065,692   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

Drive: sdf ___________________ _____________________________________________________

Disque /dev/sdf: 2011 Mo, 2011168768 octets
255 têtes, 63 secteurs/piste, 244 cylindres, total 3928064 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Identifiant de disque : 0x00048373

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63     3,919,859     3,919,797   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        128CC9CD8CC9AC13                       ntfs                                     
/dev/sda3        20AD96412B8D1A91                       ntfs                                     
/dev/sda5        5f6f2a40-ccf8-4366-9391-73a218189182   ext4                                     
/dev/sda6        65b864b2-32af-4b57-8a8d-ea2f24dc1b9c   swap                                     
/dev/sdf1        24CE-674B                              vfat       RACHID_USB                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sdf1        /media/RACHID_USB        vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda3        /media/disk              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /noexecute=optin /fastdetect /TUTag=FOS6W0 /Kernel=TUKernel.exe 
;multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=FOS6W0-BAK 
;multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel (TuneUp Backup)" /NOEXECUTE=OPTIN /FASTDETECT /TUTAG=ACGFOH-BAK 

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5f6f2a40-ccf8-4366-9391-73a218189182

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

uuid        5f6f2a40-ccf8-4366-9391-73a218189182
background 336633
foreground 66FF33
splashimage=(hd0,6)/boot/grub/splashimages/medine_moon_right_below.xpm.gz

title        Ubuntu 9.04, kernel 2.6.28-18-generic
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5f6f2a40-ccf8-4366-9391-73a218189182 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5f6f2a40-ccf8-4366-9391-73a218189182
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=5f6f2a40-ccf8-4366-9391-73a218189182 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=65b864b2-32af-4b57-8a8d-ea2f24dc1b9c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  43.8GB: boot/grub/menu.lst
  38.3GB: boot/grub/stage2
  42.5GB: boot/initrd.img-2.6.28-11-generic
  44.0GB: boot/initrd.img-2.6.28-18-generic
  38.7GB: boot/vmlinuz-2.6.28-11-generic
  35.7GB: boot/vmlinuz-2.6.28-18-generic
  33.6GB: grub/stage2
  44.0GB: initrd.img
  42.5GB: initrd.img.old
  35.7GB: vmlinuz
  38.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by oldfred on 2010-04-03
You have a partition problem that the fdisk w command fixed enough to allow you to reinstall grub and boot but you still have some issue in the partition table:

/dev/sda2 overlaps with /dev/sda3

---

### Post by m3asmi on 2010-04-03
> **oldfred said:**
> You have a partition problem that the fdisk w command fixed enough to allow you to reinstall grub and boot but you still have some issue in the partition table:

/dev/sda2 overlaps with /dev/sda3


Yes  [SIZE=2][COLOR=Navy]/dev/sda2 overlaps with /dev/sda3  [/COLOR][/SIZE]when I open now Gparted  he doesn't show me my partition he show me just one partition[SIZE=2][COLOR=DarkOrange] /dev/sda (149,05Gio)[/COLOR][/SIZE]!!!!!!!!!!!!!!!!!

he doesn't now my table partition 

```

m3asmi@EL-GHAZI:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set at 19,457. 
There is nothing'incorrect with that, but it is bigger than 1024, 
and this could cause problems for some installations: 
1) software that is executed at boot time (eg, old versions of LILO) 
2) software and boot partition for other OS 
   (I.e., DOS FDISK, OS / 2 FDISK) 

Command (m for help): w 
The partition table has been altered! 

Calling ioctl () to reread the partition table. 

WARNING: [SIZE=3][COLOR=Red]rereading partition table failed with error 16[/COLOR][/SIZE][SIZE=3]:[/SIZE] Device or resource busy. 
The kernel will continue to use the old table. 
The new table will be used at the next reboot. 
```
Syncing disks.

---

