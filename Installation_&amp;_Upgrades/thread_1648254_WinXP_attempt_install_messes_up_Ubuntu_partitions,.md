---
title: "WinXP attempt install messes up Ubuntu partitions, auto-mounting"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by dh003i on 2010-12-18
**Background information:** 

I need to install WinXP on my computer to use Spectraview II software for monitor profiling. Tried it under Wine, didn't work...thought about virtualization, but Graeme Gill (creator of Argyll) said that probably wouldn't work:

> The problem is that emulators often don't implement hardware details properly or at all. There's no standard way on Linux to read/write the DDC, so there is no surprise that wine doesn't emulate MSWin's API's for this. It's doubtful that any of the VM's do either. USB can be an issue too, and some instruments may not work in an emulated environment.


I already had Ubuntu 10.10 installed, so thought I'd try installing WinXP after, then recovering the MBR. Lots of headache.

**Problems installing WinXP**

My initial setup was like so (all non-swap partitions ext4):
```
/dev/sda1 -- 16GB swap
/dev/sda2 -- /boot
/dev/sda3 -- /
/dev/sda4 -- extended
  /dev/sda5 -- /backup
  /dev/sda6 -- /tmp
  /dev/sda7 -- /var
  /dev/sda8 -- /home

```

First I tried installing WinXP on /dev/sda5. I didn't realize that it had to be a primary partition. WinXP failed to install and destroyed the MBR (no OS loaded when trying to boot). I tried to reinstall GRUB2 [using this method]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), but I had GRUB & GRUB2, so didn't work. So then used the [purge & reinstall method]("file:///media/DIESEL/Grub2%20-%20Purge%20and%20Reinstall.html"), that worked. 

