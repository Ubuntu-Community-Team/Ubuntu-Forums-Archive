---
title: "Chain-loading Windows 7 after Ubuntu 10.04"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by orihon on 2010-07-10
I've recently installed Ubuntu 10.04 it installed and chain-loaded correctly however I installed it on partition that was too small so I used gParted to copy the files 1:1 to a freed up partition.
The result was it copied fine but the Grub file became messed up.

I had to manually reinstall Grub2 from the LiveCD and the Linux was starting up fine, however now I'm unable to boot to Windows.

The question is:
Is there an easy way to reinstall/re-chain the Windows bootloader so its able to chain-load from Grub.

Thanks!

---

### Post by efflandt on 2010-07-10
It is usually considered best to resize Win7 from its own admin tools (computer management).  But it is not really clear what you did with other partitions, so it is not clear if you messed something up for Win7 booting.  Normally **sudo update-grub** would automatically find Windows and add it to its menu.

But if you messed up something with Win7 boot, you might need to use the Win7 disk to get that booting, then install grub wherever you want it and then everything should work.

There is a boot info script at [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) that can help determine how things are currently set up.  Download it, chmod 755 it, then **sudo ./boot_info_script055.sh** and paste content of RESULTS.txt with code tags (highlight it and use **#** at top of message window).

---

### Post by orihon on 2010-07-11
I deleted an old Vista partition (at the same time) which I assume had the bootloader on it that Grub was pointed to.
I still have Windows 7 installed on another HDD and from the looks of it Grub is trying to boot from the old location (of the Vista install, *sda3*).
Can I correct Grub's bootloader pointer to the Windows 7 location (*sdb1*)?

> Normally **sudo update-grub** would automatically find Windows and add it to its menu.
Tried this with no luck.

> But if you messed up something with Win7 boot, you might need to use the Win7 disk to get that booting, then install grub
I'll do this as a last-ditch effort but I was really hoping to solve the issue without it.

Thanks for your assist so far.

---

### Post by orihon on 2010-07-12
Boot info:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 400446756 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Utility
/dev/sda2              96,390    10,088,819     9,992,430  82 Linux swap / Solaris
/dev/sda3          21,069,824   273,027,071   251,957,248   7 HPFS/NTFS
/dev/sda4         273,040,740   488,279,609   215,238,870  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  63 2,930,277,166 2,930,277,104   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0307                              vfat       Utility                   
/dev/sda2        c3a1add7-fcce-4005-8fa5-60a154dc189e   swap       swap                          
/dev/sda3        40875D6C47732397                       ntfs                                     
/dev/sda4        1e14af5d-f02d-4d8a-8bfa-ddd9c2912956   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D8C6DA13C6D9F1AC                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        DE53-FF2C                              vfat       Vid1                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        9E3409F13409CD69                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        7E28A80E28A7C38D                       ntfs       Vid2                        
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext3       (rw,errors=remount-ro)
/dev/sdc1        /media/Vid1          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1        /media/9E3409F13409CD69  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sde1        /media/Vid2            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid		1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-23-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid		1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
kernel		/boot/vmlinuz-2.6.32-23-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro  single
initrd		/boot/initrd.img-2.6.32-23-generic

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid		1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
kernel		/boot/grub/core.img

title		Ubuntu 10.04 LTS, memtest86+
uuid		1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d7-0307
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 9ea2576fa2574b43
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d8c6da13c6d9f1ac
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ffcb4b6b-35ea-4c21-a850-ed1349f6117e none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
 141.8GB: boot/grub/grub.cfg
 205.0GB: boot/grub/menu.lst
 205.0GB: boot/grub/stage2
 141.8GB: boot/initrd.img-2.6.32-21-generic
 141.8GB: boot/initrd.img-2.6.32-23-generic
 141.8GB: boot/vmlinuz-2.6.32-21-generic
 141.9GB: boot/vmlinuz-2.6.32-23-generic
 141.8GB: initrd.img
 141.8GB: initrd.img.old
 141.9GB: vmlinuz
 141.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  e6 0e 37 31 00 00 80 01  |..........71....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 82 8a a1 12 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

ls: reading directory sda3/: Input/output error
```

---

### Post by kansasnoob on 2010-07-12
I'm rather surprised that even Ubuntu boots. You have a grub 2 mbr on sda:

>  => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

But grub 2 is still using partition #6 for boot:

> menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	**[COLOR="Red"]set root='(hd0,6)'[/COLOR]**
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic

But I see you have mixed legacy grub and grub 2 boot files and that can prevent grub 2 from updating properly:

> sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 400446756 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/**[COLOR="Red"]menu.lst[/COLOR]** /boot/grub/**[COLOR="Red"]grub.cfg[/COLOR]** /etc/fstab 
                       /boot/grub/core.img

Once you get boot straightened out you also need to do some fixing so SWAP will be on at reboot:

```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D7-0307                              vfat       Utility                   
/dev/sda2        **[COLOR="Red"]c3a1add7-fcce-4005-8fa5-60a154dc189e[/COLOR]**   swap       swap                          
/dev/sda3        40875D6C47732397                       ntfs                                     
/dev/sda4        1e14af5d-f02d-4d8a-8bfa-ddd9c2912956   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D8C6DA13C6D9F1AC                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        DE53-FF2C                              vfat       Vid1                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        9E3409F13409CD69                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        7E28A80E28A7C38D                       ntfs       Vid2                        
/dev/sde: PTTYPE="dos" 
```

```
=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=**[COLOR="Red"]ffcb4b6b-35ea-4c21-a850-ed1349f6117e[/COLOR]** none            swap    sw              0       0

```

But we'll worry about SWAP later, for now let's try to get grub straightened out. **Please read this all, and DO NOT reboot!** I'll want to see the new grub.cfg before you try to reboot.

So, while booted into Ubuntu, copy-n-paste the following commands:

```
sudo mv /boot/grub /boot/grub_old
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub
```

Don't worry if it says, "not installed so not removed", just continue:

```
sudo apt-get --purge remove grub-common
```

```
sudo apt-get install grub-pc
```

You'll notice that also reinstalls grub-common, that's OK, we just want a new configuration, so continue:

```
sudo update-grub
```

Wait for it to say done, then:

```
sudo grub-install /dev/sda
```

If that returns any errors also run:

```
sudo grub-install --recheck /dev/sda
```

Now, as I said above, DO NOT reboot! Just post the full output of the following command so I can look at it first:

```
cat /boot/grub/grub.cfg
```

---

### Post by orihon on 2010-07-12
```
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
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
menuentry 'Uc' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d7-0307
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d8c6da13c6d9f1ac
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

On a side note. Is there a reason for it to be listing 2 Ubuntu options (Ubuntu, with Linux 2.6.32-**23**-generic and Ubuntu, with Linux 2.6.32-**21**-generic?

---

### Post by kansasnoob on 2010-07-12
> **orihon said:**
> ```
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
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
menuentry 'Uc' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1e14af5d-f02d-4d8a-8bfa-ddd9c2912956 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 1e14af5d-f02d-4d8a-8bfa-ddd9c2912956
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Utility Partition (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 07d7-0307
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d8c6da13c6d9f1ac
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

On a side note. Is there a reason for it to be listing 2 Ubuntu options (Ubuntu, with Linux 2.6.32-**23**-generic and Ubuntu, with Linux 2.6.32-**21**-generic?

Well that looks good so it's time to try a reboot. Do you have an Ubuntu Live CD just in case things go awry?

> On a side note. Is there a reason for it to be listing 2 Ubuntu options (Ubuntu, with Linux 2.6.32-**23**-generic and Ubuntu, with Linux 2.6.32-**21**-generic?

They're just different kernel versions. It's best to always keep one older kernel just in case the newest kernel won't boot.

Let me know what boots and what doesn't :)

If both Ubuntu and Windows now boot (remember to use "Windows Vista (loader) (on /dev/sdb1)" and NOT the "Utility" option) then we'll straighten out that SWAP problem.

I can also help you create a Custom Menu like shown here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

That way you can reduce the boot menu to just two entries, one for Ubuntu and one for Windows, but we must first know that Ubuntu and Windows both boot.

Oh, and if Windows won't boot, the next thing I'd try is changing the boot order in BIOS to see if Windows will boot if it's drive is set to boot first. I see that the Ubuntu drive is 250GB and the Windows drive is 500GB if that helps.

---

### Post by orihon on 2010-07-12
> Let me know what boots and what doesn't

So I just rebooted and Linux is coming up fine, however Win7 isn't booting. Its stating that it can't find the bootloader and to use the "Repair Startup" option from the OS install disc to restored it (to MBR I assume).

Also tried reordering the HDD boot order in BIOS, same result.

Thanks for your help this far!

---

### Post by kansasnoob on 2010-07-12
Well, the problem is not obvious to me, that is the boot files look right:

> sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe


Did you perhaps resize Windows 7 using Gparted? That can move the beginning of the Windows partition and cause problems. Regardless look here at the "detailed instructions":

[http://ubuntuforums.org/showpost.php?p=8929988&postcount=357](http://ubuntuforums.org/showpost.php?p=8929988&postcount=357)

I also think I saw oldfred around earlier and he sometimes spots Windows problems that I overlook.

---

### Post by orihon on 2010-07-12
> Did you perhaps resize Windows 7 using Gparted? That can move the beginning of the Windows partition and cause problems. 
No didn't touch the 500gb HDD while using Gparted only messed with the primary 250gb HDD.

I might give the info in that link a chance and head back here with an update. It mentions running startup repair several times to fix start up issues incrementally so I'll run with that atm.

Thanks again.
If anyone else has thoughts I welcome them.

---

### Post by confused57 on 2010-07-12
I don't believe oldfred has seen your thread yet, but here's some instructions he gave in another post:
[http://ubuntuforums.org/showpost.php?p=9555621&postcount=13](http://ubuntuforums.org/showpost.php?p=9555621&postcount=13)

---

### Post by kansasnoob on 2010-07-13
I'm curious where we ended up with this :confused:

Any luck at all?

---

