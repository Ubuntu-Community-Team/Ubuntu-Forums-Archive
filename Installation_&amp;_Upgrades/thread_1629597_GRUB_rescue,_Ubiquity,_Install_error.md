---
title: "GRUB rescue, Ubiquity, Install error"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by M. Amin on 2010-11-23
Hi,

I recently convinced my uncle to use Ubuntu, and then I screwed up his laptop!

Toshiba A300 PSAJ4E, it came with Vista installed on it

I have attempted to install Ubuntu 10.04, and 10.10 on an external hard drive, installed, restarted, I get the error
error: no such partition
grub rescue>

I tried installing again and again and again about a million times and most of them crashes and tells me it's something called Ubiquity that can't be installed..

Now I can't even log to either Ubuntu or Vista, and I don't even know how to recover it!  I only get two buttons F2 for Setup and F12 for Boot Selection Menu.. and that's all.

Any help.. please?!

---

### Post by oldfred on 2010-11-24
Are you using liveCD or USB flash drive to install? If so use f12 to boot the liveCD and do not do install but run it as the liveCD. Leave external plugged in so we see it also.

Download and run this script which will tell us what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by M. Amin on 2010-11-24
Ok I was running first on a LiveCD but I tried one more time with a USB flash drive, the install went smoothly without any errors, yet I still get the grub rescue> error.

My results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   246,786,047   243,712,000   7 HPFS/NTFS
/dev/sda3         246,786,048   488,394,751   241,608,704   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    37,158,344    37,158,282  83 Linux
/dev/sdb2          41,254,981    78,124,094    36,869,114   f W95 Ext d (LBA)
/dev/sdb5          41,254,983    78,124,094    36,869,112   b W95 FAT32
/dev/sdb3          37,158,345    41,254,919     4,096,575  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             80    15,663,103    15,663,024   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B6C8A839C8A7F5B1                       ntfs       WinRE                         
/dev/sda2        9C48ADD148ADAA8A                       ntfs       Vista                         
/dev/sda3        3AB2ACADB2AC6ED7                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c2b7752f-9974-45e9-9e1e-8a84a6535819   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        e1aad2f5-807e-4f8b-83dd-95755b8a2e82   swap                                     
/dev/sdb5        ACC7-8FF8                              vfat       NEW VOLUME                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0E3A-C3CE                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/NEW VOLUME        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /media/c2b7752f-9974-45e9-9e1e-8a84a6535819 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c2b7752f-9974-45e9-9e1e-8a84a6535819
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set c2b7752f-9974-45e9-9e1e-8a84a6535819
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c2b7752f-9974-45e9-9e1e-8a84a6535819
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c2b7752f-9974-45e9-9e1e-8a84a6535819 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c2b7752f-9974-45e9-9e1e-8a84a6535819
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c2b7752f-9974-45e9-9e1e-8a84a6535819 ro single 
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
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c2b7752f-9974-45e9-9e1e-8a84a6535819
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c2b7752f-9974-45e9-9e1e-8a84a6535819
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 9c48add148adaa8a
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=c2b7752f-9974-45e9-9e1e-8a84a6535819 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=e1aad2f5-807e-4f8b-83dd-95755b8a2e82 none            swap    sw              0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  13.1GB: boot/grub/core.img
  11.0GB: boot/grub/grub.cfg
  13.1GB: boot/initrd.img-2.6.35-22-generic
  13.1GB: boot/vmlinuz-2.6.35-22-generic
  13.1GB: initrd.img
  13.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  44 76 67 f3 3a f6 72 97  55 c2 c5 6a ab a7 33 64  |Dvg.:.r.U..j..3d|
