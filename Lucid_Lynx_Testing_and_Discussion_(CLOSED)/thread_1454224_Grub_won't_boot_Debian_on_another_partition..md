---
title: "Grub won't boot Debian on another partition."
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by frankzen on 2010-04-14
I've been running Lucid for a few days now - This morning update brought in a new version of Grub. Now Debian on hda2 won't boot. Grub has replaced references to hda2 with those da**ed UUID's. Fine but it still won't boot Debian. 

Lucid is on hda3 (which Ubuntu refers to as sda3 for some reason) and Grub is installed in the MBR.

Even tried going into /etc/default/grub and uncommenting the line which is supposed to prevent Grub from using UUID's. Ran update-grub but no change the UUID's are still there. Fine for Lucid which boots fine...but no go for Debian.

Any ideas from anyone??

---

### Post by ibuclaw on 2010-04-14
> **frankzen said:**
> 
Lucid is on hda3 (which Ubuntu refers to as sda3 for some reason) and Grub is installed in the MBR.


You should keep up with the times... As of around 2007, PATA and SATA are now handled by the libata library. It calls all the drives sd*.

See [http://linux-ata.org/](http://linux-ata.org/)

Regards

---

### Post by frankzen on 2010-04-14
Yeah..well thanks for all your help.

---

### Post by kansasnoob on 2010-04-14
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Actually if grub2 is working properly simply running the command "sudo update-grub" should find Debian.

---

### Post by frankzen on 2010-04-14
> **kansasnoob said:**
> Please post the output of the Boot Info Script as described here:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/hda and looks on the same drive in 
    partition #3 for /boot/grub.

hda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of hda2 and looks 
                       at sector 32573594 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Debian GNU/Linux squeeze/sid
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

hda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 30.0 GB, 30003240960 bytes
15 heads, 63 sectors/track, 62010 cylinders, total 58600080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000b504

Partition  Boot         Start           End          Size  Id System

/dev/hda1                  63       394,064       394,002  82 Linux swap / Solaris
/dev/hda2             394,065    29,065,364    28,671,300  83 Linux
/dev/hda3    *     29,788,290    57,436,154    27,647,865  83 Linux
/dev/hda4          57,436,216    58,599,449     1,163,234   5 Extended
/dev/hda5          57,436,218    58,599,449     1,163,232  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1                                               swap                                     
/dev/hda2        e27e5d70-6d89-407c-a7c0-078ae4a0e704   ext3                                     
/dev/hda3        3fbd293c-4ebd-46f0-a349-9ccca909dd6b   ext3                                     
/dev/hda5                                               swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/hda2        /                        ext3       (rw,errors=remount-ro)
/dev/hda3        /media/intrepid          ext3       (rw,noexec,nosuid,nodev)


=========================== hda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=3fbd293c-4ebd-46f0-a349-9ccca909dd6b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3fbd293c-4ebd-46f0-a349-9ccca909dd6b

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
##      altoptions=(single-user) single
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

title		Debian GNU/Linux, kernel 2.6.32-3-686
root		3fbd293c-4ebd-46f0-a349-9ccca909dd6b
kernel		/boot/vmlinuz-2.6.32-3-686 root=UUID=3fbd293c-4ebd-46f0-a349-9ccca909dd6b ro quiet splash
initrd		/boot/initrd.img-2.6.32-3-686

title		Debian GNU/Linux, kernel 2.6.32-3-686 (recovery mode)
root		3fbd293c-4ebd-46f0-a349-9ccca909dd6b
kernel		/boot/vmlinuz-2.6.32-3-686 root=UUID=3fbd293c-4ebd-46f0-a349-9ccca909dd6b ro single
initrd		/boot/initrd.img-2.6.32-3-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.32-3-686 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-3-686 root=/dev/hda2 ro quiet 
initrd		/boot/initrd.img-2.6.32-3-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.32-3-686 (single-user mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-3-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.32-3-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.30-2-686 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.30-2-686 root=/dev/hda2 ro quiet 
initrd		/boot/initrd.img-2.6.30-2-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.30-2-686 (single-user mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.30-2-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.30-2-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.30-1-686 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.30-1-686 root=/dev/hda2 ro quiet 
initrd		/boot/initrd.img-2.6.30-1-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.30-1-686 (single-user mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.30-1-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.30-1-686
savedefault
boot


=============================== hda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/dvd      udf,iso9660 rw,user,noauto,unhide     0       0
/dev/hdd        /media/dvd-rom   udf,iso9660 rw,user,noauto,unhide     0       0
#/dev/fd0        /media/floppy0    auto    rw,user,noauto  0       0
/dev/hda3       /media/intrepid    auto    rw,user,auto     0       2
/dev/sda1       /media/FlashDrive  vfat    rw,user,auto    0       0
/dev/sdb1       /media/camera      vfat    rw,user,auto       0       0



=================== hda2: Location of files loaded by Grub: ===================


  10.6GB: boot/grub/menu.lst
  10.6GB: boot/initrd.img-2.6.32-3-686
  10.5GB: boot/vmlinuz-2.6.32-3-686
  10.6GB: initrd.img
  10.5GB: vmlinuz

=========================== hda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
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
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
	linux	/boot/vmlinuz-2.6.32-19-generic root=/dev/sda3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
	echo	'Loading Linux 2.6.32-19-generic ...'
	linux	/boot/vmlinuz-2.6.32-19-generic root=/dev/sda3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-18-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
	linux	/boot/vmlinuz-2.6.28-18-generic root=/dev/sda3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
	echo	'Loading Linux 2.6.28-18-generic ...'
	linux	/boot/vmlinuz-2.6.28-18-generic root=/dev/sda3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.28-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
	linux	/boot/vmlinuz-2.6.27-17-generic root=/dev/sda3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.27-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.27-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
	echo	'Loading Linux 2.6.27-17-generic ...'
	linux	/boot/vmlinuz-2.6.27-17-generic root=/dev/sda3 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.27-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 3fbd293c-4ebd-46f0-a349-9ccca909dd6b
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Debian GNU/Linux, kernel 2.6.32-3-686 (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e27e5d70-6d89-407c-a7c0-078ae4a0e704
	linux /boot/vmlinuz-2.6.32-3-686 root=/dev/hda2 ro quiet splash
	initrd /boot/initrd.img-2.6.32-3-686
}
menuentry "Debian GNU/Linux, kernel 2.6.32-3-686 (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e27e5d70-6d89-407c-a7c0-078ae4a0e704
	linux /boot/vmlinuz-2.6.32-3-686 root=/dev/hda2 ro single
	initrd /boot/initrd.img-2.6.32-3-686
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== hda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=3fbd293c-4ebd-46f0-a349-9ccca909dd6b /               ext3    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/sda5       none            swap    sw              0       0
/dev/sda2       /media/sda2     ext3    rw,auto,user              0       2

=================== hda3: Location of files loaded by Grub: ===================


  16.6GB: boot/grub/core.img
  16.6GB: boot/grub/grub.cfg
  16.6GB: boot/grub/stage2
  16.7GB: boot/initrd.img-2.6.27-17-generic
  16.7GB: boot/initrd.img-2.6.28-18-generic
  16.6GB: boot/initrd.img-2.6.32-19-generic
  16.7GB: boot/vmlinuz-2.6.27-17-generic
  16.7GB: boot/vmlinuz-2.6.28-18-generic
  16.7GB: boot/vmlinuz-2.6.32-19-generic
  16.6GB: initrd.img
  16.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hdc hdd 

```




Actually if grub2 is working properly simply running the command "sudo update-grub" should find Debian.

It found it...but used UUID's - the system then wouldn't boot. Since then I have gone into grub.cfg and manually changed the UUID's to /dev/hda2 without which the system will not boot.

It now boots, but I am still wondering why it won't boot when UUID's are used. Could it be something to do with the fact the original grub was installed in the boot sector of hda2. This is a leftover - Debian squeeze WAS the last system installed ( Now Lucid is the last).

Does any of this make any sense ????:popcorn:

---

### Post by kansasnoob on 2010-04-14
Well this is interesting, sadly I don't have a definitive answer but I'll do some "thinking out loud" here and maybe you can give some feedback and we'll figure it out.

Before I get into the really interesting part let me make a couple of observations, maybe just pointing out things you already know. First I know from recently trying Squeeze that it still does use the **hda** designation, whereas Ubuntu uses only **sda**.

That can matter so look at this entry in Lucid's grub.cfg:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Debian GNU/Linux, kernel 2.6.32-3-686 (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e27e5d70-6d89-407c-a7c0-078ae4a0e704                                           
	linux /boot/vmlinuz-2.6.32-3-686 root=**[COLOR="Red"]/dev/hda2[/COLOR]** ro quiet splash
	initrd /boot/initrd.img-2.6.32-3-686
}
menuentry "Debian GNU/Linux, kernel 2.6.32-3-686 (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set e27e5d70-6d89-407c-a7c0-078ae4a0e704
	linux /boot/vmlinuz-2.6.32-3-686 root=**[COLOR="Red"]/dev/hda2[/COLOR]** ro single
	initrd /boot/initrd.img-2.6.32-3-686
}
### END /etc/grub.d/30_os-prober ###
```

That certainly could make a difference in the long run.

Next you may know but the grub.cfg file is actually not meant to be directly edited. The following link is IMHO the best guide around regarding grub2 (not a light read):

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Now for the interesting part, from your results.txt the "blkid -c /dev/null" shows the Debian UUID as e27e5d70-6d89-407c-a7c0-078ae4a0e704 and the Ubuntu UUID as 3fbd293c-4ebd-46f0-a349-9ccca909dd6b:

```
/dev/hda2        e27e5d70-6d89-407c-a7c0-078ae4a0e704   ext3                                     
/dev/hda3        3fbd293c-4ebd-46f0-a349-9ccca909dd6b   ext3                                     
```

But when I look at Debian's menu.lst the UUID is different (I pasted in the one in red just for comparison):

```
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3fbd293c-4ebd-46f0-a349-9ccca909dd6b ro
                 **[COLOR="Red"]e27e5d70-6d89-407c-a7c0-078ae4a0e704[/COLOR]**
## default grub root device
## e.g. groot=(hd0,0)
# groot=3fbd293c-4ebd-46f0-a349-9ccca909dd6b
```

So I'm scratching my head as to why even Debian's own menu.lst would have it's own UUID wrong :confused:

Was this partition copied at some point? This is an interesting puzzle :)

---

### Post by frankzen on 2010-04-14
Well, as I said the ONLY way to get Debian to boot was to go back to /dev/hda2 instead of the UUID. Before I edited the grub.cfg file I modified the /etc/default/grub file to NOT do UUIDs. Then I ran update-grub...but it insisted on using UUIDs for Ubuntu and Debian partitions. That's when I said " screw it " and hand edited the file.
That's when Debian could be booted.

As to the difference between  UUIDs ... I have no explanation, except to say the boot sector of hda2 still contains the old version of Grub which was installed a couple of years back. Maybe there is a difference/conflict between the two I dunno.

As far as I can see Grub 2 is still not ready for prime time - I have seen too many problems even on the Debian User list related to the way it handles things. One guy is even pushing LILO as a replacement for Grub 2!!!
About a year ago Debian testing updates offered to install Grub 2 so I went for it. Problem was it did not install osprober which is need to help Grub 2 find other OS'es . That left me without a bootable Ubuntu partition. And created so many problems I almost deleted both partitions and started from scratch. And why wasn't Osprober at least a Debian "recommendtion"...no explanation from the developers.
When Grub 2 was installed on my System last weekend (Lucid Beta)...it also failed to carry over an important kernel command line (i925.mode=1) which keeps my Intel graphics in line.

Thanks for your thoughts anyway...I have filed a bug on Grub 2...dunno whether it'll do any good.

---

### Post by nanog on 2010-04-14
Gotta say that grub2 has been flawless on most of my installs. I have had just as many problems with legacy grub which liked to write itself to raid arrays or unix drives.

---

### Post by ranch hand on 2010-04-14
I would recommend adding this to your /etc/grub.d/40_custom file;
```

echo "Adding Debian on hda2" >&2 
cat << EOF
menuentry "Debian on hda2" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
EOF

```
I think that will work even with the reference to sda2 in the linux line.  I boot lenny with that.

You could also just do this;

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

and be done with it.

---

### Post by jrothwell97 on 2010-04-14
Coincidentally, I was mulling a thread on this very issue.

As far as I know, the only way to fix it is to replace the references to "sda" in the Debian boot line with "hda" manually, every time grub.cfg is regenerated.

I'm not sure if upstream will bother trying to fix this (since the only major distributions still using kernels that are old enough to worry about are debian-stable and -testing and DSL), but I'd hazard a guess that the best and easiest way to fix it would be to implement some kind of version check on the kernel, and adjust the output to grub.cfg accordingly.

Just my two cents' worth.

---

### Post by ranch hand on 2010-04-14
> **jrothwell97 said:**
> Coincidentally, I was mulling a thread on this very issue.

As far as I know, the only way to fix it is to replace the references to "sda" in the Debian boot line with "hda" manually, every time grub.cfg is regenerated.

I'm not sure if upstream will bother trying to fix this (since the only major distributions still using kernels that are old enough to worry about are debian-stable and -testing and DSL), but I'd hazard a guess that the best and easiest way to fix it would be to implement some kind of version check on the kernel, and adjust the output to grub.cfg accordingly.

Just my two cents' worth.
I can tell you that the grub in 10.04 is quite a bit different than the grub in 9.10.

I would try the entry for your /40_custom file I gave above.  Should edit to fit your box remembering tht the partition number is the one gparted uses and the (hd0) number starts with 0 as in grub-legacy.

That should boot any Debian based OS that is on that partition (do not change the reference to sd in the linux line with out trying it first).

Ofcoarse you must run;
```

sudo update-grub

```
to have this on your menu.

This is what the 40_custom file is there for.  This is how you edit the /boot/grub/cfg file.

---

### Post by frankzen on 2010-04-14
> **ranch hand said:**
> I would recommend adding this to your /etc/grub.d/40_custom file;
```

echo "Adding Debian on hda2" >&2 
cat << EOF
menuentry "Debian on hda2" {
    set root=(hd0,2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img
}
EOF

```
I think that will work even with the reference to sda2 in the linux line.  I boot lenny with that.

You could also just do this;

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

and be done with it.


I'll try your suggestion...and we'll see what happens when the next kernel comes down the line :P

If all else fails -- grub legacy is waiting!

---

### Post by frankzen on 2010-04-14
> **jrothwell97 said:**
> Coincidentally, I was mulling a thread on this very issue.

As far as I know, the only way to fix it is to replace the references to "sda" in the Debian boot line with "hda" manually, every time grub.cfg is regenerated.

That's gotta be a pain - I'll try the other suggestion first.


> **jrothwell97 said:**
> I'm not sure if upstream will bother trying to fix this (since the only major distributions still using kernels that are old enough to worry about are debian-stable and -testing and DSL), but I'd hazard a guess that the best and easiest way to fix it would be to implement some kind of version check on the kernel, and adjust the output to grub.cfg accordingly.

Probably not - I recall their reaction to suggestions osprober be included in the new grub package :)

Thanks

---

### Post by ranch hand on 2010-04-14
Do remember, if you go back to grub-legacy, that it is no longer supported by the grub project folks.

---

### Post by kansasnoob on 2010-04-14
Just to give you an idea how thoroughly I've tested grub2 here's a "blkid" from a previous testing installation:

```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       bc1516d1-981b-4797-a1ad-7379b2e5fa67   ext3       Hardy Home                    
/dev/sda11       3128dea7-b986-4b45-8004-0b48bf97f9dd   ext3       Lucid Home                    
/dev/sda12       33b90c3d-da7e-4671-b78a-5adafb0a927d   ext3       Karmic Root                   
/dev/sda13       4f260672-aff0-4912-9bb3-5e8c2b6158d2   ext3       Karmic Home                   
/dev/sda14       bc99fdc7-0dd8-40e7-8567-f0882352d256   swap                                     
/dev/sda15       16ebe9de-80aa-42c0-804f-ccdd81e43e95   ext3                                     
/dev/sda16       5ebdcaaf-da9e-4695-847e-200054e7559e   ext3                                     
/dev/sda17       115e96dd-3ef5-4cee-8e2b-7ef6a5e1a9ef   ext3       Pictures                      
/dev/sda18       84f9bd6c-4042-495a-99c5-2136f706bfc3   ext3       Debian Root                   
/dev/sda19       c67d9b53-8226-4c67-ab44-2f189e058b47   ext3       Debian Home                   
/dev/sda1        C02402022401FC62                       ntfs       Windows XP                    
/dev/sda2: PTTYPE="dos" 
/dev/sda3        91760bb5-455b-4adc-8e34-a8f2d5cae023   ext3                                     
/dev/sda5        6ceb25f1-5904-490b-a7cc-d14b9d63c3b7   ext3       Jaunty Root                   
/dev/sda6        238b5ad8-c8fd-4c65-a190-1828af9fe54a   ext3       Jaunty Home                   
/dev/sda7        51ebb887-909b-43cb-b022-1300ddd78074   ext3       Gloria Root                   
/dev/sda8        2c9d2789-e4b6-46c3-b9c8-145951f916cc   ext3       Gloria Home                   
/dev/sda9        ee620c21-7f87-41fb-a7af-d868f72ce754   ext3       Hardy Root                    
/dev/sda: PTTYPE="dos" 
/dev/sdb10       63839fec-0a76-40f4-b049-12469e5eee7b   ext3       Backups                       
/dev/sdb1        5A3CAE183CADEEE7                       ntfs       Old Win XP                    
/dev/sdb2        4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1   ext4       Fedora-12-i686-L              
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        dcdced28-c63f-4405-b143-05876492b04d   ext4       Fedora 12 Home                
/dev/sdb6        58aec1b2-6dfe-4f02-b77d-207fe6cc5551   swap                                     
/dev/sdb7        571cfad8-68c7-4703-883e-c0baa2a381d4   ext3       Documents                     
/dev/sdb8        05289ee4-d681-4806-b6fd-aefd784f9323   ext3       Downloads                     
/dev/sdb9        ded953b6-3c52-4b2b-9053-d5d99f193f5e   ext3       Pictures                      
/dev/sdb: PTTYPE="dos" 
```

Here's the full results.txt just in case anyone is curious:

[ATTACH]153290[/ATTACH]

But I had grub2 in Lucid controlling the boot of everything there and it required NO fiddling around at all! Nothing was needed but "sudo update-grub"! Not even with Fedora on a separate drive. The only modification I'd made to grub2 was eliminating the memtest option.

Anyway, in that scenario Squeeze also had grub2 and if you look at the "/etc/grub.d/30_os-prober" section of it's grub.cfg or it's fstab you'll see it was using the **[COLOR="Red"]hd[/COLOR]** prefix (I highlighted just a few examples in red):

```
========================== sda18/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
insmod ext2
set root=(hd0,18)
search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
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
set locale_dir=/boot/grub/locale
set lang=en
insmod gettext
set timeout=60
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,18)
search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Debian GNU/Linux, with Linux 2.6.32-trunk-686" {
	insmod ext2
	set root=(hd0,18)
	search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
	echo	Loading Linux 2.6.32-trunk-686 ...
	linux	/boot/vmlinuz-2.6.32-trunk-686 root=UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 ro  splash quiet quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-trunk-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-trunk-686 (recovery mode)" {
	insmod ext2
	set root=(hd0,18)
	search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
	echo	Loading Linux 2.6.32-trunk-686 ...
	linux	/boot/vmlinuz-2.6.32-trunk-686 root=UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 ro single  splash quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-trunk-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on **[COLOR="Red"]/dev/hda1[/COLOR]**)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c02402022401fc62
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on **[COLOR="Red"]/dev/hda12[/COLOR]**)" {
	insmod ext2
	set root=(hd0,12)
	search --no-floppy --fs-uuid --set 33b90c3d-da7e-4671-b78a-5adafb0a927d
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/hda12)" {
	insmod ext2
	set root=(hd0,12)
	search --no-floppy --fs-uuid --set 33b90c3d-da7e-4671-b78a-5adafb0a927d
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-16-generic (on /dev/hda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 9c10b8f7-89d3-4a72-a0ab-e89d061653b0
	linux /boot/vmlinuz-2.6.32-16-generic root=UUID=9c10b8f7-89d3-4a72-a0ab-e89d061653b0 ro quiet splash
	initrd /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-16-generic (recovery mode) (on /dev/hda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 9c10b8f7-89d3-4a72-a0ab-e89d061653b0
	linux /boot/vmlinuz-2.6.32-16-generic root=UUID=9c10b8f7-89d3-4a72-a0ab-e89d061653b0 ro single
	initrd /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (on /dev/hda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6ceb25f1-5904-490b-a7cc-d14b9d63c3b7
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro quiet splash
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/hda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6ceb25f1-5904-490b-a7cc-d14b9d63c3b7
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro single
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-15-generic (on /dev/hda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 51ebb887-909b-43cb-b022-1300ddd78074
	linux /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-15-generic (recovery mode) (on /dev/hda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 51ebb887-909b-43cb-b022-1300ddd78074
	linux /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/hda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set ee620c21-7f87-41fb-a7af-d868f72ce754
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro quiet splash
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/hda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set ee620c21-7f87-41fb-a7af-d868f72ce754
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro single
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Microsoft Windows XP Home Edition (on /dev/hdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 5a3cae183cadeee7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Fedora (2.6.31.12-174.2.22.fc12.i686) (on /dev/hdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1
	linux /boot/vmlinuz-2.6.31.12-174.2.22.fc12.i686 ro root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.12-174.2.22.fc12.i686.img
}
menuentry "Fedora (2.6.31.5-127.fc12.i686) (on **[COLOR="Red"]/dev/hdb2[/COLOR]**)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1
	linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda18/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on **[COLOR="Red"]/dev/hda18[/COLOR]** during installation
UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 /               ext3    errors=remount-ro 0       1
# /home was on **[COLOR="Red"]/dev/hda19[/COLOR]** during installation
UUID=c67d9b53-8226-4c67-ab44-2f189e058b47 /home           ext3    defaults        0       2
# swap was on /dev/hda14 during installation
UUID=bc99fdc7-0dd8-40e7-8567-f0882352d256 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

However look at the Squeeze entries in Lucid's grub.cfg:

```
menuentry "Debian GNU/Linux, with Linux 2.6.32-trunk-686 (on **[COLOR="Red"]/dev/sda18[/COLOR]**)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
	linux /boot/vmlinuz-2.6.32-trunk-686 root=UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 ro splash quiet quiet
	initrd /boot/initrd.img-2.6.32-trunk-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-trunk-686 (recovery mode) (on **[COLOR="Red"]/dev/sda18[/COLOR]**)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
	linux /boot/vmlinuz-2.6.32-trunk-686 root=UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 ro single splash quiet
	initrd /boot/initrd.img-2.6.32-trunk-686
}
```

Yes it uses the **[COLOR="Red"]sd[/COLOR]** prefix :)

So I think the "wrong" UUID thing is the root of the problem. You may have noticed that I'm the one who wrote that detailed HowTo that Ranch Hand linked to about reverting to legacy grub.

I also helped someone at the Debian forums:

[http://forums.debian.net/viewtopic.php?f=17&t=50132](http://forums.debian.net/viewtopic.php?f=17&t=50132)

You'll notice there are some differences particularly in package names. Like the package "grub" in Ubuntu is equivalent to the package "grub-legacy" in Squeeze.

Anyway you can see I've grown quite comfortable playing with both legacy grub and grub2. I don't mean that as bragging by any means :)

It's just that I've grown so comfortable with it that I don't worry about breaking grub (any version)! That's great for me because if I'm between the chair and the keyboard I know how to start from scratch if I really hose things :)

OTOH it's not so good if someone on the other end hoses things and gets left in the lurch waiting for me to help them fix things. And a lot can get lost in translation. Hey, I even goof sometimes :P

I'm really only bringing this up because since you can boot it's probably wise to wait until you really have time to fiddle around, and it would be great if I could be available at the same time. That could be hard or nearly impossible.

Anyway, back to diagnosing your machine. Look at your Debian menu.lst (again highlighting some examples in red):

```
## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.32-3-686
root		**[COLOR="Red"]3fbd293c-4ebd-46f0-a349-9ccca909dd6b[/COLOR]**
kernel		/boot/vmlinuz-2.6.32-3-686 root=UUID=3fbd293c-4ebd-46f0-a349-9ccca909dd6b ro quiet splash
initrd		/boot/initrd.img-2.6.32-3-686

title		Debian GNU/Linux, kernel 2.6.32-3-686 (recovery mode)
root		3fbd293c-4ebd-46f0-a349-9ccca909dd6b
kernel		/boot/vmlinuz-2.6.32-3-686 root=UUID=3fbd293c-4ebd-46f0-a349-9ccca909dd6b ro single
initrd		/boot/initrd.img-2.6.32-3-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on **[COLOR="Red"]/dev/sda2[/COLOR]**.
title		Debian GNU/Linux, kernel 2.6.32-3-686 (on **[COLOR="Red"]/dev/sda2[/COLOR]**)
root		**[COLOR="Red"](hd0,1)[/COLOR]**
kernel		/boot/vmlinuz-2.6.32-3-686 root=/dev/hda2 ro quiet 
initrd		/boot/initrd.img-2.6.32-3-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.32-3-686 (single-user mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.32-3-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.32-3-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.30-2-686 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.30-2-686 root=/dev/hda2 ro quiet 
initrd		/boot/initrd.img-2.6.30-2-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.30-2-686 (single-user mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.30-2-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.30-2-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.30-1-686 (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.30-1-686 root=/dev/hda2 ro quiet 
initrd		/boot/initrd.img-2.6.30-1-686
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Debian GNU/Linux, kernel 2.6.30-1-686 (single-user mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.30-1-686 root=/dev/hda2 ro single 
initrd		/boot/initrd.img-2.6.30-1-686
savedefault
boot
```

We've already discussed the UUID problem but you'll notice that menu.lst seems to have shown a different Debian on sda2 :confused: Odd to say the least.

I should also pause here and explain the difference in legacy grub and grub2 numbering. Drive numbering has remained the same, that is sda or hda still amount to 0 (zero) in both legacy grub and grub2.

**But partition numbering in grub2 has changed!** Where partitions began with 0 (zero) in legacy grub they now begin with 1 (one) in grub2!

So in legacy grub sda2 = (hd0,1).
Whereas in grub2 sda2 = (hd0,2).

Just something you should know :)

Anyway your Debian menu.lst appears to be a total mess. Now I do know that grub2 "reads" some info from any existing "grub". For instance if I use "startupmanager" in a legacy grub OS and choose to NOT have it show the recovery mode or memtest mode for that OS then grub2 respects that.

I honestly wish I knew what grub2 looked at first for info! Existing bootloaders? The fstab? Maybe blkid? I just don't know.

So, from what I see combined with my own experiences, I would personally first check to see what "grub" packages are installed in Squeeze. You should be able to do that by booting into Squeeze and running the command:

```
aptitude show grub-legacy|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```

I'm honestly reluctant to proceed until I see the output of that command. But where I'm going is cleaning up your Squeezes grub (either creating a clean menu.lst or grub.cfg) and then purging your old Lucid grub2 config and starting fresh there :)

---

### Post by frankzen on 2010-04-22
Still having trouble with the new Grub. Just today I tried again to get it to write a grub.cfg that will boot Debian on another partition. It first of all insists on using UUID's...even though I have commented out the
appropriate line in /etc/default/grub . Problem is when it uses UUIDs Lucid boots fine...but Debian squeeze doesn't. It starts, but then ends up at the Ubuntu splash screen with 4 dots and sits there with the dots moving back and forth :) I have to go in, and blantantly disregard the no-edit warning and replace the UUID with /dev/hda2.

Now the release candidate is coming with no solution to my problem.
Anybody have any ideas????

---

### Post by dino99 on 2010-04-22
thats let me thinking about plymouth rather than grub: remove/purge plymouth then reinstall it 

or run sudo dpkg-reconfigure plymouth

one of my system have multi boot with sid, i use grub2 from lucid to boot it: grub2 installed on LBR (sda). If you have doubts, run sudo grub-mkconfig then sudo update-grub

note: you might let the system use uuid , you might have less troubles.

---

### Post by frankzen on 2010-04-22
>>thats let me thinking about plymouth rather than grub: >>remove/purge plymouth then reinstall it 

Did that. No change.


>>or run sudo dpkg-reconfigure plymouth

Did that too.

>>>run sudo grub-mkconfig then sudo update-grub

Also done. No change

>>you might let the system use uuid , you might have less >>troubles.

Can't do that. Debian won't boot when Grub uses UUIDs. It MUST HAVE /dev/hda2 in grub.cfg or it goes nowhere. Well it gets to the Ubuntu flashscreen and the 4 dots just go back and forth, back and forth..back and forth. You get it.

I've filed a bug

But if they release the RC with as many bugs in it as there are now......I dunno.

Thanks for trying.

---

### Post by kansasnoob on 2010-04-22
Did you even read my last post in your old thread?

[http://ubuntuforums.org/showthread.php?p=9123144#post9123144](http://ubuntuforums.org/showthread.php?p=9123144#post9123144)

---

### Post by frankzen on 2010-04-22
No, as a matter of fact. I am not in these forums that much...and never got notified by the faultless instant notification system :) Read it just now. All that stuff is interesting..and it probably qualifies you as "The Grub Expert" for these forums. Nevertheless, not knowing you had replied...I thought I would cast another line and see what I could bring in. In the meantime, I filed a bug on Grub2.

Here's what it boils down to:
There is no grub package on Debian squeeze,the bootloader was in the MBR of hda/sda, whichever ie preferred. That was effectively eliminated when I installed Lucid. Grub2 went into the MBR. So I fail to see the connection between Grub and Grub2 or Squeeze and Lucid. Unless of course Grub2 looks at menu.lst or osprober does when it's looking for other OS'es.

Today I went through the routine again: Change /etc/default/grub to NOT use UUID's, and re-run update-grub. Same result. Discovered that the (true) at the end of the line has to be in double-quotes. Filed a bug. Re-ran update-grub after adding quotes. This time it created the Lucid lines NOT using UUID's...but still created the Debian lines using UUID's. Can you beat that!

Colin Watson is handling the bug - just gave him grub.cfg.

Thanks

---

### Post by frankzen on 2010-04-22
Here's the output of your aptitude command:

root@squeeze:~# aptitude show grub-legacy|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common

Package: grub-legacy
State: not installed
Version: 0.97-59
Priority: optional
Package: grub-pc
State: not installed
Version: 1.98-1
Priority: extra
Package: grub-common
State: not installed
Version: 1.98-1
Priority: extra
Section: admin
Maintainer: GRUB Maintainers <pkg-grub-devel@lists.alioth.debian.org>
Uncompressed Size: 2,970k
Depends: base-files (>= 4.0.1~), dpkg (>= 1.15.4) | install-info | dpkg (<= 1.14.25), libc6 (>= 2.3), libfreetype6 (>= 2.2.1), zlib1g (>= 1:1.1.4), gettext-base
Recommends: os-prober (>= 1.33)
Suggests: multiboot-doc, grub-emu
Conflicts: grub-doc (< 0.97-32), grub-legacy-doc (< 0.97-59), mdadm (< 2.6.7-2)
Replaces: grub-coreboot (< 1.97+20091114-1), grub-efi (< 1.96+20080831-1), grub-ieee1275 (< 1.96+20080831-1), grub-linuxbios (< 1.96+20080831-1), grub-pc (< 1.97+20091114-1)
Description: GRand Unified Bootloader, version 2 (common files)
 This package contains common files shared by the distinct flavours of GRUB.
Homepage: [http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)

That's it: We'll see what the dev boys say.

---

### Post by ranch hand on 2010-04-22
The package is not grub-legacy.  The package is grub.

Grub2 is grub-pc

They both use the same grub-common.

---

### Post by kansasnoob on 2010-04-22
> **ranch hand said:**
> The package is not grub-legacy.  The package is grub.

Grub2 is grub-pc

They both use the same grub-common.

Ranch hand, "grub-legacy" is right. I wanted to see what packages are installed in his Debian, not his Ubuntu :)

FYI if he'd run that command in Lucid the result would be:

```
lance@lance-desktop:~$ aptitude show grub-legacy|head -4
No current or candidate version found for grub-legacy
Package: grub-legacy
State: not a real package

```

---

### Post by kansasnoob on 2010-04-22
> **frankzen said:**
> Here's the output of your aptitude command:

root@squeeze:~# aptitude show grub-legacy|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common

Package: grub-legacy
State: not installed
Version: 0.97-59
Priority: optional
Package: grub-pc
State: not installed
Version: 1.98-1
Priority: extra
Package: grub-common
State: not installed
Version: 1.98-1
Priority: extra
Section: admin
Maintainer: GRUB Maintainers <pkg-grub-devel@lists.alioth.debian.org>
Uncompressed Size: 2,970k
Depends: base-files (>= 4.0.1~), dpkg (>= 1.15.4) | install-info | dpkg (<= 1.14.25), libc6 (>= 2.3), libfreetype6 (>= 2.2.1), zlib1g (>= 1:1.1.4), gettext-base
Recommends: os-prober (>= 1.33)
Suggests: multiboot-doc, grub-emu
Conflicts: grub-doc (< 0.97-32), grub-legacy-doc (< 0.97-59), mdadm (< 2.6.7-2)
Replaces: grub-coreboot (< 1.97+20091114-1), grub-efi (< 1.96+20080831-1), grub-ieee1275 (< 1.96+20080831-1), grub-linuxbios (< 1.96+20080831-1), grub-pc (< 1.97+20091114-1)
Description: GRand Unified Bootloader, version 2 (common files)
 This package contains common files shared by the distinct flavours of GRUB.
Homepage: [http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)

That's it: We'll see what the dev boys say.

I'm going to do just a bit of experimenting on my own machine, but you see you have no grub packages installed and yet you have some old grub menu.lst that doesn't match anything.

I'm willing to bet that Lucid's grub2 is reading bad info from that old menu.lst. As I said previously I know for a fact that grub2 does "read" some info from other OS's bootloaders. I'm just not totally sure what.

Besides I'm in the midst of a bad thunderstorm and the odds of a power outage are quite likely :)

---

### Post by kansasnoob on 2010-04-22
OK look, below I added two stars "**" to end of the UUID in my Squeeze's menu.lst entry:

```
hiddenmenu
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=2d74adb5-1d41-46b0-b1ae-c0a2bf65cdcd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,11)

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
# defoptions=quiet

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.32-trunk-686
root		(hd0,11)
**kernel		/boot/vmlinuz-2.6.32-trunk-686 root=UUID=2d74adb5-1d41-46b0-b1ae-c0a2bf65cdcd[COLOR="Red"]**[/COLOR] ro quiet**
initrd		/boot/initrd.img-2.6.32-trunk-686

title		Debian GNU/Linux, kernel 2.6.32-trunk-686 (single-user mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.32-trunk-686 root=UUID=2d74adb5-1d41-46b0-b1ae-c0a2bf65cdcd ro single
initrd		/boot/initrd.img-2.6.32-trunk-686

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Then I ran "sudo update-grub" in Lucid and look at it's grub.cfg entry:

```
menuentry "Debian GNU/Linux, kernel 2.6.32-trunk-686 (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 2d74adb5-1d41-46b0-b1ae-c0a2bf65cdcd
	**linux /boot/vmlinuz-2.6.32-trunk-686 root=UUID=2d74adb5-1d41-46b0-b1ae-c0a2bf65cdcd[COLOR="Red"]**[/COLOR] ro quiet**
	initrd /boot/initrd.img-2.6.32-trunk-686
}
menuentry "Debian GNU/Linux, kernel 2.6.32-trunk-686 (single-user mode) (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 2d74adb5-1d41-46b0-b1ae-c0a2bf65cdcd
	linux /boot/vmlinuz-2.6.32-trunk-686 root=UUID=2d74adb5-1d41-46b0-b1ae-c0a2bf65cdcd ro single
	initrd /boot/initrd.img-2.6.32-trunk-686
}

```

So that proves what I'm saying :)

Lucid's grub2 is not borked, it's just reading borked info from that old menu.lst.

Should you doubt me here's the whole Boot Info Script RESULTS.txt:

[ATTACH]154063[/ATTACH]

In the next post I'll discuss possible remedies.

---

### Post by kansasnoob on 2010-04-22
What I've found multi-booting other Linux OS's from grub2 is that having no grub.cfg or menu.lst to read is that it will boot but no recovery mode is produced for that OS in grub2, and I consider a recovery mode a necessity, so I'd recommend backing up Squeeze's old /boot/grub, creating a new one, and then installing either legacy grub or grub2.

I tend to prefer using legacy grub for my "other" OS's because it still plays well with startupmanager so I can "graphically" choose how many kernels to show, whether or not to show the memtest or recovery mode for that OS, etc. That's how my Squeeze is set up right now.

One sort of odd thing I ran into was that I couldn't get the "update-grub" command to produce a menu.lst unless I actually installed grub somewhere, so I installed it to the partition like you would if you were going to chain-load, but I'm not chain-loading.

So **[COLOR="Red"]if you want to do that[/COLOR]** boot into Squeeze, become root and:

```
mv /boot/grub /boot/grub_old
```

```
mkdir /boot/grub
```

```
apt-get install grub-legacy
```

```
grub-install /dev/hda2
```

```
update-grub
```

That should ask if you want to create a menu.lst, yes you do!

Next I'd boot into Lucid and since you've edited some files other than grub.cfg I'd:

```
sudo apt-get install --reinstall grub-pc
```

Hopefully that will restore the grub2 files to their original state (if not you might have to purge and reinstall "grub-pc").

Then just:

```
sudo update-grub
```

And see what the results are.

---

### Post by kansasnoob on 2010-04-22
Well, I've just got to say "I'm 99% sure I've found the problem":)

In fact to begin with I wish 23meg would combine these two threads:

[http://ubuntuforums.org/showthread.php?t=1454224](http://ubuntuforums.org/showthread.php?t=1454224)

Clearly Lucid's grub2 is reading bad info from that old menu.lst. where did that come from?

Colin will not know that if this is your bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/568538](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/568538)

So he'll waste precious time that could be spent actually fixing bugs :)

Then people will have less of an excuse to say things like:

> But if they release the RC with as many bugs in it as there are now......I dunno.

Those are your own words :)

This is not a bug! Lucid's grub2 is reading info from that Squeeze menu.lst which was obviously NOT even generated in that Squeeze because the package "grub-legacy" is not installed. Nor is grub-pc.

---

### Post by frankzen on 2010-04-22
> **kansasnoob said:**
> Well, I've just got to say "I'm 99% sure I've found the problem":)

learly Lucid's grub2 is reading bad info from that old menu.lst. where did that come from?

Not true. I moved menu.lst out of the way. Re-running update-grub leaves me with a grub.cfg that refers to hda2 as sda2...and leaves the boot
"waiting for root filesystem"


> **kansasnoob said:**
> This is not a bug! Lucid's grub2 is reading info from that Squeeze menu.lst which was obviously NOT even generated in that Squeeze because the package "grub-legacy" is not installed. Nor is grub-pc.

The menu.lst was leftover from when grub-legacy was installed. Purge doesn't, as you should know.

---

### Post by kansasnoob on 2010-04-22
Well I'm done!

I've explained in your other thread all I possibly can!

---

### Post by drs305 on 2010-04-22
> **frankzen said:**
> Discovered that the (true) at the end of the line has to be in double-quotes. Filed a bug. Re-ran update-grub after adding quotes. This time it created the Lucid lines NOT using UUID's...but still created the Debian lines using UUID's. Can you beat that!

Colin Watson is handling the bug - just gave him grub.cfg.

Thanks

Nice catch! At one time the *true* was quoted but that changed at some point in the development. I know they changed how quotes were treated several weeks ago. I guess they didn't catch this problem. I'll update my guides to reflect the need to add the quotes but would expect this bug to be fixed fairly quickly.

---

### Post by Bert Mariën on 2010-04-23
Same here.
I get a kernel panic when I try to load Mandriva or PCLinuxOS.

---

### Post by Bert Mariën on 2010-04-23
Can this be (one of) the reason(s)?

A disk is in both GRUB's referred to differently.

--------------------GRUB------------GRUB2
/dev/sda1-------(hd0,0)---------(hd0,1)
/dev/sdb1-------(hd1,0)---------(hd1,1)

So, when GRUB2 passes on (let us say for sda1) (hd0,1), but once the kernel of a distro still using GRUB is loading, it expects (hd0,0)

Does this make sense?

---

### Post by frankzen on 2010-04-23
> **drs305 said:**
> Nice catch! At one time the *true* was quoted but that changed at some point in the development. I know they changed how quotes were treated several weeks ago. I guess they didn't catch this problem. I'll update my guides to reflect the need to add the quotes but would expect this bug to be fixed fairly quickly.


Hold on! Further experimentation shows the quotes are NOT needed- in one case on my machine quoting true **seemed** to work..but since then it hasn't made any difference.

My problem now is that grub.cfg refers to the second partition on my hd as sda2..and that won't boot. To run Debian which is on the second partition I have to manually edit grub.cfg and change it to hda2. Using UUIDs doesn't work either for some unknown reason.

---

### Post by Bert Mariën on 2010-04-23
I think you better take a look at your debian menu.lst.

I fixed my problem by fixing the menu.lst files in Mandriva and PCLinuxOS.
After that I ran update-grub and everything just worked fine.

Also see that there is only one kernel in your bootfolder (menu.lst).

---

### Post by philinux on 2010-04-23
Threads merged.

---

### Post by dino99 on 2010-04-23
Everything has already been explained here and if that dont work for you, well you are the main bug, no offense anyway but check yourself first.

- grub (=grub-legacy= grub1) is not grub2 (=grub-pc)
- all hdd, ide & sata, are named as sdx by grub2, no more hdx

- if both grub & grub2 are installed on your system (same distro or an other somewhere else), you got wrong settings due to os-prober (part of grub-mkconfig) taking settings from menu.list (grub-legacy) instead of new grub2 partitions naming. That means, if you make choice of grub2, and you might as its the actual and future design, remove/purge everything about grub1 on all your multi boot system (dont worry grub2 installed on lucid or on an other distro is able to find and boot each one) 

- install grub2 (grub-pc package) on your mbr distro partition
- run sudo grub-mkconfig
- run update-grub

- reboot

You can check grub2 installation into console: grub-install
of course, there is no problem to install it on every mbr distro, but in case of older grub-pc package provide by a distro , prefer to boot with the more recent one. Just dont install grub2 on the windows partition if you have one, anyway grub-mkconfig via os-prober will find it and add it to grub.cfg

That's all, it works well and if you cant take time to read/understand this thread, well its your problem and myself stopped this buzz.

---

### Post by frankzen on 2010-04-23
> **Bert Mariën said:**
> I think you better take a look at your debian menu.lst.

I fixed my problem by fixing the menu.lst files in Mandriva and PCLinuxOS.
After that I ran update-grub and everything just worked fine.

Also see that there is only one kernel in your bootfolder (menu.lst).

I don't have a menu.lst anymore in /boot/grub on the partition which won't boot.

I don't see the connection anyway - if you grep all the files associated with update-grub, menu.lst does not appear. And what if you were booting using Lilo...you wouldn't have a menu.lst.

My problem is a little different as well - update-grub refuses to generate UUIDs for the troublesome partition...and if told not to generate UUIDs it refers to the partition as /dev/sda2...which then won't boot Debian.

---

### Post by frankzen on 2010-04-23
> Everything has already been explained here and if that dont work for you, well you are the main bug, no offense anyway but check yourself first.

:lolflag:


> - grub (=grub-legacy= grub1) is not grub2 (=grub-pc)
I never said different.

> - all hdd, ide & sata, are named as sdx by grub2, no more hdx

Yeah, so ?

> if both grub & grub2 are installed on your system (same distro or an other somewhere else), you got wrong settings due to os-prober (part of grub-mkconfig) taking settings from menu.list (grub-legacy) instead of new grub2 partitions naming.

Grub is not installed on either partition. And AFAIK, os-prober does not refer to menu.lst.


> That means, if you make choice of grub2, and you might as its the actual and future design, remove/purge everything about grub1 on all your multi boot system (dont worry grub2 installed on lucid or on an other distro is able to find and boot each one) 

Grub is not installed

> - install grub2 (grub-pc package) on your mbr distro partition

Grub2 was installed with Lucid

> - run sudo grub-mkconfig

Many times

> - run update-grub

Many times

> - reboot

Many times

> That's all, it works well and if you cant take time to read/understand this thread, well its your problem and myself stopped this buzz.

Sorry but your the one who hasn't taken the time to read and understand the thread.

It's very simple. Grub is not installed, Grub2 is.
update-grub creates a grub.cfg file which refers to root as /dev/sda2.
This will NOT boot Debian testing on the other partition.
update-grub will not create a grub.cfg containing UUIDs which will boot
Debian testing.

---

### Post by drs305 on 2010-04-23
A gentle reminder to all to keep things civil on this thread. Let's try to stay constructive.

frankzen, have you approached the debian community for assistance on this one? Grub 2 is not a proprietary Ubuntu bootloader and perhaps others using debian have dealt with this issue. 

There is also the #grub channel on the Ubuntu Server (IRC).

---

### Post by frankzen on 2010-04-23
> **drs305 said:**
> A gentle reminder to all to keep things civil on this thread. Let's try to stay constructive.

I'm trying to, under difficult circumstances :)

> frankzen, have you approached the debian community for assistance on this one? Grub 2 is not a proprietary Ubuntu bootloader and perhaps others using debian have dealt with this issue. 

Yes I had thought of that but there is, how should I say it, a certain reluctance on the Debian forums and lists about dealing with Ubuntu
problems. I have a foot in both camps so it's tough. Nevertheless that's
what I'll end up doing.

---

### Post by ranch hand on 2010-04-23
Your Debian install is using grub2 isn't it?  Have you tried chrooting into it and changing to using its boot loader?  Or installing grub2 there?  If they are using a kernel 2.6.30 or above it should support ext4 fine.

I use PhatDebian (Lenny respin with the ..30 kernel) to boot my main drive with 9.04 (ext4) on it.  No trouble at all booting or file sharing even with PhD installed on ext3.  That is using grub1.68.

---

### Post by QLee on 2010-04-23
[QUOTE=frankzen]Yes I had thought of that but there is, how should I say it, a certain reluctance on the Debian forums and lists about dealing with Ubuntu
problems. I have a foot in both camps so it's tough. Nevertheless that's
what I'll end up doing.[/QUOTE]

Ha! Yes, something about the "meaning" of the name Ubuntu, eh? From some people who do know how to configure, Debian.

You wouldn't have to mention Ubuntu.

Do you still have a device.map in that sda2/(hda2) boot/grub partition? What does it show?

I imagine that if you just delete the /boot/grub/ folder in partition 2 of drive 1 (just the grub folder) and then run grub-update  from your Lucid install that your system might work as you desire (if nothing is changed from what you have already posted, like menu.lst, you did have one now you say you don't).

---

### Post by frankzen on 2010-04-23
> **ranch hand said:**
> Your Debian install is using grub2 isn't it?  

No, the Debian install WAS using the original grub - I purged it before installing Lucid on hda3 (sda3). But the config files remained in /boot/grub for a while. I moved them out when someone here suggested the old menu.lst was messing up update-grub. There was no change after it was moved out. AFAIK update-grub does not reference menu.lst..it **may** reference  device.map...but it's gone too.

I don't use ext4.

---

### Post by frankzen on 2010-04-23
> **QLee said:**
> Ha! Yes, something about the "meaning" of the name Ubuntu, eh? From some people who do know how to configure, Debian.

You wouldn't have to mention Ubuntu.


Some of those Debian users are "touchy" about Ubuntu.

> Do you still have a device.map in that sda2/(hda2) boot/grub partition? What does it show?


No, I had one in there, but moved it out along with everything else when someone here suggested it may have been messing up update-grub.

> I imagine that if you just delete the /boot/grub/ folder in partition 2 of drive 1 (just the grub folder) and then run grub-update  from your Lucid install that your system might work as you desire

I may get to that point soon :) What I may try is renaming it, and try update-grub. My big problem now is grub.cfg keeps referring to sda2 when it creates grub.cfg. It calls the Lucid partitiion sda3 but that boots fine. Debian always has refused to boot when the root is called anything but hda3.
I have even tried telling update-grub to create UUIDs...it does but only for the Lucid partition. It refers to hda3 as sda3 :confused:

---

### Post by QLee on 2010-04-23
[QUOTE=frankzen]Some of those Debian users are "touchy" about Ubuntu.[/QUOTE]

Ya. Some of them are a bit "elitist" (and some of them with good reason, they are expert) and some just get tired of going through a couple of pages of trying to help someone and then find out the issue is because of something that Ubuntu does differently and the poster didn't divulge the OS being used (some people think based on Debian means the "same" as Debian). 

[QUOTE=frankzen]I may get to that point soon :) What I may try is renaming it, and try update-grub. My big problem now is grub.cfg keeps referring to sda2 when it creates grub.cfg. It calls the Lucid partitiion sda3 but that boots fine. Debian always has refused to boot when the root is called anything but hda3.
I have even tried telling update-grub to create UUIDs...it does but only for the Lucid partition. It refers to hda3 as sda3 :confused:[/QUOTE]

Yes, I think I followed that. If you already have an empty /boot/grub/ on that 2nd partition (you cleared it) deleting the empty directory isn't likely to change anything. I don't remember seeing anywhere in this thread the exact error message dropped when the system doesn't boot your Debian install, what is it?


Edit: I don't imagine you are going to be able to stop the prober from using the modern designations for the device node, as already mentioned newer kernels and thus, the newer GRUB use the newer designations.

---

### Post by frankzen on 2010-04-23
> **QLee said:**
> Ya. Some of them are a bit "elitist" (and some of them with good reason, they are expert) and some just get tired of going through a couple of pages of trying to help someone and then find out the issue is because of something that Ubuntu does differently and the poster didn't divulge the OS being used (some people think based on Debian means the "same" as Debian).

Yup :)
 



> I don't remember seeing anywhere in this thread the exact error message dropped when the system doesn't boot your Debian install, what is it?


Waiting for root..a common error message when things screw up :)

> 
I don't imagine you are going to be able to stop the prober from using the modern designations for the device node, as already mentioned newer kernels and thus, the newer GRUB use the newer designations.

Yeah, I know. sda is the way of the future :) If I could just get grub.cfg to create the Debian entry using UUIDs I'd be happy. For now I can edit grub.cfg (despite the fact it says not to) but you know what'll happen when a new kernel shows its face.

