---
title: "Dual Boot Win7 &amp; Ubuntu 11.04 - Boots automatically into Win7 - NO GRUB!!!"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by ezertuchev on 2011-05-15
I just fresh-installed win7 ultimate on my generic desktop computer (Core Duo, 2gb RAM, NVidia). Afterwards, I installed Ubuntu so Grub would detect both OS's and allow me to boot from either one. However, there's no GRUB!!! When I boot up, it automatically goes to win7. I must have messed up while at the partition step, because I had just the win7 partition and while installing ubuntu, I reduced the win7 partition and allocated 20gb for ubuntu. The installation went fine, but I can't boot into ubuntu.

Sorry if this thread is repeated, I searched all over the forum and found threads from people having the opposite problem (not being able to boot into win7 for instance), or grub not working properly, but none that I found similar to my problem.

I hope someone can help.

Thanks

Eduardo Zertuche

---

### Post by drs305 on 2011-05-15
Eduardo,

Welcome to the Ubuntu forums.

Please click on the "BIS" link in my signature line. Download and run the boot info script, then post the contents of RESULTS.txt. 

When you are ready to copy the contents, click on the # icon in the post's menubar. This will generate [noparse]```
 
``` [/noparse] tags. Paste between them. It helps with formatting.

RESULTS.txt will show the status of your boot files and allow us to make informed suggestions. If you have trouble running it there are instructions on the download page, and additional instructions by *louieb* on a link on the left side of the page.

---

### Post by Mark Phelps on 2011-05-16
Not knowing what you'll be doing to restore dual-boot, you should seriously consider going into the Win7 Backup feature and using it to create and burn a Win7 Repair CD.

Should your Win7 boot loader get corrupted during the dual-boot repairs, you will need this CD to be able to get Win7 boot capability back.

---

### Post by ezertuchev on 2011-05-16
Thanks for your replies. Ive run the script and here is the results from RESULTS.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   351,656,066   351,449,219   7 HPFS/NTFS
/dev/sda3         351,657,982   390,721,535    39,063,554   5 Extended
/dev/sda5         351,657,984   386,531,327    34,873,344  83 Linux
/dev/sda6         386,533,376   390,721,535     4,188,160  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1C1E21261E20FA82                       ntfs       Reservado para el sistema     
/dev/sda2        009C32949C3283E6                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        337544a6-0091-4f99-893b-814432d9d961   ext4                                     
/dev/sda6        55592b6c-7639-43b5-86c2-dcb6b8a0bb6d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6E984BBF984B8515                       ntfs       EDUX2                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 337544a6-0091-4f99-893b-814432d9d961
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 337544a6-0091-4f99-893b-814432d9d961
set locale_dir=($root)/boot/grub/locale
set lang=es_MX
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
menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 337544a6-0091-4f99-893b-814432d9d961
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=337544a6-0091-4f99-893b-814432d9d961 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, con Linux 2.6.38-8-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 337544a6-0091-4f99-893b-814432d9d961
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=337544a6-0091-4f99-893b-814432d9d961 ro single 
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
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 337544a6-0091-4f99-893b-814432d9d961
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 337544a6-0091-4f99-893b-814432d9d961
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 1C1E21261E20FA82
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
# / was on /dev/sda5 during installation
UUID=337544a6-0091-4f99-893b-814432d9d961 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=55592b6c-7639-43b5-86c2-dcb6b8a0bb6d none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 186.7GB: boot/grub/core.img
 189.6GB: boot/grub/grub.cfg
 181.4GB: boot/initrd.img-2.6.38-8-generic
 186.7GB: boot/vmlinuz-2.6.38-8-generic
 181.4GB: initrd.img
 186.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  9e 42 94 07 f8 6f 0b 60  b2 2d 63 0d 26 3f 5d 5c  |.B...o.`.-c.&?]\|
