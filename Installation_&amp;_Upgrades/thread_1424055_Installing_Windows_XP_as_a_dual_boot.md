---
title: "Installing Windows XP as a dual boot"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Louigi Verona on 2010-03-07
I have AV Linux and Ubuntu 9.04 as dual boot. I would like to replace AV Linux with Windows XP. But when I start installation, there are several partitions presented and I cannot tell which one is which (they have similar sizes).

1. Is there any way to "mark" the correct partition so that I know where to install Windows?
2. I've read that it is better to first install Windows, then Ubuntu. Why? I do not want to delete everything to create a Win/Ubuntu dualboot. How many chances the installation will go well?

---

### Post by khelben1979 on 2010-03-07
1. You can note down the exact size of the partitions on paper and then check it out once inside the Windows XP installer.

2. So Windows won't mess up the Linux bootloader.

---

### Post by Louigi Verona on 2010-03-07
1. I did write the size down, but because the partitions have very similar size and also because Windows setup programm seems to output lightly different sizes than what linux reports, comparing sizes does not help.

2. What can be done to make sure Windows does not screw up the boot loader?

---

### Post by khelben1979 on 2010-03-07
> **Louigi Verona said:**
> 2. What can be done to make sure Windows does not screw up the boot loader?

Avoid installing it on the same harddrive is the only thing I can think of right now.

---

### Post by jflaker on 2010-03-07
> **Louigi Verona said:**
> I have AV Linux and Ubuntu 9.04 as dual boot. I would like to replace AV Linux with Windows XP. But when I start installation, there are several partitions presented and I cannot tell which one is which (they have similar sizes).

1. Is there any way to "mark" the correct partition so that I know where to install Windows?
2. I've read that it is better to first install Windows, then Ubuntu. Why? I do not want to delete everything to create a Win/Ubuntu dualboot. How many chances the installation will go well?

Why not use Virtual Box for both AV Linux and Windows XP?  Fair warning, the OSE version is limited in certain features not being available, including USB support....download and follow the instructions from Sun's site for getting the repositories and installing the app correctly.

That way you can run Ubuntu + one or more of the other OS's simultaneously.

---

### Post by Louigi Verona on 2010-03-08
I have had a dual boot before, but it was first Windows, then Linux.

I cannot choose a Virtual Box because I need Windows to run a run time critical musical application and in VB it is unacceptably slow.

---

### Post by louieb on 2010-03-08
You will need exact information about your setup. 

Get and run the [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/") 

If you want help - run the script and put the results.txt file in your next post.

---

### Post by Louigi Verona on 2010-03-09
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 2965575 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Debian GNU/Linux squeeze/sid
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf90ff90f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   189,647,324   189,647,262  83 Linux
/dev/sda2         403,504,605   625,137,344   221,632,740   5 Extended
/dev/sda5         624,800,043   625,137,344       337,302  82 Linux swap / Solaris
/dev/sda6         403,504,731   624,799,979   221,295,249  83 Linux
/dev/sda3         189,647,325   403,070,849   213,423,525  83 Linux
/dev/sda4         403,070,850   403,504,604       433,755  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        60733443-09bd-4df4-96de-e6c7945723a4   ext3                                     
/dev/sda3        a3d5a8fe-c1e5-4899-a930-77837f573c33   ext3                                     
/dev/sda4        7d32aad1-3b7b-4e1d-9082-a23759165399   swap                                     
/dev/sda5        fe031795-dbc1-402f-816f-7572d56e95c2   swap                                     
/dev/sda6        6373ef58-0ca6-44ce-b0e1-7dfaf9497052   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro,commit=600)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
## e.g. kopt=root=UUID=60733443-09bd-4df4-96de-e6c7945723a4 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=60733443-09bd-4df4-96de-e6c7945723a4 ro

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
# defoptions=

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.30.1-avlinux-lowlatency-pae
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.30.1-avlinux-lowlatency-pae root=UUID=60733443-09bd-4df4-96de-e6c7945723a4 ro 
initrd        /boot/initrd.img-2.6.30.1-avlinux-lowlatency-pae