---

### Post by QLee on 2010-04-23
[QUOTE=frankzen]
Yeah, I know. sda is the way of the future :) If I could just get grub.cfg to create the Debian entry using UUIDs I'd be happy. For now I can edit grub.cfg (despite the fact it says not to) but you know what'll happen when a new kernel shows its face.[/QUOTE]

Another possible workaround until you find the "key" (there has to be something we haven't thought of yet or something you tried which didn't work and didn't get set back as it was, the update-grub from the Lucid install should have discovered the Debian install). As a workaround create static entries in the grub.d 40_custom and unset the execute bit from the prober, that'll break the system well and good and you can manually edit the grub.cfg after a kernel update. Just checking, your Lucid is fully upgraded to this point isn't it?

---

### Post by QLee on 2010-04-23
Another thought frankzen, 
Does the fstab of that Debian install use device node or UUID, is there any chance it's choking on those old device node designations during init? This is just a WAG.

Unfortunately I don't have a system similar to yours. I can chainload from a Debian legacy grub to Ubuntu grub-pc and, on another system, Ubuntu grub-pc on a Lucid install can boot a 8.04LTS but neither of those is the exact same situation as your system.

Maybe one of the lurkers has an idea that none of the rest of us has thought of yet.

---

### Post by frankzen on 2010-04-23
Grub.cfg attached.

root=/dev/hda2


have fun:)

