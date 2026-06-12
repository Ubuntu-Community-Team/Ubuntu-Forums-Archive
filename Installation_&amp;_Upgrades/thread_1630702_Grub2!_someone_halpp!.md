---
title: "Grub2! someone halpp!"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by Deicider on 2010-11-25
This is the third time grub is giving me a hard time, i can't go on forever and reformat linux everytime in windows wipes out grub.
Ok, we know windows are the main reason grub fails but why is it so hard to restore it, its just a tiny program.

I read most guides out there, saying you can easily restore grub with a live cd in '10 seconds'.
Followed most of them, none helped.

Well, booted with a 10.10 and typed 'grub', says i dont have it.
I install it, says its grub 1.
Find the installation for grub 2, says i can't run it.
When i run grub 1, it can't find /dev/sda or smth etc or 'boot' etc etc etc.
Numerous probs.

Maybe the version of ubuntu is wrong.. dunno.
I can't format this time.
Any ideas?

---

### Post by wilee-nilee on 2010-11-25
Post the generated file by running the bootscript in my signature. Come back to the thread open a reply click on the # in the reply panel paste all the text from that generated file in between the code tags.

---

### Post by Rubi1200 on 2010-11-25
+1 to running the boot info script suggested by wilee-nilee.

The results will tell us what is where and then we can help you sort this out.

---

### Post by Deicider on 2010-11-25
Here it is.


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560    92,148,839    30,716,280  83 Linux
/dev/sda3          92,148,840   153,581,399    61,432,560   7 HPFS/NTFS
/dev/sda4         153,581,461   312,576,704   158,995,244   5 Extended
/dev/sda5         153,581,463   163,814,804    10,233,342  82 Linux swap / Solaris
/dev/sda6         163,814,868   312,576,704   148,761,837  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D6C2EBFBC2EBDE2D                       ntfs                                     
/dev/sda2        c5078794-1fe1-4383-8c74-1ed2710e9943   ext4                                     
/dev/sda3        7837DBFF4D6DF3F0                       ntfs       test/data/anything            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5ad6856a-9118-4dac-a98d-07a832e0688f   swap                                     
/dev/sda6        1feda5e9-0e73-46cc-92b2-24c0c87d422c   ext4       home                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/test_data_anything fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/c5078794-1fe1-4383-8c74-1ed2710e9943 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/D6C2EBFBC2EBDE2D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set c5078794-1fe1-4383-8c74-1ed2710e9943
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set c5078794-1fe1-4383-8c74-1ed2710e9943
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
    search --no-floppy --fs-uuid --set c5078794-1fe1-4383-8c74-1ed2710e9943
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c5078794-1fe1-4383-8c74-1ed2710e9943 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set c5078794-1fe1-4383-8c74-1ed2710e9943
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c5078794-1fe1-4383-8c74-1ed2710e9943 ro single 
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
    search --no-floppy --fs-uuid --set c5078794-1fe1-4383-8c74-1ed2710e9943
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set c5078794-1fe1-4383-8c74-1ed2710e9943
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e06cd30a6cd2da7c
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
UUID=c5078794-1fe1-4383-8c74-1ed2710e9943 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=1feda5e9-0e73-46cc-92b2-24c0c87d422c /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5ad6856a-9118-4dac-a98d-07a832e0688f none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  42.9GB: boot/grub/core.img
  34.1GB: boot/grub/grub.cfg
  34.3GB: boot/initrd.img-2.6.35-22-generic
  43.1GB: boot/vmlinuz-2.6.35-22-generic
  34.3GB: initrd.img
  43.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  71 50 32 c5 8d 2b 8b 4e  82 d6 3e e3 ca 96 3f a5  |qP2..+.N..>...?.|