00000010  3e cc ee a5 1b 10 c1 1e  04 ae f2 c8 50 5e 40 a6  |>...........P^@.|
00000020  b7 6e b1 a9 50 8c 6b 02  1d e2 6a 7e 2a 86 77 27  |.n..P.k...j~*.w'|
00000030  73 5e d8 14 dd 5a 6a 2c  91 91 31 7c 6c 06 38 fd  |s^...Zj,..1|l.8.|
00000040  73 8c 5d b2 ce 73 c1 a8  3d 85 52 d8 fd b2 28 2a  |s.]..s..=.R...(*|
00000050  e2 2c 28 c6 01 db 60 8b  5e ca c9 96 e9 d8 82 bc  |.,(...`.^.......|
00000060  9c 23 60 30 95 9d 5d bc  c7 5b b3 89 29 43 1c 90  |.#`0..]..[..)C..|
00000070  c0 63 c8 d5 7c d1 bb 48  72 56 ca e3 a5 1c 26 c5  |.c..|..HrV....&.|
00000080  23 01 9a df c9 40 6b 2a  9a ac 5b a9 a2 41 6c 4c  |#....@k*..[..AlL|
00000090  db 00 c7 47 49 13 67 63  f8 3b 31 ad e1 b4 16 3b  |...GI.gc.;1....;|
000000a0  eb 51 49 f4 40 29 b1 e4  bd 3e 59 06 64 82 1f 78  |.QI.@)...>Y.d..x|
000000b0  60 ed 23 f2 70 a0 55 c3  d1 89 cc b6 56 88 6d f3  |`.#.p.U.....V.m.|
000000c0  16 d8 45 58 14 68 6b 04  3f 17 a9 cb 93 03 28 e0  |..EX.hk.?.....(.|
000000d0  2e 3a c5 0d 00 7c bd 7a  03 21 c6 22 3a e2 13 08  |.:...|.z.!.":...|
000000e0  97 d4 a7 1c 4a fa 56 74  1e 61 53 db 21 03 84 95  |....J.Vt.aS.!...|
000000f0  67 c6 da 80 d9 d4 6a a0  82 09 1c e5 5c 69 18 80  |g.....j.....\i..|
00000100  6a 1d 58 3d ba e6 c3 27  44 ff 4a 56 ef 3d 1d b0  |j.X=...'D.JV.=..|
00000110  e5 b5 25 41 02 6c 6e 03  67 50 d5 16 e6 5c 7a 4e  |..%A.ln.gP...\zN|
00000120  b4 af 4d a4 99 3a 64 53  bf f6 a6 15 20 e6 20 1b  |..M..:dS.... . .|
00000130  be fb e6 67 8b 4a c5 cf  7f d7 e5 85 bb af 3f 52  |...g.J........?R|
00000140  2d ae bb 7d d1 d8 81 c6  aa 39 6f 30 a7 cc 87 e5  |-..}.....9o0....|
00000150  fa 93 f4 dd 70 9b 75 01  13 de 47 40 fb 42 3e cc  |....p.u...G@.B>.|
00000160  0d f0 6f 8d 57 c6 dd 8e  d1 c7 7a ae 9d 1b 3f 0b  |..o.W.....z...?.|
00000170  71 85 4b 97 9b 3f 8e 67  04 1e 02 61 7e 37 8f 93  |q.K..?.g...a~7..|
00000180  3c 8e 79 12 41 13 81 aa  62 c0 c6 82 d0 b4 56 79  |<.y.A...b.....Vy|
00000190  56 df f2 c9 39 3c f1 2c  3b cd 0b ee 5e 83 56 bf  |V...9<.,;...^.V.|
000001a0  cb 8f d6 c8 7c bd 96 1e  58 19 91 a9 50 b9 ae 58  |....|...X...P..X|
000001b0  95 84 15 42 0e 86 a3 69  c8 b9 5d be a0 3d 00 01  |...B...i..]..=..|
000001c0  c1 ff 0b fe ff ff 02 00  00 00 f8 93 32 02 00 00  |............2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 c0 08  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 50 00 00 00  |........?...P...|
00000020  b0 ff ee 00 a0 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ce c3 3a 0e 4e  4f 20 4e 41 4d 45 20 20  |..)..:.NO NAME  |
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
00000100  7d 00 66 b8 e0 27 16 00  66 ba 00 00 00 00 bb 00  |}.f..'..f.......|
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


```

---

### Post by wilee-nilee on 2010-11-24
First lets just try putting the sdb drive first in the bios to be read=the external. You have grub in sda we can fix that.

There is a per-session boot from menu that is a key prompt immediately at powering on mine is f12 yours may be the same or different.