---

### Post by frankzen on 2010-04-23
> **QLee said:**
> Another thought frankzen, 
Does the fstab of that Debian install use device node or UUID, is there any chance it's choking on those old device node designations during init? This is just a WAG.


It uses device nodes...not UUID



> 
Another possible workaround until you find the "key" (there has to be something we haven't thought of yet or something you tried which didn't work and didn't get set back as it was, the update-grub from the Lucid install should have discovered the Debian install). As a workaround create static entries in the grub.d 40_custom and unset the execute bit from the prober, that'll break the system well and good and you can manually edit the grub.cfg after a kernel update. Just checking, your Lucid is fully upgraded to this point isn't it?

Yup, fully upgraded. I don't want to get that drastic...I can always
violate the constitution and edit grub.cfg :)

Thanks for your ideas....we'll see

ps drs305 is trying something for me.

---

### Post by drs305 on 2010-04-23
First the disclaimer: I don't have Debian on my system, I am not a script expert, and this is a bandaid, not a solution to the underlying problem.

Having stated that, the following adds a bit to the /etc/grub.d/10_linux script. I am basing this on kansasnoob's grub.cfg, which shows Debian being governed by the 10_linux script.

Open the following files as root (one to alter, the other to check afterward). Note: grub.cfg is opened just for viewing, not editing:
```
gksu gedit /etc/grub.d/10_linux /boot/grub/grub.cfg
```

