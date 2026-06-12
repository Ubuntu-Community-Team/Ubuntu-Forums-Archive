---
title: "Destroyed Windows bootloader!"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Maelgwyn on 2010-05-01
Hi all,

I'm apparently exceedingly intelligent as I've just installed Lucid Lynx over the Windows bootloader!

Now I'm not able to view Windows at all - If I have the Windows 7 disc in the drive when I boot, it asks me to install Windows from scratch.

I've tried using FixNTLDR and that tells me that
> <Windows root>\system32\hal.dll is missing and to reinstall.

Am I buggered? Or is there a way for me to get Windows 7 back without having to reinstall?

---

### Post by Maelgwyn on 2010-05-01
Bizarrely enough, hal.dll DOES exist - I've just found it in the Windows partition... 

So I'm completely stumped now >.<

---

### Post by oldfred on 2010-05-01
I saved these notes from others with hal issues:
Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
Error message: "Windows could not start because of a computer disk hardware configuration problem"
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

Did you install grub to the PBR of the windows partition, I have seen many do this and cause windows boot issues.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by pauljwells on 2010-05-01
I had this and it's fixable!
You need to download and burn to CD the Supergrub disk
boot from that and follow through the menus to Windows, boot first partition (or second if you have a recovery partition)
Then you need to download mbrfix from [http://www.sysint.no/products/Download/tabid/536/language/en-US/Default.aspx]("http://www.sysint.no/products/Download/tabid/536/language/en-US/Default.aspx")
put it on a stick and run it in a dos shell
mbrfix /drive 0 fixmbr (I think - there is a simple help guide)
This writes a clean windows bootcode back to the MBR

shut down, remove CD and reboot - you should be back in windows

---

### Post by Maelgwyn on 2010-05-01
Well I've tried booting into the Recovery to use Bootrec.exe.

When I run /RebuildBcd I get the following
> 
Total identified Windows installations: 2
[1] C:\Windows
Add installation to boot list? Yes(Y)/No(N)/All(A): y
[2] C:\Windows.old\Windows
Add installation to boot list? Yes(Y)/No(N)/All(A): y
Element not found


If I run /FixMbr I get
> 
The operation completed successfully


If I try to run /FixBoot I get the Element not found response (same as I got for /RebuildBcd)


I *really* don't want to have to reinstall Windows! There's too much to lose on that partition =/

---

### Post by oldfred on 2010-05-01
run this so we can see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

It may be this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Maelgwyn on 2010-05-01
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   625,139,711   625,137,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    74,864,639    74,862,592  83 Linux
/dev/sdb2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sdb5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________
Note: sector size is 4096 (not 512)

Disk /dev/sdh: 7971 MB, 7971016704 bytes
35 heads, 41 sectors/track, 1356 cylinders, total 1946049 sectors
Units = sectors of 1 * 4096 = 4096 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdh1                  63     1,946,047     1,945,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C0500C80500C8000                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5a339f1e-1287-47e6-b11d-f38e66b68e30   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a23c25d4-ee61-4e36-bbe2-d014aed629ff   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        C8C4BE76C4BE667A                       ntfs       My Book                       
/dev/sdc: PTTYPE="dos" 
/dev/sdh1        3141-5926                              vfat       KYTHERA                       
/dev/sdh         A88B-3652                              vfat       iPod                          
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdh1        /media/KYTHERA           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/C0500C80500C8000  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5a339f1e-1287-47e6-b11d-f38e66b68e30
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1600x1200
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5a339f1e-1287-47e6-b11d-f38e66b68e30
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5a339f1e-1287-47e6-b11d-f38e66b68e30
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a339f1e-1287-47e6-b11d-f38e66b68e30 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5a339f1e-1287-47e6-b11d-f38e66b68e30
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a339f1e-1287-47e6-b11d-f38e66b68e30 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5a339f1e-1287-47e6-b11d-f38e66b68e30
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5a339f1e-1287-47e6-b11d-f38e66b68e30
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a23c25d4-ee61-4e36-bbe2-d014aed629ff none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   9.1GB: boot/grub/core.img
  19.5GB: boot/grub/grub.cfg
   9.7GB: boot/initrd.img-2.6.32-21-generic
   9.6GB: boot/vmlinuz-2.6.32-21-generic
   9.7GB: initrd.img
   9.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdh

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 10 04 00 02  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  c0 b1 1d 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 52 36 8b a8 69  50 6f 64 00 4d 45 20 20  |..)R6..iPod.ME  |
00000050  20 20 46 41 54 33 32 20  20 20 00 c9 8e d1 bc f4  |  FAT32   ......|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 41 70  |..............Ap|
000001b0  70 6c 65 20 69 50 6f 64  20 20 20 20 20 20 00 01  |ple iPod      ..|
000001c0  01 00 0b 22 29 79 3f 00  00 00 81 b1 1d 00 00 00  |...")y?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  ae 81 b7 d7 92 23 26 5f  2e 79 cc c6 3a 62 3d cf  |.....#&_.y..:b=.|
00000010  50 c6 3c c5 be a0 05 16  9e b3 3b ee cc 7e db d6  |P.<.......;..~..|
00000020  70 90 2e 66 2a fd 67 58  ae ea bd dd 2b 85 b1 6e  |p..f*.gX....+..n|
00000030  ce 75 2e 01 7e 9d b3 70  08 35 21 50 5c 82 de e4  |.u..~..p.5!P\...|
00000040  1a ed c7 d7 3a 18 95 cd  6b b8 e3 1f 6b 8f e4 52  |....:...k...k..R|
00000050  9e 9f 5d ba bd 08 80 e9  d8 b6 75 98 ff 47 7a c4  |..].......u..Gz.|
00000060  4b 4f 3d 0f 0c 68 22 36  13 3e 4e 23 b8 74 31 11  |KO=..h"6.>N#.t1.|
00000070  76 3d c0 63 ae aa 8d 1e  ad c6 48 8f 2e a0 d8 c4  |v=.c......H.....|
00000080  bc 7f 94 a6 ab b2 f3 96  b4 44 93 ad 8f 25 9c 3e  |.........D...%.>|
00000090  2b 4a ea 23 65 8c 1d 99  a6 7c c2 95 4d fd e1 e9  |+J.#e....|..M...|
000000a0  09 fc 76 f6 6c 18 07 6d  e1 40 b5 ca 29 2d 6b 72  |..v.l..m.@..)-kr|
000000b0  73 39 94 47 ac e7 ca 40  39 37 f8 91 f9 fb 27 44  |s9.G...@97....'D|
000000c0  5b f5 58 60 0f c4 91 0b  fc 88 ae b2 8b f9 c0 79  |[.X`...........y|
000000d0  fb c4 37 50 ca e3 0b a1  4f 34 82 f3 14 1a 52 02  |..7P....O4....R.|
000000e0  64 36 1a 7d 7d 1c 58 7e  db 1d 54 56 7c 25 25 e8  |d6.}}.X~..TV|%%.|
000000f0  fb d9 18 a1 e6 c9 87 5d  a7 eb 2b b3 34 e6 eb de  |.......]..+.4...|
00000100  ad 85 c7 4c 2f 33 48 0e  b0 49 52 72 5b 6a 6b 51  |...L/3H..IRr[jkQ|
00000110  c0 26 72 1e 53 46 dc b2  66 bf 8c 4d b0 bc 3c 22  |.&r.SF..f..M..<"|
00000120  cb 63 1d 15 f9 c3 5c d1  94 75 22 37 6f 14 52 ca  |.c....\..u"7o.R.|
00000130  1c 65 85 f5 19 10 78 79  eb 18 60 a0 fc b1 f8 7a  |.e....xy..`....z|
00000140  f2 29 f5 43 01 21 4a 98  a5 bc 25 19 c5 9c c9 7c  |.).C.!J...%....||
00000150  23 7e 72 a6 af b0 7d c6  30 ae 2d 2d be e2 32 ae  |#~r...}.0.--..2.|
00000160  6f ce d9 9d 31 5e 45 aa  1f 85 32 aa 53 c0 ef 0e  |o...1^E...2.S...|
00000170  1e aa 53 9b a0 50 5e bf  0e dc 57 36 03 13 50 ae  |..S..P^...W6..P.|
00000180  a5 96 7d 41 20 48 27 1b  c2 01 c7 83 c6 d5 e2 44  |..}A H'........D|
00000190  2c e2 92 a2 0d 01 f6 07  f5 00 a6 2b 19 31 6c 0d  |,..........+.1l.|
000001a0  43 93 e6 0e 82 a2 0f cc  0b 99 8c 54 27 32 41 ab  |C..........T'2A.|
000001b0  85 c0 33 47 39 c1 c5 36  6c 70 08 06 ce b3 00 fe  |..3G9..6lp......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdh1

