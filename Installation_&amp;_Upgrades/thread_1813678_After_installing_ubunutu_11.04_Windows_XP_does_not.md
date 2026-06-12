---
title: "After installing ubunutu 11.04 Windows XP does not start"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by peppino1 on 2011-07-28
Hello,
yesterday I installed ubuntu 11.04 on my laptop. Installation was ok, no errors. I can run Ubuntu with no problem. Grub detects Windows XP, but when I chose it to boot I have a black screen with two symbols on the left-upper part of the screen so Windows XP does not boot.
All windows system files are there, I can mount its partition with no problems.

I tried "sudo update-grub" but no changes

Any idea for a simple fix?
thanks

---

### Post by YesWeCan on 2011-07-28
Would you run this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post RESULTS.txt here inside code tags?

---

### Post by peppino1 on 2011-07-29
> **YesWeCan said:**
> Would you run this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post RESULTS.txt here inside code tags?
Thanks for your answer. I could not ran it yesterday, but here there are the results. What do you think?

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   195,462,854   195,462,792   7 NTFS / exFAT / HPFS
/dev/sda2         195,462,855   359,768,757   164,305,903   7 NTFS / exFAT / HPFS
/dev/sda3         359,770,110   488,396,799   128,626,690   5 Extended
/dev/sda5         359,770,112   480,434,175   120,664,064  83 Linux
/dev/sda6         480,436,224   488,396,799     7,960,576  82 Linux swap / Solaris

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8166 MB, 8166309888 bytes
212 heads, 51 sectors/track, 1475 cylinders, total 15949824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               8,192    15,949,823    15,941,632   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01CB60876023C700                       ntfs       Unidad de Sistema
/dev/sda2        01CB60876023C700                       ntfs       Unidad de Datos
/dev/sda5        f435d386-3fea-4e79-933a-04a8eee55bda   ext4       
/dev/sda6        82113a96-95f7-4bdc-bc19-14ef6323026e   swap       
/dev/sdb1        D612-6350                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/Unidad de Datos   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/D612-6350         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f435d386-3fea-4e79-933a-04a8eee55bda
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f435d386-3fea-4e79-933a-04a8eee55bda
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=25
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos5)'
        search --no-floppy --fs-uuid --set=root f435d386-3fea-4e79-933a-04a8eee55bda
        linux   /boot/vmlinuz-2.6.38-10-generic root=UUID=f435d386-3fea-4e79-933a-04a8eee55bda ro   quiet splash vt.handoff=7
        initrd  /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos5)'
        search --no-floppy --fs-uuid --set=root f435d386-3fea-4e79-933a-04a8eee55bda
        echo    'Loading Linux 2.6.38-10-generic ...'
        linux   /boot/vmlinuz-2.6.38-10-generic root=UUID=f435d386-3fea-4e79-933a-04a8eee55bda ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos5)'
        search --no-floppy --fs-uuid --set=root f435d386-3fea-4e79-933a-04a8eee55bda
linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=f435d386-3fea-4e79-933a-04a8eee55bda ro   quiet splash vt.handoff=7
        initrd  /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos5)'
        search --no-floppy --fs-uuid --set=root f435d386-3fea-4e79-933a-04a8eee55bda
        echo    'Loading Linux 2.6.38-8-generic ...'
        linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=f435d386-3fea-4e79-933a-04a8eee55bda ro single 
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos5)'
        search --no-floppy --fs-uuid --set=root f435d386-3fea-4e79-933a-04a8eee55bda
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
set root='(/dev/sda,msdos5)'
        search --no-floppy --fs-uuid --set=root f435d386-3fea-4e79-933a-04a8eee55bda
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(/dev/sda,msdos1)'
        search --no-floppy --fs-uuid --set=root 01CB60876023C700
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Mocosoft Windows XP" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(/dev/sda1,msdos1)'
        search --no-floppy --fs-uuid --set=root 01CB60876023C700
        drivemap -s (hd0) ${root}
        chainloader +1
}

### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f435d386-3fea-4e79-933a-04a8eee55bda /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=82113a96-95f7-4bdc-bc19-14ef6323026e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 207.725978851 = 223.044071424  boot/grub/core.img                             1
 213.702735901 = 229.461565440  boot/grub/grub.cfg                             1
 172.805919647 = 185.548943360  boot/initrd.img-2.6.38-10-generic              2
 211.848632812 = 227.470737408  boot/initrd.img-2.6.38-8-generic               2
 172.126285553 = 184.819191808  boot/vmlinuz-2.6.38-10-generic                 1
 207.784671783 = 223.107092480  boot/vmlinuz-2.6.38-8-generic                  1
 172.805919647 = 185.548943360  initrd.img                                     2
