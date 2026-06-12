---
title: "Another Grub problem"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by Dzanjin on 2011-05-19
Hello all!

SHORT VERSION: 
My computer loads up to a black screen that just says:
Grub>








WHOLE STORY:
I've been trying to fix this all last night and this morning :-/

I have a laptop that has BT4 on it as well as CrunchBang. I decided that I was going to make another partition and run winblows xp :-( I know I know! I've been without windows free for almost a year now. I have ubuntu studio on my desktop. I only need xp to run fruityloops (music editing software).

ANYWAY,
of course xp overwrote my grub and now I'm trying to get it back.
I used the #! live cd and tried the popular "sudo grub" command and everything that goes with it only to find an hour later that those commands wont work because its for legacy grub which #! does not use.
I thought most of my problems were from following tutorials that were directed to using Ubuntu live cd's. So I made a brand new Ubuntu 11 live cd - AMAZING btw...prob going to use that for quad boot haha.

Finally found instructions to install grub using some --root-directory commands and rebooted.
Now my computer loads up to a black screen that just says:
Grub>

So now I'm stuck. Haha. Can anyone help? I'm guessing it's just a matter of manually typing some commands to tell it where everything is and what it should be named etc.?

I'm exhausted from trying to fix this but it is essential that I get this computer back to running condition today.

Thank you to all those that read this lengthy post and thanks in advance to those who can help!

Side Notes: My #! (CrunchBang) Live CD works for me to have internet (wifi) access.
                  My Ubuntu 11 Live CD does not work for me to get internet.

---

### Post by oldfred on 2011-05-19
What boot loader do your installs use, some do still use grub legacy.

To see what is where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
New Version 060 has improved formating and requires code tags to make it legible. It is also a .zip file that you have to extract to get the script.

For wifi do you have wired connection. Not all wireless drivers are on liveCd and you have to download the correct driver, but have to have wired connection to do that.

Another useful disk to have:
Supergrub2 boots most systems
[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)

---

### Post by Dzanjin on 2011-05-19
> **oldfred said:**
> What boot loader do your installs use, some do still use grub legacy.

To see what is where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
New Version 060 has improved formating and requires code tags to make it legible. It is also a .zip file that you have to extract to get the script.

For wifi do you have wired connection. Not all wireless drivers are on liveCd and you have to download the correct driver, but have to have wired connection to do that.

Another useful disk to have:
Supergrub2 boots most systems
[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)


Hey! Thanks for the reply!
I'm going to try your advice, but I have a quick question....
If I install Ubuntu 11 as a 4th O.S. would that fix my grub problem? I mean when I setup ubuntu won't it install the grub correctly?
After seeing the live cd I definitely want it installed, so since I'm planning on installing sometime anyway would that make sense?

---

### Post by Dzanjin on 2011-05-19
Wow, that is one amazing script!

Alright, here is the results:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,msdos2)/boot/grub.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  BackTrack 4 R2 Codename Nemesis
    Boot files:        /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 6.0
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     4,208,639     4,206,592  82 Linux swap / Solaris
/dev/sda2           4,208,640    46,153,727    41,945,088  83 Linux
/dev/sda3          46,153,728    94,838,783    48,685,056  83 Linux
/dev/sda4    *     94,838,784   124,198,911    29,360,128   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        ce8d974b-ad4d-4d1a-b29e-8ee531f5e8be   swap       
/dev/sda2        4b585086-da10-45f1-9d32-c3b1cbc9e11b   ext3       
/dev/sda3        99e4124e-5d62-4c6e-9ab4-43b8cbe6ae5d   ext4       
/dev/sda4        8C8C3F428C3F25DC                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=4b585086-da10-45f1-9d32-c3b1cbc9e11b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4b585086-da10-45f1-9d32-c3b1cbc9e11b

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

vga=0x317image=4b585086-da10-45f1-9d32-c3b1cbc9e11b/boot/grub/vga=0x317.xpm.gz

title		BackTrack 4 R2, kernel 2.6.35.8
uuid		4b585086-da10-45f1-9d32-c3b1cbc9e11b
kernel		/boot/vmlinuz-2.6.35.8 root=UUID=4b585086-da10-45f1-9d32-c3b1cbc9e11b ro vga=0x317 
initrd		/boot/initrd.img-2.6.35.8
quiet

title		BackTrack 4 R2, kernel 2.6.35.8 (recovery mode)
uuid		4b585086-da10-45f1-9d32-c3b1cbc9e11b
kernel		/boot/vmlinuz-2.6.35.8 root=UUID=4b585086-da10-45f1-9d32-c3b1cbc9e11b ro  single
initrd		/boot/initrd.img-2.6.35.8

title		BackTrack 4 R2, memtest86+
uuid		4b585086-da10-45f1-9d32-c3b1cbc9e11b
kernel		/boot/memtest86+.bin
quiet

