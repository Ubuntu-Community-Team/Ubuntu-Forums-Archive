---
title: "Editing menu.lst for multiple Linux distros"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by balkrishna on 2010-02-19
My hard disk is :
/dev/sda2   Primary Linux ext3
/dev/sda3   Primary Windows
/dev/sda5   Logical Linux ext3   /boot
/dev/sda6   Logical Swap   
/dev/sda7   Logical Linux Ext3   /home
/dev/sda8   Logical Linux ext3   /
I did install Ubuntu 9.10 with /dev/sda8 as /   => logical
/dev/sda7 as /home logical
/dev/sda6 as swap logical
/dev/sda5 as /boot logical

After this install I wished to try out Backtrack 4 which I installed on /dev/sda2 .
The version of GRUB which was installed with Ubuntu 9.10 got wiped out and the version of GRUB with backtrack was installed . However the menu did not consist of the Ubuntu 9.10 booting option . How should I edit menu.lst so that I can get all my Ubuntu 9.10 booting option along with my backtrack installation

---

### Post by kansasnoob on 2010-02-19
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You'll probably need to use the Ubuntu Live CD. I'll do a little reading about Backtrack 4.

---

### Post by kansasnoob on 2010-02-19
I see that Backtrack is Debian/Ubuntu based so this shouldn't be too difficult :D

---

### Post by balkrishna on 2010-02-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 PwnSauce
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 2453506 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2             160,650    21,125,474    20,964,825  83 Linux
/dev/sda3    *     21,133,312   204,843,007   183,709,696   7 HPFS/NTFS
/dev/sda4         204,844,815   312,576,704   107,731,890   5 Extended
/dev/sda5         204,844,878   206,274,599     1,429,722  83 Linux
/dev/sda6         206,274,663   208,379,114     2,104,452  82 Linux swap / Solaris
/dev/sda7         208,379,178   288,912,959    80,533,782  83 Linux
/dev/sda8         288,913,023   312,576,704    23,663,682  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-060B                              vfat       DellUtility                   
/dev/sda2        f3fa2672-7df8-4bdc-92aa-371cb487f60f   ext3                                     
/dev/sda3        18001DC5001DAAB0                       ntfs                                     
/dev/sda5        0a77a5c4-3bad-412e-9ffa-5936b2a118a4   ext4                                     
/dev/sda6        bb14a827-be2a-484c-bc3f-445d5d503b5a   swap                                     
/dev/sda7        6e818aa8-5c8f-464b-a824-0a90557c1edb   ext4                                     
/dev/sda8        e244f48e-a25f-4e28-8f87-58b2399f8fe8   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda3        /media/Win               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda2/boot/grub/menu.lst: ===========================

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
timeout		10

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
# kopt=root=UUID=f3fa2672-7df8-4bdc-92aa-371cb487f60f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f3fa2672-7df8-4bdc-92aa-371cb487f60f

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
## e.g. defoptions=vga=0x317 resume=/dev/hda5
# defoptions=vga=0x317

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

splashimage=f3fa2672-7df8-4bdc-92aa-371cb487f60f/boot/grub/splash.xpm.gz

title           Ubuntu 9.10, kernel i.dont.know
root            (hd0,7)
kernel          /vmlinuz root=/dev/sda8 ro quiet splash
initrd          /initrd.img 
boot 

title		Ubuntu 8.10, kernel 2.6.29.4
uuid		f3fa2672-7df8-4bdc-92aa-371cb487f60f
kernel		/boot/vmlinuz-2.6.29.4 root=UUID=f3fa2672-7df8-4bdc-92aa-371cb487f60f ro vga=0x317 
initrd		/boot/initrd.img-2.6.29.4
quiet

title		Ubuntu 8.10, kernel 2.6.29.4 (recovery mode)
uuid		f3fa2672-7df8-4bdc-92aa-371cb487f60f
kernel		/boot/vmlinuz-2.6.29.4 root=UUID=f3fa2672-7df8-4bdc-92aa-371cb487f60f ro  single
initrd		/boot/initrd.img-2.6.29.4

