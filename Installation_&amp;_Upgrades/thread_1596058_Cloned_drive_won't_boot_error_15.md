---
title: "Cloned drive won't boot error 15"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by ak07 on 2010-10-13
OK so i've got a new OCZ vertex 2 SSD drive my current setup works like this...

I have a separate hard disk that i use to boot up with ubuntu I have achieved this is by creating a grub boot floppy when i want to boot ubuntu i load the floppy disk when i want windows i remove the floppy disk and windows boots.

I have cloned the ubuntu hard disk using clonezilla and the partition size was smaller than the new SSD so no issues with disk size.

I have installed the new SSD drive and restored the clone using clonezilla so far everything OK

When i try to boot ubuntu from the floppy using the SSD drive i get grub error message error 15 file not found.

If i try and boot with the floppy with the original ubuntu hard disk it works.

After having cloned the ubuntu hard drive the SSD drive won't boot - i think it could be a grub issue i've run out of ideas i hope someone can help.

---

### Post by ak07 on 2010-10-14
Anyone...

Thanks in advance

---

### Post by ak07 on 2010-10-14
Last try anyone...

---

### Post by oldfred on 2010-10-15
Post this.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Often the issue with cloned drives is duplicate UUIDs. But your error 15 is a old grub/grub2 issue.

---

### Post by ak07 on 2010-10-15
Thanks for your help results listed below I hope you can find something I'm going to look myself but still in early stages of using Linux - as if you couldn't tell...

Also when cloning i understand the uuids get copied as well but i don't understand why this would cause a problem with grub as in the menu.lst file it is referring to the uuid which is the same on the cloned disk


```
Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sde and looks on the same drive
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/mapper/isw_cceffhjieb_System

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sde1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

isw_cceffhjieb_System1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2fe7494c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,717,248 1,953,519,615 1,743,802,368   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004dacf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   102,762,495   102,760,448   6 FAT16
/dev/sdb2         102,762,496   117,225,471    14,462,976  82 Linux swap / Solaris
Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004dacf

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63   101,335,039   101,334,977  83 Linux
/dev/sde2         299,805,030   312,576,704    12,771,675   5 Extended
/dev/sde5         299,805,093   312,576,704    12,771,612  82 Linux swap / Solaris


Drive: isw_cceffhjieb_System ___________________ _____________________________________________________

Disk /dev/mapper/isw_cceffhjieb_System: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd952ebf6

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_cceffhjieb_System1              2,048 1,953,531,903 1,953,529,856   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/isw_cceffhjieb_System1 248CA4C78CA494B8                       ntfs       Striped
/dev/sda1        E2D8A46DD8A441A1                       ntfs       System
/dev/sda2        B0285A60285A261E                       ntfs       Local Backup
/dev/sdb1        15729ae2-c65b-4790-8b73-f836028aef13   ext3
/dev/sdb1        c7a3b0e0-e9b5-4c47-8851-15a7db4b871d   ext3
/dev/sdb2        c1e9f84a-d856-40bd-9e68-17161cc87e22   swap
/dev/sdc                                                isw_raid_member
/dev/sdd                                                isw_raid_member
/dev/sde1        c7a3b0e0-e9b5-4c47-8851-15a7db4b871d   ext3
/dev/sde5        06b6a1b7-2e96-4aa2-ae8f-83c82128c8d0   swap
/dev/sde                                                promise_fasttrack_raid_member

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_cceffhjieb_System
isw_cceffhjieb_System1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sde1        /                        ext3       (rw,relatime,errors=remount-ro)


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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# kopt=root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d

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

title           Ubuntu 9.10, kernel 2.6.31-22-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-22-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-22-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-22-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-22-generic

title           Ubuntu 9.10, kernel 2.6.31-21-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-21-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-21-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-21-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-21-generic

title           Ubuntu 9.10, kernel 2.6.31-20-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-20-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-20-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-20-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-20-generic

title           Ubuntu 9.10, kernel 2.6.31-19-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-19-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-19-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-19-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-19-generic

title           Ubuntu 9.10, kernel 2.6.31-17-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-17-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-17-generic

title           Ubuntu 9.10, kernel 2.6.31-15-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-15-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-15-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-15-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-15-generic

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, memtest86+
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=06b6a1b7-2e96-4aa2-ae8f-83c82128c8d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   7.5GB: boot/grub/grub.conf
   7.5GB: boot/grub/menu.lst
  44.0GB: boot/grub/stage2
   7.5GB: boot/initrd.img-2.6.31-14-generic
   7.6GB: boot/initrd.img-2.6.31-15-generic
   7.6GB: boot/initrd.img-2.6.31-17-generic
   7.5GB: boot/initrd.img-2.6.31-19-generic
   7.5GB: boot/initrd.img-2.6.31-20-generic
   7.5GB: boot/initrd.img-2.6.31-21-generic
   7.6GB: boot/initrd.img-2.6.31-22-generic
   7.5GB: boot/vmlinuz-2.6.31-14-generic
   7.6GB: boot/vmlinuz-2.6.31-15-generic
   7.5GB: boot/vmlinuz-2.6.31-17-generic
   7.5GB: boot/vmlinuz-2.6.31-19-generic
   7.6GB: boot/vmlinuz-2.6.31-20-generic
   7.5GB: boot/vmlinuz-2.6.31-21-generic
   7.5GB: boot/vmlinuz-2.6.31-22-generic
   7.6GB: initrd.img
   7.5GB: initrd.img.old
   7.5GB: vmlinuz
   7.5GB: vmlinuz.old
=========================== sde1/boot/grub/menu.lst: ===========================

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
timeout         3

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
# kopt=root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d

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

title           Ubuntu 9.10, kernel 2.6.31-22-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-22-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-22-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-22-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-22-generic

title           Ubuntu 9.10, kernel 2.6.31-21-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-21-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-21-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-21-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-21-generic

title           Ubuntu 9.10, kernel 2.6.31-20-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-20-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-20-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-20-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-20-generic

title           Ubuntu 9.10, kernel 2.6.31-19-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-19-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-19-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-19-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-19-generic

title           Ubuntu 9.10, kernel 2.6.31-17-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-17-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-17-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-17-generic

title           Ubuntu 9.10, kernel 2.6.31-15-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-15-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-15-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-15-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-15-generic

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro quiet splash
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d ro  single
initrd          /boot/initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, memtest86+
uuid            c7a3b0e0-e9b5-4c47-8851-15a7db4b871d
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=c7a3b0e0-e9b5-4c47-8851-15a7db4b871d /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=06b6a1b7-2e96-4aa2-ae8f-83c82128c8d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde1: Location of files loaded by Grub: ===================


   7.5GB: boot/grub/menu.lst
   7.6GB: boot/grub/stage2
   7.5GB: boot/initrd.img-2.6.31-14-generic
   7.6GB: boot/initrd.img-2.6.31-15-generic
   7.6GB: boot/initrd.img-2.6.31-17-generic
   7.5GB: boot/initrd.img-2.6.31-19-generic
   7.5GB: boot/initrd.img-2.6.31-20-generic
   7.5GB: boot/initrd.img-2.6.31-21-generic
   7.6GB: boot/initrd.img-2.6.31-22-generic
   7.5GB: boot/vmlinuz-2.6.31-14-generic
   7.6GB: boot/vmlinuz-2.6.31-15-generic
   7.5GB: boot/vmlinuz-2.6.31-17-generic
   7.5GB: boot/vmlinuz-2.6.31-19-generic
   7.6GB: boot/vmlinuz-2.6.31-20-generic
   7.5GB: boot/vmlinuz-2.6.31-21-generic
   7.5GB: boot/vmlinuz-2.6.31-22-generic
   7.6GB: initrd.img
   7.5GB: initrd.img.old
   7.5GB: vmlinuz
   7.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdf sdg sdh sdi
=============================== StdErr Messages: ===============================

ERROR: pdc: wrong # of devices in RAID set "pdc_dahcbjhdjf" [1/2] on /dev/sde
ERROR: removing inconsistent RAID set "pdc_dahcbjhdjf"
ERROR: pdc: wrong # of devices in RAID set "pdc_dahcbjhdjf" [1/2] on /dev/sde
ERROR: removing inconsistent RAID set "pdc_dahcbjhdjf"
ERROR: pdc: wrong # of devices in RAID set "pdc_dahcbjhdjf" [1/2] on /dev/sde
ERROR: removing inconsistent RAID set "pdc_dahcbjhdjf"

```

