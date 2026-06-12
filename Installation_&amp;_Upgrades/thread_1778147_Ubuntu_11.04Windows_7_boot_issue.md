---
title: "Ubuntu 11.04/Windows 7 boot issue"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by Tornikee on 2011-06-08
Hello.

I had Ubuntu 11.04 installed, to which I added Windows 7 (created a new NTFS partition and installed W7 on it), although system doesn't recognize Ubuntu on startup - when the Ubuntu partition is marked as 'boot' from Gparted, this causes the 'OS missing' error in DOS, while if I mark the W7 partition as 'boot', W7 loads with no problems.

How can I enable the boot menu?

Thanks in advance.

---

### Post by oldfred on 2011-06-08
You need to reinstall grub2's boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Grub does not use boot flag, leave it on windows boot partition as if you have to do repairs to windows it will need to see boot flag.

---

### Post by Tornikee on 2011-06-08
Thanks for quick reply.

---

### Post by Tornikee on 2011-06-09
I did everything as instructed, although now *Ubuntu* loads as only OS, still without the boot OS selection menu. I guess I'm missing something?

---

### Post by Quackers on 2011-06-09
In Ubuntu open up a terminal and run ```
sudo update-grub
``` You should see the Windows Loader picked up as grub.cfg is configured. If you see that you can reboot and you should now get a grub menu.
If that doesn't happen the output of the boot script will be needed to help with further diagnostics.

---

### Post by Tornikee on 2011-06-09
This is what appears after I run that command:

[IMG]http://i.imgur.com/3cKkg.png[/IMG]

No mention of Windows boot part as much as I see, and when I open the menu.lst file to see if I can find anything there, it just appears to be a text file full of comments (stuff marked with '#'). Anywhere else I can check/modify/etc?

---

### Post by Quackers on 2011-06-09
That's not right. It looks like grub legacy has been installed rather than grub2, maybe? Grub2 does not use a menu.lst file - it should be empty.

Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Tornikee on 2011-06-09
Thank you for the instructions. Here is the full content of the generated file:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   547,065,855   547,063,808  83 Linux
/dev/sda2    *    547,065,856   618,852,351    71,786,496   7 NTFS / exFAT / HPFS
/dev/sda3         618,854,398   625,141,759     6,287,362   5 Extended
/dev/sda5         618,854,400   625,141,759     6,287,360  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6   ext4       U
/dev/sda2        79A919697D0093F3                       ntfs       W7
/dev/sda5        4c16db26-ceca-4b44-8743-6e7a109bbecc   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
# kopt=root=UUID=cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6

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

title		Ubuntu 11.04, kernel 2.6.38-8-generic
uuid		cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6 ro quiet splash 
initrd		/boot/initrd.img-2.6.38-8-generic

title		Ubuntu 11.04, kernel 2.6.38-8-generic (recovery mode)
uuid		cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
kernel		/boot/vmlinuz-2.6.38-8-generic root=UUID=cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6 ro  single
initrd		/boot/initrd.img-2.6.38-8-generic

title		Chainload into GRUB 2
root		cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
kernel		/boot/grub/core.img

