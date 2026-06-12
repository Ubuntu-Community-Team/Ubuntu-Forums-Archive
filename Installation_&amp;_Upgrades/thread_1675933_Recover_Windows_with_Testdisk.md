---
title: "Recover Windows with Testdisk?"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by freshmeat20 on 2011-01-26
So when I installed Ubuntu apparently I made 5 partitions and the Windows partition converted itself to 
SFS. Im able to change type to NTFS to read the files but have no idea how to boot Windowes from this point. Any ideas?

heres my output of fdisk

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40129+   6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2               6        1918    15360000   83  Linux
/dev/sda3   *        1918       38654   295086424    7  HPFS/NTFS
/dev/sda4           38654       38914     2082817    5  Extended
/dev/sda5           38654       38914     2082816   82  Linux swap / Solaris

```

And heres what Testdisk says.

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63

     Partition                  Start        End    Size in sectors
 1 P FAT16 >32M               0   1  1     4 254 60      80259 [DellUtility]
 2 P Linux                    5  25 21  1917  84 23   30720000
 3 * HPFS - NTFS           1917  84 24 38653 227 22  590172848 [OS]
 4 E extended             38653 248 58 38913  70  5    4165634
 5 L Linux Swap           38653 248 60 38913  70  5    4165632

```

But when I do quick search in testdisk it says this

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
D FAT16 >32M               0   1  1     4 254 60      80259 [DellUtility]
D Linux                    5  25 21  1917  84 23   30720000
D HPFS - NTFS           1917  84 24 38653 227 22  590172848 [OS]
D Linux Swap           38653 227 23 38913  48 15    4165616

```

---

### Post by Quackers on 2011-01-26
You currently appear to have 3 primary partitions and an extended partition, which holds a swap partition. That's fine. Why do you think that Windows has been converted to SFS?
Have you run ```
sudo update-grub
``` in a terminal and watched to see if the Windows Loader is picked up?
If that doesn't pick up Windows please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by freshmeat20 on 2011-01-26
it USED to be SFS, until I changed type but couldnt really be for sure if thsts what it did. 

It still sess the Windows partition as unknown.
```
         Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,321        80,259   6 FAT16
/dev/sda2              81,920    30,801,919    30,720,000  83 Linux
/dev/sda3    *     30,801,920   620,974,767   590,172,848   7 HPFS/NTFS
/dev/sda4         620,976,126   625,141,759     4,165,634   5 Extended
/dev/sda5         620,976,128   625,141,759     4,165,632  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        469f5028-988c-4d8e-b107-0b42ff7af935   ext4                                     
/dev/sda3        0975AA55FB810F72                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        72f07cda-c209-412e-86a0-3c231351887c   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=469f5028-988c-4d8e-b107-0b42ff7af935 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=469f5028-988c-4d8e-b107-0b42ff7af935

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

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        469f5028-988c-4d8e-b107-0b42ff7af935
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=469f5028-988c-4d8e-b107-0b42ff7af935 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        469f5028-988c-4d8e-b107-0b42ff7af935
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=469f5028-988c-4d8e-b107-0b42ff7af935 ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Chainload into GRUB 2
root        469f5028-988c-4d8e-b107-0b42ff7af935
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        469f5028-988c-4d8e-b107-0b42ff7af935
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 469f5028-988c-4d8e-b107-0b42ff7af935
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 469f5028-988c-4d8e-b107-0b42ff7af935
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 469f5028-988c-4d8e-b107-0b42ff7af935
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=469f5028-988c-4d8e-b107-0b42ff7af935 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 469f5028-988c-4d8e-b107-0b42ff7af935
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=469f5028-988c-4d8e-b107-0b42ff7af935 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 469f5028-988c-4d8e-b107-0b42ff7af935
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 469f5028-988c-4d8e-b107-0b42ff7af935
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=469f5028-988c-4d8e-b107-0b42ff7af935 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=72f07cda-c209-412e-86a0-3c231351887c none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


   9.0GB: boot/grub/core.img
   8.8GB: boot/grub/grub.cfg
   8.8GB: boot/grub/menu.lst
   1.1GB: boot/initrd.img-2.6.35-22-generic
   9.1GB: boot/vmlinuz-2.6.35-22-generic
   1.1GB: initrd.img
   9.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  33 c0 8e 4e 54 46 53 20  20 20 20 00 02 08 00 00  |3..NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 d6 01  |........?.......|