From (approx line 95 of /etc/grub.d/10_linux):
> 
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF



Change to:
> 
[B][COLOR="DarkRed"]if [ ${OS} = "Debian" ]; then
linux_root_device_thisversion="/dev/hda2"
fi[/COLOR][/B]
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF


Save the file, run update-grub, then check grub.cfg to see if it did what you want.

Two things:
The OS may be a longer entry than "Debian", in which case we'll have to tweak the OS= line. You can place the following immediately above the altered section to check the value of $OS. Find the resulting line in /boot/grub/grub.cfg and use the results between the quotes in the OS="Debian" conditional line. Once you have determined the vaule remove the "echo" line.
> echo "the value of OS is "${OS}"
"
I don't know if Grub2 will pass "hda" rather than "sda". My guess it will pass whatever is on the line, and that as long as the Debian kernel accepts the input it should be ok.

I go on two weeks vacation in a few hours, so I'll be available for a short while to help tweak this mod as necessary.

EDIT: Sorry for the delay, something came up that I had to deal with.

---

### Post by frankzen on 2010-04-23
> **drs305 said:**
> First the disclaimer: I don't have Debian on my system, I am not a script expert, and this is a bandaid, not a solution to the underlying problem.

Having stated that, the following adds a bit to the /etc/grub.d/10_linux script. I am basing this on kansasnoob's grub.cfg, which shows Debian being governed by the 10_linux script.

