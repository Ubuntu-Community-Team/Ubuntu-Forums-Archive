---
title: "Upgraded Ubuntu server to 10.04, now won't boot"
date: 2014-02-17
forum: Installation &amp; Upgrades
---

### Post by bforsse on 2014-02-17
Hi Ubuntu community, it's my first post here because I am really stuck with this upgrade, I would say I'm an intermediate user.

The upgrade from server to 10.04 went smoothly until reboot.  

Lilo starts and displays "bios data check successful", then hangs.

When I try to boot from the LinuxOLD configuration, I get:

udevd[898]: error initializing netlink socket
...
libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument
[23.636532] wait-for-root[905]: segfault at 00000030 eip b7ef4f2b esp bff8c36
0 error 4
Segmentation fault
[COLOR=#000000]Gave up waiting for root deive. Common problems:[/COLOR]
[COLOR=#000000]- Boot args (cat /proc/cmdline)[/COLOR]
[COLOR=#000000]- Check rootdelay= [/COLOR]
[COLOR=#000000]- Check root= [/COLOR]
[COLOR=#000000]- Missing modules (cat /proc/modules; ls /dev)[/COLOR]
[COLOR=#000000]ALERT! /dev/sda1 does not exist. Dropping to a shell![/COLOR]

[COLOR=#000000]Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)[/COLOR]
[COLOR=#000000]Enter 'help' for a list of built-in commands.[/COLOR]

[COLOR=#000000](initramfs)
[/COLOR]

The bootloader being used is LILO, the hard disk is still functional and I can mount it from a bootable USB stick.

My issue sounds very similar to the issue seen in this post (I am not using vmware):

[http://ubuntuforums.org/showthread.php?t=1690498](http://ubuntuforums.org/showthread.php?t=1690498)

I also tried increasing bootdelay with no luck.

Can you please give me suggestions for how to resolve this issue?  Here is the bootinfoscript result as requested in the similar post.

Thank you kindly, -Brian


```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab /etc/lilo.conf /boot/map


sda2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 643 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *             63   964,671,119   964,671,057  83 Linux
/dev/sda2         964,671,120   976,768,064    12,096,945   5 Extended
/dev/sda5         964,671,183   976,768,064    12,096,882  82 Linux swap / Solaris




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 2017 MB, 2017460224 bytes
18 heads, 17 sectors/track, 12876 cylinders, total 3940352 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *            253     3,940,351     3,940,099   6 FAT16




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        9e57b75a-7d5f-4048-a633-7bf5c0b45e24   ext3       
/dev/sda5        6403611a-f9c1-481b-aad3-7eeeda1aa73a   swap       
/dev/sdb1        6711-70CC                              vfat       UUI


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=========================== sda1/boot/grub/menu.lst: ===========================


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
# kopt=root=UUID=9e57b75a-7d5f-4048-a633-7bf5c0b45e24 ro


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


title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=9e57b75a-7d5f-4048-a633-7bf5c0b45e24 ro quiet splash
quiet


title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=9e57b75a-7d5f-4048-a633-7bf5c0b45e24 ro single


title        Ubuntu 10.04 LTS, kernel 2.6.24-16-server
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-server root=UUID=9e57b75a-7d5f-4048-a633-7bf5c0b45e24 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-server
quiet


title        Ubuntu 10.04 LTS, kernel 2.6.24-16-server (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-server root=UUID=9e57b75a-7d5f-4048-a633-7bf5c0b45e24 ro single
initrd        /boot/initrd.img-2.6.24-16-server


title        Ubuntu 10.04 LTS, kernel 2.6.22-14-server
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-server root=UUID=9e57b75a-7d5f-4048-a633-7bf5c0b45e24 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-server
quiet


title        Ubuntu 10.04 LTS, kernel 2.6.22-14-server (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-server root=UUID=9e57b75a-7d5f-4048-a633-7bf5c0b45e24 ro single
initrd        /boot/initrd.img-2.6.22-14-server


title        Ubuntu 10.04 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------


=============================== sda1/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9e57b75a-7d5f-4048-a633-7bf5c0b45e24 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6403611a-f9c1-481b-aad3-7eeeda1aa73a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
--------------------------------------------------------------------------------


============================= sda1/etc/lilo.conf: ==============================


--------------------------------------------------------------------------------
# /etc/lilo.conf - See: `lilo(8)' and `lilo.conf(5)',
# ---------------       `install-mbr(8)', `/usr/share/doc/lilo/',
#                       and `/usr/share/doc/mbr/'.


# +---------------------------------------------------------------+
# |                        !! Reminder !!                         |
# |                                                               |
# | Don't forget to run `lilo' after you make changes to this     |
# | conffile, `/boot/bootmess.txt' (if you have created it), or   |
# | install a new kernel.  The computer will most likely fail to  |
# | boot if a kernel-image post-install script or you don't       |
# | remember to run `lilo'.                                       |
# |                                                               |
# +---------------------------------------------------------------+


# Specifies the boot device.  This is where Lilo installs its boot
# block.  It can be either a partition, or the raw device, in which
# case it installs in the MBR, and will overwrite the current MBR.
#
boot=/dev/sda


# Specifies the device that should be mounted as root. (`/')
#
root=/dev/sda1


# This option may be needed for some software RAID installs.
#
# raid-extra-boot=mbr-only


# Enable map compaction:
# Tries to merge read requests for adjacent sectors into a single
# read request. This drastically reduces load time and keeps the
# map smaller.  Using `compact' is especially recommended when
# booting from a floppy disk.  It is disabled here by default
# because it doesn't always work.
#
# compact


# Installs the specified file as the new boot sector
# You have the choice between: text, bmp, and menu
# Look in lilo.conf(5) manpage for details
#
#install=menu


# Specifies the location of the map file
#
map=/boot/map


# You can set a password here, and uncomment the `restricted' lines
# in the image definitions below to make it so that a password must
# be typed to boot anything but a default configuration.  If a
# command line is given, other than one specified by an `append'
# statement in `lilo.conf', the password will be required, but a
# standard default boot will not require one.
#
# This will, for instance, prevent anyone with access to the
# console from booting with something like `Linux init=/bin/sh',
# and thus becoming `root' without proper authorization.
#
# Note that if you really need this type of security, you will
# likely also want to use `install-mbr' to reconfigure the MBR
# program, as well as set up your BIOS to disallow booting from
# removable disk or CD-ROM, then put a password on getting into the
# BIOS configuration as well.  Please RTFM `install-mbr(8)'.
#
# password=tatercounter2000


# Specifies the number of deciseconds (0.1 seconds) LILO should
# wait before booting the first image.
#
delay=90


# You can put a customized boot message up if you like.  If you use
# `prompt', and this computer may need to reboot unattended, you
# must specify a `timeout', or it will sit there forever waiting
# for a keypress.  `single-key' goes with the `alias' lines in the
# `image' configurations below.  eg: You can press `1' to boot
# `Linux', `2' to boot `LinuxOLD', if you uncomment the `alias'.
#
# message=/boot/bootmess.txt
#    prompt
#    delay=100
#    timeout=100


# Specifies the VGA text mode at boot time. (normal, extended, ask, <mode>)
#
# vga=ask
# vga=9
#




# Kernel command line options that apply to all installed images go
# here.  See: The `boot-prompt-HOWTO' and `kernel-parameters.txt' in
# the Linux kernel `Documentation' directory.
#
# append=""
 
# If you used a serial console to install Ubuntu, this option should be
# enabled by default.
# serial=


#
# Boot up Linux by default.
#
default=Linux


image=/vmlinuz
    label=Linux
    read-only
#    restricted
#    alias=1
    append="root=/dev/sda1  "
    initrd=/initrd.img


image=/vmlinuz.old
    label=LinuxOLD
    read-only
    optional
#    restricted
#    alias=2
    append="root=/dev/sda1  "
    initrd=/initrd.img.old




# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#    label=HURD
#    restricted
#    alias=3
--------------------------------------------------------------------------------


=================== sda1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


               =                boot/grub/menu.lst                             1
               =                boot/grub/stage2                               2
               =                boot/initrd.img-2.6.22-14-server               3
               =                boot/initrd.img-2.6.22-14-server.bak           3
               =                boot/initrd.img-2.6.24-16-server               3
               =                boot/initrd.img-2.6.24-16-server.bak           3
               =                boot/initrd.img-2.6.32-21-generic-pae          3
               =                boot/vmlinuz-2.6.22-14-server                  2
               =                boot/vmlinuz-2.6.24-16-server                  2
               =                boot/vmlinuz-2.6.32-21-generic-pae             2
               =                initrd.img                                     3
               =                initrd.img.old                                 3
               =                vmlinuz                                        2
               =                vmlinuz.old                                    2


=============================== StdErr Messages: ===============================


awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected



```

---

### Post by mörgæs on 2014-02-18
Hi, welcome to the fora.

You are entering a version (10.04) which most users here have abandoned. The upgrade failed (like many of them do), and still you are an upgrade away from 12.04, which is used by most people here. 

Besides, my guess is that not many here are familiar with and able to give advice about LILO. GRUB is the most common.

Have you thought of salvaging the important files and doing a fresh install of 12.04? In addition to solving the problem it will also give you the better performing ext4 file system.

---

### Post by bforsse on 2014-02-18
Bummer, i was hoping to get the system back to functional.  Thank you for the reply.  Please let me know if you or anyone has any further suggestions -Brian

---

### Post by grahammechanical on 2014-02-18
My guess, and it is a complete and utter guess, is that the Lilo configuration files need to be updated to boot Ubuntu 10.04.

When we upgrade from one version of Ubuntu to another version of Ubuntu then the Grub configuration files are also updated to load the new Linux kernels. But a Ubuntu upgrade will not update the Lilo configuration files.

So, Lilo is still looking for the previous Ubuntu Linux image and it is not finding it. And so the boot process panics and drops to a command shell.

Regards.

---

### Post by Bucky Ball on 2014-02-18
10.04 LTS server version is supported until 2015. The desktop version reached end-of-life April last year. Not only is no one using the desktop version, it is no longer supported and you will not receive updates, including security updates.

---