title        Debian GNU/Linux, kernel 2.6.30.1-avlinux-lowlatency-pae (single-user mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.30.1-avlinux-lowlatency-pae root=UUID=60733443-09bd-4df4-96de-e6c7945723a4 ro single
initrd        /boot/initrd.img-2.6.30.1-avlinux-lowlatency-pae

title        Debian GNU/Linux, kernel memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Ubuntu 9.04 (9.04), kernel-2.6.28-11-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=#
UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro  quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04 (9.04), kernel-2.6.28-11-generic (single-user mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=#
UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro single
initrd        /boot/initrd.img-2.6.28-11-generic


title        Ubuntu 9.04 (9.04), kernel-2.6.28-17-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=#
UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro  quiet splash
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04 (9.04), kernel-2.6.28-17-generic (single-user mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-17-generic root=#
UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro single
initrd        /boot/initrd.img-2.6.28-17-generic


title        Ubuntu 9.04 (9.04), kernel-2.6.28-3-rt
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-3-rt root=#
UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro  quiet splash
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04 (9.04), kernel-2.6.28-3-rt (single-user mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-3-rt root=#
UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro single
initrd        /boot/initrd.img-2.6.28-3-rt


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# /dev/sda1
UUID=60733443-09bd-4df4-96de-e6c7945723a4 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda3 home
UUID=a3d5a8fe-c1e5-4899-a930-77837f573c33 /home ext3 relatime 0 0
# /dev/sda4
UUID=7d32aad1-3b7b-4e1d-9082-a23759165399 none swap sw 0 0
# cdrom
/dev/sr0 /media/cdrom udf,iso9660 user,noauto,exec,utf8 0 0


=================== sda1: Location of files loaded by Grub: ===================


   1.5GB: boot/grub/menu.lst
   1.5GB: boot/grub/stage2
   1.5GB: boot/initrd.img-2.6.30.1-avlinux-lowlatency-pae
   1.5GB: boot/vmlinuz-2.6.30.1-avlinux-lowlatency-pae
   1.5GB: initrd.img
   1.5GB: vmlinuz

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
# kopt=root=UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6373ef58-0ca6-44ce-b0e1-7dfaf9497052

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
uuid        6373ef58-0ca6-44ce-b0e1-7dfaf9497052
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid        6373ef58-0ca6-44ce-b0e1-7dfaf9497052
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        6373ef58-0ca6-44ce-b0e1-7dfaf9497052
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        6373ef58-0ca6-44ce-b0e1-7dfaf9497052
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        6373ef58-0ca6-44ce-b0e1-7dfaf9497052
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        6373ef58-0ca6-44ce-b0e1-7dfaf9497052
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        6373ef58-0ca6-44ce-b0e1-7dfaf9497052
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        6373ef58-0ca6-44ce-b0e1-7dfaf9497052
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        6373ef58-0ca6-44ce-b0e1-7dfaf9497052
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional RU
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
# / was on /dev/sda6 during installation
UUID=6373ef58-0ca6-44ce-b0e1-7dfaf9497052 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=fe031795-dbc1-402f-816f-7572d56e95c2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 278.3GB: boot/grub/menu.lst
 277.1GB: boot/grub/stage2
 277.0GB: boot/initrd.img-2.6.28-11-generic
 277.1GB: boot/initrd.img-2.6.28-17-generic
 278.3GB: boot/initrd.img-2.6.28-18-generic
 312.2GB: boot/initrd.img-2.6.28-3-rt
 277.1GB: boot/vmlinuz-2.6.28-11-generic
 277.1GB: boot/vmlinuz-2.6.28-17-generic
 247.8GB: boot/vmlinuz-2.6.28-18-generic
 277.0GB: boot/vmlinuz-2.6.28-3-rt
 278.3GB: initrd.img
 312.2GB: initrd.img.old
 247.8GB: vmlinuz
 277.0GB: vmlinuz.old

---

### Post by louieb on 2010-03-09
AV Linux is in sda1 - Ubuntu is in sda6, Ubuntu uses sda5 for swap.

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf90ff90f

Partition  Boot         Start           End          Size  Id System

[COLOR=Red]/dev/sda1    *             63   189,647,324   189,647,262  83 Linux[/COLOR]
/dev/sda3         189,647,325   403,070,849   213,423,525  83 Linux
 /dev/sda4         403,070,850   403,504,604       433,755  82 Linux swap / Solaris
/dev/sda2         403,504,605   625,137,344   221,632,740   5 Extended
[COLOR=Red]/dev/sda6         403,504,731   624,799,979   221,295,249  83 Linux[/COLOR]
/dev/sda5         624,800,043   625,137,344       337,302  82 [COLOR=Red]Linux swap / Solaris[/COLOR]

```

Hope this helped.

BTW: Something odd about sda2 and sda3 - No UUID - what have you used to partition with? 

```

blkid -c /dev/null: __________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        60733443-09bd-4df4-96de-e6c7945723a4   ext3                                     
/dev/sda3        a3d5a8fe-c1e5-4899-a930-77837f573c33   ext3                                     
/dev/sda4        7d32aad1-3b7b-4e1d-9082-a23759165399   swap                                     
/dev/sda5        fe031795-dbc1-402f-816f-7572d56e95c2   swap                                     
/dev/sda6        6373ef58-0ca6-44ce-b0e1-7dfaf9497052   ext3                                     

```

---

