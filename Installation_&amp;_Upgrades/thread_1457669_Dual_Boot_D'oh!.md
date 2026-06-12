---
title: "Dual Boot D'oh!"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by jaamzg on 2010-04-18
Got a new HP a couple of months ago with Windows 7 and installed ubuntu 9.10 with wubi.  Dual boot worked well and I have been enjoying linux thoroughly.  But, I apparently ran wubi incorrectly and though I had set up about 340 gigs for linux, the /home directory only got about 15 and I was soon getting low disk space messages.  

So, I backed up the /home directory, booted into windows 7 and repartioned giving linux about 340 gigs of it's own partition with the intent of doing a true install.

Well, I did it and now get the error 21 screen.  I went in with the Windows 7 recovery disk and got Windows 7 booting.  Then, went in with supergrub and tried to get grub reinstalled.  I then got grub set up, but Windows 7 wasn't showing up.  So, I tried using supergrub to fix things and ended up with error 21.  

So, how can I get this working again?  I am using supergrub to boot up into linux from a pendrive, so it shows up as sdb1 in my list.  I've tried some different things from around the site, but I'm not having any luck.  Can someone help out a poor noob?

  ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97-os.1 is installed in the MBR of /dev/sda and looks on boot drive 
    #2 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97-os.1 is installed in the MBR of /dev/sdb and looks at sector 
    532573 of the same hard drive for the stage2 file. A stage2 file is at 
    this location on /dev/sdb. Stage2 looks on partition #1 for 
    /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xccfbc4d0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       202,751       200,704   7 HPFS/NTFS
/dev/sda2             208,845   751,472,504   751,263,660   7 HPFS/NTFS
/dev/sda3         751,472,505 1,439,263,349   687,790,845   5 Extended
/dev/sda5         751,472,568 1,411,326,314   659,853,747  83 Linux
/dev/sda6       1,411,326,378 1,439,263,349    27,936,972  82 Linux swap / Solaris
/dev/sda4       1,439,264,768 1,465,145,343    25,880,576   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 506 MB, 506461696 bytes
129 heads, 8 sectors/track, 958 cylinders, total 989183 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5befc7a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *              8       989,182       989,175   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1EB008A1B008820F                       ntfs       SYSTEM                        
/dev/sda2        18966F98966F7562                       ntfs       HP                            
/dev/sda4        6E3087AD30877ABB                       ntfs       FACTORY_IMAGE                 
/dev/sda5        014cff23-0297-4968-afb2-7797f4930a37   ext4                                     
/dev/sda6        444c4ae0-802e-4650-bd24-a1cb5a16b922   swap                                     
/dev/sdb1        F23F-9FD3                              vfat       My 512MB                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/My 512MB          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr1         /media/Ativa U3 System   iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=014cff23-0297-4968-afb2-7797f4930a37 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=014cff23-0297-4968-afb2-7797f4930a37

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        014cff23-0297-4968-afb2-7797f4930a37
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=014cff23-0297-4968-afb2-7797f4930a37 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        014cff23-0297-4968-afb2-7797f4930a37
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=014cff23-0297-4968-afb2-7797f4930a37 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        014cff23-0297-4968-afb2-7797f4930a37
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=014cff23-0297-4968-afb2-7797f4930a37 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        014cff23-0297-4968-afb2-7797f4930a37
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=014cff23-0297-4968-afb2-7797f4930a37 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        014cff23-0297-4968-afb2-7797f4930a37
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        014cff23-0297-4968-afb2-7797f4930a37
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 014cff23-0297-4968-afb2-7797f4930a37
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 014cff23-0297-4968-afb2-7797f4930a37
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=014cff23-0297-4968-afb2-7797f4930a37 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 014cff23-0297-4968-afb2-7797f4930a37
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=014cff23-0297-4968-afb2-7797f4930a37 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 6e3087ad30877abb
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=014cff23-0297-4968-afb2-7797f4930a37 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=444c4ae0-802e-4650-bd24-a1cb5a16b922 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 384.8GB: boot/grub/core.img
 385.3GB: boot/grub/grub.cfg
 397.0GB: boot/grub/menu.lst
 385.3GB: boot/initrd.img-2.6.31-14-generic
 385.5GB: boot/initrd.img-2.6.31-20-generic
 385.3GB: boot/vmlinuz-2.6.31-14-generic
 385.4GB: boot/vmlinuz-2.6.31-20-generic
 385.5GB: initrd.img
 385.3GB: initrd.img.old
 385.4GB: vmlinuz
 385.3GB: vmlinuz.old

=========================== sdb1/boot/grub/menu.lst: ===========================

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 0
timeout 2
setgrubdevice # This is compulsory
#sgdgfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


#title Inicio normal / Normal Boot 
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs

#title Soporte de accesibilidad / Accesibility Support -->
#configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

#title Normal boot. Kernel is aware of Boot device
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
#initrd $(grub_device)/initramfs

#title Normal boot. Selecting kernel and initrd files depending on grub_device
#kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs_$(grub_device_string)

#title Selecthd test
#configfile $(grub_device)/boot/grub/choose/selecthd.lst

#title findp test
#configfile $(grub_device)/boot/grub/choose/selectpart.lst
#title set SGD variables and boot SGD
#
#configfile $(grub_device)/boot/sgd/menu.lst

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/menu.lst
    ??GB: boot/grub/stage2
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 10 01 00  |.<.DOK01.02.....|
00000010  02 00 02 00 00 f8 f2 00  08 00 80 00 08 00 00 00  |................|
00000020  f7 17 0f 00 80 01 29 d3  9f 3f f2 4d 79 20 35 31  |......)..?.My 51|
00000030  32 4d 42 00 00 00 46 41  54 31 36 20 20 20 33 c9  |2MB...FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by jaamzg on 2010-04-19
Soooo...just to add a little info.

