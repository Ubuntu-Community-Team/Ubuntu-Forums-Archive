---
title: "Can't boot W8.1 any longer after using Grub's menu option"
date: 2014-01-11
forum: Installation &amp; Upgrades
---

### Post by dowoshek on 2014-01-11
Hello,
I've used dual-boot Xubuntu 13.04 and Windows8 in my new Asus notebook for half a year without problems. I had no Grub option for W8. Whenever I wanted to use W8 i pressed ESC during computer restart and directly used UEFI Windows option. I recently upgraded Xubuntu to 13.10 and there're no problems with W8 booting (I used it few times after upgade). But a new option for Windows appeared in Grub menu and I tried it _once_. It didn't work and moreover I can't boot W8 using ESC now too. I just can't boot W8 any way.
After chosing W8 Grub's option i get:
```
/EndEntire
file path : ACPI.........more info
error can't find end of file /EFI/Microsoft/Boot/bootmgfw.efi
```
Please, help me fix the problem.
Here's BootInfoScript log:
```
                Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/debian/grubx64.efi 
                       /efi/ubuntu/grubx64.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: nieznany typ systemu plików ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 91201, w sumie sektorów: 1465149168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 4096

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 Windows Recovery Environment (Windows)
/dev/sda2         616,448       821,247       204,800 EFI System partition
/dev/sda3         821,248     1,083,391       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,083,392   113,778,687   112,695,296 Data partition (Windows/Linux)
/dev/sda5     113,778,688   420,978,687   307,200,000 Data partition (Windows/Linux)
/dev/sda6     420,978,688   529,483,775   108,505,088 Data partition (Windows/Linux)
/dev/sda7     529,483,776   833,302,527   303,818,752 Data partition (Windows/Linux)
/dev/sda8     833,302,528 1,455,382,527   622,080,000 Data partition (Windows/Linux)
/dev/sda9   1,455,382,528 1,465,147,391     9,764,864 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        C2568EF7568EEB8B                       ntfs       Recovery
/dev/sda2        F892-3C6C                              vfat       
/dev/sda4        3ADA3F3DDA3EF52B                       ntfs       
/dev/sda5        9ED4D104D4D0DF97                       ntfs       
/dev/sda6        5117fd14-c3b5-422d-ad46-2a2ab5641682   ext4       
/dev/sda7        d3c3aadf-dee8-4282-9720-9c4f7bfabaa5   ext4       
/dev/sda8        c5e65be3-f37f-46e6-a885-114dfa4b0340   ext4       
/dev/sda9        1fa5a837-2888-4ea1-aab3-89b6adb775d1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw)
/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda7        /home                    ext4       (rw)
/dev/sda8        /mnt/magazynek           ext4       (rw)


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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  5117fd14-c3b5-422d-ad46-2a2ab5641682
else
  search --no-floppy --fs-uuid --set=root 5117fd14-c3b5-422d-ad46-2a2ab5641682
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=pl_PL
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=20
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5117fd14-c3b5-422d-ad46-2a2ab5641682' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  5117fd14-c3b5-422d-ad46-2a2ab5641682
    else
      search --no-floppy --fs-uuid --set=root 5117fd14-c3b5-422d-ad46-2a2ab5641682
    fi
    linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=5117fd14-c3b5-422d-ad46-2a2ab5641682 ro   
    initrd    /boot/initrd.img-3.11.0-15-generic
}
submenu 'Opcje zaawansowane dla systemu Ubuntu' $menuentry_id_option 'gnulinux-advanced-5117fd14-c3b5-422d-ad46-2a2ab5641682' {
    menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.11.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-15-generic-advanced-5117fd14-c3b5-422d-ad46-2a2ab5641682' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  5117fd14-c3b5-422d-ad46-2a2ab5641682
        else
          search --no-floppy --fs-uuid --set=root 5117fd14-c3b5-422d-ad46-2a2ab5641682
        fi
        echo    'Wczytywanie systemu Linux 3.11.0-15-generic...'
        linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=5117fd14-c3b5-422d-ad46-2a2ab5641682 ro   
        echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
        initrd    /boot/initrd.img-3.11.0-15-generic
    }
    menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.11.0-15-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-15-generic-recovery-5117fd14-c3b5-422d-ad46-2a2ab5641682' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  5117fd14-c3b5-422d-ad46-2a2ab5641682
        else
          search --no-floppy --fs-uuid --set=root 5117fd14-c3b5-422d-ad46-2a2ab5641682
        fi
        echo    'Wczytywanie systemu Linux 3.11.0-15-generic...'
        linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=5117fd14-c3b5-422d-ad46-2a2ab5641682 ro recovery nomodeset 
        echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
        initrd    /boot/initrd.img-3.11.0-15-generic
    }
    menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.8.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-advanced-5117fd14-c3b5-422d-ad46-2a2ab5641682' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  5117fd14-c3b5-422d-ad46-2a2ab5641682
        else
          search --no-floppy --fs-uuid --set=root 5117fd14-c3b5-422d-ad46-2a2ab5641682
        fi
        echo    'Wczytywanie systemu Linux 3.8.0-35-generic...'
        linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=5117fd14-c3b5-422d-ad46-2a2ab5641682 ro   
        echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
    menuentry 'Ubuntu, za pomoc&#261; systemu Linux 3.8.0-35-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-recovery-5117fd14-c3b5-422d-ad46-2a2ab5641682' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  5117fd14-c3b5-422d-ad46-2a2ab5641682
        else
          search --no-floppy --fs-uuid --set=root 5117fd14-c3b5-422d-ad46-2a2ab5641682
        fi
        echo    'Wczytywanie systemu Linux 3.8.0-35-generic...'
        linux    /boot/vmlinuz-3.8.0-35-generic root=UUID=5117fd14-c3b5-422d-ad46-2a2ab5641682 ro recovery nomodeset 
        echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Boot Manager (UEFI on /dev/sda2)" --class windows --class os {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  F892-3C6C
    else
      search --no-floppy --fs-uuid --set=root F892-3C6C
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=5117fd14-c3b5-422d-ad46-2a2ab5641682 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=F892-3C6C  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda7 during installation
UUID=d3c3aadf-dee8-4282-9720-9c4f7bfabaa5 /home           ext4    defaults        0       2
# /mnt/magazynek was on /dev/sda8 during installation
UUID=c5e65be3-f37f-46e6-a885-114dfa4b0340 /mnt/magazynek  ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=1fa5a837-2888-4ea1-aab3-89b6adb775d1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 09 00  |........?....h..|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 6c 3c 92 f8 4e  4f 20 4e 41 4d 45 20 20  |..)l<..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-qzOEVp6D/Tmp_Log: Nie ma takiego pliku ani katalogu
```

---

### Post by oldfred on 2014-01-11
Old versions of Ubuntu used to erase efi partition and create a new one. But your update to grub found Windows files in the efi partition to boot with, but those files now are missing in efi partition.
Boot script only shows bootmgr & BCD but there should a Microsoft folder with other support files also. That entire folder is missing.

You need to use a Windows 8 UEFI repair flash drive to repair the efi partition.
         Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

You may be able to create this folder and copy bootmgr into it.

 /EFI/Microsoft/Boot/bootmgfw.efi

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.
And then with third party Windows tools create a BCD.
But do not use EasyBCD to boot Ubuntu as with UEFI you do not need that.

 [http://neosmart.net/blog/](http://neosmart.net/blog/)

      
 Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
BCDboot Command-Line Options Windows 8 recreates boot files.
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)
BCD technical info Vista & efi
[http://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc721886%28v=ws.10%29.aspx)

---

### Post by dowoshek on 2014-01-11
Thank you for your answer. Before reading your post I decided to use Boot-Repair disk (though it was not recommended in simmilar situations I've found on the web) and it did the job. I can boot W8 using Grub's menu entry now :)

---

