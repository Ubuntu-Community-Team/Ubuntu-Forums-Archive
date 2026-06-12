---
title: "Ubuntu black screen at login"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by jeffreylees on 2011-06-27
I just used a LiveCD to install Ubuntu 11.04 x64 on my HP desktop. I'm not sure what you need to troubleshoot. It has the following specs:

HP Pavilion Media Center m8539f PC
AMD Phenom X4 9550 QC Processor
5gb ram, 750 gb hdd
Came with vista home prem, nothing left of that except the old restore partition, which I have left intact. It had Windows XP installed recently, but that's completely erased. GeForce 9300GE Video Card


Anyway, I want the x64 so that I can have access to my RAM, among other things. 

After installation with the LiveCD, it will come on, present me with generic/safe/etc boot options, and then when either safe or generic is chosen, it goes to an (active?) cursor for a few seconds before revving the HD, screen going black, and then... nothing. No indication it is even still powered at all except the light on front.


Help :( 

I'm very familiar with support/troubleshooting Windows side but I've never had much education, self or any other kind, on Linux systems. 

PS I think the black screen occurs around login time, but I had it set to auto login so that I could more easily use it remotely - I usually do a lot of setup on a new computer remotely, ie updates and things, and then remove the capability and restore the login screen later.

I already tried another reinstall once. Same results.

---

### Post by nzjethro on 2011-06-27
Hi Jeffreylees. You'll see in my signature a link to a "bootinfo script". Please boot to your Ubuntu Live CD, then run this script (all instructions are given at the link), and post the results.txt file back here (either as an attachment, or inside [CODE] tags, which can be activated by clicking the **#** above the reply box). This will give us an idea of where the problem is in terms of booting, or even whether this is a boot issue (I know some people have run into similar issues due to video card problems).

:)

---

### Post by jeffreylees on 2011-06-30
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.COM

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,046 1,441,189,887 1,441,187,842   5 Extended
/dev/sda5               2,048     7,813,119     7,811,072  82 Linux swap / Solaris
/dev/sda6           7,815,168 1,432,803,327 1,424,988,160  83 Linux
/dev/sda7       1,432,805,376 1,441,189,887     8,384,512  82 Linux swap / Solaris
/dev/sda2    *  1,441,191,150 1,465,144,064    23,952,915   7 NTFS / exFAT / HPFS


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63    15,682,526    15,682,464   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/sda5        935655e8-7d9c-4863-a6eb-bb124b20641b   swap       
/dev/sda6        716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f   ext4       
/dev/sda7        01025dbc-2655-471f-b09e-99a7d6681f30   swap       
/dev/sdf1        00AD-17EE                              vfat       JEFFS-DRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/JEFFS-DRIVE       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=716e3dfe-c0d0-4c66-84d1-b1fdcc00b37f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=01025dbc-2655-471f-b09e-99a7d6681f30 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 359.861099243 = 386.397913088  boot/grub/core.img                             1
 643.864723206 = 691.344482304  boot/grub/grub.cfg                             1
   5.301303864 = 5.692231680    boot/initrd.img-2.6.38-8-generic               1
 359.859378815 = 386.396065792  boot/vmlinuz-2.6.38-8-generic                  1
   5.301303864 = 5.692231680    initrd.img                                     1
 359.859378815 = 386.396065792  vmlinuz                                        1

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  01 00 3d 33 31 62 66 33  38 35 36 61 64 33 36 34  |..=31bf3856ad364|
00000010  65 33 35 26 61 6d 70 3b  76 65 72 73 69 6f 6e 53  |e35&amp;versionS|
00000020  63 6f 70 65 3d 6e 6f 6e  53 78 53 26 61 6d 70 3b  |cope=nonSxS&amp;|
00000030  73 63 6f 70 65 3d 61 6c  6c 55 73 65 72 73 5c 6d  |scope=allUsers\m|
00000040  65 74 61 64 61 74 61 5c  65 6c 65 6d 65 6e 74 73  |etadata\elements|
00000050  5c 52 61 64 69 6f 4c 6f  63 61 74 69 6f 6e 22 20  |\RadioLocation" |
00000060  6e 61 6d 65 3d 22 40 73  75 62 53 63 6f 70 65 22  |name="@subScope"|
00000070  20 74 79 70 65 3d 22 30  78 31 30 30 30 30 30 30  | type="0x1000000|
00000080  63 22 20 65 6e 63 6f 64  69 6e 67 3d 22 62 61 73  |c" encoding="bas|
00000090  65 36 34 22 20 76 61 6c  75 65 3d 22 62 51 42 68  |e64" value="bQBh|
000000a0  41 47 4d 41 61 41 42 70  41 47 34 41 5a 51 42 54  |AGMAaABpAG4AZQBT|
000000b0  41 48 41 41 5a 51 42 6a  41 47 6b 41 5a 67 42 70  |AHAAZQBjAGkAZgBp|
000000c0  41 47 4d 41 41 41 41 3d  22 2f 3e 0a 20 20 20 20  |AGMAAAA="/>.    |
000000d0  20 20 20 20 3c 53 65 74  4b 65 79 56 61 6c 75 65  |    <SetKeyValue|
000000e0  20 70 61 74 68 3d 22 5c  52 65 67 69 73 74 72 79  | path="\Registry|
000000f0  5c 6d 61 63 68 69 6e 65  5c 53 63 68 65 6d 61 5c  |\machine\Schema\|
00000100  77 63 6d 3a 2f 2f 4d 69  63 72 6f 73 6f 66 74 2d  |wcm://Microsoft-|
00000110  57 69 6e 64 6f 77 73 2d  57 6c 61 6e 73 76 63 3f  |Windows-Wlansvc?|
00000120  76 65 72 73 69 6f 6e 3d  36 2e 30 2e 36 30 30 31  |version=6.0.6001|
00000130  2e 31 38 32 38 38 26 61  6d 70 3b 6c 61 6e 67 75  |.18288&amp;langu|
00000140  61 67 65 3d 6e 65 75 74  72 61 6c 26 61 6d 70 3b  |age=neutral&amp;|
00000150  70 72 6f 63 65 73 73 6f  72 41 72 63 68 69 74 65  |processorArchite|
00000160  63 74 75 72 65 3d 61 6d  64 36 34 26 61 6d 70 3b  |cture=amd64&amp;|
00000170  70 75 62 6c 69 63 4b 65  79 54 6f 6b 65 6e 3d 33  |publicKeyToken=3|
00000180  31 62 66 33 38 35 36 61  64 33 36 34 65 33 35 26  |1bf3856ad364e35&|
00000190  61 6d 70 3b 76 65 72 73  69 6f 6e 53 63 6f 70 65  |amp;versionScope|
000001a0  3d 6e 6f 6e 53 78 53 26  61 6d 70 3b 73 63 6f 70  |=nonSxS&amp;scop|
000001b0  65 3d 61 6c 6c 55 73 65  72 73 5c 6d 65 74 00 20  |e=allUsers\met. |
000001c0  21 00 82 57 71 e6 02 00  00 00 00 30 77 00 00 57  |!..Wq......0w..W|
000001d0  72 e6 05 fe ff ff 02 30  77 00 00 a0 ef 54 00 00  |r......0w....T..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdf1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 08 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 ff 00 00 00 00 00  |........ .......|
00000020  a0 4b ef 00 b6 3b 00 00  00 00 00 00 02 00 00 00  |.K...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 ee 17 ad 00 4a  45 46 46 53 2d 44 52 49  |..)....JEFFS-DRI|
00000050  56 45 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |VEFAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

