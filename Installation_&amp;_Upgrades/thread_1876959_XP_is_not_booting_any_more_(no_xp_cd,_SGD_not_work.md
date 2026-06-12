---
title: "XP is not booting any more (no xp cd, SGD not working)"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by maximovic on 2011-11-07
Hi, I'm really in trouble with my dual boot XP-Ubuntu 11.10.
I installed ubuntu after XP on the same hd. Windows was on three nfts partitions (C-D-E). Dual boot was working fine (XP was on dev/sda2). Then I tried to remove Ubuntu but I made some mess. 
At the moment this is the situation. 
Grub loader without xp, ubunt working fine.
I have used SGD. rescatux without success (probabily I have created more problems using these tools). 
I need to restore xp using Linux. No chance to use xp recovery CD. 
I think to have created problems with table partitions and mbr. 
 
fdisk -l.
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS
/dev/sda2            9730       19458    78141825    f  W95 Ext'd (LBA)
/dev/sda5            9730        9991     2104483+   7  HPFS/NTFS
/dev/sda6            9992       14751    38233205+   7  HPFS/NTFS
/dev/sda7           19222       19458     1892352   82  Linux swap / Solaris
/dev/sda8           18986       19221     1893376   82  Linux swap / Solaris
/dev/sda9           14751       18750    32116736   83  Linux
/dev/sda10          18750       18986     1893376   82  Linux swap / Solaris

```
fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda9       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=bec04d76-6981-4587-a3d4-111bf7196ed7 none            swap    sw              0       0

```
 
I'm very newbye. I have installed ms-sys but Im not sure how to use it. I yhink I have to write xp mbr, fixpartition tables and grub loader. But I don't know how to do.
Please help me step by step. At least I need to recover my data on XP.
Thanks in advance for your support.
Massimo

---

### Post by mastablasta on 2011-11-07
are oyu saying you can't see the data in Ubuntu on windows partition? You shoudl be able to see it even if windows is not in grub.
 
windows XP repair CD is available at microsoft to download (i think it's somewhere here: [http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)). you can use it to fixmrb and then you can update/restore grub using Ubuntu live CD. i don't know how to fix partition tables in Ubuntu but my guess is LiveCD and Gparted (found on liveCD) will do it.
 
if you wish you could post the results of boot info script to see what is going wrong at boot: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by BillyBoa on 2011-11-07
> **maximovic said:**
> 
I need to restore xp using Linux. No chance to use xp recovery CD. 


If you deleted Win boot sector then only with a Win CD or with windows XP repair CD mentioned above, you can solve your problem.

---

### Post by darkod on 2011-11-07
It's best to have more detailed info about your system current status. Follow the link in my signature, download and run the bootinfoscript and post the result here. If copying the text from the results.txt file please put it in code tags as explained in that link (select the text and hit the # button in the toolbat above when creating the post).

The main issue is do you have your XP boot files present. I think not. Ubuntu can't discover them, so it doesn't report XP as a present OS.

Even if they are not there, it's fixable without the XP CD. I just don't have the link right now. There were instructions how to fix that with ubuntu cd and a link where to download the xp files.

---

### Post by maximovic on 2011-11-07
Thanks for your advices.
I want to clarify that I can successfully boot Ubuntu. The problem is XP.
Results from boot info script


```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos9)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub/grub.cfg /boot.ini /ntldr /NTDETECT.COM 
                       /grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

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

/dev/sda1    *             63   156,296,384   156,296,322   7 NTFS / exFAT / HPFS
/dev/sda2         156,296,446   312,580,095   156,283,650   f W95 Extended (LBA)
/dev/sda5         156,296,448   160,505,414     4,208,967   7 NTFS / exFAT / HPFS
/dev/sda6         160,505,478   236,971,888    76,466,411   7 NTFS / exFAT / HPFS
/dev/sda7         308,795,392   312,580,095     3,784,704  82 Linux swap / Solaris
/dev/sda8         304,998,400   308,785,151     3,786,752  82 Linux swap / Solaris
/dev/sda9         236,972,032   301,205,503    64,233,472  83 Linux
/dev/sda10        301,207,552   304,994,303     3,786,752  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        88F2EB10CD0EB400                       ntfs       DISCOC
/dev/sda10       bec04d76-6981-4587-a3d4-111bf7196ed7   swap       
/dev/sda5        7C20BEEF20BEB00E                       ntfs       DiscoD
/dev/sda6        4EE0BFE4E0BFD087                       ntfs       DiscoE
/dev/sda7        2da8d2e7-5f45-4028-ba44-ec7d098a2059   swap       
/dev/sda8        3df786fa-3e94-4610-8b6b-2f24cb68b8f1   swap       
/dev/sda9        b78b956f-a5b2-4997-b9df-5500ba006c47   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /root/Desktop/windows    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda9        /                        ext4       (rw,errors=remount-ro,commit=0)


============================= sda1/grub/grub.cfg: ==============================

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
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root b78b956f-a5b2-4997-b9df-5500ba006c47
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root AA68BE7068BE3B41
set locale_dir=($root)/grub/locale
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows XP" {
set root=(hd0,0)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root AA68BE7068BE3B41
    drivemap -s (hd0) ${root}
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

================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Console di ripristino di emergenza di Microsoft Windows XP" /cmdcons 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos9)'
search --no-floppy --fs-uuid --set=root b78b956f-a5b2-4997-b9df-5500ba006c47
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos9)'
search --no-floppy --fs-uuid --set=root b78b956f-a5b2-4997-b9df-5500ba006c47
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
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root b78b956f-a5b2-4997-b9df-5500ba006c47
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b78b956f-a5b2-4997-b9df-5500ba006c47 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root b78b956f-a5b2-4997-b9df-5500ba006c47
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b78b956f-a5b2-4997-b9df-5500ba006c47 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows XP" {
set root=(sd0,0)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root b78b956f-a5b2-4997-b9df-5500ba006c47
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root b78b956f-a5b2-4997-b9df-5500ba006c47
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda9       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=bec04d76-6981-4587-a3d4-111bf7196ed7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 119.155483246 = 127.942225920  boot/grub/core.img                             1
 119.259040833 = 128.053420032  boot/grub/grub.cfg                             1
 114.251197815 = 122.676289536  boot/initrd.img-2.6.38-8-generic               2
 119.188781738 = 127.977979904  boot/vmlinuz-2.6.38-8-generic                  1
 114.251197815 = 122.676289536  initrd.img                                     2
 119.188781738 = 127.977979904  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  33 c0 8e 4e 54 46 53 20  20 20 20 00 02 08 00 00  |3..NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 09 75 13 83  81 e4 50 09 00 00 00 00  |.....u....P.....|
00000030  00 00 0c 00 00 00 00 00  48 0e 95 00 00 00 00 00  |........H.......|
00000040  f6 00 00 00 01 00 00 00  00 b4 0e cd 10 eb f2 88  |................|
00000050  00 00 00 00 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |.....s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  6d 70 72 65 73 73 6f 00  |.....,Dcmpresso.|
000001c0  0d 0a 50 72 65 6d 65 72  65 20 43 54 52 4c 2b 41  |..Premere CTRL+A|
000001d0  4c 54 2b 43 41 4e 43 20  70 65 72 20 72 69 61 76  |LT+CANC per riav|
000001e0  76 69 61 72 65 0d 0a 00  0d 0a 00 00 00 00 00 00  |viare...........|
000001f0  00 00 00 00 00 00 00 00  83 9d ae c0 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda2

00000000  33 c0 8e d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |3.....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 07 8b  |...It.8,t.......|
00000040  f0 ac 3c 00 74 fc bb 07  00 b4 0e cd 10 eb f2 88  |..<.t...........|
00000050  4e 10 e8 46 00 73 2a fe  46 10 80 7e 04 0b 74 0b  |N..F.s*.F..~..t.|
00000060  80 7e 04 0c 74 05 a0 b6  07 75 d2 80 46 02 06 83  |.~..t....u..F...|
00000070  46 08 06 83 56 0a 00 e8  21 00 73 05 a0 b6 07 eb  |F...V...!.s.....|
00000080  bc 81 3e fe 7d 55 aa 74  0b 80 7e 10 00 74 c8 a0  |..>.}U.t..~..t..|
00000090  b7 07 eb a9 8b fc 1e 57  8b f5 cb bf 05 00 8a 56  |.......W.......V|
000000a0  00 b4 08 cd 13 72 23 8a  c1 24 3f 98 8a de 8a fc  |.....r#..$?.....|
000000b0  43 f7 e3 8b d1 86 d6 b1  06 d2 ee 42 f7 e2 39 56  |C..........B..9V|
000000c0  0a 77 23 72 05 39 46 08  73 1c b8 01 02 bb 00 7c  |.w#r.9F.s......||
000000d0  8b 4e 02 8b 56 00 cd 13  73 51 4f 74 4e 32 e4 8a  |.N..V...sQOtN2..|
000000e0  56 00 cd 13 eb e4 8a 56  00 60 bb aa 55 b4 41 cd  |V......V.`..U.A.|
000000f0  13 72 36 81 fb 55 aa 75  30 f6 c1 01 74 2b 61 60  |.r6..U.u0...t+a`|
00000100  6a 00 6a 00 ff 76 0a ff  76 08 6a 00 68 00 7c 6a  |j.j..v..v.j.h.|j|
00000110  01 6a 10 b4 42 8b f4 cd  13 61 61 73 0e 4f 74 0b  |.j..B....aas.Ot.|
00000120  32 e4 8a 56 00 cd 13 eb  d6 61 f9 c3 49 6e 76 61  |2..V.....a..Inva|
00000130  6c 69 64 20 70 61 72 74  69 74 69 6f 6e 20 74 61  |lid partition ta|
00000140  62 6c 65 00 45 72 72 6f  72 20 6c 6f 61 64 69 6e  |ble.Error loadin|
00000150  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
00000160  65 6d 00 4d 69 73 73 69  6e 67 20 6f 70 65 72 61  |em.Missing opera|
00000170  74 69 6e 67 20 73 79 73  74 65 6d 00 00 00 00 00  |ting system.....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 2c 44 63  00 00 00 00 00 00 00 01  |.....,Dc........|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 47 39 40 00 00 fe  |..........G9@...|
000001d0  ff ff 05 fe ff ff 49 39  40 00 2a c9 8e 04 00 00  |......I9@.*.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
```I need to boot xp again. Please could you help me? I cannot use a XP cd.
I have a tools called ms-sys that can write MBR but I cannot how to use it.
Thanks again for your support.
Massimo

---

### Post by darkod on 2011-11-07
OK. Test 1:
1. Boot your ubuntu as normal.
2. Open /dev/sda1 partition. There should be a folder called grub there according to your results.
3. Move that folder from there, to your ubuntu Home folder for example.
4. Open terminal and run:
sudo update-grub

If you see that it reported XP as found, that's good. Reboot and try to boot both XP and ubuntu.

Let us know if it worked.

---

### Post by maximovic on 2011-11-07
Thank you for your answer. These the results of test1.

Not sure when you say open /dev/sda1. I have mounted /dev/sda1 on a desktop folder, found grub folder and renamed it. (hope it was the right procedure!)
```
update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
**Found Microsoft Windows XP Professional on /dev/sda1**
done

```At reboot I found in grub list the voice Microsoft Windows XP Professional on /dev/sda1. I have selected it but then only dark screen without any message and no xp reboot. 

I think we have to go for test2...
Thanks again for your support.
Massimo

---

### Post by darkod on 2011-11-07
OK, you are one step closer. Do you feel confident to do the following procedure to repair the boot sector of the partition? I think SGD messed it up. Ubuntu saw the XP boot files and reported it, but it doesn't boot, which is windows fault not ubuntu. The following is a copy of another thread, and be very careful to follow the instructions exactly when using testdisk, it's a very powerful tool.

**Step 5:  Rebuild the Boot sector of the Windows partition.**

Install and run "testdisk:

Code:
```

sudo apt-get install testdisk
sudo testdisk  /dev/sda

```


Press "enter" to "proceed"
Press "enter" to select "intel"
Use the "down arrow" and "enter" to select "advanced"
Use the down arrrow to select the "XP" partition and then "enter" to select "boot"
Use the "right arrow" key and "enter" to select "Rebuild BS"
This might take a while. Once done:
Use the "right arrow" key and "enter" to select "write". This will write a modified boot sector to the Windows partition.
Press q a few times to quit testdisk.

Reboot.

---

### Post by maximovic on 2011-11-07
Darkod thank you again for your efforts.

Before rebuild BS
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  9728 254 63  156296322 [DISCOC]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

[  Quit  ]  [  List  ]  [**Rebuild BS**]  [Repair MFT]  [  Dump  ]
                              Rebuild boot sector

```After Rebuild BS (it took less than 1 second and no "write" selection available
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  9728 254 63  156296322 [DISCOC]

filesystem size           156296322
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               9768520
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

[  Dump  ]  [  List  ]  [  Quit  ]

```Anyway I rebooted but nothing has changed.
Massimo

---

### Post by darkod on 2011-11-07
OK, the sectors were identical, nothing was changed so no write option. The last step is replacing the XP boot files with new ones in case they are corrupted. If that doesn't help, it doesn't look good. :)

First from ubuntu open again /dev/sda1 and change the names of your current boot files (don't delete them just in case). It's enough to add .original for example, it will be considered like a new extension and the files will be ignored by windows. The boot files are:
boot.ini
NTLDR
NTDETECT.COM

After you have renamed them, open this post and at the bottom there is a compressed archive with a new set of boot files. Download it, right-click on it and open with archive manager. Extract them where ever you want, in your Home for example. After they are extracted, they should be named the same as the three files you renamed. Copy them to /dev/sda1. Reboot and keep your fingers crossed.
[http://ubuntuforums.org/showpost.php?p=5082723&postcount=1](http://ubuntuforums.org/showpost.php?p=5082723&postcount=1)

---

### Post by maximovic on 2011-11-07
done, Darkod.
But no good news. XP doesn't reboot. Dark screen.
In boot.ini I didn't changed anything.  I left partition 1 because XP is on /dev/sda1

I have run again update-grab, but no results. Again testdisk.
I tried with grub-install and I got this error.

```
grub-install /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

```No chance to recover my XP :(

Thanks for your support

---

### Post by maximovic on 2011-11-07
When I run gparted, dev/sda1 info gives some warnings.

A series of clusters (from 3250493 to 3250502) referenced multiple times (error 70). So file system check failed and suggests to run chkdsk from windows.

Can be this information useful?

Thanks

---

### Post by darkod on 2011-11-07
Sorry to hear that. I don't know if this is a result of SGD, or something... But it seems the XP is broken.

You can always access all your data from ubuntu. You can even reinstall XP later if you choose to.

---

### Post by darkod on 2011-11-07
> **maximovic said:**
> When I run gparted, dev/sda1 info gives some warnings.

A series of clusters (from 3250493 to 3250502) referenced multiple times (error 70). So file system check failed and suggests to run chkdsk from windows.

Can be this information useful?

Thanks

Yes, chkdsk might help but without XP CD to boot from into recovery console, I have no idea how to do a chkdsk. There was a similar tool in ubuntu, but don't remember it right now, and not sure it can help.

---

### Post by grizzly54 on 2011-11-07
There are other options for restoring the MBR other than having the original XP CD !
Didn't mention what other Windows you may have had in the past, so not sure what 
other means to restore XP you may have. Do you have a Windows '98 startup Disk?
Also not sure if you have the XP installation CD? Still more options, don't give up the
ship:)

---

### Post by darkod on 2011-11-07
This is not about restoring the MBR. Grub is very good at booting XP as long as the XP installation is good. In this case it seems it's not.
Could be related to the errors reported on the XP partition.

---

### Post by maximovic on 2011-11-08
I'd like to provide you more information in order to try to solve my xp reboot.
Normal XP CD doesn't work and I cannot open recovery console probabily because my business laptop mounts a customised version of XP. 
 
I have the original DVD used for the installation of this customised xp version and unfortunately it doesn'have any recovery tools.
 
This DVD has a .wim of C unity that will be copied for the installation of this XP version.  I have tried to open the .wim image of C unity and I have copied all the files necessary for booting according to [http://technet.microsoft.com/en-us/library/bb457123.aspx](http://technet.microsoft.com/en-us/library/bb457123.aspx) table 29.1.
 
I have rebooted Ubuntu, mounted C unity and added all the files extracted from .wim image. 
I have restarted the system but XP still doesn't reboot!
 
What else can I do? Which kind of permission should have these files?
Thanks for your support
Massimo

---

### Post by oldfred on 2011-11-09
I do not think the issue is the files, but the boot sector and/or file structure. You need to run fixboot & chkdsk. Only Windows can run chkdsk.

XP repair disk
[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)
[http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip](http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip)

I have run chkdsk from a Windows 7 repairCD on my XP partition. It actually found more issues than the XP chkdsk. But it wrote a windows 7 boot sector, that still worked for some reason. I was able to write a XP boot sector from the Windows 7 repairCD.

We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.

Another download site Despotism Believed to be ok.
[http://ubuntuforums.org/showpost.php?p=11249721&postcount=439](http://ubuntuforums.org/showpost.php?p=11249721&postcount=439)
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links (Now $10.00):
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