00000010  0a 77 f4 8b 8b b2 33 b4  3c a7 ae f6 ea 54 d4 8a  |.w....3.<....T..|
00000020  5c 10 83 0b 4e 11 ad 7f  2a 61 83 03 a0 5b f5 6c  |\...N...*a...[.l|
00000030  8f d3 e0 a6 bb e2 19 65  3a a1 97 dc 17 51 3b c1  |.......e:....Q;.|
00000040  48 ed dd 0a 66 f5 f9 bc  3c f0 a7 5f 16 be c6 cf  |H...f...<.._....|
00000050  da 6c 91 77 33 bc fa 5e  f0 fb c9 d0 b7 8b 01 1b  |.l.w3..^........|
00000060  5b 55 9c 7d 8e bc 63 73  cf 3a e1 0b 58 28 3b 37  |[U.}..cs.:..X(;7|
00000070  8e 70 cf 16 b1 78 35 dd  72 86 c5 c6 d3 5b d1 a6  |.p...x5.r....[..|
00000080  9c ac 91 bc 10 4e 9a 4d  39 ef 71 6a d2 66 86 2d  |.....N.M9.qj.f.-|
00000090  e7 0e 4a 75 7c db c6 2a  b0 de 9a fb 07 8d 85 5e  |..Ju|..*.......^|
000000a0  9e b4 9c f1 91 9e 2e ab  3e 61 ca 2b 70 8f 32 f2  |........>a.+p.2.|
000000b0  6c 87 dc 08 b7 d6 18 1f  72 7b 78 43 fe 6a 26 88  |l.......r{xC.j&.|
000000c0  c6 e9 72 bf 82 f1 9f 76  ed 48 7a e1 dc 58 87 ef  |..r....v.Hz..X..|
000000d0  27 19 f3 e6 ac e0 8c 13  32 15 43 d2 41 a0 2b df  |'.......2.C.A.+.|
000000e0  75 35 ef 78 cf 9d cc 07  0a ec e4 a8 4a 1b 26 66  |u5.x........J.&f|
000000f0  a5 2c ee 8a a0 9c 84 9d  3b 79 1d d1 70 ba 78 c5  |.,......;y..p.x.|
00000100  3a e3 d6 8a dc 14 7e 34  35 c6 91 d1 85 3e f8 60  |:.....~45....>.`|
00000110  6b b3 5e 36 17 13 0c bb  c9 ff f1 69 30 14 d2 7a  |k.^6.......i0..z|
00000120  d5 7d 38 8c 23 7d 3a 99  90 67 c1 bc 16 31 5c 5f  |.}8.#}:..g...1\_|
00000130  e5 5b 07 e3 ff d0 51 17  2a 9f 2f cc e2 95 7e f4  |.[....Q.*./...~.|
00000140  b0 0b f7 21 d4 cf 14 8c  f8 8c c7 13 9f 51 67 fd  |...!.........Qg.|
00000150  ec 11 62 95 17 2e 23 9c  a8 b5 d7 08 9e 31 fa 94  |..b...#......1..|
00000160  61 ce 80 45 c3 9c 78 20  95 76 89 70 28 b6 73 a4  |a..E..x .v.p(.s.|
00000170  c7 c6 75 58 e1 b2 82 d3  cc 26 e8 d4 3b 31 f3 80  |..uX.....&..;1..|
00000180  a5 fd 4f 8e a6 0d 2e 75  b6 d3 b6 44 f1 1f 18 1b  |..O....u...D....|
00000190  1f ea 35 c3 0e 85 fd 46  c3 cd 01 47 fa 8b d9 91  |..5....F...G....|
000001a0  24 79 87 3c 29 ab 3a 85  ff 08 c4 ff 40 38 14 f5  |$y.<).:.....@8..|
000001b0  d5 e1 4f 3d fd 01 f9 6f  08 d7 0a de 68 2d 00 fe  |..O=...o....h-..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 14 02 00 fe  |........... ....|
000001d0  ff ff 05 fe ff ff 02 20  14 02 00 f0 3f 00 00 00  |....... ....?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

Ive got win7 on sda1 and sda2 (win created both partitions). Ubuntu created sda3, 5 and 6, and as far as I can tell, installed itself on sda5. I can see no boot info for ubuntu... what can I do?

Thanks again!

Eduardo Zertuche

---

### Post by ezertuchev on 2011-05-16
BTW, thanks Mark for your repair CD advice. I will do that.

---

### Post by drs305 on 2011-05-16
Grub2 needs to be installed. It will remove the Windows bootloader but you will be able to access Windows from Grub2.

From the LiveCD:
```

sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
Don't use the partition number in the second command.

Reboot and you should have your Grub menu.

---

### Post by ezertuchev on 2011-05-17
Thank you DRS305, it worked perfectly!!! It is now booting to GRUB2 and presenting me with both options, just as it is supposed to.
 
One quick question, is there any way to configure GRUB2 so win7 is first option? Where can I find documentation?
 
Thank you
 
Eduardo Zertuche

---

### Post by drs305 on 2011-05-17
> **ezertuchev said:**
> 
One quick question, is there any way to configure GRUB2 so win7 is first option? Where can I find documentation?
Eduardo Zertuche

Yes there is. But how depends on the question... ;-)

If you want to make Windows the default setting, you can either change the setting by editing the /etc/default/grub configuration file.

*Moving* the Windows entry to the top used to be a bit trickier but can be done.

The good news is that there is an app called Grub Customizer than can easily do both these things. Click on the 'Customizer' tag in my signature line to take you to a page I wrote on installing and using GC. 

If you would rather manually edit the files, click on the 'Tasks' link. (To change the default boot OS, but not the order in the menu).

When you are done with this thread, please mark it 'Solved' via the 'Thread Tools' link at the upper right of the first post.

Happy Ubuntu-ing !

---

### Post by ezertuchev on 2011-05-17
Thank you very much for all your advice, and your trouble. I will try out your solutions for the grub thing. I haven't already since I'm not at my Ubuntu computer, but it will be first priority once I'm back at my desktop.
 
Thanks!!
 
Eduardo Zertuche.

---

