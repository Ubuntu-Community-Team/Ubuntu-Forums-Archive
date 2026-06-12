---
title: "Ubuntu/Windows7 dual boot - no boot menu"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by mirandalc on 2011-08-15
Installed Ubuntu on a 40 GB partition side by side with Windows 7 currently installed. I have had this exact setup before. Problem, boot menu never shows. The system boots into Ubuntu automatically. Windows seems to be intact and accessible. How can I get the boot menu to appear at startup?

---

### Post by jramshu on 2011-08-15
Have you tried?
```
sudo os-prober
```
```
sudo update-grub
```

EDIT: Press esc when starting. May have to edit grub configs.
Read through this also.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

EDIT 2: Always include which version of Ubuntu you are running, makes a difference. Thanks.

---

### Post by mirandalc on 2011-08-15
I tried both. No avail. Should I be concerned that GParted has a warning exclamation point beside the Windows partition stating: unable to detect file system?

Here's my terminal:
miranda@mirandas:~$ sudo os-prober
[sudo] password for miranda: 
miranda@mirandas:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by oldfred on 2011-08-15
Post the results.txt from this. You are finding menu.lst from grub legacy.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by mirandalc on 2011-08-15
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 37159111 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 124505843 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 3 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       208,844       208,782   7 NTFS / exFAT / HPFS
/dev/sda2    *        208,845    84,100,274    83,891,430   7 NTFS / exFAT / HPFS
/dev/sda3          84,100,275   234,432,846   150,332,572   7 NTFS / exFAT / HPFS
/dev/sda4         234,434,558   312,580,095    78,145,538   5 Extended
/dev/sda5         234,434,560   309,282,815    74,848,256  83 Linux
/dev/sda6         309,284,864   312,580,095     3,295,232  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda3        740C8DFD788351E5                       ntfs       Storage
/dev/sda5        082dfad7-b00d-4d04-9438-1dd0816cb71c   ext4       
/dev/sda6        5eba8cea-42d3-4e06-8b1a-cddb9e9c235f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=082dfad7-b00d-4d04-9438-1dd0816cb71c

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		082dfad7-b00d-4d04-9438-1dd0816cb71c
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		082dfad7-b00d-4d04-9438-1dd0816cb71c
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Chainload into GRUB 2
root		082dfad7-b00d-4d04-9438-1dd0816cb71c
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		082dfad7-b00d-4d04-9438-1dd0816cb71c
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5eba8cea-42d3-4e06-8b1a-cddb9e9c235f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 113.919719696 = 122.320367616  boot/grub/core.img                             1
 129.983707428 = 139.568943104  boot/grub/grub.cfg                             1
 136.023998260 = 146.054656000  boot/grub/menu.lst                             1
 114.044528961 = 122.454380544  boot/initrd.img-2.6.32-24-generic              1
 113.918319702 = 122.318864384  boot/vmlinuz-2.6.32-24-generic                 1
 114.044528961 = 122.454380544  initrd.img                                     1
 113.918319702 = 122.318864384  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  21 c4 04 3b 39 42 a1 03  1f 89 7f 52 ad 4e b7 1c  |!..;9B.....R.N..|
