---
title: "Multiple OS, need to remove 2 whilst saving GRUB"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by computer_nerd on 2011-01-20
Ok, so this is my first post to the forum. I'm fairly new to Ubuntu and am still learning. Basically my laptop did have a Windows 7 partition that came with the system(which I no longer need), a  Ubuntu partition and a separate partition for storage. This was until I formatted the separate partition using Windows and it did something which gave me a file system error and would not let me boot into any os. Then because I was in a rush and had lectures in a hour I installed another Ubuntu partition of 3gb just to reinstall GRUB so I could boot into my original Ubuntu to get my files.
 

 Now I would like to delete the 3gb Ubuntu partition and the Windows partition to be left with my original Ubuntu partition and then merge the hard drive into just the one partition. My main fear before I attempt this is again destroying my GRUB.
 

 I know I have made a mess of this but would really appreciate being pointed into the right direction. I have done some searching and reading but struggled to find clearish instructions on how to do it properly.
 

 Thanks for any help

---

### Post by 1clue on 2011-01-20
If you're using LVM2, then I would recommend simply marking your other partitions as LVM autodetect, add them to the same volume group as your working partition and let the system take care of the rest.

---

### Post by presence1960 on 2011-01-20
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by computer_nerd on 2011-01-21
1clue -  I looked into LVM2 and found a version with a GUI but it wasn't letting me change anything though. Ill keep reading into it though.

I managed to restore GRUB but it doesn't have a menu to boot into the os. I only have a shell at the moment.

presence1960 - I ran the script which is below. I saw it still has Windows 7 there although I removed that os. But im sure you can see what is going on there a lot better than I am.

RESULTS.txt

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 339807328 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *     27,265,024    27,469,823       204,800   7 HPFS/NTFS
/dev/sda4         318,435,326   488,396,799   169,961,474   f W95 Ext d (LBA)
/dev/sda5         318,435,328   402,776,063    84,340,736  83 Linux
/dev/sda6         402,778,112   406,476,799     3,698,688  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     6,146,047     6,144,000   b W95 FAT32
/dev/sdb2           6,146,048   312,575,999   306,429,952   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       9f6814ae-c76e-ae4d-b8a9-e98c6e2a9560   ext2       casper-rw                     
/dev/sda2        C2647A51647A47E5                       ntfs       SYSTEM RESERVED               
/dev/sda4: PTTYPE="dos" 
/dev/sda5        3787adf7-8603-4ae2-9865-34e69c2ff503   ext4                                     
/dev/sda6                                               swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F6BB-75D7                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/3787adf7-8603-4ae2-9865-34e69c2ff503 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3787adf7-8603-4ae2-9865-34e69c2ff503
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3787adf7-8603-4ae2-9865-34e69c2ff503
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3787adf7-8603-4ae2-9865-34e69c2ff503
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=3787adf7-8603-4ae2-9865-34e69c2ff503 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3787adf7-8603-4ae2-9865-34e69c2ff503
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=3787adf7-8603-4ae2-9865-34e69c2ff503 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3787adf7-8603-4ae2-9865-34e69c2ff503
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3787adf7-8603-4ae2-9865-34e69c2ff503 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3787adf7-8603-4ae2-9865-34e69c2ff503
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3787adf7-8603-4ae2-9865-34e69c2ff503 ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3787adf7-8603-4ae2-9865-34e69c2ff503
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3787adf7-8603-4ae2-9865-34e69c2ff503
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set c2647a51647a47e5
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=3787adf7-8603-4ae2-9865-34e69c2ff503 /               ext4    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 167.6GB: boot/grub/grub.cfg
 173.9GB: boot/grub/stage2
 164.2GB: boot/initrd.img-2.6.35-22-generic
 165.7GB: boot/initrd.img-2.6.35-24-generic
 173.9GB: boot/vmlinuz-2.6.35-22-generic
 173.9GB: boot/vmlinuz-2.6.35-24-generic
 165.7GB: initrd.img
 164.2GB: initrd.img.old
 173.9GB: vmlinuz
 173.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  44 44 49 4e 47 58 58 58  50 41 44 44 49 4e 47 58  |DDINGXXXPADDINGX|