Second, I tried installing WinXP where /dev/sda1 was. Booted WinXP That didn't work either. I booted the WinXP CD, deleted /dev/sda1 to make it unused space, tried to create an XP partition on it (which didn't work), and tried to install XP there (which didn't work). It gave me some error about "Disk 0 ld 0 on atapi (MBR)" and "no Win XP compatible partition" and said something about not being able to create more partitions. (paraphrased).

Third, again of course my MBR was gone, so I reinstalled GRUB2 there. Now, Ubuntu 10.10 boots, but shows 16GB of unusable space in the beginning. 

**Current situation**

I've kind of "fixed" ubuntu 10.10, but the partitions are a little bit out of whack, and there is 16GB of "unusable space" where I tried to install WinXP.

See the results of [[FONT="Courier New"]mount[/FONT], [FONT="Courier New"]sudo fdisk -l[/FONT], and [FONT="Courier New"]sudo cfdisk /dev/sda[/FONT] in this pastebin]("http://pastebin.com/PJ81Mz9Z"). 

```
$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda4 on /tmp type ext4 (rw,commit=0)
/dev/sda6 on /var type ext4 (rw,commit=0)
/dev/sda1 on /boot type ext4 (rw,commit=0)
/dev/sda7 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/davidjheinrich/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=davidjheinrich)



$ sudo fdisk -l
[sudo] password for davidjheinrich: 
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004258c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1993        2022      240975   83  Linux
/dev/sda2            2023        5912    31246425   83  Linux
/dev/sda3            5913      121601   929271862    5  Extended
/dev/sda4            9803       11047    10000431   83  Linux
/dev/sda5            5913        9802    31246362   82  Linux swap / Solaris
/dev/sda6           11048       12292    10000431   83  Linux
/dev/sda7           12293      121601   878024511   83  Linux

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 22 sectors/track, 15477 cylinders
Units = cylinders of 506 * 512 = 259072 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d3285cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16       15478     3911744    c  W95 FAT32 (LBA)



$ sudo cfdisk /dev/sda
                                            cfdisk (util-linux-ng 2.17.2)

                                                 Disk Drive: /dev/sda
                                         Size: 1000204886016 bytes, 1000.2 GB
                                Heads: 255   Sectors per Track: 63   Cylinders: 121601

     Name              Flags            Part Type       FS Type                 [Label]               Size (MB)
 --------------------------------------------------------------------------------------------------------------------
                                                        Unusable                                       16384.76
     sda1              Boot              Primary        Linux ext3                                       246.76
     sda2                                Primary        Linux ext3                                     31996.34
                                         Logical        Free Space                                         0.04      *
     sda5              NC                Logical        Linux swap / Solaris                           31996.31      *
                                         Logical        Free Space                                         0.04      *
     sda4                                Primary        Linux ext3                                     10240.45      *
     sda6                                Logical        Linux ext3                                     10240.48
     sda7                                Logical        Linux ext3                                    899097.14
```

Also see the results of running [[FONT="Courier New"]sudo bash ./boot_info_script055.sh[/FONT] on this pastebin]("http://pastebin.com/D4V1Tk0Y") (see this [boot info script website]("http://bootinfoscript.sourceforge.net/")):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => No boot loader? is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     32,001,480    32,483,429       481,950  83 Linux
/dev/sda2          32,483,430    94,976,279    62,492,850  83 Linux
/dev/sda3          94,976,341 1,953,520,064 1,858,543,724   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5          94,976,406   157,469,129    62,492,724  82 Linux swap / Solaris
/dev/sda6         177,470,118   197,470,979    20,000,862  83 Linux
/dev/sda7         197,471,043 1,953,520,064 1,756,049,022  83 Linux
/dev/sda4         157,469,193   177,470,054    20,000,862  83 Linux

/dev/sda3 overlaps with /dev/sda4

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 22 sectors/track, 15477 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,064     7,831,551     7,823,488   c W95 FAT32 (LBA)


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdh1              34 3,907,029,134 3,907,029,101 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3695fb5e-2c7b-4991-928a-e2648c4e5b1d   ext4                                     
/dev/sda2        df856144-d9bf-4ea2-8829-691eee29e4a0   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        c3dc04e2-0baf-4d00-97d4-1c2c60d19802   ext4                                     
/dev/sda5        2442d81f-02f3-4833-81c2-c5b6bb83a31a   swap                                     
/dev/sda6        c0c31913-68a6-4ba6-8d4d-6391baebe119   ext4                                     
/dev/sda7        fed753a6-3668-4475-bf93-4644791a3566   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1547-F258                              vfat       DIESEL                        
/dev/sdb: PTTYPE="dos" 
/dev/sdh1        99354207-cfae-4373-8c2a-11003514ac94   ext4       Backup 1                      
/dev/sdh: PTTYPE="gpt" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda4        /tmp                     ext4       (rw,commit=0)
/dev/sda6        /var                     ext4       (rw,commit=0)
/dev/sda1        /boot                    ext4       (rw,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


============================= sda1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set df856144-d9bf-4ea2-8829-691eee29e4a0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 3695fb5e-2c7b-4991-928a-e2648c4e5b1d
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3695fb5e-2c7b-4991-928a-e2648c4e5b1d
	linux	/vmlinuz-2.6.35-23-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro   quiet splash
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3695fb5e-2c7b-4991-928a-e2648c4e5b1d
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/vmlinuz-2.6.35-23-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3695fb5e-2c7b-4991-928a-e2648c4e5b1d
	linux	/vmlinuz-2.6.35-22-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3695fb5e-2c7b-4991-928a-e2648c4e5b1d
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3695fb5e-2c7b-4991-928a-e2648c4e5b1d
	linux	/vmlinuz-2.6.32-26-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro   quiet splash
	initrd	/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3695fb5e-2c7b-4991-928a-e2648c4e5b1d
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/vmlinuz-2.6.32-26-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3695fb5e-2c7b-4991-928a-e2648c4e5b1d
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 3695fb5e-2c7b-4991-928a-e2648c4e5b1d
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda1: Location of files loaded by Grub: ===================


  16.3GB: boot/grub/core.img
  16.3GB: grub/core.img
  16.4GB: grub/grub.cfg
  16.3GB: grub/stage2
  16.5GB: initrd.img-2.6.32-26-generic
  16.4GB: initrd.img-2.6.35-22-generic
  16.4GB: initrd.img-2.6.35-23-generic
  16.4GB: vmlinuz-2.6.32-26-generic
  16.4GB: vmlinuz-2.6.35-22-generic
  16.4GB: vmlinuz-2.6.35-23-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 /               ext4    errors=remount-ro 0       1
# /backup was on /dev/sda5 during installation
#UUID=bd3a4de2-6118-4a88-9e76-9e2a153f9682 /backup         ext4    defaults        0       2
# /boot was on /dev/sda2 during installation
UUID=3695fb5e-2c7b-4991-928a-e2648c4e5b1d /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=fed753a6-3668-4475-bf93-4644791a3566 /home           ext4    defaults        0       2
# /tmp was on /dev/sda6 during installation
UUID=c3dc04e2-0baf-4d00-97d4-1c2c60d19802 /tmp            ext4    defaults        0       2
# /var was on /dev/sda7 during installation
UUID=c0c31913-68a6-4ba6-8d4d-6391baebe119 /var            ext4    defaults        0       2
# swap was on /dev/sda1 during installation
# UUID=d6e7656c-54a0-44d6-baa5-1432b296af91 none            swap    sw              0       0
UUID=2442d81f-02f3-4833-81c2-c5b6bb83a31a none            swap    sw              0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/scd1       /media/floppy1  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  16.7GB: initrd.img
  16.7GB: initrd.img.old
  16.6GB: vmlinuz
  16.6GB: vmlinuz.old

=========================== sdh1/boot/grub/menu.lst: ===========================

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
timeout		3

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
# kopt=root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3695fb5e-2c7b-4991-928a-e2648c4e5b1d

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid		3695fb5e-2c7b-4991-928a-e2648c4e5b1d
kernel		/vmlinuz-2.6.32-25-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro quiet splash 
initrd		/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid		3695fb5e-2c7b-4991-928a-e2648c4e5b1d
kernel		/vmlinuz-2.6.32-25-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro  single
initrd		/initrd.img-2.6.32-25-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		3695fb5e-2c7b-4991-928a-e2648c4e5b1d
kernel		/vmlinuz-2.6.32-24-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro quiet splash 
initrd		/initrd.img-2.6.32-24-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		3695fb5e-2c7b-4991-928a-e2648c4e5b1d
kernel		/vmlinuz-2.6.32-24-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro  single
initrd		/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic
uuid		3695fb5e-2c7b-4991-928a-e2648c4e5b1d
kernel		/vmlinuz-2.6.32-23-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro quiet splash 
initrd		/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		3695fb5e-2c7b-4991-928a-e2648c4e5b1d
kernel		/vmlinuz-2.6.32-23-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro  single
initrd		/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic
uuid		3695fb5e-2c7b-4991-928a-e2648c4e5b1d
kernel		/vmlinuz-2.6.32-22-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro quiet splash 
initrd		/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		3695fb5e-2c7b-4991-928a-e2648c4e5b1d
kernel		/vmlinuz-2.6.32-22-generic root=UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 ro  single
initrd		/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		3695fb5e-2c7b-4991-928a-e2648c4e5b1d
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdh1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=df856144-d9bf-4ea2-8829-691eee29e4a0 /               ext4    relatime,errors=remount-ro 0       1
# /backup was on /dev/sda5 during installation
UUID=bd3a4de2-6118-4a88-9e76-9e2a153f9682 /backup         ext4    relatime        0       2
# /boot was on /dev/sda2 during installation
UUID=3695fb5e-2c7b-4991-928a-e2648c4e5b1d /boot           ext4    relatime        0       2
# /home was on /dev/sda8 during installation
UUID=fed753a6-3668-4475-bf93-4644791a3566 /home           ext4    relatime        0       2
# /tmp was on /dev/sda6 during installation
UUID=c3dc04e2-0baf-4d00-97d4-1c2c60d19802 /tmp            ext4    relatime        0       2
# /var was on /dev/sda7 during installation
UUID=c0c31913-68a6-4ba6-8d4d-6391baebe119 /var            ext4    relatime        0       2
# swap was on /dev/sda1 during installation
UUID=d6e7656c-54a0-44d6-baa5-1432b296af91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdh1: Location of files loaded by Grub: ===================


 610.0GB: boot/grub/menu.lst
 610.0GB: boot/grub/stage2
 610.0GB: boot/initrd.img-2.6.32-22-generic
 610.0GB: boot/initrd.img-2.6.32-23-generic
 610.0GB: boot/initrd.img-2.6.32-24-generic
 610.0GB: boot/initrd.img-2.6.32-25-generic
 610.0GB: boot/vmlinuz-2.6.32-22-generic
 610.0GB: boot/vmlinuz-2.6.32-23-generic
 610.0GB: boot/vmlinuz-2.6.32-24-generic
 610.1GB: boot/vmlinuz-2.6.32-25-generic
 610.0GB: initrd.img
 610.0GB: initrd.img.old
    .1GB: vmlinuz
    .1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg
```

**Plan and Suggestions?**

My thinking is I'm going to run [FONT="Courier New"]sudo rsync -arux / /mnt/Backup 1[/FONT] (my 2TB backup HD's name) from a new admin user to backup, before I try anything else. I have SATA hard-drives, and wilee-nilee has told me that because my HD's are SATA, WinXP won't work well with them unless I change the BIOS to ahci/ide, but then Ubuntu might not boot. So maybe I should get Win Vista? (Spectraview II can't yet run in Windows7, so I can't use that). 

But if Windows won't even let me install, isn't there a problem even if I backup everything and try to install windows first?

---

### Post by akand074 on 2010-12-18
You only have 3 primary partitions. Meaning your allowed to make one more primary partition. Just delete whatever partition you don't want and make enough room for Windows XP (you can even leave it as unallocated space). Then boot into your Windows XP disk and choose the unallocated space to install Windows in (that way it will automatically make it Primary/NTFS and whatever other settings it may want). It will wipe out your GRUB again, so you'll have to reinstall it after that.

EDIT: I forgot to mention, if I were you I would avoid Vista. Stick with XP if you can't use 7.

---

### Post by wilee-nilee on 2010-12-18
Have you looked in the bios to see if it is set to sata or ide HD? Try the old non sata and see if Ubuntu boots if it does you should be able to do a custom install of XP in the empty space. Custom from the XP CD, to unallocated space before the Ubuntu.

This will change the partition number for Ubuntu though no big deal as MS will be in the MBR, and the grub2 bootloader can be reloaded.

---