title OpenSUSE 11.3
root (hd0,2)
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=4b585086-da10-45f1-9d32-c3b1cbc9e11b /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda1
UUID=ce8d974b-ad4d-4d1a-b29e-8ee531f5e8be none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  20.623046875 = 22.143827968   boot/grub/core.img                             1
  10.459468842 = 11.230769152   boot/grub/menu.lst                             1
  10.397579193 = 11.164315648   boot/grub/stage2                               2
  11.013404846 = 11.825553408   boot/initrd.img-2.6.35.8                       7
  10.459251404 = 11.230535680   boot/vmlinuz-2.6.35.8                          3
  11.013404846 = 11.825553408   initrd.img                                     7
  10.459251404 = 11.230535680   vmlinuz                                        3

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 99e4124e-5d62-4c6e-9ab4-43b8cbe6ae5d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 99e4124e-5d62-4c6e-9ab4-43b8cbe6ae5d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 99e4124e-5d62-4c6e-9ab4-43b8cbe6ae5d
insmod png
if background_image /usr/share/images/desktop-base/grub-splash-crunchbang.png ; then
  set color_normal=light-gray/black
  set color_highlight=black/white
else
  set menu_color_normal=light-gray/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'CrunchBang Linux, with Linux 2.6.32-5-686' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 99e4124e-5d62-4c6e-9ab4-43b8cbe6ae5d
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/boot/vmlinuz-2.6.32-5-686 root=UUID=99e4124e-5d62-4c6e-9ab4-43b8cbe6ae5d ro  quiet splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-686
}
menuentry 'CrunchBang Linux, with Linux 2.6.32-5-686 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 99e4124e-5d62-4c6e-9ab4-43b8cbe6ae5d
	echo	'Loading Linux 2.6.32-5-686 ...'
	linux	/boot/vmlinuz-2.6.32-5-686 root=UUID=99e4124e-5d62-4c6e-9ab4-43b8cbe6ae5d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-5-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4b585086-da10-45f1-9d32-c3b1cbc9e11b
	linux /boot/vmlinuz-2.6.35.8 root=UUID=4b585086-da10-45f1-9d32-c3b1cbc9e11b ro vga=0x317
	initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, kernel 2.6.35.8 (recovery mode) (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4b585086-da10-45f1-9d32-c3b1cbc9e11b
	linux /boot/vmlinuz-2.6.35.8 root=UUID=4b585086-da10-45f1-9d32-c3b1cbc9e11b ro single
	initrd /boot/initrd.img-2.6.35.8
}
menuentry "BackTrack 4 R2, memtest86+ (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4b585086-da10-45f1-9d32-c3b1cbc9e11b
	linux /boot/memtest86+.bin 
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda3	/	ext4	rw,errors=remount-ro	0	0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  24.141330719 = 25.921556480   boot/grub/core.img                             1
  24.141281128 = 25.921503232   boot/grub/grub.cfg                             1
  33.042888641 = 35.479531520   boot/initrd.img-2.6.32-5-686                   2
  32.882999420 = 35.307851776   boot/vmlinuz-2.6.32-5-686                      1
  33.042888641 = 35.479531520   initrd.img                                     2
  32.882999420 = 35.307851776   vmlinuz                                        1

================================ sda4/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1


```

Hope this helps. Thanks again for the reply!

---

### Post by oldfred on 2011-05-19
It looks like it is configured to boot to backtrack, but backtrack has a mix of grub legacy with menu.lst and core.img from grub2. Grub2 stops since there is no grub.cfg. You can manuall boot or use Supergrub to boot. With Ubuntu we would have you chroot into the install can cleaning uninstall both and install just grub2. But do not know if that works or not with Backtrack.

I would install Debian's grub to the MBR or as you are planning install Ubuntu to a new partition and use that grub to boot. But you have used all 4 primary partitions which is a problem.


You do have an extra grub folder in your windows:
/boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

---

### Post by Dzanjin on 2011-05-19
> **oldfred said:**
> It looks like it is configured to boot to backtrack, but backtrack has a mix of grub legacy with menu.lst and core.img from grub2. Grub2 stops since there is no grub.cfg. You can manuall boot or use Supergrub to boot. With Ubuntu we would have you chroot into the install can cleaning uninstall both and install just grub2. But do not know if that works or not with Backtrack.

I would install Debian's grub to the MBR or as you are planning install Ubuntu to a new partition and use that grub to boot. But you have used all 4 primary partitions which is a problem.


You do have an extra grub folder in your windows:
/boot.ini /ntldr /NTDETECT.COM [COLOR=Red]/boot/grub/core.img[/COLOR]

Okay, so can I just install Ubuntu over the windows partition? I can always just dual boot my ubuntu studio desktop with xp.

If I install ubuntu 11 over the xp partition on the laptop will that allow me to have grub to where I can choose what I want to boot into once I start my laptop? Is there anything I need to do when installing ubuntu? I remember I installed Backtrack one time and somehow lost my OpenSuse partition because of where I installed root or something. Where am I supposed to install it? I always assumed /

---

### Post by oldfred on 2011-05-20
Ubuntu's os-prober will find the other installs and add boot stanzas. Not sure if it will work with Backtrack as I think the prober first looks for grub.cfg. It may find the menu.lst and create a entry.

You can use the same swap. With only one partition you have to install everything in / (root). Back up XP if you think you ever will want it  again.

---