00000020  00 00 00 00 7e 00 00 7c  af 52 2d 23 00 00 00 00  |....~..|.R-#....|
00000030  00 00 0c 00 00 00 00 00  ff 2f 75 00 00 00 00 00  |........./u.....|
00000040  f6 00 00 00 01 00 00 00  72 0f 81 fb 55 aa 75 09  |........r...U.u.|
00000050  00 00 00 00 74 03 fe 46  10 66 60 80 7e 10 00 74  |....t..F.f`.~..t|
00000060  26 66 68 00 00 00 00 66  ff 76 08 68 00 00 68 00  |&fh....f.v.h..h.|
00000070  7c 68 01 00 68 10 00 b4  42 8a 56 00 8b f4 cd 13  ||h..h...B.V.....|
00000080  9f 83 c4 10 9e eb 14 b8  01 02 bb 00 7c 8a 56 00  |............|.V.|
00000090  8a 76 01 8a 4e 02 8a 6e  03 cd 13 66 61 73 1c fe  |.v..N..n...fas..|
000000a0  4e 11 75 0c 80 7e 00 80  0f 84 8a 00 b2 80 eb 84  |N.u..~..........|
000000b0  55 32 e4 8a 56 00 cd 13  5d eb 9e 81 3e fe 7d 55  |U2..V...]...>.}U|
000000c0  aa 75 6e ff 76 00 e8 8d  00 75 17 fa b0 d1 e6 64  |.un.v....u.....d|
000000d0  e8 83 00 b0 df e6 60 e8  7c 00 b0 ff e6 64 e8 75  |......`.|....d.u|
000000e0  00 fb b8 00 bb cd 1a 66  23 c0 75 3b 66 81 fb 54  |.......f#.u;f..T|
000000f0  43 50 41 75 32 81 f9 02  01 72 2c 66 68 07 bb 00  |CPAu2....r,fh...|
00000100  00 66 68 00 02 00 00 66  68 08 00 00 00 66 53 66  |.fh....fh....fSf|
00000110  53 66 55 66 68 00 00 00  00 66 68 00 7c 00 00 66  |SfUfh....fh.|..f|
00000120  61 68 00 00 07 cd 1a 5a  32 f6 ea 00 7c 00 00 cd  |ah.....Z2...|...|
00000130  18 a0 b7 07 eb 08 a0 b6  07 eb 03 a0 b5 07 32 e4  |..............2.|
00000140  05 00 07 8b f0 ac 3c 00  74 09 bb 07 00 b4 0e cd  |......<.t.......|
00000150  10 eb f2 f4 eb fd 2b c9  e4 64 eb 00 24 02 e0 f8  |......+..d..$...|
00000160  24 02 c3 49 6e 76 61 6c  69 64 20 70 61 72 74 69  |$..Invalid parti|
00000170  74 69 6f 6e 20 74 61 62  6c 65 00 45 72 72 6f 72  |tion table.Error|
00000180  20 6c 6f 61 64 69 6e 67  20 6f 70 65 72 61 74 69  | loading operati|
00000190  6e 67 20 73 79 73 74 65  6d 00 4d 69 73 73 69 6e  |ng system.Missin|
000001a0  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
000001b0  65 6d 00 00 00 63 7b 9a  73 73 69 6e 67 00 0d 0a  |em...c{.ssing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
```

---

### Post by Quackers on 2011-01-26
The boot sector is unknown, but the file system is reported correctly ```
/dev/sda3    *     30,801,920   620,974,767   590,172,848   7 HPFS/NTFS
```
Does the Windows partition mount ok? Can you view its files?
You also have a mixture of grub legacy and grub2 files which will not help things.

---

### Post by oldfred on 2011-01-26
What version of Windows? If XP you can do all the repairs from Ubuntu except chkdsk which may also be required. You can use any windows repair CD to run chkdsk on any NTFS partition.

Testdisk also has a function to recover backup boot sector or RebuildBS to fix a NTFS boot sector. If you have a full windows install but any of the 3 boot files are missing or corrupt you can copy them from the XP cd or from locations in the install.

Restore PBR boot sector for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by freshmeat20 on 2011-01-26
I can view the files in testdisk but when I try to open the filesystem icon in Places it has a DELL, Python and a chkdsk folder in a System Volume Info folder but I cant view any of my main files(program files etc). Im running Windows 7 but Cant use the recovery disk because I dont have a cd drive. I have the option to boot from usb but cant load the ISO from linux.I restored the boot sector. Lol and how can i remove the grub legacy?

---

### Post by Quackers on 2011-01-26
It may be better to try to recover that partition with testdisk, then look at oldfred's links.
Depending on whether all of Windows boot files are present, it may be possible to get it booting without a Windows repair disc - possibly.
oldfred also has a working Windows repair usb, I believe. He may be able to advise on that.

---

### Post by oldfred on 2011-01-26
I did download the window repair CD from neo and tried to make a USB version of it from Ubuntu. I tried several ways to copy to USB, unetbootin, extract to USB, extract and try to repair to make it bootable, but the only one that worked was to create the CD and use the CD to copy to the USB with windows USB create commands.


Use unetbootin to copy windows iso to partition and install:
[http://ubuntuforums.org/showthread.php?t=1480974](http://ubuntuforums.org/showthread.php?t=1480974)

Create Windows 7 USB
[http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx)
[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool)
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by freshmeat20 on 2011-01-26
Damn, theres no way to make the recovery USB in Ubuntu at all? I have no access to a Windows system...

---

### Post by freshmeat20 on 2011-01-26
Ok so I loaded the Windows 7 recovery disk via USB. But when I ran it it couldnt find my windows install. now when I try to boot the same recovery disk it says theres a BCD error. Would this have something to do with Windows not being recognized as an OS in my boot info script?

Edit: The BCD error came up after attemping to repair the windows files?

---

### Post by oldfred on 2011-01-26
Boot sector has to be a windows boot sector. If windows will not repair boot sector then you can use testdisk to recover from back up or create one.

As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you cannot recover the backup boot sector:

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"

then press "q" a few times to quit testdisk

Then try the windows repair disk USB again. How did you create Flash drive version?

---

### Post by freshmeat20 on 2011-01-26
I had to format the drive to NTFS to get it to boot (weird) and just with the contents of the ISO file not the file itself. on a 8g sandisk cruzer.

So testdisk says the boot sector is fine. theres nothing to do but I noticed it thinks the partition is bigger than it really is. From what I remember it was around <280GB not 300. I installed Ubuntu via wubi the first time and thats what caused this mess. I can find the individual boot files if need be via testdisk but I dont know what they are. Still wondering how to get it to realize the files its viewing is actually my C:/

Edit: tried again. the boot manager came up (YAY) but says the error is 0xc0000098 and has to do with /boot/BCD? says no valid OS selection

---

### Post by freshmeat20 on 2011-01-27
bump...

---

### Post by oldfred on 2011-01-27
You are really into Windows fixes, which we know only a little about in trying to dual boot.

The window repair CD normally replaces/repairs BCD. Is the rest of your windows showing correctly in the windows partition - /Windows/System32 & /Windows/System?

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by freshmeat20 on 2011-01-27
Sure is, Everything is untouched  and I can view every individual file with testdisk as if I was already in Windows. Its when I try to boot the USB it gets the boot/BCD error. It can start the windows boot manager but the 0xc000098 error is where it stops. Im thinking its because the BCD in the flash drive somehow is shot.

---

### Post by Mark Phelps on 2011-01-27
If you're really trying to fix a Win7 boot problem, not to belittle the support you get here -- but you really need to take that problem to a Win7 forum.  Suggest sevenforums.com.

They have lots of tutorials you can read through that help solve various kinds of boot problems.

BTW, if you're trying to boot Win7 from USB, AFAIK, that can NOT be done.  MS does not want folks walking around with portable versions of their OS's.

If you've copied the contents of the Win7 Repair CD to USB, AFAIK, that should boot, but again, I'd check on the Win7 forums to see what advice they will give you.  It may be a simple change to make that workable.

---

### Post by freshmeat20 on 2011-01-27
Lol I know. Sorry about the mostly Win7 question but I have a thread started at sevenforums too to help me with the recovery software itself. I didnt think you could build the USB in ubuntu but you can boot it if its NTFS formatted. Thats what I thought was weird because shouldnt it be FAT? Anyway I think Ive got it covered from this point in Ubuntu thanks for the help all.

---