---

### Post by M. Amin on 2010-11-24
the external hard drive doesn't even appear in the boot list

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
> the external hard drive doesn't even appear in the boot list

Well that is going to make things difficult if this is the actual case, you can use a plop cd to boot a usb.
[http://www.plop.at/](http://www.plop.at/)

To fix the bootloader to boot to windows 7 again here is a link for a recovery and the command you need with instructions. This just reloads the W7 bootloader to get to W7.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by wilee-nilee on 2010-11-24
Do the windows bootloader with the external unplugged. 

Try the f12 key prompt or another to see if the external shows up in that boot from menu after fixing W7

---

### Post by M. Amin on 2010-11-24
I'm sorry.. Toshiba doesn't come with an installation disk. So I dunno what to do.. and I read on the forum about something called lilo, will that help?

I did unplug the external. Same thing.

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
> I'm sorry.. Toshiba doesn't come with an installation disk. So I dunno what to do.. and I read on the forum about something called lilo, will that help?

I did unplug the external. Same thing.

Your stressing out, look at my post I gave you a link to a recovery disc download it, burn it to a cd and run the one command. post#6

Personally lilo is a latch ditch if you can load the stock MS bootloader IMHO your better off.

---

### Post by M. Amin on 2010-11-24
Oh I'm sorry, I am stressing out already..
But before I do that, I just wanna tell you that there is indeed a recovery partition on there but it's hidden and I dunno how to use it, and will the recovery erase the data on other partitions?
I appreciate your help very much. Thank you.

And isn't there any way of just fixing grub without all the mess of recovery? It would be good if I actually did get Ubuntu to work too.

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
> Oh I'm sorry, I am stressing out already..
But before I do that, I just wanna tell you that there is indeed a recovery partition on there but it's hidden and I dunno how to use it, and will the recovery erase the data on other partitions?
I appreciate your help very much. Thank you.

And isn't there any way of just fixing grub without all the mess of recovery? It would be good if I actually did get Ubuntu to work too.

Grub generally only works on the HD that Ubuntu is installed to. In that if you could boot the external you could boot Vista. But you would not be able to boot Vista with the external unplugged

What I was trying to do is make both independently bootable.

No the recovery disc is only to get you to the recovery terminal to run that command to reload the master boot record to boot into vista.

Hey I would be stressed to just download that recovery ISO it is very small burn it and run the command then we can figure out how to get Ubuntu to boot.

---

### Post by M. Amin on 2010-11-24
Well thank you very much for you help that's exactly what I wanted (about the separate boot thing). I will download the ISO now. I really appreciate your help and I hope you don't sleep soon :D

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
> Well thank you very much for you help that's exactly what I wanted (about the separate boot thing). I will download the ISO now. I really appreciate your help and I hope you don't sleep soon :D


Also download the plop link, that cd should boot the external as it is. The external is set to boot per the script so I was just trying to at first get it read first in the bios. But if this truly isn't the case the plop cd will boot it.
[http://www.plop.at/](http://www.plop.at/)

Lets get Vista working first though leave the external unplugged for now.

I will be up for a couple more hours.

---

### Post by M. Amin on 2010-11-24
ok I don't quite understand the plop thing but I will download it of course, just tell me which of those to download:
Boot Manager downloads

Plop Linux downloads

DOS tools downloads

Linux tools downloads

Windows tools downloads

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
> ok I don't quite understand the plop thing but I will download it of course, just tell me which of those to download:
Boot Manager downloads

Plop Linux downloads

DOS tools downloads

Linux tools downloads

Windows tools downloads

It has been a while since I have downloaded the plop boot ISO for burning to a cd so lets get the Vista working I will look through the plop site and see if I can get the correct download.

We don't want to be mixed up here lets do one thing at a time so to speak, I remember saying download plop but nobody ever asks which one give me a few minutes.

---

### Post by M. Amin on 2010-11-24
Take all time you need I appreciate all you do.

I unplugged the external and now I have a grub> prompt instead of grub rescue>
It says:


```


GNU BRUB version 1.98+20100804-5ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>
```

And I have the Recovery CD ready.

---

### Post by wilee-nilee on 2010-11-24
This link says the f12 prompt will bring up the boot from menu choose the usb HD and go.
[http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=218875](http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=218875)

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
>  
And I have the Recovery CD ready.

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section.
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr

It appears that the f12 prompt at power up will get you to the boot from menu, this menu will be your regular hard drive, the cd/dvd reader, and the usb if plugged in get there open the cd reader put the cd in choose it to boot and follow the above directions.

**Do the Vista MBR repair first.**

---

### Post by M. Amin on 2010-11-24
> **wilee-nilee said:**
> This link says the f12 prompt will bring up the boot from menu choose the usb HD and go.
[http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=218875](http://forums.computers.toshiba-europe.com/forums/thread.jspa?messageID=218875)

"usb HD" meaning the external? it's not listed in the boot menu. And I get grub> instead of grub rescue>

---

### Post by M. Amin on 2010-11-24
Done.
Completed successfully.

now what?

---

### Post by wilee-nilee on 2010-11-24
b

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
> Done.
Completed successfully.

now what?

what is done?

---

### Post by M. Amin on 2010-11-24
ok ok it's done! I fixed the MBR thing, now what?

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
> ok ok it's done! I fixed the MBR thing, now what?

So you can boot into vista correct?

You also said that the external is not showing are you hitting the f12 key as soon as you hit the power up button? Please give a exact description.

Please read carefully and answer exactly what I asked.

---

### Post by M. Amin on 2010-11-24
Now the Vista loaded.. that's great thank you so much :)

Now to the Ubuntu thing, only if you didn't hate me already :D

---

### Post by M. Amin on 2010-11-24
> **wilee-nilee said:**
> So you can boot into vista correct?

You also said that the external is not showing are you hitting the f12 key as soon as you hit the power up button? Please give a exact description.

Please read carefully and answer exactly what I asked.

I am double checking please give me a minute..

---

### Post by M. Amin on 2010-11-24
Yes. The external does not show up when I press F12 as soon as I hit the power up button.

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
> Yes. The external does not show up when I press F12 as soon as I hit the power up button.

First I don't hate anybody, but I have a short fuse at times sorry.;)

So when you use the f12 what do you see?

---

### Post by M. Amin on 2010-11-24
> **wilee-nilee said:**
> First I don't hate anybody, but I have a short fuse at times sorry.;)

So when you use the f12 what do you see?

ok thanks for not hating me (so far) :D

and I only get this:
> CD/DVD: HL-DT-ST DVDRAM GSA-T20N
HDD1: TOSHIBA MK2546GSX
LAN: Marvell Yukon 88E8040T

<Enter Setup>

---

### Post by wilee-nilee on 2010-11-24
> **M. Amin said:**
> ok thanks for not hating me (so far) :D

and I only get this:

Okay, don't worry I never will.;)

So down load that plop ISO and burn it to a cd. Then you will use the cd reader to boot the external with the plop cd. You just choose the cd in that menu then look closely at what comes up you will see another menu, choose the usb, and it should boot into Ubuntu.

Your doing good here it is just easy to for us regular users who are familiar with certain things to forget we may be just giving to much information that makes it more difficult for a newer or stressed user. No finger pointing except at myself here.

The problem with the plop site is every time you choose a page it doesn't change the http url. So I will give you this link your just looking for a ISO to burn that will be bootable from that f12 menu, or just plain bootable.
[http://www.plop.at/en/ploplinux.html](http://www.plop.at/en/ploplinux.html)

I think you get the idea though you will have to use the f12 to get to the cd boot or put the cd reader at the top in the bios, but that will mean any bootable cd will boot does this make sense.

---

### Post by M. Amin on 2010-11-24
> **wilee-nilee said:**
> Okay, don't worry I never will.;)

So down load that plop ISO and burn it to a cd. Then you will use the cd reader to boot the external with the plop cd. You just choose the cd in that menu then look closely at what comes up you will see another menu, choose the usb, and it should boot into Ubuntu.

Your doing good here it is just easy to for us regular users who are familiar with certain things to forget we may be just giving to much information that makes it more difficult for a newer or stressed user. No finger pointing except at myself here.

The problem with the plop site is every time you choose a page it doesn't change the http url. So I will give you this link your just looking for a ISO to burn that will be bootable from that f12 menu, or just plain bootable.
[http://www.plop.at/en/ploplinux.html](http://www.plop.at/en/ploplinux.html)

I think you get the idea though you will have to use the f12 to get to the cd boot or put the cd reader at the top in the bios, but that will mean any bootable cd will boot does this make sense.

I don't think you're giving too much info, you're doing great as an instructor and I'm really grateful for your time and effort


Yea I know the boot device priority stuff. It makes sense.
I'm on plop now, I got some choices:
[LIST]
[*]plop linux
[*]plop linux framebuffer mode
[*]more start modes

[*]plop boot manager   (I chose this)
[*]plop boot manager installer
[*]pcmcia

[*]memtest
[*]boot harddisk
[/LIST]

I figured that "plop boot manager" is what we're looking for. When I chose it I got this list:
[LIST]
[*]HDA PARTITION 1
[*]HDA PARTITION 2
[*]HDA PARTITION 3
[*]FLOPPY
[*]CDROM
[*]USB   (I chose this one)
[*]NETWORK
[/LIST]

When I chose USB I finally get the GRUB list, but when I chose Ubuntu from this list the laptop just restarts. Should I choose Ubuntu (recover mode)? Or what?

---

### Post by wilee-nilee on 2010-11-24
I have to crash, I think that your computer will boot a USB external. Call Toshiba tomorrow or wait for an answer I need to get some sleep. You are back in Vista so really my work is done

To be honest Ubuntu isn't going to run that well from a external anyway the data transfer is just to slow, I would dual boot it if it was me. As you see loading a bootlaoder to the mbr is easy work generally one command for windows 2 for Ubuntu.

good luck 
wilee

---

### Post by M. Amin on 2010-11-24
> **wilee-nilee said:**
> I have to crash, I think that your computer will boot a USB external. Call Toshiba tomorrow or wait for an answer I need to get some sleep. You are back in Vista so really my work is done

To be honest Ubuntu isn't going to run that well from a external anyway the data transfer is just to slow, I would dual boot it if it was me. As you see loading a bootlaoder to the mbr is easy work generally one command for windows 2 for Ubuntu.

good luck 
wilee

Well thank you very much, you did help a lot :)
and sorry for keeping you up so late. Good night!

---

### Post by Quackers on 2010-11-24
Do you have the available hard drive space to create new partitions for Ubuntu on the installed hard drive? Or can you make the space?

---

### Post by M. Amin on 2010-11-24
> **Quackers said:**
> Do you have the available hard drive space to create new partitions for Ubuntu on the installed hard drive? Or can you make the space?

Actually it is not my laptop, it's my uncle's, so I don't think I have this option.  And I actually like the idea of having the whole system installed on an external HD, or even a USB.

See this from [[COLOR="Blue"]another thread[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10064351&postcount=31")
> On a separate happy note, I have now successfully created two fully functional Ubuntu 10.10 USB sticks. I gave one to my daughter to use while I struggle with a Vundo variant virus that was the original cause of the problems with her computer that led me to try to put Ubuntu on a stick. She actually likes having a complete computer in her pocket! She can surf, do her homework, print, etc. If we could get iTunes to work she probably would be ready to abandon Windoze forever ...:p


---

### Post by Quackers on 2010-11-24
I think what you may want is called a persistent usb installation.
This is one where you can just boot up the system from a usb stick and update files and settings that remain. You don't have to start afresh every time you boot into it.
I've never used it myself so don't know how to implement it. Try a search for that term or Google.

---

### Post by M. Amin on 2010-11-24
> **Quackers said:**
> I think what you may want is called a persistent usb installation.
This is one where you can just boot up the system from a usb stick and update files and settings that remain. You don't have to start afresh every time you boot into it.
I've never used it myself so don't know how to implement it. Try a search for that term or Google.

Thank you, I will. And thanks for the term I didn't know what's it called.

---

### Post by Quackers on 2010-11-24
No problem :-)
Have fun!

---