00000010  a9 50 ec b8 ba 82 a0 32  c7 00 bb ee 3c 75 68 29  |.P.....2....<uh)|
00000020  c1 71 37 a9 13 e1 51 e3  a0 36 1e d8 16 90 09 e8  |.q7...Q..6......|
00000030  bb 95 37 c1 c2 70 a4 05  ee 63 7c 20 7c b5 ad dc  |..7..p...c| |...|
00000040  02 ed 0c 7a b7 41 d1 bc  d0 80 38 2a ad 88 94 b0  |...z.A....8*....|
00000050  58 84 1c 62 2d 05 1a 8d  18 5b 17 d7 36 06 3f d5  |X..b-....[..6.?.|
00000060  a4 0c c0 d0 0c da 68 ac  1c 52 86 21 72 09 b0 2b  |......h..R.!r..+|
00000070  83 00 d0 ad ce 03 19 4d  4c 30 ec a0 66 03 90 28  |.......ML0..f..(|
00000080  18 64 f0 29 10 a0 77 19  03 e8 21 43 fa 95 02 b2  |.d.)..w...!C....|
00000090  bd 17 0a 91 0a ba 0e 1f  51 63 6c ff e8 45 98 92  |........Qcl..E..|
000000a0  f0 1c 0a d2 b0 cd 29 24  68 11 40 28 42 5a e8 0e  |......)$h.@(BZ..|
000000b0  1c 83 8e 5e 68 05 91 1c  05 58 44 32 20 98 40 21  |...^h....XD2 .@!|
000000c0  23 d6 35 e0 6b c0 e3 65  5a 30 ee 81 90 26 21 bc  |#.5.k..eZ0...&!.|
000000d0  50 8d 70 31 42 32 d0 61  20 30 71 58 0b 0a 62 71  |P.p1B2.a 0qX..bq|
000000e0  98 d5 b1 bc 1c 1f 9b 13  8d 21 08 0b 2a 35 36 da  |.........!..*56.|
000000f0  60 21 41 c5 a5 9a 54 0e  33 83 50 17 0a 86 82 f1  |`!A...T.3.P.....|
00000100  15 b3 b3 09 40 59 c0 3a  48 da 61 aa 1e 05 98 2c  |....@Y.:H.a....,|
00000110  9d 5c f8 af 34 66 80 07  78 bb 54 44 6d 01 57 8e  |.\..4f..x.TDm.W.|
00000120  80 b5 d2 54 5c 94 91 05  29 b7 01 34 6e ec 99 ac  |...T\...)..4n...|
00000130  9c a8 c1 ce 00 b0 fe e1  b9 b0 9f bd 0f 9f 3c 3f  |..............<?|
00000140  1e b1 66 05 a3 21 44 63  52 c4 2e 11 e7 3f 6d 94  |..f..!DcR....?m.|
00000150  b4 64 22 01 8f f3 92 a8  52 59 26 a3 72 5f 22 72  |.d".....RY&.r_"r|
00000160  b5 65 21 80 7b db 28 28  94 b3 cc 18 7e e4 57 9c  |.e!.{.((....~.W.|
00000170  cd 6f 28 e6 8c 06 ae 4a  a1 59 46 31 83 50 3f 77  |.o(....J.YF1.P?w|
00000180  f7 22 88 a6 a5 18 a8 f0  18 f4 9a 14 82 d0 05 89  |."..............|
00000190  0b 89 e0 4b 78 1f 0b 7a  c5 b8 12 4d 82 00 aa 70  |...Kx..z...M...p|
000001a0  4e 02 d3 28 6e 2c f0 ef  04 3b 50 7a 3d 1e d2 30  |N..(n,...;Pz=..0|
000001b0  20 0e 08 f4 5d 3a 60 51  5a 82 d0 68 d0 17 00 fe  | ...]:`QZ..h....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 18 76 04 00 fe  |............v...|
000001d0  ff ff 05 fe ff ff 36 1a  76 04 cc 4d 32 00 00 00  |......6.v..M2...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2011-08-15
You installed grub2's boot loader intopartition boot sectors of  sda1 & sda3 which are NTFS. NTFS partitions have to have NTFS signatures and if bootable have to be configured with info on which boot loader to use in the partition boot sector. You almost never install grub2 to a partition like sda1, sda2 but just to the drive's MBR or sda or sdb etc.

Windows does keep a backup of the boot sector and if it is good this will let you recover it. 

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You also have parts of grub legacy and grub2 in your install. It is best to chroot into your system, uninstall both grub legacy & grub2 and reinstall grub2(package grub-pc).

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Not sure about sda2, it may just need chkdsk from windows or other repairs since the script could not mount it.

Run all of above and if you cannot boot anything rerun script to see where we are at. Or tell us what errors you get.

---

### Post by mirandalc on 2011-08-15
Thank you! I got the boot menu up. If only I could mount the Windows partition.
I'm still unable to boot into windows. It's not showing up in Places anymore so I can't mount it. Disk utility says it's fine. Is there anything I can do outside of Windows?
Thanks again for the help!

---

### Post by oldfred on 2011-08-15
Repost boot script. 

Linux has no way to run chkdsk, some utilities in Linux's ntfs driver do a minor fix and then set the chkdsk flag so chkdsk will run on next windows reboot. But once chkdsk flag is set Ubuntu will not mount the NTFS partition to prevent damage that then chkdsk might not be able to fix.

---

### Post by mirandalc on 2011-08-16
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda1 and looks at sector 37159111 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda3 and looks at sector 124505843 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 3 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       208,844       208,782   7 NTFS / exFAT / HPFS
/dev/sda2    *        208,845    84,100,274    83,891,430   7 NTFS / exFAT / HPFS
/dev/sda3          84,100,275   234,432,846   150,332,572   7 NTFS / exFAT / HPFS
/dev/sda4         234,434,558   312,580,095    78,145,538   5 Extended
/dev/sda5         234,434,560   309,282,815    74,848,256  83 Linux
/dev/sda6         309,284,864   312,580,095     3,295,232  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda3        740C8DFD788351E5                       ntfs       Storage
/dev/sda5        082dfad7-b00d-4d04-9438-1dd0816cb71c   ext4       
/dev/sda6        5eba8cea-42d3-4e06-8b1a-cddb9e9c235f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=082dfad7-b00d-4d04-9438-1dd0816cb71c

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

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid		082dfad7-b00d-4d04-9438-1dd0816cb71c
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro quiet splash 
initrd		/boot/initrd.img-2.6.32-24-generic

title		Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid		082dfad7-b00d-4d04-9438-1dd0816cb71c
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro  single
initrd		/boot/initrd.img-2.6.32-24-generic

title		Chainload into GRUB 2
root		082dfad7-b00d-4d04-9438-1dd0816cb71c
kernel		/boot/grub/core.img

title		Ubuntu 10.04.1 LTS, memtest86+
uuid		082dfad7-b00d-4d04-9438-1dd0816cb71c
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 082dfad7-b00d-4d04-9438-1dd0816cb71c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=082dfad7-b00d-4d04-9438-1dd0816cb71c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5eba8cea-42d3-4e06-8b1a-cddb9e9c235f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 113.919544220 = 122.320179200  boot/grub/core.img                             1
 139.922088623 = 150.240198656  boot/grub/grub.cfg                             1
 136.023998260 = 146.054656000  boot/grub/menu.lst                             1
 114.044528961 = 122.454380544  boot/initrd.img-2.6.32-24-generic              1
 113.918319702 = 122.318864384  boot/vmlinuz-2.6.32-24-generic                 1
 114.044528961 = 122.454380544  initrd.img                                     1
 113.918319702 = 122.318864384  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  21 c4 04 3b 39 42 a1 03  1f 89 7f 52 ad 4e b7 1c  |!..;9B.....R.N..|
00000010  a9 50 ec b8 ba 82 a0 32  c7 00 bb ee 3c 75 68 29  |.P.....2....<uh)|
00000020  c1 71 37 a9 13 e1 51 e3  a0 36 1e d8 16 90 09 e8  |.q7...Q..6......|
00000030  bb 95 37 c1 c2 70 a4 05  ee 63 7c 20 7c b5 ad dc  |..7..p...c| |...|
00000040  02 ed 0c 7a b7 41 d1 bc  d0 80 38 2a ad 88 94 b0  |...z.A....8*....|
00000050  58 84 1c 62 2d 05 1a 8d  18 5b 17 d7 36 06 3f d5  |X..b-....[..6.?.|
00000060  a4 0c c0 d0 0c da 68 ac  1c 52 86 21 72 09 b0 2b  |......h..R.!r..+|
00000070  83 00 d0 ad ce 03 19 4d  4c 30 ec a0 66 03 90 28  |.......ML0..f..(|
00000080  18 64 f0 29 10 a0 77 19  03 e8 21 43 fa 95 02 b2  |.d.)..w...!C....|
00000090  bd 17 0a 91 0a ba 0e 1f  51 63 6c ff e8 45 98 92  |........Qcl..E..|
000000a0  f0 1c 0a d2 b0 cd 29 24  68 11 40 28 42 5a e8 0e  |......)$h.@(BZ..|
000000b0  1c 83 8e 5e 68 05 91 1c  05 58 44 32 20 98 40 21  |...^h....XD2 .@!|
000000c0  23 d6 35 e0 6b c0 e3 65  5a 30 ee 81 90 26 21 bc  |#.5.k..eZ0...&!.|
000000d0  50 8d 70 31 42 32 d0 61  20 30 71 58 0b 0a 62 71  |P.p1B2.a 0qX..bq|
000000e0  98 d5 b1 bc 1c 1f 9b 13  8d 21 08 0b 2a 35 36 da  |.........!..*56.|
000000f0  60 21 41 c5 a5 9a 54 0e  33 83 50 17 0a 86 82 f1  |`!A...T.3.P.....|
00000100  15 b3 b3 09 40 59 c0 3a  48 da 61 aa 1e 05 98 2c  |....@Y.:H.a....,|
00000110  9d 5c f8 af 34 66 80 07  78 bb 54 44 6d 01 57 8e  |.\..4f..x.TDm.W.|
00000120  80 b5 d2 54 5c 94 91 05  29 b7 01 34 6e ec 99 ac  |...T\...)..4n...|
00000130  9c a8 c1 ce 00 b0 fe e1  b9 b0 9f bd 0f 9f 3c 3f  |..............<?|
00000140  1e b1 66 05 a3 21 44 63  52 c4 2e 11 e7 3f 6d 94  |..f..!DcR....?m.|
00000150  b4 64 22 01 8f f3 92 a8  52 59 26 a3 72 5f 22 72  |.d".....RY&.r_"r|
00000160  b5 65 21 80 7b db 28 28  94 b3 cc 18 7e e4 57 9c  |.e!.{.((....~.W.|
00000170  cd 6f 28 e6 8c 06 ae 4a  a1 59 46 31 83 50 3f 77  |.o(....J.YF1.P?w|
00000180  f7 22 88 a6 a5 18 a8 f0  18 f4 9a 14 82 d0 05 89  |."..............|
00000190  0b 89 e0 4b 78 1f 0b 7a  c5 b8 12 4d 82 00 aa 70  |...Kx..z...M...p|
000001a0  4e 02 d3 28 6e 2c f0 ef  04 3b 50 7a 3d 1e d2 30  |N..(n,...;Pz=..0|
000001b0  20 0e 08 f4 5d 3a 60 51  5a 82 d0 68 d0 17 00 fe  | ...]:`QZ..h....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 18 76 04 00 fe  |............v...|
000001d0  ff ff 05 fe ff ff 36 1a  76 04 cc 4d 32 00 00 00  |......6.v..M2...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

That makes sense. I am worried that I can't boot into Windows to fix it though.

---

### Post by oldfred on 2011-08-16
You still have grub installed to the boot sector of the NTFS partitions.

Did you try testdisk as recommended in the post #6 above. You should get a screen like this and if backup is good then click on backupBS to restore it. Do this for both sda1 & sda3.

---

### Post by mirandalc on 2011-08-21
I did try testdisk, but I didn't get the BackupBS option, only Rebuild. I even tried updating the Grub. I'm lost.

---

### Post by oldfred on 2011-08-22
If the backup is not valid you can try the rebuild, but I think you will still need a windows repair CD to run its fixboot commands then to fix windows.

I think now you have to run fixboot & chkdsk several times and possibly alternate them to complete the full repair as each does part but does not work fully without the other. And/or the bootsect.exe commands.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

