---
title: "GRUB Error 15 after reinstallation"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by radish_ on 2010-12-01
I have reinstalled my computer twice already.  

I decided to reinstall ubuntu because it was screwing up from something i did so i downloaded a new 10.10 x64 installer and put it on a usb stick to install from. 

Everything went well but now after installing grub won't start and when i go into the live usb stick it states that the partition i made for my grub boot files is empty even though i explicitly stated in the installer to install the /boot folder to a 200 mb partition which i created for this purpose.

I would reinstall grub manually from my live usb ubuntu stick only unlike tutorials and other help forums have stated my live ubuntu stick doesnt have the commands to run grub.  When i go into the terminal and type

sudo grub

it tells me that the command grub doesn't exist.

my folder structure when i installed was

200mb /boot                            format

20000mb /home

50000mb /                               format

this folder structure worked the first time i installed ubuntu.

---

### Post by radish_ on 2010-12-01
thank you ubuntu community for the speedy response(or lack thereof) with my ubuntu related installation problem.

I'll remember next time to not bother wasting my time posting here and solve my own problems.

---

### Post by sikander3786 on 2010-12-01
Welcome to the forums :-)

You need to give some time to the community to try and help you. All of the members here are volunteers and they try to help whenever they are free. None of them gets paid for anything at all. You know :-)

You are going to stay at the forums I hope and I'd advise you not to start bumping the thread before at least 24 hours. Hope you understand, why.

Regarding your original issue, please boot an Ubuntu Live CD, go to try mode and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap your output with proper code # tags from the post menu. [/code] at the end and [code] at the beginning.

Thanks.

---

### Post by radish_ on 2010-12-01
upon using the commands

```

sudo sh '/home/ubuntu/Downloads/boot_info_script055.sh'

ubuntu@ubuntu:~/Downloads$ ./boot_info_script055.sh
bash: ./boot_info_script055.sh: Permission denied

ubuntu@ubuntu:~/Downloads$ sudo ./boot_info_script055.sh
sudo: ./boot_info_script055.sh: command not found

ubuntu@ubuntu:~/Downloads$ sudo /home/ubuntu/Downloads/boot_info_script055.sh
sudo: /home/ubuntu/Downloads/boot_info_script055.sh: command not found

ubuntu@ubuntu:~/Downloads$ sudo sh ./boot_info_script055.sh

ubuntu@ubuntu:~/Downloads$ ./boot_info_script055.sh
bash: ./boot_info_script055.sh: Permission denied

ubuntu@ubuntu:~/Downloads$ sudo '/home/ubuntu/Downloads/boot_info_script055.sh'
sudo: /home/ubuntu/Downloads/boot_info_script055.sh: command not found

ubuntu@ubuntu:~/Downloads$ sudo sh '/home/ubuntu/Downloads/boot_info_script055.sh'


```the script promptly gave me no response


nevermind got it to work

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 282143 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdc2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34       262,177       262,144 Microsoft Windows
/dev/sda2         264,192 1,953,523,711 1,953,259,520 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   129,419,639   129,419,577   7 HPFS/NTFS
/dev/sdb2         129,419,701   137,232,202     7,812,502   5 Extended
/dev/sdb5         129,419,703   137,232,202     7,812,500  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63       530,144       530,082  83 Linux
/dev/sdc2             530,145    41,495,894    40,965,750  83 Linux
/dev/sdc3          41,495,956   156,301,311   114,805,356   5 Extended
/dev/sdc5          41,495,958   147,011,582   105,515,625  83 Linux
/dev/sdc6         147,011,584   156,301,311     9,289,728   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   586,070,015   586,067,968   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 3984 MB, 3984588800 bytes
123 heads, 62 sectors/track, 1020 cylinders, total 7782400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             62     7,778,519     7,778,458   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       2c77409e-9002-4f33-8d82-24c0cdb767f7   ext3                                     
/dev/sda2        40640117640110F8                       ntfs                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        029C0BDC9C0BC95D                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        64c578b1-1017-46fa-827e-b678c1c660d7   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        e433ca78-b0a1-4dce-ae6f-5c163c9ec43a   ext4                                     
/dev/sdc2        89df0580-1c03-45b4-998d-2852f2b9e9d5   ext4       Home                          
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        46a4df5a-2c5c-4cb0-8e47-5cc087e432ab   ext4                                     
/dev/sdc6        15AB2F0D6FE11D18                       ntfs       New Volume                    
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        AA36DF7A36DF464B                       ntfs       Music & Production            
/dev/sdd: PTTYPE="dos" 
/dev/sde1        B36B-79AA                              vfat                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sde1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/e433ca78-b0a1-4dce-ae6f-5c163c9ec43a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc5        /mnt/root                ext4       (rw)
/dev             /mnt/root/dev            none       (rw,bind)


