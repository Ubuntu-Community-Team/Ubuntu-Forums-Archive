---
title: "Grub2 could not find Windows XP on second hard drive"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by liquifred on 2010-11-28
I have already solved this problem but thought I should share the solution in case it helped others.

I have three hard drives in my PC.  A while ago I formatted one of them and put Ubuntu and the Windows 7 Release Candidate on it (it was when that came out).  I set up a simple triple boot, leaving XP untouched on a second hard drive.  It was long enough ago that the original GRUB was used (I think it was Ubuntu 9.05).  It all worked fine.  As my wife didnt want to change I reverted back to XP as the main OS but left the others on the other drive to fool around with every now and then.

To cut a long story short I decided to give Ubuntu another go recently, so formatted the second drive again and installed Ubuntu 10.10 fresh.  Here I struck a problem: the Grub2 os-prober thought that my XP hard drive was Windows 7.  If I chose that option the loader would just go to a blinking cursor.  If I used the BIOS to boot  directly from the WindowsXP hard drive, it would boot fine.

I tried a lot of different things to fix the situation:
- quite a few custom GRUB entries found on these forums - none worked.  In fact I couldnt get them to add any Windows entries to the GRUB menu, it seems that GRUB would always check whether it was actually valid and just ignore them when I did an update-grub.  I may have been doing something wrong, although if I added custom Ubuntu menu items they worked fine.
- using EasyBCD on the windows XP installation to check whether that boot sector was ok.  It did say that Windows 7 was still there somewhere
- looking in the C:/ drive from XP for C:/boot.  It didnt show up in XP.
- using the startup-manager UI version.  Any custom menu items I was trying showed up on this but never on the GRUB menu itself.
- the results.txt script from these forums, which didnt seem to show any errors:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    29,296,937    29,296,875  83 Linux
/dev/sda2         149,838,316   156,296,384     6,458,069   5 Extended
/dev/sda5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris
/dev/sda4          29,298,688   149,837,823   120,539,136  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,953,520,064 1,953,520,002   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        d22e8f2e-18a1-43c4-bfe5-16ff046374ba   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda4        92301411-73e5-4256-b48f-845595bb55c4   ext4                                     
/dev/sda5        5981edcd-c83f-4aab-81c6-ccd8304fc03b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F4D84F61D84F20EA                       ntfs       windowsxp                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        48F4503FF4503204                       ntfs       data                          
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda4        /home                    ext4       (rw,commit=0)
/dev/sdc1        /media/data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d22e8f2e-18a1-43c4-bfe5-16ff046374ba
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d22e8f2e-18a1-43c4-bfe5-16ff046374ba
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=7
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d22e8f2e-18a1-43c4-bfe5-16ff046374ba
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=d22e8f2e-18a1-43c4-bfe5-16ff046374ba ro  vga=788  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d22e8f2e-18a1-43c4-bfe5-16ff046374ba
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=d22e8f2e-18a1-43c4-bfe5-16ff046374ba ro single  vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d22e8f2e-18a1-43c4-bfe5-16ff046374ba
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d22e8f2e-18a1-43c4-bfe5-16ff046374ba ro  vga=788  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d22e8f2e-18a1-43c4-bfe5-16ff046374ba
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d22e8f2e-18a1-43c4-bfe5-16ff046374ba ro single  vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set f4d84f61d84f20ea
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d22e8f2e-18a1-43c4-bfe5-16ff046374ba /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=92301411-73e5-4256-b48f-845595bb55c4 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5981edcd-c83f-4aab-81c6-ccd8304fc03b none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   8.6GB: boot/grub/core.img
   8.6GB: boot/grub/grub.cfg
   8.6GB: boot/initrd.img-2.6.35-22-generic
   8.6GB: boot/initrd.img-2.6.35-23-generic
   8.6GB: boot/vmlinuz-2.6.35-22-generic
   8.6GB: boot/vmlinuz-2.6.35-23-generic
   8.6GB: initrd.img
   8.6GB: initrd.img.old
   8.6GB: vmlinuz
   8.6GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /FASTDETECT /NOEXECUTE=OPTIN
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  26 5a 59 32 f6 4b d8 52  5d 9c b0 89 58 9d 38 6d  |&ZY2.K.R]...X.8m|
00000010  e9 59 2c 46 bd a1 82 26  81 fc 3e bd d7 c1 47 d5  |.Y,F...&..>...G.|
00000020  8d 96 98 ad e7 e8 7b fc  56 dd bb 72 b3 c5 2d 75  |......{.V..r..-u|
00000030  57 77 09 69 cb ee c6 f7  6d 0f c1 96 9d db 75 6b  |Ww.i....m.....uk|
00000040  1c 91 3e 6a ce 2c fc cf  d1 c3 13 f6 9b b5 c6 cb  |..>j.,..........|
00000050  02 81 60 32 58 93 96 0d  1d 38 ff 1e 05 d4 56 10  |..`2X....8....V.|
00000060  c2 a9 b2 8d 2d 39 5f 0c  d1 5c fc 2d 74 36 32 d2  |....-9_..\.-t62.|
00000070  fd b5 f6 e9 ad ea 0a 39  14 47 44 e4 0d 33 5c 50  |.......9.GD..3\P|
00000080  f0 f8 2c ae 64 04 e5 3e  43 ba 70 6d 33 43 8b 59  |..,.d..>C.pm3C.Y|
00000090  50 52 2a 5c 5c 6d f5 00  f0 76 f5 6c 72 85 b8 5b  |PR*\\m...v.lr..[|
000000a0  2e ef e8 45 99 7f 77 f0  c5 61 8d fe 5e f8 88 17  |...E..w..a..^...|
000000b0  f2 41 37 78 93 8a df f1  fe 96 fc d0 4f 77 ef 7f  |.A7x........Ow..|
000000c0  ec 14 99 2e c7 08 a6 eb  bb bd 8a 89 61 4e ee 2b  |............aN.+|
000000d0  3d e2 07 bd 9b 75 26 1a  3d 81 ff 0f 81 ab f2 14  |=....u&.=.......|
000000e0  6c 79 c1 1b 43 5e 49 f6  9f c4 ba 1d 83 f5 fc c2  |ly..C^I.........|
000000f0  0d 78 56 fb fd 31 8f 8a  97 af 8e 7a d7 b5 95 35  |.xV..1.....z...5|
00000100  55 ed 78 72 66 43 8b 09  75 86 25 26 3e 38 7a 5c  |U.xrfC..u.%&>8z\|
00000110  6f 8a 9f 85 33 18 98 45  a4 67 4b 35 0f 2e 7e 95  |o...3..E.gK5..~.|
00000120  5e 99 72 ab ea ec 13 dd  fb 4b 6d d6 6d 34 c7 fd  |^.r......Km.m4..|
00000130  e3 f4 8b 13 3b 9a d3 49  b6 bf 22 59 26 30 d5 ba  |....;..I.."Y&0..|
00000140  4b 1b 49 06 cb 5d b3 cb  a0 7e fc 5c a8 9f 0f f0  |K.I..]...~.\....|
00000150  48 fd 3f fa ff d5 dd f4  48 86 1b ee eb f8 b4 94  |H.?.....H.......|
00000160  bf 79 b9 ae fd 74 08 e9  bb bb 52 97 09 65 fb b6  |.y...t....R..e..|
00000170  2b d7 8e bd ed d0 9c 6c  44 9f 3c bf ef 85 21 66  |+......lD.<...!f|
00000180  c1 ee 37 2c 77 c7 12 ee  d2 19 69 53 f8 92 87 82  |..7,w.....iS....|
00000190  a8 6b 75 52 32 a9 d2 93  7b d3 39 f4 15 67 96 e3  |.kuR2...{.9..g..|
000001a0  c2 73 67 49 3b db 88 0d  b6 db 2d ea 13 92 3a 0d  |.sgI;.....-...:.|
000001b0  4c 62 d3 33 5f 89 8f 65  b1 84 e2 b9 84 52 00 fe  |Lb.3_..e.....R..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 d3 8a 62 00 00 00  |............b...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

The fix finally came when I mounted the XP drive in Ubuntu, copying across information from My Documents preparing to format that drive and start again.  I noticed that from Ubuntu there was actually a C:/boot folder, and a bootmgr file.  I deleted both of them (saving them to another disk just in case) and ran update-grub again.  Now the Windows hard drive showed up as Windows XP, and on a reboot it worked a treat!

So to cut a long story short - if you ever install Windows Vista or Windows 7 on the same computer as an existing XP installation, and get rid of that "upgrade", you'll need to remove the BCD it installs on your old XP or grub will never realise that it is actually XP.  I should note that I'm no expert so if this advice is likely to stuff someone's XP installation up please speak up!

Hope this helps someone avoid the frustrating day I had trying all sorts of other solutions.

---