I ran grub then find /boot/grub/stage1 and it tells me its on (hd1,0) which I suspect is the pendrive.  Taking the pendrive out, I rerun and get an error 15.  I'm guessing I don't have stage1 loaded on my hard drive?  I ran sudo apt-get install grub and then sudo update-grub then reran the find /boot/grub/stage1 and no dice.  

Is my problem that I don't have stage1 on my hard drive or grub is not creating the file?  When I run the update-grub, it finds the two linux kernels, the recovery kernels, some memtest something, and the vista loader, but not the Win 7.  And when I boot from supergrub, it finds all that, but not the win 7.  But I can't boot from the hard drive because I get the error 21.  

It seems like it should be something simple...any suggestions?

---

### Post by oldfred on 2010-04-21
I see several problems that look like you have mixed up grub and grub2.

Operating System:  
    Boot files/dirs:   /bootmgr [COLOR=Blue]/Boot/BCD[/COLOR] [COLOR=Red]/boot/grub/core.img[/COLOR]

You windows will not boot has you have /Boot/BCD (windows files) and /boot (grub files) directories and windows sees that as the same where as in linux capital and small are different. From a liveCd delete /boot/grub/core.img - all files and directories so you do not have two boot directories. Be sure to keep /Boot/BCD as that is essential to windows.

The grub in the MBR is looking to boot from sdb which is not a linux partition. Your install is in sda5 and is mostly grub2 but has menu.lst which is grub legacy. I have seen where just reinstalling grub2 to the MBR does not work as old grub somehow interfers but we will try that first.
Use a liveCD and reinstall grub2 to the MBR of sda.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

From LiveCD
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-install --recheck --root-directory=/mnt /dev/sda

After rebooting if it works
sudo update-grub

If you fixed the /boot /Boot problem in windows it will find the windows in sda and add it to you grub menu grub.cfg file.

---

### Post by jaamzg on 2010-04-21
Hi Oldfred!

Thanks so much for your help, it had been a couple of days since I posted and I thought I was going to be left floating in a see of noreplies!

I deleted the small b /boot as you instructed.  I did not run the windows 7 install disk yet because I was assuming (incorrectly perhaps) that going through this first step would allow for a proper booting and the finding of the windows 7 boot info under big B /Boot/BCD

I did run the instructions from LiveCD as you printed and was able to reboot.  It gave me a list of options to boot, including the older -14 linux kernel.  I rebooted and ran the sudo update-grub command.  This is what it gave me...

```
james@james-desktop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

After rebooting, I get the grub menu but it does not list the -20 kernel nor Windows 7.  I also see that it updates the menu.lst file, but from your commentary I take that to be legacy grub and that it should not be there.  I thought I could manually delete the grub folder and/or files and rerun your instructions, but I was not allowed access.  I can now boot from the hard drive without the pendrive, but still can't get the other boot options going.  

What should I try next?

thanks again

---

### Post by oldfred on 2010-04-21
I did not know that grub would update the menu.lst. Since they are in system directories you need to use sudo to delete.

This may be better as it will totally uninstall grub & grub2 then reinstall grub2 so it has a new clean install. Since you seem to be able to boot.

sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by jaamzg on 2010-04-21
Oldfred,

I had tried using sudo rm instead of purge (i'm such a noob) to get rid of the old grub files.  Anyway, the purge worked great and the reinstall went smoothly.

This is the new output after the update-grub:

```
james@james-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda4
done

``` 

It looks like it found everything.  I'm going to reboot.  I'll report back with the results.

---

### Post by jaamzg on 2010-04-21
oldfred,

Success!!

I was able to reboot into the -20 generic of linux and was also able to boot into windows 7!

I thought it was something simple, but had no idea how to figure it out.  Just to review for my personal learning and for anyone else the might read this later, this is my understanding of what was wrong and how it got fixed.

Somehow, the grub boot got installed on sda1, which is the win 7 partition.  So, there was confusion in the windows system.  In addition, on the linux partition of sda5, grub2 was mixed with grub legacy and so neither was booting.  The system was booting because I was using Supergrub on a pendrive, but the grub was pointing back at the pendrive sdb1, and not recognizing anything on the hard drive.

So, you had me manually remove the extra /boot file on the win7 sda1 partition which was grub and leave the /Boot files on there which was win7 startup.  This cleared some confusion, but the grub on sda5 was still mixed with grub2 and legacy grub and not allowing a proper read of the different bootable files.  Then the instructions were to purge the entire /grub from the /boot of sda5 and start with a fresh grub install.
Then, it was updated and able to read everything properly.

Was that about right?

Thanks so much for your help.  I hereby christen thee Wisefred (sounds better than old).

---

### Post by oldfred on 2010-04-21
I think you have it down pat.

Thank you for the complement. I was not so wise starting out. I go back and look at some old attempts to help and sometimes they were not so good:(. Fortunately most here on the forum politely correct things, offer alternatives, and you also learn:). I have learned more in the last year trying to help than I did in my first few years just using & fixing my Ubuntu.

---

### Post by jaamzg on 2010-04-21
Well, I'm about 2 months into linux, so I've got a long way to go.  It is a pretty steep learning curve, but I think I would rather learn this than win 7.  

Thanks again for your help, and hopefully this helps others!

---