Open the following files as root (one to alter, the other to check afterward). Note: grub.cfg is opened just for viewing, not editing:
```
gksu gedit /etc/grub.d/10_linux /boot/grub/grub.cfg
```

From (approx line 95 of /etc/grub.d/10_linux):



Change to:


Save the file, run update-grub, then check grub.cfg to see if it did what you want.

Two things:
The OS may be a longer entry than "Debian", in which case we'll have to tweak the OS= line.

I don't know if Grub2 will pass "hda" rather than "sda". My guess it will pass whatever is on the line, and that as long as the Debian kernel accepts the input it should be ok.

I go on two weeks vacation in a few hours, so I'll be available for a short while to help tweak this mod as necessary.

EDIT: Sorry for the delay, something came up that I had to deal with.
Strange, I don't see the code changes. I do in the systems email to me
so I'll do it that way.

---

### Post by frankzen on 2010-04-23
> **drs305 said:**
> First the disclaimer: I don't have Debian on my system, I am not a script expert, and this is a bandaid, not a solution to the underlying problem.

Having stated that, the following adds a bit to the /etc/grub.d/10_linux script. I am basing this on kansasnoob's grub.cfg, which shows Debian being governed by the 10_linux script.


I think this is where it's going wrong - from grub.cfg, the Debian entries
on /dev/hda2 are supposed to be picked up by the os-prober script. I made your changes to 10_linux adding the OS id line...and grub.cfg didn't change except for the line "OS is Ubuntu". /dev/sda2 still being passed to kernel boot line.