============================= sdc1/grub/grub.cfg: =============================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set 46a4df5a-2c5c-4cb0-8e47-5cc087e432ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos1)'
search --no-floppy --fs-uuid --set e433ca78-b0a1-4dce-ae6f-5c163c9ec43a
set locale_dir=($root)/grub/locale
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
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set e433ca78-b0a1-4dce-ae6f-5c163c9ec43a
    linux    /vmlinuz-2.6.35-22-generic root=UUID=46a4df5a-2c5c-4cb0-8e47-5cc087e432ab ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set e433ca78-b0a1-4dce-ae6f-5c163c9ec43a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=46a4df5a-2c5c-4cb0-8e47-5cc087e432ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set e433ca78-b0a1-4dce-ae6f-5c163c9ec43a
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set e433ca78-b0a1-4dce-ae6f-5c163c9ec43a
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 029c0bdc9c0bc95d
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

=================== sdc1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=46a4df5a-2c5c-4cb0-8e47-5cc087e432ab /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=e433ca78-b0a1-4dce-ae6f-5c163c9ec43a /boot           ext4    defaults        0       2
# /home was on /dev/sdc2 during installation
UUID=89df0580-1c03-45b4-998d-2852f2b9e9d5 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=64c578b1-1017-46fa-827e-b678c1c660d7 none            swap    sw              0       0