title		Ubuntu 11.04, memtest86+
uuid		cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=cfbe114b-52b8-44a8-bf11-0d2b4bfe0cc6 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  32.140445709 = 34.510540800   boot/grub/core.img                             1
  32.135017395 = 34.504712192   boot/grub/grub.cfg                             1
  24.574996948 = 26.387202048   boot/grub/menu.lst                             1
  97.255104065 = 104.426872832  boot/initrd.img-2.6.38-8-generic               2
  32.133281708 = 34.502848512   boot/vmlinuz-2.6.38-8-generic                  1
  97.255104065 = 104.426872832  initrd.img                                     2
  32.133281708 = 34.502848512   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  ef 61 71 4f 11 2b 9b 24  4c 7b d2 c2 2e a0 bd f2  |.aqO.+.$L{......|
00000010  60 f8 cc 35 86 ee 76 0a  a8 2e 65 73 a5 ae 10 0f  |`..5..v...es....|
00000020  5f 5d bf 86 b0 db 36 ca  d0 dd 95 3d ed 61 7e 13  |_]....6....=.a~.|
00000030  db 8d 9b d3 f5 3d e0 a8  9c d9 b1 30 aa 01 78 13  |.....=.....0..x.|
00000040  96 2c 94 1d 41 3e 09 42  3b 19 fd c6 0c ee 7f ca  |.,..A>.B;.......|
00000050  02 20 61 33 dc dd 8e ce  5f 96 a1 e5 c4 c7 5b af  |. a3...._.....[.|
00000060  cd bf 2a 09 67 f3 c4 c8  87 f4 ad 1f 44 5b 04 ae  |..*.g.......D[..|
00000070  06 24 73 2a 87 f2 a8 26  a0 86 45 d1 e2 c1 3e 87  |.$s*...&..E...>.|
00000080  2d c7 45 e9 2d a7 f6 b0  5a 71 e1 00 0e 8a 40 b7  |-.E.-...Zq....@.|
00000090  62 db 6e 7d 44 d8 d2 9b  75 10 64 28 3e 15 1b 97  |b.n}D...u.d(>...|
000000a0  5f f9 3d 6d 41 2e fa c6  b6 0f 71 14 45 f7 d0 35  |_.=mA.....q.E..5|
000000b0  d9 be a4 c0 e8 82 7b 12  e8 1e 28 a5 23 7e f9 d8  |......{...(.#~..|
000000c0  dd bc 5f 48 d6 fc 5c 08  84 70 f3 dc c1 6d 31 f1  |.._H..\..p...m1.|
000000d0  43 32 c0 5f ce 6a ff 58  dc b9 6d 57 f2 41 4e fa  |C2._.j.X..mW.AN.|
000000e0  f1 cb 4f ef 15 cc a9 af  9d 3c 82 17 90 7e 38 28  |..O......<...~8(|
000000f0  a5 60 a2 8c 9d 8d 8d b5  19 5a c6 65 55 fa 4a f9  |.`.......Z.eU.J.|
00000100  6a 6b 3a 75 e9 2a d9 5c  b7 9e e9 4e ee 54 b9 71  |jk:u.*.\...N.T.q|
00000110  12 c1 20 b2 1d b4 e6 95  d5 7d 41 15 c2 f0 23 3f  |.. ......}A...#?|
00000120  b0 e8 41 b9 aa 2b a5 05  7e 8f e3 75 a9 22 d1 6f  |..A..+..~..u.".o|
00000130  42 ea c2 db 52 85 be e3  60 31 d0 f3 75 ba 59 85  |B...R...`1..u.Y.|
00000140  7b ec f9 4c 32 55 04 48  41 57 03 d1 ab ea 02 86  |{..L2U.HAW......|
00000150  be 91 d3 a8 46 b6 2b 58  f5 6f 34 ea e1 18 d0 7b  |....F.+X.o4....{|
00000160  00 2c 3e 41 c6 7c 3c db  85 86 27 78 f9 f8 e4 35  |.,>A.|<...'x...5|
00000170  1c 5e db b9 b2 8a 8d 74  4e 26 ef 36 47 96 23 22  |.^.....tN&.6G.#"|
00000180  ab 50 03 2c 07 b7 8e a1  d9 b0 bd 4c 24 be ab 37  |.P.,.......L$..7|
00000190  b5 b5 00 e6 01 8a 61 40  f6 af a1 c7 5a 9b f1 ca  |......a@....Z...|
000001a0  49 2d fe 06 8f ae f4 cc  73 4e a9 0f 22 43 96 e2  |I-......sN.."C..|
000001b0  ce 3c 0d 5a df 6e 6c 67  6d 74 50 f0 1d 4b 00 fe  |.<.Z.nlgmtP..K..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 5f 00 00 00  |............_...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Quackers on 2011-06-09
You appear to have grub2 installed, but /boot/grub/menu.lst appears in with the boot files. This is not normally the case and I'm not sure how it got there unless grub legacy has been installed at some time.
See if oldfred agrees but I would suggest purging grub then re-installing grub2 using the CHROOT section of the guide below.
The partition you need to mount first is /dev/sda1 and grub should be installed to /dev/sda
The process uses the live cd desktop to achieve this. You should use the 11.04 live cd/usb.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Tornikee on 2011-06-09
Thank you for the information. Will follow the instructions on that link.

---

### Post by Quackers on 2011-06-09
Ok, it looks a bit daunting but it's not that bad really. Use the CHROOT section and you should be ok. If you get stuck just holler!
Good luck :-)

---

### Post by Tornikee on 2011-06-09
Issue's solved. I followed those instructions (with the difference that as I've been able to log in to the full Ubuntu installation without using the Live CD I only used steps 2-5, skipping the CHROOT part) and now have boot OS menu.

Thanks again for the assistance.

---

### Post by Quackers on 2011-06-09
Oh yes, I'm a foolish duck! I always forget about that! Well done anyway :-)
Glad things are now working.

Please mark the thread as solved using Thread Tools near the top of the screen.

---