I think the os-prober script is where changes have to be made but I don't know enough about bash scripting to even think about it :)


Thanks

---

### Post by drs305 on 2010-04-23
I never got your grub.cfg file to see what is happening or to give you the exact entry to make, but if it still shows "sda" on the linux line then there is probably a mistake in the way I wrote the change. If the OS definition is correct *and* we are modifying the correct section of the grub scripts the "hda" should show up on the linux line. Whether it will be passed correctly I cannot guarantee but it should be listed as such in grub.cfg regardless.

Since kansasnoob's cfg script showed the entry in the 10_linux section, that is where I'm assuming your Debian install is being picked up and that is the file I modified. You don't need to keep the "echo" line once the name of the "OS" is - it was only to determine the value of what should be within the "Debian" quotes.

Added:
Off on 17 days vacation without a computer. Hope you get this worked out.

---

### Post by frankzen on 2010-04-24
> **drs305 said:**
> I never got your grub.cfg file to see what is happening or to give you the exact entry to make, but if it still shows "sda" on the linux line then there is probably a mistake in the way I wrote the change.

Yes it still shows "sda" - I think because we are changing the wrong script. I looked through grub.cfg and to me it looks like the extra os's are supposedto be picked up by os-prober.


> 
Off on 17 days vacation without a computer. Hope you get this worked out.


Enjoy it. I'm sure you will especially without a computer :)

---

### Post by recluce on 2010-04-24
After readin 6 pages of the /sda2 versus /hda2 trouble in GRUB2, I am wondering if it is worth the struggle. Why not re-install GRUB1 in the Debian partition (not to the MBR) and chainload into Debian's GRUB1 from Ubuntu's GRUB2?

Or (BLASPHEMY!) use GRUB1 in a dedicated partition to chainload whatever other bootloader is needed for a given OS?

---

### Post by frankzen on 2010-04-24
> **recluce said:**
> After reading 6 pages of the /sda2 versus /hda2 trouble in GRUB2, I am wondering if it is worth the struggle. Why not re-install GRUB1 in the Debian partition (not to the MBR) and chainload into Debian's GRUB1 from Ubuntu's GRUB2?

Or (BLASPHEMY!) use GRUB1 in a dedicated partition to chainload whatever other bootloader is needed for a given OS?


Or even reinstall Grub1 in the MBR. Never had this type of problem using Grub1 and it always found new kernels on the Ubuntu partition :)

Nobody is more tired of the problem than me:sad:

---

### Post by QLee on 2010-04-24
[QUOTE=recluce]After readin 6 pages of the /sda2 versus /hda2 trouble in GRUB2, I am wondering if it is worth the struggle. Why not re-install GRUB1 in the Debian partition (not to the MBR) and chainload into Debian's GRUB1 from Ubuntu's GRUB2?

Or (BLASPHEMY!) use GRUB1 in a dedicated partition to chainload whatever other bootloader is needed for a given OS?[/QUOTE]

Presumably, because we aren't here to help some newbie learn how to configure Gnome, it a Lucid testing and discussion sub forum. There is potential for us all to learn from the exercise by finding out what happened. I imagine some people have already learned some things.

But, frankzen, how did you know about what drs305 was going to post before it was posted? I thought we are all supposed to be in the same "room". And what attachment are you talking about?

I think unseting the execute bit on the prober is easier than trying to modify the script.

---

### Post by QLee on 2010-04-24
[QUOTE=frankzen]It uses device nodes...not UUID[/QUOTE]

Since nothing else is working, if I was doing this I would try with UUID in fstab but I realise that is extra work and I can't guarantee success. What happens if you rename the fstab and boot without one, does the error dropped change or is it exactly the same?

Edit: I don't know if grub-pc looks at fstab for the install at menu config time, but if you try this maybe see if the config is written differently with the fstab gone.

2nd_Edit: How did you end up with device nodes in fstab on a Squeeze install, I'm assuming Squeeze from the kernel version. Or is some backported kernel or one you rolled yourself?

---

### Post by frankzen on 2010-04-24
> **QLee said:**
> Presumably, because we aren't here to help some newbie learn how to configure Gnome, it a Lucid testing and discussion sub forum. There is potential for us all to learn from the exercise by finding out what happened. I imagine some people have already learned some things.

But, frankzen, how did you know about what drs305 was going to post before it was posted? I thought we are all supposed to be in the same "room". And what attachment are you talking about?

drs305 emailed me offering to come up with changes to the /etc/grub/010_linux script which update-grub references to try to solve the problem. It hasn't worked yet...but we were modifying the wrong script - The os-prober script I think actually does the searching for other os's.

>  I think unsetting the execute bit on the prober is easier than trying to modify the script.

I think I (we, someone) is going to have to modify it or something else to solve this problem. As a last resort I think Ill post on the Debian mailing list to see if anyone has any ideas or workarounds.

I do appreciate (nearly) all the suggestions people here have been making but even I am beginning to think this has gone on too long:confused:

---

### Post by QLee on 2010-04-24
[QUOTE=frankzen]drs305 emailed me offering to come up with changes to the /etc/grub/010_linux script which update-grub references to try to solve the problem. It hasn't worked yet...but we were modifying the wrong script - The os-prober script I think actually does the searching for other os's.[/QUOTE]

You are correct for the prober.

However, if I we were working in the same room and people started to have private side conversations about the issue we were working on, I would choose to leave the room . Note, this is not a criticism, I'm just explaining the choices I make.

[QUOTE=frankzen]I think I (we, someone) is going to have to modify it or something else to solve this problem. As a last resort I think Ill post on the Debian mailing list to see if anyone has any ideas or workarounds.[/QUOTE]

Maybe tell them you're trying from a Sid install and not mention Ubu.

Until we prove the source of the issue, it isn't really possible to say just where the problem lies or what needs to be done to correct it.

[QUOTE=frankzen]I do appreciate (nearly) all the suggestions people here have been making but even I am beginning to think this has gone on too long:confused:[/QUOTE]

It's what we're here for (well, most of us). However, if you've lost the desire and energy to keep trying things, I accept your choice. You have workarounds that will allow you to use the system as is and eventually, someone will probably have a flash of insight (heck, we might even get incite in further posts)

