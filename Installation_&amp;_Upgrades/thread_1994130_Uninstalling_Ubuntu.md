---
title: "Uninstalling Ubuntu"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by Rhetoric Camel on 2012-06-02
Hope I'm in the right section of the forum for this, there is really a specific "Uninstall Ubuntu" subforum.

I haven't used Ubuntu for a while, but I just recently upgraded to 11.10 (I know it's not the newest version) and I really don't like the way it's laid out, and it lags a lot for me. I think I'm ready to completely uninstall Ubuntu and maybe try another flavor of Linux. 
Problem is, I'm not sure how to go about removing Ubuntu without losing everything else that is on that partition.

Here's how I have it set up:
C:\ has Windows and that's about it
I:\ has all my windows programs, saved pics, videos, music, documents, and so on... and it also is the partition with Ubuntu installed.

How do I go about uninstalling Ubuntu from I:\ without losing all the other data on the drive? Only uninstall info I found on a quick google search mentions deleting the partition, but if I do that I'll be losing pretty much everything I have on my computer.

---

### Post by TheFu on 2012-06-02
> **Rhetoric Camel said:**
> I:\ has all my windows programs, saved pics, videos, music, documents, and so on... and it also is the partition with Ubuntu installed.

**Is this a WUBI install?**
Adding that to the subject, if true, would be helpful.  

Most Linux installations are to Linux specific file systems and are not shared with drive letters available to Windows too.

This link [http://ubuntuforums.org/showthread.php?t=861983](http://ubuntuforums.org/showthread.php?t=861983) should help.

---

### Post by Rhetoric Camel on 2012-06-02
I do not believe it was a Wubi install. I used a cd when I originally installed 8.10

---

### Post by ajgreeny on 2012-06-02
So from ubuntu let's see the output of the terminal command```
sudo fdisk -l
```Then we'll know a bit more about your setup.

---

### Post by darkod on 2012-06-02
> **Rhetoric Camel said:**
> I do not believe it was a Wubi install. I used a cd when I originally installed 8.10

Plain and simple, ubuntu can't be on I:, only wubi. Windows assigns letters only to ntfs partitions and ubuntu doesn't install on ntfs.

So, it's either a wubi installation, or something is very weird. If it's wubi, simply go into Control Panel - Programs and deinstall it just like any windows program. That's how you uninstall wubi.

If it's an installation on a separate linux partition, simply delete that partition and ubuntu is gone (together with all the data inside, so copy all that you need first). If you do this and you have grub2 on the MBR it will probably stop grub2 from working, so either restore the windows bootloader before deleting the partition, or be ready to restore it after that.

---

### Post by Rhetoric Camel on 2012-06-02
> **ajgreeny said:**
> So from ubuntu let's see the output of the terminal command```
sudo fdisk -l
```Then we'll know a bit more about your setup.

Here is what I got after putting that in the terminal

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf6cdf6cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS/exFAT
/dev/sda2       102398310   625137344   261369517+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe794ac88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   411344324   205672131    7  HPFS/NTFS/exFAT
/dev/sdb2       411344325   625137344   106896510   83  Linux
```


> **darkod said:**
> Plain and simple, ubuntu can't be on I:, only wubi. Windows assigns letters only to ntfs partitions and ubuntu doesn't install on ntfs.

So, it's either a wubi installation, or something is very weird. If it's wubi, simply go into Control Panel - Programs and deinstall it just like any windows program. That's how you uninstall wubi.

If it's an installation on a separate linux partition, simply delete that partition and ubuntu is gone (together with all the data inside, so copy all that you need first). If you do this and you have grub2 on the MBR it will probably stop grub2 from working, so either restore the windows bootloader before deleting the partition, or be ready to restore it after that.

There is no sign of Wubi or any way to uninstall it or Ubuntu from within Windows. I have also reinstalled Windows twice since my first install of Ubuntu, so that may be why it not in Add/Remove Programs?

---

### Post by ajgreeny on 2012-06-02
OK, so it seems you have an approximately 100Gb partition sdb2, with a linux formatted filesystem, presumably your ubuntu installation, even though there is no swap.

If you really don't want ubuntu on there any more, you need to restore the windows bootloader to the MBR, then delete the sdb2 partition.  How you restore the win bootloader depends on the windows version and what windows disk you have to use for the restoration.

It is also possible that you put grub on sdb and left the windows bootloader on sda, so it would help if you clicked on the boot-info-script in my signature and followed the info there to get the RESULTS.txt file.

Paste contents of RESULTS.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ CODE] paste here [ /CODE] tags.
The script V60 has improved formating and requires code tags to make it legible.  Version is also a zip file that you have to extract to get the bootscriptinfo.sh to run.