---

### Post by oldfred on 2010-10-15
The script says your have sdc & sdd as RAID. I do not know about RAID systems. It also shows some inconsistencies with your RAID. You still are using grub legacy with Karmic 9.10 so you must have upgraded.

But it has this:
/dev/sdb1        15729ae2-c65b-4790-8b73-f836028aef13   ext3
/dev/sdb1        c7a3b0e0-e9b5-4c47-8851-15a7db4b871d   ext3

You cannot have the same partition with different UUIDs. Grub (and I) gets very confused. You also show a /boot/grub/grub.conf which I do not think is Ubuntu's version of grub. Grub legacy uses menu.lst and grub2 uses grub.cfg. 

Which drive is the SSD and is sde part of the RAID? Grub does have issues with drives that were RAID but are not now.
/dev/sde      promise_fasttrack_raid_member

Why are you booting with a floppy when you just could boot sde, or put grub in the SSD and let you choose windows or Ubuntu (would still load part of grub from sde so maybe not as fast booting)?

---

### Post by ak07 on 2010-10-15
OK so the raided drives are my windows 7 disks so no issues with them.

The different uuids are down to me trying to change the uuid on the SSD drive **dev/sdb** in case this was causing a problem - me playing without really understanding.

The working ubuntu standard hard disk used to be in a raid configuration but not anymore this is **dev/sde** 

Before cloning the dev/sde drive I resized it so it would restore back to a smaller SSD drive.

I am using a boot floppy because I originally installed the ubuntu drive and was booting straight from it, but I then installed windows 7 and didn't what to have dual boot grub setup. So I created a boot floppy and it's been working well - whenever I need to boot ubuntu I load the floppy.

Until now :confused:

I have since realised that my motherboards raid controller does not see the new SSD drive.

So I cannot use it in a raid configurations - but the other issues with that is I cannot also select the drive to boot from within BIOS.

So ideally I would like to restore the cloned drive to the SSD drive and continue using the floppy :)

Sorry I know this post is quite long just trying to clarify the issue I hope you can help me out with any suggestions as my ubuntu setup is for my studies so would be nice to have the SSD drive working kinda regretting buying it now.

---

### Post by oldfred on 2010-10-15
I do not know about SSDs nor RAID. Which drive is the SSD? And when you say you cloned sde to it, did it also copy some RAID metadata from the sde drive?

But if sde is not RAID, you need to remove the hidden RAID metadata. DO NOT run this against sdc or sdd as it will destroy your raid configuration.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sde
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