Good Luck, frankzen!

---

### Post by frankzen on 2010-04-24
> **QLee said:**
> Since nothing else is working, if I was doing this I would try with UUID in fstab but I realise that is extra work and I can't guarantee success. What happens if you rename the fstab and boot without one, does the error dropped change or is it exactly the same?

I don't know..but when I get a minute and can deal with any possible breakage...I may try it.

> I don't know if grub-pc looks at fstab for the install at menu config time, but if you try this maybe see if the config is written differently with the fstab gone.

Might be worth it.



> How did you end up with device nodes in fstab on a Squeeze install, I'm assuming Squeeze from the kernel version. Or is some backported kernel or one you rolled yourself?


This is an old install..I was running Sid, but it went through a period of breakage...so I changed to Squeeze. But this was about 18 months ago when there was a big debate over device nodes vs UUID :)

---

### Post by frankzen on 2010-04-24
> **QLee said:**
> You are correct for the prober.

I thought I was

> However, if I we were working in the same room and people started to have private side conversations about the issue we were working on, I would choose to leave the room . Note, this is not a criticism, I'm just explaining the choices I make.

I have no idea why he went to email --- I suspect it was because he was going on vacation in a few hours..and assumed email would be a quicker way. I dunno. Ask him :)


> re: debian list Maybe tell them you're trying from a Sid install and not mention Ubu.

Those are my plans

> 
It's what we're here for (well, most of us). However, if you've lost the desire and energy to keep trying things, I accept your choice. You have workarounds that will allow you to use the system as is and eventually, someone will probably have a flash of insight (heck, we might even get incite in further posts)

Good Luck, frankzen!

Its not a loss of desire or energy..it's a matter of time.
Thanks for the best wishes...I am gonna need them :)

---

### Post by frankzen on 2010-04-24
> **jrothwell97 said:**
> Coincidentally, I was mulling a thread on this very issue.

As far as I know, the only way to fix it is to replace the references to "sda" in the Debian boot line with "hda" manually, every time grub.cfg is regenerated.

I'm not sure if upstream will bother trying to fix this (since the only major distributions still using kernels that are old enough to worry about are debian-stable and -testing and DSL), but I'd hazard a guess that the best and easiest way to fix it would be to implement some kind of version check on the kernel, and adjust the output to grub.cfg accordingly.

Just my two cents' worth.

I was just going back through the thread and noticed you seem to be the only other person with the problem. Guess there aren't too
many Debian/Ubuntu people around.

This is a real pain however.

---

### Post by jrothwell97 on 2010-04-24
> **frankzen said:**
> I was just going back through the thread and noticed you seem to be the only other person with the problem. Guess there aren't too
many Debian/Ubuntu people around.

This is a real pain however.

It's a pain, yes, but the fault lies mostly with Debian in this case. The kernel is, sadly, antiquated by Linux standards, even if it's still rock-solid and stable.

I think your best bet is to try upgrading to Debian testing, or to use a backported kernel (if there is one - I'm not an expert on these issues.)

---

### Post by frankzen on 2010-04-24
> **jrothwell97 said:**
> It's a pain, yes, but the fault lies mostly with Debian in this case. The kernel is, sadly, antiquated by Linux standards, even if it's still rock-solid and stable.

I think your best bet is to try upgrading to Debian testing, or to use a backported kernel (if there is one - I'm not an expert on these issues.)
Apparently it is Debians problem... I am already running testing..and hesitate to use any other kernel...I've backed myself into a corner that way in the past :)

Maybe if Lucid proves to be a winner....I'll devote the while drive to it...if not I'll make Debian the only distro.

---

### Post by QLee on 2010-04-24
[QUOTE=frankzen]This is an old install..I was running Sid, but it went through a period of breakage...so I changed to Squeeze. But this was about 18 months ago when there was a big debate over device nodes vs UUID :)[/QUOTE]

So, is it currently upgraded to the same versions of packages as a new Squeeze install?

BTW, there is even a backport for GRUB2 for Lenny (Debian, stable) so you would be able to install GRUB2 from your Squeeze install, can't see how that would get the device node wrong and, if it did, we would have more data, including data you could post in a semi-hostile environment. <chuckle>

---

### Post by QLee on 2010-04-24
[QUOTE=jrothwell97]It's a pain, yes, but the fault lies mostly with Debian in this case.[/QUOTE]

Huh? Based on what evidence?

[QUOTE=jrothwell97] The kernel is, sadly, antiquated by Linux standards, even if it's still rock-solid and stable.[/QUOTE]

Huh? Based on what evidence? 

BTW, "Linux" is the kernel with free software running on it.

[QUOTE=jrothwell97]I think your best bet is to try upgrading to Debian testing, or to use a backported kernel (if there is one - I'm not an expert on these issues.)[/QUOTE]

He's already at Debian testing, that's the codename for Squeeze.

There are no backports for Squeeze, packages migrate to Squeeze from Sid.

---

### Post by QLee on 2010-04-24
BTW, frankzen, if you do post on a Debian forum I wouldn't mind following the thread so if you are willing, mention which forum. I mostly hang at Debian newsgroups like a lot of the other old guys, probably wouldn't come across your post without looking for it, I don't even know if you use the same nick all through cyberspace, I certainly don't.

---

### Post by drs305 on 2010-04-24
Just a quick cleanup post from the airport.

If the Debian listing is in the 10_linux section of grub.cfg, editing the 10_linux file will produce an altered grub.cfg. os-prober does indeed search for other operating systems. If the Debian entry had been in 30_os-prober that is the file I would have tried to edit. 

Doing a more in-depth search of the root cause of the problem may be a cleaner way to resolve the issue, but trying to change the output at the last source of input to grub.cfg (10_linux) was the most direct route to take.

@ QLee,

Regarding the use of email - these forums do not endorse the use of PM/Emails for several reasons: a) Malicious code could be sent without being under the watchful eye of the community; b) Others reading a thread wouldn't benefit from the flow of information and c) any mention of obtaining help outside forum posts would lead to more one-on-one requests, which is not desired (see a & b). 

I contacted him directly as the thread was already over 30 posts long and the tone at times was getting a bit testy. I was about to leave on an extended vacation, and the OP was off-line. I'd hoped to provide a quick solution but required a timely reply which didn't appear likely since he was not currently monitoring the forum.

This post isn't meant to be defensive; it just looked like a good opportunity to bring up a few things that users can take away from this thread whether a solution is found here or not.

---

### Post by Irihapeti on 2010-04-24
Just an idea, which may or may not be relevant.

In the course of my own testing of installations, I have discovered that OS prober was picking up stuff that I thought had been deleted from menu.lst in my old Hardy installation. On checking, I found that I indeed had. BUT, there were a couple of other files: menu.lst~ and menu.lst.save (made by me as a backup file). It might be worth checking for the presence of something of this kind and removing it/them.

---

### Post by frankzen on 2010-04-24
> **QLee said:**
> So, is it currently upgraded to the same versions of packages as a new Squeeze install?

BTW, there is even a backport for GRUB2 for Lenny (Debian, stable) so you would be able to install GRUB2 from your Squeeze install, can't see how that would get the device node wrong and, if it did, we would have more data, including data you could post in a semi-hostile environment. <chuckle>

Yup, upgraded daily.

That's one of the things I am considering - but first I thought I exhaust everyones thoughts on how to solve the problem I now face.
If nothing turns up...posting on debian.users and then perhaps installing Grub2 on /dev/hda2 (Squeeze) is next. (If I survive the flames from debian.users :) )

---

### Post by frankzen on 2010-04-24
> **Irihapeti said:**
> Just an idea, which may or may not be relevant.

In the course of my own testing of installations, I have discovered that OS prober was picking up stuff that I thought had been deleted from menu.lst in my old Hardy installation. On checking, I found that I indeed had. BUT, there were a couple of other files: menu.lst~ and menu.lst.save (made by me as a backup file). It might be worth checking for the presence of something of this kind and removing it/them.

Nope, all are gone to bit-heaven. /boot/grub on /dev/hda2 is barren.

---

### Post by frankzen on 2010-04-24
> **QLee said:**
> BTW, frankzen, if you do post on a Debian forum I wouldn't mind following the thread so if you are willing, mention which forum. I mostly hang at Debian newsgroups like a lot of the other old guys, probably wouldn't come across your post without looking for it, I don't even know if you use the same nick all through cyberspace, I certainly don't.

Will do. I am frankzen everywhere (boring eh?) I don't post a lot in debian.user mainly because I don't have that many problems..or solutions for other peoples' problems. :)

---

### Post by Irihapeti on 2010-04-24
> **frankzen said:**
> Nope, all are gone to bit-heaven. /boot/grub on /dev/hda2 is barren.

Oh, well, it was worth a try.

I've got a Debian testing install on my machine and grub2 handles it OK. Mind you, it's only a very recent addition.

If I were in your situation, I would probably disable the OS prober with chmod -x and set up a custom file with the commands that would keep Debian happy. If you point it to /vmlinuz and /initrd.img, you will automatically get the latest installed kernel, so no need to edit when Debian does a kernel upgrade.

---

### Post by frankzen on 2010-04-24
> **Irihapeti said:**
> Oh, well, it was worth a try.

If I were in your situation, I would probably disable the OS prober with chmod -x and set up a custom file with the commands that would keep Debian happy. If you point it to /vmlinuz and /initrd.img, you will automatically get the latest installed kernel, so no need to edit when Debian does a kernel upgrade.


That's a good idea...matter of fact I have some code that another person here suggested for the 010_linux script...which would probably do the job with a few mods in the custom file.

I'll give it a shot later tonight.

Thanks

---

### Post by andrewthomas on 2010-04-24
> **QLee said:**
> So, is it currently upgraded to the same versions of packages as a new Squeeze install?

BTW, there is even a backport for GRUB2 for Lenny (Debian, stable) so you would be able to install GRUB2 from your Squeeze install, can't see how that would get the device node wrong and, if it did, we would have more data, including data you could post in a semi-hostile environment. <chuckle>
This thread got me curious and I did a Squeeze install.  I installed it on a machine that has both SATA  and PATA drives, using a partition on the PATA drive.  When it came time to choose where to install the bootloader I opted to call the partition /dev/hda10 as opposed to (hd0,10) - which was the other way I could have choosen to refer to it.  By default it installed grub2 and used '(hd0,10)' in the set root statement and root=UUID= on the kernel (linux)  line.

---