00000010  62 a3 8f 0f ff a7 92 be  5a cc 8f 88 4b d5 8e bf  |b.......Z...K...|
00000020  e6 cf e4 86 aa 65 99 1e  c1 cf 08 e6 89 22 2b 6a  |.....e......."+j|
00000030  d5 00 00 09 52 1a 7d de  92 8a 2c 76 6f 83 8c cc  |....R.}...,vo...|
00000040  5e 91 97 4c 33 c4 8e 5f  02 49 55 e9 8e e1 c1 12  |^..L3.._.IU.....|
00000050  19 4d 13 95 0d 46 19 cb  5a 54 f4 66 0b 8d 1d d1  |.M...F..ZT.f....|
00000060  f8 73 26 72 b7 f9 41 e9  7c 84 f1 3d 70 7a de 40  |.s&r..A.|..=pz.@|
00000070  6a 79 a5 2c a5 f4 5f ba  d9 5a 47 18 0d a0 f9 c4  |jy.,.._..ZG.....|
00000080  96 4f 51 17 73 ed 30 30  64 63 7b 8b 00 00 00 00  |.OQ.s.00dc{.....|
00000090  01 b0 03 00 00 01 b5 09  00 00 01 00 00 00 01 20  |............... |
000000a0  00 86 87 ff ff 0a ad 89  c2 10 0a 4c 7f 00 00 01  |...........L....|
000000b0  b2 58 76 69 44 30 30 33  36 00 00 01 b6 16 b8 bc  |.XviD0036.......|
000000c0  08 8a 08 f6 fe de 65 a4  8f e1 03 11 be d6 a9 ce  |......e.........|
000000d0  d4 70 8e 64 e7 1d 67 2c  3e c6 db 79 e8 79 cd b6  |.p.d..g,>..y.y..|
000000e0  f3 d9 e6 36 db cf 67 89  df d4 54 50 f5 45 45 1d  |...6..g...TP.EE.|
000000f0  b1 6a 28 25 71 7c 82 8d  fc 36 73 bb 90 ad b6 86  |.j(%q|...6s.....|
00000100  0a 61 06 d8 c1 2f e6 37  fe a2 2d 7c 35 23 2b 4e  |.a.../.7..-|5#+N|
00000110  2d 79 3a 28 34 21 a5 2c  fb 6b a2 67 60 c1 e5 c2  |-y:(4!.,.k.g`...|
00000120  17 e3 7e ad f4 45 e7 09  38 4e aa 29 61 f3 7b 2e  |..~..E..8N.)a.{.|
00000130  d8 2b 6e 74 ba 44 38 71  5d f4 96 9c 86 d5 96 ab  |.+nt.D8q].......|
00000140  8c 65 9d b6 d1 93 93 8c  74 45 83 5a bc e7 5f ad  |.e......tE.Z.._.|
00000150  48 9f ab d9 0e 39 7b b2  3d e5 95 17 06 95 69 ab  |H....9{.=.....i.|
00000160  46 2e 97 1d c3 2b d6 4b  62 c7 dd fd d5 19 98 a2  |F....+.Kb.......|
00000170  2f 66 ee d9 33 2c 8b de  db 67 27 22 eb bf 95 5e  |/f..3,...g'"...^|
00000180  a3 15 7d 5e 13 67 eb e3  e0 6f 03 32 0c 9c 03 44  |..}^.g...o.2...D|
00000190  99 e6 95 6b 1b 35 50 e9  88 c3 3f b6 62 b6 4a a2  |...k.5P...?.b.J.|
000001a0  ea 21 be 76 84 e6 12 32  3f 4c 3c 08 01 01 35 12  |.!.v...2?L<...5.|
000001b0  c7 b5 43 63 f2 f2 f6 87  63 fb bb e1 25 2d 00 fe  |..Cc....c...%-..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 fe 25 9c 00 00 fe  |...........%....|
000001d0  ff ff 05 fe ff ff 00 26  9c 00 2c ed dd 08 00 00  |.......&..,.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by wilee-nilee on 2010-11-25
Boot a live cd of 10.10, and run these two commands.

```
sudo mount /dev/sda2 /mnt
```

then

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Then reboot to the Ubuntu install and run.

```
sudo update-grub
```

If this works which it should I can give you or another will how to do this. Reloading the MBR the small file you mentioned is quite easy you just have to have the right information and tools. 

This is the link to reloading grub2 to the mbr, it defaults to the commands here.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Deicider on 2010-11-25
> **wilee-nilee said:**
> Boot a live cd of 10.10, and run these two commands.

```
sudo mount /dev/sda2 /mnt
```

then

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Then reboot to the Ubuntu install and run.

```
sudo update-grub
```

If this works which it should I can give you or another will how to do this. Reloading the MBR the small file you mentioned is quite easy you just have to have the right information and tools. 

This is the link to reloading grub2 to the mbr, it defaults to the commands here.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
You really saved me.
Well, [[COLOR="Blue"]_thnx_[/COLOR]]("http://www.whosawesome.com/")

---

### Post by wilee-nilee on 2010-11-25
> **Deicider said:**
> You really saved you me.
Well, [[COLOR="Blue"]_thnx_[/COLOR]]("http://www.whosawesome.com/")

It is really quite simple once you know whats up. Glad it works, if you need more help there are a bunch of regular daily users that can be helpful.;)

---