title		Ubuntu 8.10, memtest86+
uuid		f3fa2672-7df8-4bdc-92aa-371cb487f60f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Professional
root		(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=f3fa2672-7df8-4bdc-92aa-371cb487f60f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=bb14a827-be2a-484c-bc3f-445d5d503b5a none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


   1.2GB: boot/grub/menu.lst
   1.2GB: boot/grub/stage2
   1.2GB: boot/initrd.img-2.6.29.4
   1.2GB: boot/vmlinuz-2.6.29.4
   1.2GB: initrd.img
   1.2GB: initrd.img.old
   1.2GB: vmlinuz

================================ sda3/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

============================= sda5/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set e244f48e-a25f-4e28-8f87-58b2399f8fe8
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0a77a5c4-3bad-412e-9ffa-5936b2a118a4
	linux	/vmlinuz-2.6.31-16-generic root=UUID=e244f48e-a25f-4e28-8f87-58b2399f8fe8 ro   quiet splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0a77a5c4-3bad-412e-9ffa-5936b2a118a4
	linux	/vmlinuz-2.6.31-16-generic root=UUID=e244f48e-a25f-4e28-8f87-58b2399f8fe8 ro single 
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0a77a5c4-3bad-412e-9ffa-5936b2a118a4
	linux	/vmlinuz-2.6.31-14-generic root=UUID=e244f48e-a25f-4e28-8f87-58b2399f8fe8 ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0a77a5c4-3bad-412e-9ffa-5936b2a118a4
	linux	/vmlinuz-2.6.31-14-generic root=UUID=e244f48e-a25f-4e28-8f87-58b2399f8fe8 ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 18001dc5001daab0
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda5: Location of files loaded by Grub: ===================


 105.0GB: grub/core.img
 105.0GB: grub/grub.cfg
 105.0GB: initrd.img-2.6.31-14-generic
 105.0GB: initrd.img-2.6.31-16-generic
 105.0GB: vmlinuz-2.6.31-14-generic
 105.0GB: vmlinuz-2.6.31-16-generic

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=e244f48e-a25f-4e28-8f87-58b2399f8fe8 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=0a77a5c4-3bad-412e-9ffa-5936b2a118a4 /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=6e818aa8-5c8f-464b-a824-0a90557c1edb /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=bb14a827-be2a-484c-bc3f-445d5d503b5a none            swap    sw              0       0
=======Devices which don't seem to have a corresponding hard drive==============

hda 

```

---

### Post by kansasnoob on 2010-02-20
You have two options:

#1. Add Ubuntu to the Backtrack menu.lst.

#2. Restore Ubuntu's grub2 and run "sudo update-grub" to add Backtrack to it's grub.cfg.

I'll describe both in more detail after I slurp down a little more coffee.

If you happen to read this in the meanwhile I'd like to know if you have any older Ubuntu Live CD's around, or what Live CD's you do have laying around.

---

### Post by kansasnoob on 2010-02-20
Some observations first:

Backtrack is on sda2, Windows is on sda3, and Ubuntu is on sda8 but it has a separate /boot on sda5.

You must have added this to Backtracks menu.lst (the suspect portion in red):

```
## ## End Default Options ##

splashimage=f3fa2672-7df8-4bdc-92aa-371cb487f60f/boot/grub/splash.xpm.gz

[B][COLOR="Red"]title           Ubuntu 9.10, kernel i.dont.know
root            (hd0,7)
kernel          /vmlinuz root=/dev/sda8 ro quiet splash
initrd          /initrd.img 
boot [/COLOR][/B]

title		Ubuntu 8.10, kernel 2.6.29.4
uuid		f3fa2672-7df8-4bdc-92aa-371cb487f60f
kernel		/boot/vmlinuz-2.6.29.4 root=UUID=f3fa2672-7df8-4bdc-92aa-371cb487f60f ro vga=0x317 
initrd		/boot/initrd.img-2.6.29.4
quiet

title		Ubuntu 8.10, kernel 2.6.29.4 (recovery mode)
uuid		f3fa2672-7df8-4bdc-92aa-371cb487f60f
kernel		/boot/vmlinuz-2.6.29.4 root=UUID=f3fa2672-7df8-4bdc-92aa-371cb487f60f ro  single
initrd		/boot/initrd.img-2.6.29.4

title		Ubuntu 8.10, memtest86+
uuid		f3fa2672-7df8-4bdc-92aa-371cb487f60f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

That should be removed because manually editing things in the "Automagic" section of the menu.lst "breaks" the "Automagic" capability of legacy grub to "Automagically" handle kernel updates.

If you want to add Karmic to Backtracks menu.lst it should be added below this:

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
```

The same way that Windows was automatically added. It can go above or below the Windows entry.

Now, since Karmic has a separate /boot partition I'm not absolutely certain whether you'd want the legacy grub menu.lst to boot the grub2 /boot partition or the / (aka: root) partition. I could write an entry for both and then you could just delete the one that doesn't work.

What really sort of throws me is this:

> sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 2453506 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img


As I said before, Karmic's fstab shows that sda5 was it's /boot partition and it shows grub2 files/directories, but that line "Grub 0.97 is installed in the boot sector of sda5" worries me slightly. You see legacy grub = Grub 0.97, whereas grub2 = Grub 1.9*. NOTE: I used the * because the oldest I've seen is 1.96 and the newest is 1.98.

Anyway I'm a tad bit afraid that could cause some havoc if we try handing boot back to Karmic's grub2. I'm just not sure. I do think it would be preferable to have grub2 handle the boot process simply because it handles kernel updates for most installed Linux OS's.

I'll have to study that a bit and maybe ask a friend what he thinks, but for now it's probably safest to let Backtrack's legacy grub handle the boot process. **I assume that you can boot both Backtrack and Windows, eh?**

I'd like you to read the following just so you know why it's seldom wise to use a separate /boot partition (that regards legacy grub but I think the same principles apply to grub2):

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

Specifically this:

> Don't do that.

The main disadvantage of having to use a separate /boot partition is that is you want to dual boot more than one Linux installation, it is a bit tricky to get two or more linuxes to share the same separate /boot partition.
If you try, any files with the same name in the new system you might be installing will overwrite files belonging to your existing system and you will lose the boot of your existing Linux.

Anyway I'll write some proper entries for your menu.lst and post them ASAP.

---

### Post by kansasnoob on 2010-02-20
I decided it would be foolish to try and boot sda8 (your karmic /) because sda5 has the goodies:

> =================== sda5: Location of files loaded by Grub: ===================


 105.0GB: grub/core.img
 105.0GB: grub/grub.cfg
 105.0GB: initrd.img-2.6.31-14-generic
 105.0GB: initrd.img-2.6.31-16-generic
 105.0GB: vmlinuz-2.6.31-14-generic
 105.0GB: vmlinuz-2.6.31-16-generic


So I think this should be right:

```
title Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.31-16-generic root=UUID=0a77a5c4-3bad-412e-9ffa-5936b2a118a4 ro quiet splash
initrd /boot/initrd.img-2.6.31-16-generic
savedefault
boot

title Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.31-16-generic root=UUID=0a77a5c4-3bad-412e-9ffa-5936b2a118a4 ro single
initrd /boot/initrd.img-2.6.31-16-generic
savedefault
boot 
```

I hope so :)

I'm curious about your kernel. My Karmic is up to 2.6.31-20 (but that may be from proposed updates). Are you intentionally holding back kernel updates?

It doesn't really matter I guess, I'm just curious. You should know that you'll have to maually update those entries when you do have a kernel update.

I just copy-n-paste the existing entries below the existing ones, and then change all of the kernel designations, ie: from 2.6.31-16 to 2.6.31-20 in the upper-most entries.

---

### Post by meierfra. on 2010-02-20
I would use this for the Ubuntu entries in Backtrack's menu.lst:

```
title Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sda5)
[COLOR="Red"]uuid 0a77a5c4-3bad-412e-9ffa-5936b2a118a4[/COLOR]
kernel [COLOR="Red"]/vmlinuz-[/COLOR]2.6.31-16-generic root=[COLOR="Red"]UUID=e244f48e-a25f-4e28-8f87-58b2399f8fe8 [/COLOR]ro quiet splash
initrd [COLOR="Red"]/initrd[/COLOR].img-2.6.31-16-generic



title Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda5)
[COLOR="Red"]uuid 0a77a5c4-3bad-412e-9ffa-5936b2a118a4[/COLOR]
kernel [COLOR="Red"]/vmlinuz-[/COLOR]2.6.31-16-generic root=UUID=[COLOR="Red"]e244f48e-a25f-4e28-8f87-58b2399f8fe8 [/COLOR]ro single
initrd [COLOR="Red"]/initrd[/COLOR].img-2.6.31-16-generic
```


You also need to place those two entries after the line

### END DEBIAN AUTOMAGIC KERNELS LIST

otherwise they will deleted during the next backtrack kernel update.


But I'm not sure that this will work. I have seem various cases where the Backtrack grub was not able to boot Ubuntu (might be due to the "ext4" file system).  So I suggest to put Ubuntu Grub2 back in charge:


Boot from the Ubuntu LiveCD:

```
sudo mount /dev/sda8 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

Reboot and you should be able to boot into Ubuntu. Once in Ubuntu:

```
sudo update-grub
```

Reboot and  you should have an entry for Backtrack on the Grub menu.

---

### Post by kansasnoob on 2010-02-20
Thanks Meierfra :)

By all means follow his advice, he knows 100 times more than I do about such things.

He is the person I referred to when I said, "I'll have to study that a bit and maybe ask a friend what he thinks".

---

### Post by kansasnoob on 2010-02-20
> You also need to place those two entries after the line

### END DEBIAN AUTOMAGIC KERNELS LIST

otherwise they will deleted during the next backtrack kernel update.

I did try to address that issue in post #6.

So from your notes I should have used the UUID for root partition rather than the one for the boot partition???????????? I think you're right because that's what grub2 used.

I'm learning :confused: I hope.

---

### Post by meierfra. on 2010-02-20
> I did try to address that issue in post #6.
Opps. I overlooked  that part (but saying it twice won't hurt).

> I should have used the UUID for root partition rather than the one for the boot partition

Exactly,  the "root=UUID" statement in the kernel line needs to point to the root partition.

> because that's what grub2 used.
Good argument. The parameters in the kernel line are only read by the kernel and not by Grub.   So Grub 2 and Legacy Grub use the exact same parameters.

Also it needed to be

kernel /vmlinuz-2.6.31-16-generic

rather than

kernel /boot/vmlinuz-2.6.31-16-generic

since there is no /boot folder on the boot partition.

---

### Post by balkrishna on 2010-02-20
Thanks a lot guys ..... Ubuntu rocks coz of the kinda of support you get ... thanks a lot .... again

---