### Post by frankzen on 2010-04-24
> **andrewthomas said:**
> This thread got me curious and I did a Squeeze install.  I installed it on a machine that has both SATA  and PATA drives, using a partition on the PATA drive.  When it came time to choose where to install the bootloader I opted to call the partition /dev/hda10 as opposed to (hd0,10) - which was the other way I could have choosen to refer to it.  By default it installed grub2 and used '(hd0,10)' in the set root statement and root=UUID= on the kernel (linux)  line.

That's interesting because in my installation even when /etc/default/grub has the UUID line left uncommented  (to use UUID on all drives) Grub2 sets up Debian Squeeze on hda2 with sda2 in the kernel line. It uses UUID on all the kernel lines for Lucid.

This is my fstab

#/etc/fstab: static file system information.

 Use 'blkid -o value -s UUID' to print the universally unique identifier
 for a device; this may be used with UUID= as a more robust way to name
 devices that works even if disks are added and removed. See fstab(5).

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
 / was on /dev/sda3 during installation
UUID=3fbd293c-4ebd-46f0-a349-9ccca909dd6b /               ext3    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/sda5       none            swap    sw              0       0
/dev/sda2      /media/sda2     ext3    rw,auto,user              0       2#


Sorry code block didn't work..all those # I guess.

But notice what would be /dev/sda3 uses UUID
everything else uses /dev/sdax

I have tried using blkid to get the UUID for /sda2 and using that in
fstab, but then the machine wouldn't boot even Lucid.

---

### Post by Irihapeti on 2010-04-24
> **frankzen said:**
> That's interesting because in my installation even when /etc/default/grub has the UUID line left uncommented  (to use UUID on all drives) Grub2 sets up Debian Squeeze on hda2 with sda2 in the kernel line. It uses UUID on all the kernel lines for Lucid.


I've just noticed that grub2 is doing that for my Hardy entry, but not the Debian ones. Hardy is the first on the list of other OSes.

I'm setting up a custom entry which I'm going to test shortly.

I need to use UUIDs because I have mixed SATA and IDE drives (the latter were given to me) and Ubuntu sometimes has difficulty deciding if a particular drive is /dev/sda or /dev/sdc.

---

### Post by Irihapeti on 2010-04-24
Just as I suspected might happen, update-grub gave me an OS-prober entry that Hardy proceeded to choke on.

However, my 40_custom entry worked, because I'd put the UUID in it. So, yes, that appears to be an option.

I'd say grub2's OS prober has a bug.

---

### Post by andrewthomas on 2010-04-25
> **frankzen said:**
> 
This is my fstab

#/etc/fstab: static file system information.

 Use 'blkid -o value -s UUID' to print the universally unique identifier
 for a device; this may be used with UUID= as a more robust way to name
 devices that works even if disks are added and removed. See fstab(5).

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
 / was on /dev/sda3 during installation
UUID=3fbd293c-4ebd-46f0-a349-9ccca909dd6b /               ext3    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/sda5       none            swap    sw              0       0
/dev/sda2      /media/sda2     ext3    rw,auto,user              0       2#



my debian /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/hda10 during installation
UUID=fb02d455-dc53-4fcd-bfc2-baae01430142 /               ext3    errors=remount-ro 0       1
# swap was on /dev/hda6 during installation
UUID=8a7194f0-9471-452d-a931-d105b7ed357d none            swap    sw              0       0
# swap was on /dev/sda6 during installation
UUID=99ac44f5-36be-4460-992f-c00637da84d0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```I have no idea why it does not work for you to use UUID's

---

### Post by frankzen on 2010-04-25
> **Irihapeti said:**
> Just as I suspected might happen, update-grub gave me an OS-prober entry that Hardy proceeded to choke on.

However, my 40_custom entry worked, because I'd put the UUID in it. So, yes, that appears to be an option.

I'd say grub2's OS prober has a bug.

I think so..but apparently it only rears its' head under certain
conditions.

What does your custom entry consist of ?

Thanks

---

### Post by QLee on 2010-04-25
> **QLee]So, is it currently upgraded to the same versions of packages as a new Squeeze install?

BTW, there is even a backport for GRUB2 for Lenny (Debian, stable) so you would be able to install GRUB2 from your Squeeze install, can't see how that would get the device node wrong and, if it did, we would have more data, including data you could post in a semi-hostile environment. <chuckle>[/QUOTE]


[QUOTE=frankzen said:**
> Yup, upgraded daily.

That's one of the things I am considering - but first I thought I exhaust everyones thoughts on how to solve the problem I now face.
If nothing turns up...posting on debian.users and then perhaps installing Grub2 on /dev/hda2 (Squeeze) is next. (If I survive the flames from debian.users :) )

Well, perhaps you misunderstood me, the suggestion was not as a way to get your system working, it was to obtain more data regarding the issue. And, as stated, to give you data so that you had facts with which to counter any flame posts like the ones you have previously encountered in the Debian forum.

The "problem you now face", at least according to what you have written, was not being able to boot into the Debian install and you have been given suggestions for a temporary workaround for that. If you had tried the GRUB2 from the Debian install and it did boot all your operating systems, then we could compare the revision level of the two GRUBs and see if there was any difference. It would be interesting to me to see if the GRUB2 that you have from Squeeze would act the same or differently from the grub-pc you have from Lucid.

You've already written that you don't have much time for this, however, it may not be effective to merely wait for someone to show up with "the answer", there have been several posts from obviously knowledgable users but you are the only one who has hands on the equipment that we are trying to figure out. 

I wonder if the fact that it was an old Sid install, which you had to downgrade to Squeeze because of unspecified instability which you weren't able to fix has any affect on the situation. I'm still not sure how you ended up with only device node designations in your fstab on that install.

---

### Post by Irihapeti on 2010-04-25
> What does your custom entry consist of ?

Here we are:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu 8.04.4 LTS (8.04) (manual)" {
        insmod ext2
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set 2dd04c68-6a98-456d-b7fc-fb4255ac090c
        linux /vmlinuz root=UUID=2dd04c68-6a98-456d-b7fc-fb4255ac090c ro quiet splash
        initrd /initrd.img
}
```

I've also used /dev/sdXY notation (on another machine) and it works fine.

If you like to keep two kernels installed, you can also have another entry pointing to /vmlinuz.old and /initrd.img.old

As long as update-initramfs works correctly on Debian, you shouldn't need to update grub when Debian has a kernel upgrade.

---

### Post by frankzen on 2010-04-25
> **QLee said:**
> Well, perhaps you misunderstood me, the suggestion was not as a way to get your system working, it was to obtain more data regarding the issue. And, as stated, to give you data so that you had facts with which to counter any flame posts like the ones you have previously encountered in the Debian forum.

As you can tell I am not really anxious to get into a flame war or debate on the Debian list over this. I have seen what happens in the wake of Ubuntu users posting...basically they are told to go to the Ubuntu forum.

> 
The "problem you now face", at least according to what you have written, was not being able to boot into the Debian install and you have been given suggestions for a temporary workaround for that.

That's not what I need. I had a work around (edit grub.cfg) what I hoped to find here was someone knowledgeable enough about Grub2 to explain why os-prober refuses to use UUIDs, and insists the other partition is /dev/sda2 and can't be made to change its mind. :)

> 
If you had tried the GRUB2 from the Debian install and it did boot all your operating systems, then we could compare the revision level of the two GRUBs and see if there was any difference. It would be interesting to me to see if the GRUB2 that you have from Squeeze would act the same or differently from the grub-pc you have from Lucid.

I plan to check both Grub2 from Debian...and reinstall Grub2 from Lucid, but not until I have enough time to fiddle

> 
You've already written that you don't have much time for this, however, it may not be effective to merely wait for someone to show up with "the answer", there have been several posts from obviously knowledgable users but you are the only one who has hands on the equipment that we are trying to figure out. 


I am not waiting for "the answer" - I was hoping to find someone with the knowledge to perhaps explain the problem, and suggest a solution.


> 
I wonder if the fact that it was an old Sid install, which you had to downgrade to Squeeze because of unspecified instability which you weren't able to fix has any affect on the situation. I'm still not sure how you ended up with only device node designations in your fstab on that install.

I can't answer either of those questions - but from reading debian.users
I'm not the only one with /device node references in fstab. There was a whole "discussion" on that a few months back. The transition to UUIDs
like the move from Grub1 to Grub2 was not absolutely smooth.

---

### Post by frankzen on 2010-04-25
> **Irihapeti said:**
> Here we are:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu 8.04.4 LTS (8.04) (manual)" {
        insmod ext2
        set root='(hd0,6)'
        search --no-floppy --fs-uuid --set 2dd04c68-6a98-456d-b7fc-fb4255ac090c
        linux /vmlinuz root=UUID=2dd04c68-6a98-456d-b7fc-fb4255ac090c ro quiet splash
        initrd /initrd.img
}
```

I've also used /dev/sdXY notation (on another machine) and it works fine.

If you like to keep two kernels installed, you can also have another entry pointing to /vmlinuz.old and /initrd.img.old

As long as update-initramfs works correctly on Debian, you shouldn't need to update grub when Debian has a kernel upgrade.


Thanks for this . I'll play around with it and see what I can get working.

---

### Post by QLee on 2010-04-25
[QUOTE=frankzen]
I am not waiting for "the answer" - I was hoping to find someone with the knowledge to perhaps explain the problem, and suggest a solution.
[/QUOTE]

Okay, I understand. 

Without further data, I can't make any reasonable guesses and you have made the choice to not try any of the several things I have suggested in order to obtain more data. So, I'm sorry but I can't help any further but I do wish you bon courage.

---

### Post by frankzen on 2010-04-25
Well, I and apparently everyone else here was growing tired of this thread so I took the bull by the horns.

I reinstalled Grub2 on Ubuntu against all evidence that Grub2 in Ubuntu could boot  Debian Squeeze on another partition. The reason is that Ubuntu knows nothing about /dev/hdax. It knows only of /dev/sdax. Stands to reason it can't boot a kernel which understands /dev/hdax.

So after the reinstall, nothing changed. It created lines for Ubuntu using UUIDs, or /dev/sda3, and os-prober created a line for squeeze that called the partition /dev/sda2. 

So, boot into [COLOR="Red"]Debian [/COLOR],(by editing grub.cfg) and [COLOR="Red"]aptitude install grub2[/COLOR].It went through its routine, asked me where to install it (into the mbr of hda) and 20 seconds later said it was finished. Result ? Grub 2 in Debian boots both, using UUIDs for Ubuntu and /dev/hda2 for Debian.
 
So there have it - for the very few people running both or having the same problem, the answer is to install Grub from Debian, not from Ubuntu.

Thanks to the many who made suggestions.

---