00000000  eb 3c 90 2a 55 4f 4b 4a  49 48 43 00 10 04 20 00  |.<.*UOKJIHC... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  7e b1 1d 00 db 01 00 00  00 00 00 00 02 00 00 00  |~...............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 26 59 41 31 49  50 4f 44 20 20 20 20 20  |..)&YA1IPOD     |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 5b 7c ac  |  FAT32   ...[|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 7b  7b 7e 7e 7c 20 53 20 54  |.......{{~~| S T|
00000080  20 4f 20 50 20 7c 20 54  68 69 73 20 69 73 20 41  | O P | This is A|
00000090  70 70 6c 65 20 69 50 6f  64 20 6e 6f 74 20 61 20  |pple iPod not a |
000000a0  62 6f 6f 74 61 62 6c 65  20 64 69 73 6b 2e 50 6c  |bootable disk.Pl|
000000b0  65 61 73 65 20 74 72 79  20 61 67 61 69 6e 20 2e  |ease try again .|
000000c0  2e 2e 20 00 00 00 00 00  00 00 00 00 00 00 00 00  |.. .............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

For what it's worth, I have:
 * 1Tb drive for storage
 * 320Gb drive (Windows 7)
 * 30Gb drive (Ubuntu)

---

### Post by kooia on 2010-05-02
Try this:
```
sudo apt-get install testdisk
sudo testdisk
```

---

### Post by oldfred on 2010-05-02
Are you able to boot Ubuntu? The script shows grub in sda and boot is in same drive sda1, but your install is in sdb1. My  system has grub 1.98 in sda and the script says I boot from 7th partition, except my install is sdc7 and it works. So I think their is a problem with the script and the newest grub 1.98.

I would reinstall windows boot loader to sda, repair windows,  and reinstall grub to sdb. Then set BIOS to boot from sdb which should then find the working windows with a sudo update-grub and then let you boot both.

Your windows partition only has
/Windows/System32/winload.exe
It should also have 
/bootmgr /Boot/BCD 

If you can boot into Ubuntu you can reinstall grub to sdb from there, otherwise you have to use a liveCD.
reinstall from working system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub

To repair windows:
Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

Windows should boot from sda after repairs. If you have reinstalled grub to sdb, select sdb to boot in BIOS and run a sudo update-grub to find the windows and add it to your grub menu (grub.cfg).

If you cannot boot sdb (be sure to use sdb):
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Maelgwyn on 2010-05-02
Thanks for all the help oldfred!

I've actually just gone ahead and re-installed Windows 7. I'd been playing around with Bootrec to no avail.

Now I can at least get into Windows (although I have to have the disc in the drive!).

---