00000010  58 58 50 41 44 44 49 4e  47 58 58 58 50 41 44 44  |XXPADDINGXXXPADD|
00000020  49 4e 47 58 58 58 50 41  44 44 49 4e 47 58 58 58  |INGXXXPADDINGXXX|
00000030  50 41 44 44 49 4e 47 58  58 58 50 41 44 44 49 4e  |PADDINGXXXPADDIN|
00000040  47 58 58 58 50 41 44 44  49 4e 47 58 58 58 50 41  |GXXXPADDINGXXXPA|
00000050  44 44 49 4e 47 58 58 58  0d 0a 50 41 44 44 49 4e  |DDINGXXX..PADDIN|
00000060  47 58 58 58 50 41 44 44  49 4e 47 58 58 58 50 41  |GXXXPADDINGXXXPA|
00000070  44 44 49 4e 47 58 58 58  50 41 44 44 49 4e 47 58  |DDINGXXXPADDINGX|
00000080  58 58 50 41 44 44 49 4e  47 58 58 58 50 41 44 44  |XXPADDINGXXXPADD|
00000090  49 4e 47 58 58 58 50 41  44 44 49 4e 47 58 58 58  |INGXXXPADDINGXXX|
000000a0  50 41 44 44 49 4e 47 58  58 58 50 41 44 44 49 4e  |PADDINGXXXPADDIN|
000000b0  47 58 58 58 50 41 44 44  49 4e 47 58 58 58 0d 0a  |GXXXPADDINGXXX..|
000000c0  50 41 44 44 49 4e 47 58  58 58 50 41 44 44 49 4e  |PADDINGXXXPADDIN|
000000d0  47 58 58 58 50 41 44 44  49 4e 47 58 58 58 50 41  |GXXXPADDINGXXXPA|
000000e0  44 44 49 4e 47 58 58 58  50 41 44 44 49 4e 47 58  |DDINGXXXPADDINGX|
000000f0  58 58 50 41 44 44 49 4e  47 58 58 58 50 41 44 44  |XXPADDINGXXXPADD|
00000100  49 4e 47 58 58 58 50 41  44 44 49 4e 47 58 58 58  |INGXXXPADDINGXXX|
00000110  50 41 44 44 49 4e 47 58  58 58 50 41 44 44 49 4e  |PADDINGXXXPADDIN|
00000120  47 58 58 58 0d 0a 50 41  44 44 49 4e 47 58 58 58  |GXXX..PADDINGXXX|
00000130  50 41 44 44 49 4e 47 58  58 58 50 41 44 44 49 4e  |PADDINGXXXPADDIN|
00000140  47 58 58 58 50 41 44 44  49 4e 47 58 58 58 50 41  |GXXXPADDINGXXXPA|
00000150  44 44 49 4e 47 58 58 58  50 41 44 44 49 4e 47 58  |DDINGXXXPADDINGX|
00000160  58 58 50 41 44 44 49 4e  47 58 58 58 50 41 44 44  |XXPADDINGXXXPADD|
00000170  49 4e 47 58 58 58 50 41  44 44 49 4e 47 58 58 58  |INGXXXPADDINGXXX|
00000180  50 41 44 44 49 4e 47 58  58 58 0d 0a 50 41 44 44  |PADDINGXXX..PADD|
00000190  49 4e 47 58 58 58 50 41  44 44 49 4e 47 58 58 58  |INGXXXPADDINGXXX|
000001a0  50 41 44 44 49 4e 47 58  58 58 50 41 44 44 49 4e  |PADDINGXXXPADDIN|
000001b0  47 58 58 58 50 41 44 44  49 4e 47 58 58 58 00 fe  |GXXXPADDINGXXX..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f0 06 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f0  06 05 00 78 38 00 00 00  |...........x8...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 3e 11  |.X.SYSLINUX...>.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 c0 5d 00 61 17 00 00  00 00 00 00 02 00 00 00  |..].a...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 d7 75 bb f6 4e  4f 20 4e 41 4d 45 20 20  |..).u..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 00 40 58 00  66 ba 00 00 00 00 bb 00  |}.f..@X.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  eb 76 90 45 58 46 41 54  20 20 20 00 00 00 00 00  |.v.EXFAT   .....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000040  00 c8 5d 00 00 00 00 00  00 c0 43 12 00 00 00 00  |..].......C.....|
00000050  00 08 00 00 00 25 00 00  00 30 00 00 90 43 12 00  |.....%...0...C..|
00000060  05 00 00 00 7f a5 07 30  00 01 00 00 09 08 01 80  |.......0........|
00000070  05 00 00 00 00 00 00 00  33 c9 8e d1 bc f0 7b 8e  |........3.....{.|
00000080  d9 a0 fb 7d b4 7d 8b f0  ac 98 40 74 0c 48 74 0e  |...}.}....@t.Ht.|
00000090  b4 0e bb 07 00 cd 10 eb  ef a0 fd 7d eb e6 cd 16  |...........}....|
000000a0  cd 19 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  0d 0a 52 65 6d 6f 76 65  20 64 69 73 6b 73 20 6f  |..Remove disks o|
00000110  72 20 6f 74 68 65 72 20  6d 65 64 69 61 2e ff 0d  |r other media...|
00000120  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
00000130  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
00000140  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 ff ff  |................|
000001c0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001f0  ff ff ff ff ff ff ff ff  ff ff ff 00 1f 2c 55 aa  |.............,U.|
00000200

---

### Post by presence1960 on 2011-01-21
Your ubuntu is located inside an extended partition. sda2 is the System Reserved partition for windows 7 which is similar to a /boot partition in linux.

I would remove the sda2 partition and create an ext3 or ext4 partition for storage from all the unallocated space from sda1 & sda2.

---

### Post by computer_nerd on 2011-01-21
Ok, I have removed the sda2 partition and reformatted the other partitions. Do you know how I can get my GRUB menu back. Also do you know how I can boot into my os using the GRUB shell for the moment?

---

### Post by 1clue on 2011-01-21
Completely disregard my post.  You seem to be using a non-LVM system.

---

### Post by computer_nerd on 2011-01-21
1clue - Ok Thanks for trying to help anyway.

---