---

### Post by Rhetoric Camel on 2012-06-02
Here is what I got from the BootInfoScript... it does seem to look like I did use Wubi to install it. But I'll let you guys be the judge of it.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid e575e192-7cce-4709-8dc3-ce2309fa8f90 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 9.04
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   102,398,309   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda2         102,398,310   625,137,344   522,739,035   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   411,344,324   411,344,262   7 NTFS / exFAT / HPFS
/dev/sdb2         411,344,325   625,137,344   213,793,020  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        727069E07069AC13                       ntfs       
/dev/sda2        488CCED98CCEC124                       ntfs       For Programs
/dev/sdb1        B2E0BED6E0BE9FD1                       ntfs       Second HDD
/dev/sdb2        e575e192-7cce-4709-8dc3-ce2309fa8f90   ext3       Ubuntu 10.04

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

==================== sda2/ubuntu/disks/boot/grub/menu.lst: =====================

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
# kopt=root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 9.04, kernel 2.6.28-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=488CCED98CCEC124 loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1

--------------------------------------------------------------------------------

======================== sda2/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ubuntu/disks/boot/grub/menu.lst                1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.27-14-generic 30
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-15-generic  2
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-16-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-18-generic  1
            ?? = ??             ubuntu/disks/boot/initrd.img-2.6.28-19-generic  6
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.27-14-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-15-generic   15
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-16-generic    3
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-18-generic    1
            ?? = ??             ubuntu/disks/boot/vmlinuz-2.6.28-19-generic   24

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro,relatime 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="14"
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos2)'
  search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-20-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux	/boot/vmlinuz-3.0.0-20-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-20-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-20-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	echo	'Loading Linux 3.0.0-20-generic-pae ...'
	linux	/boot/vmlinuz-3.0.0-20-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-20-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux	/boot/vmlinuz-3.0.0-20-generic root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-20-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	echo	'Loading Linux 3.0.0-20-generic ...'
	linux	/boot/vmlinuz-3.0.0-20-generic root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux	/boot/vmlinuz-2.6.38-13-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-13-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	echo	'Loading Linux 2.6.38-13-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-13-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 3.0.0-20-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux	/boot/vmlinuz-3.0.0-20-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro   quiet splash
	initrd	/boot/initrd.img-3.0.0-20-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-20-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	echo	'Loading Linux 3.0.0-20-generic-pae ...'
	linux	/boot/vmlinuz-3.0.0-20-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-20-generic-pae
}
menuentry "Ubuntu, with Linux 3.0.0-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux	/boot/vmlinuz-3.0.0-20-generic root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro   quiet splash
	initrd	/boot/initrd.img-3.0.0-20-generic
}
menuentry "Ubuntu, with Linux 3.0.0-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	echo	'Loading Linux 3.0.0-20-generic ...'
	linux	/boot/vmlinuz-3.0.0-20-generic root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-20-generic
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux	/boot/vmlinuz-2.6.38-13-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro   quiet splash
	initrd	/boot/initrd.img-2.6.38-13-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	echo	'Loading Linux 2.6.38-13-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-13-generic-pae root=UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-13-generic-pae
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root e575e192-7cce-4709-8dc3-ce2309fa8f90
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 727069E07069AC13
	drivemap -s (hd0) ${root}
	chainloader +1
}
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
--------------------------------------------------------------------------------

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=e575e192-7cce-4709-8dc3-ce2309fa8f90 /               ext3    errors=remount-ro 0       1
/mnt/512.swap non swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 218.613352299 = 234.734299648  boot/grub/core.img                             1
 218.550627232 = 234.666949120  boot/grub/grub.cfg                             2
 218.539701939 = 234.655218176  boot/initrd.img-2.6.38-13-generic-pae          9
 218.597120762 = 234.716871168  boot/initrd.img-3.0.0-20-generic               6
 218.555021763 = 234.671667712  boot/initrd.img-3.0.0-20-generic-pae           8
 218.612535954 = 234.733423104  boot/vmlinuz-2.6.38-13-generic-pae             3
 218.639524937 = 234.762402304  boot/vmlinuz-3.0.0-20-generic                  6
 218.648848057 = 234.772412928  boot/vmlinuz-3.0.0-20-generic-pae              4
 218.555021763 = 234.671667712  initrd.img                                     8
 218.597120762 = 234.716871168  initrd.img.old                                 6
 218.648848057 = 234.772412928  vmlinuz                                        4
 218.639524937 = 234.762402304  vmlinuz.old                                    6

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```

---

### Post by darkod on 2012-06-02
Both. You seem to have (or had) wubi 9.04 on the second partition of the first disk, /dev/sda2. You also seem to have ubuntu 11.10 on /dev/sdb2. You have grub on both MBRs so you will have to restore windows bootloader to at least one.

Get your XP CD and restore the windows bootloader on the MBR of /dev/sda. You can find instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once that is done and the computer boots in XP directly, you can delete the /dev/sdb2 partition and create a new ntfs partition from that space.

If XP was reinstalled after the wubi 9.04 installation, that would explain why there is no ubuntu entry in Add/Remove Programs. In that case you could simply delete the ubuntu folder from /dev/sda2.

---

### Post by Rhetoric Camel on 2012-06-02
> **darkod said:**
> Both. You seem to have (or had) wubi 9.04 on the second partition of the first disk, /dev/sda2. You also seem to have ubuntu 11.10 on /dev/sdb2. You have grub on both MBRs so you will have to restore windows bootloader to at least one.

Get your XP CD and restore the windows bootloader on the MBR of /dev/sda. You can find instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once that is done and the computer boots in XP directly, you can delete the /dev/sdb2 partition and create a new ntfs partition from that space.

If XP was reinstalled after the wubi 9.04 installation, that would explain why there is no ubuntu entry in Add/Remove Programs. In that case you could simply delete the ubuntu folder from /dev/sda2.

Excellent, thank you very much for the help!! Should my recovery disc for windows do what needs to be done? My computer didn't come with an actual windows disc so all I have is the recovery one it came with.

---

### Post by darkod on 2012-06-02
Depends. The recovery disc might actually start to wipe your computer so it can restore it to factory state, the way it was shipped to you. That could lose all your data and programs. I wouldn't play with that disc. But that is just me. :)

There is also a way to do this with linux tools. You would usually do it from live mode, but you are deleting your ubuntu 11.10 anyway so it doesn't matter if you do it from it.

Open terminal and try:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be a warning about the lilo bootloader configuration, ignore it and continue. That should write a generic mbr on /dev/sda which does the same job as the windows bootloader.

Test this by restarting. If your computer is set in bios to boot from the first disk, it should boot XP directly.

If that works, remove ubuntu and wubi as discussed above.

---

### Post by TheFu on 2012-06-03
[ajgreeny]("http://ubuntuforums.org/member.php?u=27747") - that boot-info script is fantastic!  Thanks for sharing the info here.

---