211.848632812 = 227.470737408  initrd.img.old                                 2
 172.126285553 = 184.819191808  vmlinuz                                        1
 207.784671783 = 223.107092480  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 c7 86 a6 0b  |........?.......|
00000020  00 00 00 00 80 00 80 00  e0 1b cb 09 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  10 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  00 c7 23 60 87 60 cb 01  |..........#`.`..|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 e8 16  |.3.....|........|
00000060  00 b8 00 0d 8e c0 33 db  c6 06 0e 00 10 e8 53 00  |......3.......S.|
00000070  68 00 0d 68 6a 02 cb 8a  16 24 00 b4 08 cd 13 73  |h..hj....$.....s|
00000080  05 b9 ff ff 8a f1 66 0f  b6 c6 40 66 0f b6 d1 80  |......f...@f....|
00000090  e2 3f f7 e2 86 cd c0 ed  06 41 66 0f b7 c9 66 f7  |.?.......Af...f.|
000000a0  e1 66 a3 20 00 c3 b4 41  bb aa 55 8a 16 24 00 cd  |.f. ...A..U..$..|
000000b0  13 72 0f 81 fb 55 aa 75  09 f6 c1 01 74 04 fe 06  |.r...U.u....t...|
000000c0  14 00 c3 66 60 1e 06 66  a1 10 00 66 03 06 1c 00  |...f`..f...f....|
000000d0  66 3b 06 20 00 0f 82 3a  00 1e 66 6a 00 66 50 06  |f;. ...:..fj.fP.|
000000e0  53 66 68 10 00 01 00 80  3e 14 00 00 0f 85 0c 00  |Sfh.....>.......|
000000f0  e8 b3 ff 80 3e 14 00 00  0f 84 61 00 b4 42 8a 16  |....>.....a..B..|
00000100  24 00 16 1f 8b f4 cd 13  66 58 5b 07 66 58 66 58  |$.......fX[.fXfX|
00000110  1f eb 2d 66 33 d2 66 0f  b7 0e 18 00 66 f7 f1 fe  |..-f3.f.....f...|
00000120  c2 8a ca 66 8b d0 66 c1  ea 10 f7 36 1a 00 86 d6  |...f..f....6....|
00000130  8a 16 24 00 8a e8 c0 e4  06 0a cc b8 01 02 cd 13  |..$.............|
00000140  0f 82 19 00 8c c0 05 20  00 8e c0 66 ff 06 10 00  |....... ...f....|
00000150  ff 0e 0e 00 0f 85 6f ff  07 1f 66 61 c3 a0 f8 01  |......o...fa....|
00000160  e8 09 00 a0 fb 01 e8 03  00 fb eb fe b4 01 8b f0  |................|
00000170  ac 3c 00 74 09 b4 0e bb  07 00 cd 10 eb f2 c3 0d  |.<.t............|
00000180  0a 41 20 64 69 73 6b 20  72 65 61 64 20 65 72 72  |.A disk read err|
00000190  6f 72 20 6f 63 63 75 72  72 65 64 00 0d 0a 4e 54  |or occurred...NT|
000001a0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 00 0d  |LDR is missing..|
000001b0  0a 4e 54 4c 44 52 20 69  73 20 63 6f 6d 70 72 65  |.NTLDR is compre|
000001c0  73 73 65 64 00 0d 0a 50  72 65 73 73 20 43 74 72  |ssed...Press Ctr|
000001d0  6c 2b 41 6c 74 2b 44 65  6c 20 74 6f 20 72 65 73  |l+Alt+Del to res|
000001e0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 00 00  |tart............|
000001f0  00 00 00 00 83 a0 b3 c9  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by YesWeCan on 2011-07-29
Hi. If you edit your post and put [c0de] at the beginning of the text and [/c0de] (use letter o instead of 0) at the end, it will make it easier to read and also adds scroll bars so the post itself is not so long. You can also highlight an area of text and click the # symbol to automatically put the code tags around it.

I cannot see anything obviously wrong. So I don't know.

I would search this forum for similar problems. I'd try booting an XP CD and repairing its bootloader. XP should then boot but Ubuntu won't. Then use my Ubuntu live CD to reinstall Grub:
```
[COLOR="Navy"]sudo mount /dev/sda5 /mnt
sudo grub-install --root-partition=/mnt /dev/sda[/COLOR]
```

---

### Post by oldfred on 2011-07-29
I also do not see anything wrong. XP files and boot.ini all look ok.

The NTFS partition boot sector does have to have the correct start & end of the XP partition inside it as the partition table. Sometime a fixBoot will update that after a resize. (It should have been updated anyway).

Sometimes the partition just needs a chkdsk and then it works. And some have just reinstalled the boot files and it has worked. Not sure in many cases which update may have actually solved the problem

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

