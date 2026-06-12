---
title: "Unable to boot Windows after installing Ubuntu."
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by vasuma on 2012-03-09
I bought Hp Pavilion dm4-2110sp just yesterday and i did partitioning and i installed ubuntu.
My ethernet card and wireless card is not detecting to install  "testdisk" to recover my windows files.
Please help me

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => FreeDOS (eXtended FDisk) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   274,995,199   274,585,600  42 SFS
/dev/sda4         274,997,246 1,250,260,991   975,263,746   5 Extended
/dev/sda5         274,997,248   567,963,647   292,966,400  83 Linux
/dev/sda6         567,965,696   592,058,367    24,092,672  82 Linux swap / Solaris
/dev/sda7         592,060,416 1,138,933,759   546,873,344  83 Linux
/dev/sda8       1,138,935,808 1,250,260,991   111,325,184   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4089 MB, 4089446400 bytes
33 heads, 63 sectors/track, 3841 cylinders, total 7987200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  32     7,987,199     7,987,168   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        36EA356BEA35288F                       ntfs       SYSTEM
/dev/sda3        9C8ABE4F8ABE25A4                       ntfs       
/dev/sda5        512f9e13-dd31-4329-8ee7-e11e18a46b9c   ext2       
/dev/sda6        b0a4f6a2-1d8a-4810-a9c0-8ff525fd334f   swap       
/dev/sda7        a65ebd83-eca6-4ae7-9bd6-0f3856e5471f   ext4       
/dev/sda8        5E96-3DAF                              vfat       
/dev/sdb1        468A-65E0                              vfat       VASU

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /media/9C8ABE4F8ABE25A4  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext2       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sda8        /windows                 vfat       (rw,utf8,umask=007,gid=46)
/dev/sdb1        /media/VASU              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 512f9e13-dd31-4329-8ee7-e11e18a46b9c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 512f9e13-dd31-4329-8ee7-e11e18a46b9c
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
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 512f9e13-dd31-4329-8ee7-e11e18a46b9c
    linux    /boot/vmlinuz-2.6.32-38-generic root=/dev/sda5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 512f9e13-dd31-4329-8ee7-e11e18a46b9c
    echo    'Loading Linux 2.6.32-38-generic ...'
    linux    /boot/vmlinuz-2.6.32-38-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-38-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 512f9e13-dd31-4329-8ee7-e11e18a46b9c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 512f9e13-dd31-4329-8ee7-e11e18a46b9c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 36EA356BEA35288F
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 9C8ABE4F8ABE25A4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
/dev/sda5       /               ext2    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=a65ebd83-eca6-4ae7-9bd6-0f3856e5471f /home           ext4    defaults        0       2
# /windows was on /dev/sda8 during installation
UUID=5E96-3DAF  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=b0a4f6a2-1d8a-4810-a9c0-8ff525fd334f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 225.808696747 = 242.460241920  boot/grub/core.img                             1
 225.839969635 = 242.493820928  boot/grub/grub.cfg                             1
 225.664340973 = 242.305241088  boot/initrd.img-2.6.32-38-generic              3
 225.651214600 = 242.291146752  boot/vmlinuz-2.6.32-38-generic                 2
 225.664340973 = 242.305241088  initrd.img                                     3
 225.651214600 = 242.291146752  vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 50 76 11 00 fe  |...........Pv...|
000001d0  ff ff 05 fe ff ff 02 50  76 11 00 a8 6f 01 00 00  |.......Pv...o...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda5

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000200

Unknown BootLoader on sdb1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 30 03  |.X.MSDOS5.0...0.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 df 79 00 68 1e 00 00  00 00 00 00 02 00 00 00  |..y.h...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 e0 65 8a 46 4e  4f 20 4e 41 4d 45 20 20  |..).e.FNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

---

### Post by darkod on 2012-03-09
Your partitions are SFS, that means Dynamic disk in win7. Ubuntu doesn't install on dynamic disks. That is the issue.

Do you have any win7 rescue cd? Anything that you can use to restore the windows bootloader on the MBR? I am talking just restoring the bootloader, not a complete restore of win7 (that will probably destroy all your data).

---

### Post by Mark Phelps on 2012-03-12
If you have a working Windows PC, or access to one, download and burn the ISO of the EASEUS Partition Master Home Edition app.  It claims to be able to convert Dynamic Disks to Basis Disks.

If it does not actually that, then you will either need to purchase the Pro edition to do that, or you will have to buy the Pro version of Partition Wizard.

Your data -- your money -- your choice.

---

### Post by vasuma on 2012-03-14
> **darkod said:**
> Your partitions are SFS, that means Dynamic disk in win7. Ubuntu doesn't install on dynamic disks. That is the issue.

Do you have any win7 rescue cd? Anything that you can use to restore the windows bootloader on the MBR? I am talking just restoring the bootloader, not a complete restore of win7 (that will probably destroy all your data).

I don´t have win7 rescue CD.

---

### Post by Mark Phelps on 2012-03-14
> **vasuma said:**
> I don´t have win7 rescue CD.

Actually, you could have made your own, for FREE, if you had bothered to do that while Win7 was working.

But, since you didn't, you will have to go to the link below and PURCHASE the download -- and burn that to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