=========================== sde1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sde1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  2c 94 2a fd 6d b6 95 7b  e9 35 49 6f 09 7e b4 b4  |,.*.m..{.5Io.~..|
00000010  76 be 40 2b e3 00 bd 72  7d ee fe ff 8a 30 a4 a3  |v.@+...r}....0..|
00000020  c7 c2 08 42 d8 01 a2 47  e5 e0 28 42 12 b9 8b c1  |...B...G..(B....|
00000030  fc d8 5b a4 0a e3 7b 73  b2 79 2c f5 ae 08 21 03  |..[...{s.y,...!.|
00000040  81 0c 48 d6 02 09 74 e0  29 ad f7 83 24 f0 f1 78  |..H...t.)...$..x|
00000050  f0 76 70 70 b9 e5 c5 ad  9f 4f 04 44 45 08 dc 0e  |.vpp.....O.DE...|
00000060  58 a1 39 ce 86 d7 65 a8  2d 95 25 79 52 c1 a1 53  |X.9...e.-.%yR..S|
00000070  d3 c3 a0 e2 f5 c0 e0 fe  25 21 07 0e 28 c7 80 ee  |........%!..(...|
00000080  96 c4 6e 11 e3 71 b8 dd  c0 8c 1e 7c 84 1d 04 31  |..n..q.....|...1|
00000090  a0 3b 25 2c 51 5c e4 5b  e2 7a 58 c3 25 86 e0 7c  |.;%,Q\.[.zX.%..||
000000a0  51 50 9e 19 ed 5e 68 74  38 b8 46 3a 1c 14 60 6f  |QP...^ht8.F:..`o|
000000b0  1f 23 ae 58 64 e8 cf e0  38 66 73 f7 eb d7 5d bf  |.#.Xd...8fs...].|
000000c0  5f ac 81 af 22 de 3d b7  82 9f aa e4 ca 11 dd 82  |_...".=.........|
000000d0  24 e9 69 8c 96 b7 72 63  4a 8a 6d d2 c3 dc 91 84  |$.i...rcJ.m.....|
000000e0  02 d9 87 58 a6 91 6d c8  f4 3a 07 1f 70 20 7f b8  |...X..m..:..p ..|
000000f0  38 68 0e 16 c3 04 e9 75  67 33 48 17 de f1 46 f2  |8h.....ug3H...F.|
00000100  65 77 ce b4 e0 45 d5 74  0f 40 79 eb be 10 d3 6d  |ew...E.t.@y....m|
00000110  6f 65 27 bc 14 4d 6e bf  aa ff 44 92 fc bc 52 5e  |oe'..Mn...D...R^|
00000120  aa c2 c9 40 88 90 aa bd  47 6c 6d ae ea 43 95 af  |...@....Glm..C..|
00000130  fb 5b d5 37 51 ae bd 56  e1 58 8f b2 46 65 96 14  |.[.7Q..V.X..Fe..|
00000140  51 0d f9 76 77 6c e7 ef  69 8f fe 7f 17 8c d5 a5  |Q..vwl..i.......|
00000150  6e de 31 1f 8a 33 bf 4a  a1 8a cc 6d cf 4f ad 5b  |n.1..3.J...m.O.[|
00000160  5b 1e 45 3c 5a b0 8d d6  30 d4 83 af c9 7b 6a d1  |[.E<Z...0....{j.|
00000170  03 67 2c 6f df 61 ab 29  9b 9b 71 bc ec a0 a8 67  |.g,o.a.)..q....g|
00000180  13 78 da 7d ca c7 54 46  6e 3f f3 23 77 8a be 25  |.x.}..TFn?.#w..%|
00000190  29 2c b4 b1 5b ac ed f6  56 b7 f7 18 51 2e 21 b2  |),..[...V...Q.!.|
000001a0  69 1e c9 47 b6 fd b1 e2  cc 8f 15 44 00 c7 86 77  |i..G.......D...w|
000001b0  64 6e d6 d0 f2 4c 17 db  6c 51 25 a0 68 7e 00 fe  |dn...L..lQ%.h~..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 94 35 77 00 00 00  |...........5w...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc3

00000000  b1 34 1b 74 aa 39 2c f7  95 84 11 dc 6b 5e 61 9d  |.4.t.9,.....k^a.|
00000010  12 2e d9 54 0e c8 6b 4d  d6 27 f4 4b f1 5d b5 96  |...T..kM.'.K.]..|
00000020  df 79 f9 84 ea d4 5b 58  44 d2 36 fb 6d ff 71 15  |.y....[XD.6.m.q.|
00000030  3d 68 30 9d 7d b2 47 71  a8 27 a9 a1 ac 46 a6 b4  |=h0.}.Gq.'...F..|
00000040  de 2a 94 3f 5e 76 ba 8d  1a 3e 42 58 f7 20 7b 5c  |.*.?^v...>BX. {\|
00000050  b3 b2 38 78 04 80 2a 46  44 90 da ee 27 10 7d e3  |..8x..*FD...'.}.|
00000060  b2 b9 5c ec 82 f5 34 aa  3f 4d a9 55 7b 6f 00 59  |..\...4.?M.U{o.Y|
00000070  b4 c8 c9 92 4c aa 68 cc  b4 c9 cd c3 af 58 8c 4e  |....L.h......X.N|
00000080  5f 35 09 00 96 a9 14 03  13 80 51 25 d0 93 27 23  |_5........Q%..'#|
00000090  0c 33 9a 51 6c 42 8e cd  06 22 fa 86 af 17 24 0f  |.3.QlB..."....$.|
000000a0  e3 bd 53 0f 62 33 7c d8  e9 cf f9 57 49 2c ed 49  |..S.b3|....WI,.I|
000000b0  0b f1 fa 7a 5b d5 bf 4b  88 d5 79 99 2b 50 16 bf  |...z[..K..y.+P..|
000000c0  cc c4 f7 3c 55 d0 f3 66  d8 fe ea d0 6f e5 b6 a3  |...<U..f....o...|
000000d0  b3 98 32 7a 07 22 6a 5d  77 bf ff 77 ff e6 67 fd  |..2z."j]w..w..g.|
000000e0  44 00 00 00 12 a4 50 dc  18 67 eb e3 01 0f 70 76  |D.....P..g....pv|
000000f0  e2 e7 33 92 ba 3c e9 67  b3 ab 5c 20 1f 23 64 b7  |..3..<.g..\ .#d.|
00000100  72 a1 0c aa 00 4a c8 a7  5a 75 f7 b8 b9 ee 3b 71  |r....J..Zu....;q|
00000110  6f be a0 f7 33 18 2a 61  71 43 90 b2 d6 59 c8 99  |o...3.*aqC...Y..|
00000120  ef 49 69 75 fd 46 a2 b1  e3 9f f2 a6 a5 3f 8a f9  |.Iiu.F.......?..|
00000130  47 23 72 b7 8e ed 73 1b  ae 72 69 2e 2c 2b 76 e2  |G#r...s..ri.,+v.|
00000140  72 53 d2 de ad fa 5c 46  ab cc c9 5a 80 b5 fe 66  |rS....\F...Z...f|
00000150  27 b9 e2 ae 87 9b 36 c7  f7 56 83 7f 2d b5 1d 9c  |'.....6..V..-...|
00000160  c1 93 d0 39 13 52 eb bd  ff fb bf ff 33 3f ea 66  |...9.R......3?.f|
00000170  c0 02 01 4e 96 44 b8 82  9f 2c 48 e1 1d 0c 6c 51  |...N.D...,H...lQ|
00000180  6c b6 28 78 0a 42 da 34  8f 05 cf 41 23 c8 da 58  |l.(x.B.4...A#..X|
00000190  80 32 0c a0 79 61 cf b4  4a 4b 36 47 cd 32 a0 9e  |.2..ya..JK6G.2..|
000001a0  5d 5b 26 67 97 30 55 73  c4 f5 e3 33 f0 d7 42 38  |][&g.0Us...3..B8|
000001b0  81 c7 ff fb b0 00 21 80  64 a8 65 5a b9 ec 00 fe  |......!.d.eZ....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 69 0a 4a 06 00 fe  |..........i.J...|
000001d0  ff ff 05 fe ff ff 6b 0a  4a 06 01 c0 8d 00 00 00  |......k.J.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sde1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 7b 00 00 00 00 00  |........>.{.....|
00000020  9a b0 76 00 a0 1d 00 00  00 00 00 00 02 00 00 00  |..v.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 aa 79 6b b3 20  20 20 20 20 20 20 20 20  |..).yk.         |
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
00000100  7d 00 66 b8 e0 f2 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e dd ca 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
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

```

---

### Post by sikander3786 on 2010-12-01
That seems a fairly complex setup :-)

Ok try reinstalling Grub to the MBR of sdc by following these commands.

```
sudo mount /dev/sdc5 /mnt
```

```
sudo mount /dev/sdc1 /mnt/boot
```

```
sudo grub-install --root-directory=/mnt /dev/sdc
```

Note, for the last one, it is just sdc (without an integer) and not sdc1 or sdc5.

Reboot and make your Ubuntu drive i.e, sdc, first boot device in Bios. Hopefully it should boot Ubuntu 10.10 now. If it does, from your installed Ubuntu's terminal, run this command to add Windows to the Grub menu.

```
sudo update-grub
```

If re-installing Grub doesn't help, you might need to chroot, purge and re-install Grub as mentioned here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Good Luck!

---

### Post by radish_ on 2010-12-01
thank you for your help and sorry for the outburst earlier stressed out.

I should probably realize people here are not paid.

anyway the error is gone and grub starts but it doesnt find my ubuntu installation and it takes me to the grub command line.

I know why though my grub folder is missing menu.lst

I can take it from here lol :D

---

### Post by sikander3786 on 2010-12-01
Grub2 doesn't use menu.lst. It is a bit different than the Legacy one.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

See this for booting from the Grub rescue prompt.

[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by oldfred on 2010-12-01
Error #15 is almost always old grub legacy not getting along with new grub2.

sikander3786's Link in post #5 to drs305's uninstall both and reinstall grub2 has the best way to solve it.

---

### Post by radish_ on 2010-12-01
> **oldfred said:**
> Error #15 is almost always old grub legacy not getting along with new grub2.

sikander3786's Link in post #5 to drs305's uninstall both and reinstall grub2 has the best way to solve it.

how could it be an issue with grub legacy i formatted the grub boot directory and installed a new one from disk.  There shouldnt be any of the legacy grub left.

I'm still having problems. it doesnt appear to be loading its config file properly because it doesnt even show me a menu to work from it just goes straight to grub command line i'm going to attempt to reinstall it again.

wow I can't believe how much trouble this has caused me.
I've wasted all day fixing this why did ubuntu even change from the legacy grub in the first place?

I guess now the only thing left to do is to format the whole drive and start from scratch all over again..

---

### Post by oldfred on 2010-12-01
Grub2 does not have error numbers so the error has to be from grub legacy.

Are you sure you are not booting sdc which has grub legacy in the MBR. If you boot sda it should then work.

---

### Post by radish_ on 2010-12-01
I have very little knowlege when it comes to master boot records and honestly I thought grub was supposed to overwrite the legacy mbr when i reinstalled ubuntu. I'm better off just killing the whole drive at this point and remaking all the partitions over again.

I don't even know how to change what the mbr is pointing too

---

### Post by radish_ on 2010-12-01
apparently sda1 is a 134mb partition on my 1 tb storage drive

how do i overwrite the mbr with a grub2 mbr

---

### Post by radish_ on 2010-12-01
i'm currently in the ubuntu installer and the boot loader installation menu points to sda1 by default even though grub resides in sdc1

---

### Post by radish_ on 2010-12-01
wow that fixed it...  I set the mbr to sdc and the boot loader popped up when teh installation finished

---

