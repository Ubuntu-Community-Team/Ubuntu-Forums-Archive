---
title: "Ubuntu + windows 8.1 installed on top"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by tatsujb on 2015-02-28
Searched high and low. HIGH AND LOW before posting my own thread.

would you believe it noone ever thought we'd need this topic.

I installed windows 8.1 after nearly two years of using only ubuntu.

I say installed because I know the files have copied over to the hard drive I haven't seen it boot for the first time because as the second part of the install process windows needs to boot on hard drive it was installed to.

and before it can do that I need to provide it with a grub entry.

Given it's on the fourth hard drive all on it's lonesome, it didn't get to touch grub nor supersede it and I like it that way. however this also means a grub entry never existed for it and "update-grub" is as efficient as fairy dust.

How do I add windows bootloader to GRUB 2 given I know that windows is on the fourth partition of the fourth drive. (yes they have THREE extra partitions now, wth) 
[IMG]https://dl.dropboxusercontent.com/u/22720750/Screenshot%20from%202015-02-28%2020%3A30%3A04.png[/IMG]
(also this proves the installation IS there)

I'm not afraid of getting my hands dirty I already backed up my grub on a usb key and have another usb key with a ubuntu livecd on it.

I'd much rather type in the Grub entry by hand then to resort to some program which so far have all proven useless.

---

### Post by yancek on 2015-02-28
Did you install windows 8 using UEFI/GPT or did you use MBR? 
Did you install Ubuntu using UEFI/GPT or did you use MBR?

You could try downloading and running the boot repair script and selecting the option to Create Boot Info Summary and then post the output here.

---

### Post by grahammechanical on 2015-02-28
I have said this before on this forum and I do not mind saying it again because it is a forum and there is nothing wrong with someone asking the same question that someone has recently asked.

When I installed Windows 8 preview on a second hard disk the installer put the Windows boot loader into the MBR of both hard disks and I was unable to load Ubuntu. This may have happened to you.

Can you load Ubuntu? That is not clear from your post. What hard drive is Ubuntu installed on? Is it sda? Or sdb? Or sdc? Load Ubuntu and open a terminal and run

```
sudo update-grub
```

and see from the printout if the Windows boot loader is detected. But if Grub is no longer in the MBR we need to do more than run update-grub. We need to install Grub.

```
sudo grub-install /dev/sda
```

Assuming that Ubuntu is on sda. If it is one sdb or sdc than change /dev/sda to /dev/sdb or /dev/sdc as appropriate. And the set the BIOS to load an operating system from the disk with Ubuntu on it.

Or use boot repair. But be careful as boot repair defaults to installing Grub into the MBR of all drives, which is not what you want it to do. If you cannot load Ubuntu then use the Ubuntu live session and first use File Manager to open the hard disk/partition with Ubuntu on and then open a terminal and run those two commands.

Regards.

---

### Post by oldfred on 2015-02-28
Your Windows install is UEFI.
So the suggestion on Boot-Repair to see how Ubuntu is installed is important.
And if Ubuntu is also UEFI with gpt partitioning, then the sudo update-grub from inside your Ubuntu will add Windows to menu. But if in BIOS mode it will not work.
UEFI & BIOS are not compatible. You can only dual boot by restarting system and choosing in UEFI boot menu, not from grub menu, if systems are not in same boot mode.

Just post link to summary report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tatsujb on 2015-03-01
> **yancek said:**
> Did you install windows 8 using UEFI/GPT or did you use MBR? 
Did you install Ubuntu using UEFI/GPT or did you use MBR?

You could try downloading and running the boot repair script and selecting the option to Create Boot Info Summary and then post the output here.
windows uefi and ubuntu as well as i remember it.

---

### Post by tatsujb on 2015-03-01
> **grahammechanical said:**
> I have said this before on this forum and I do not mind saying it again because it is a forum and there is nothing wrong with someone asking the same question that someone has recently asked.

When I installed Windows 8 preview on a second hard disk the installer put the Windows boot loader into the MBR of both hard disks and I was unable to load Ubuntu. This may have happened to you.

no.

did you read the OP?

yes i can boot ubuntu how else could i use gparted?

the windows isn't installed on the same hard drive as such MBR did not supersede Grub, and the two do no even know each other.

windows thinks he is on the first hard drive and will boot fine if I set him as first hard drive. 

but he is on the fourth.

If I create a grub entry that sends to that hard drive I think the windows boot loader will kick in on it's own and everything will work fine.

all I need is a example grub entry (with where to place it) and I'm quite sure I'll get it working from there.

---

### Post by oldfred on 2015-03-01
Post Summary report from Boot-Repair. Then we can suggest a boot stanza. Otherwise we are just guessing.

---

### Post by tatsujb on 2015-03-01
> **yancek said:**
> 
You could try downloading and running the boot repair script and selecting the option to Create Boot Info Summary and then post the output here.

```
                  Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    5387040 of the same hard drive for core.img. core.img is at this location 
    and looks in partition 112 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid a1184ef3-5aa8-4a4e-9f21-eb4f2d1ea42e root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => No boot loader is installed in the MBR of /dev/sdd.


sda1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdc1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdc2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdd1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdd2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi


sdd3: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''


sdd4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe


sde: ___________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/boot/bootx64.efi /bootmgr /boot/bcd


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1   117,231,407   117,231,407  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048    37,771,263    37,769,216 Data partition (Linux)
/dev/sda2      37,773,312   117,229,567    79,456,256 Data partition (Linux)


Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS




Drive: sdc _____________________________________________________________________


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdc1               2,048 2,375,475,199 2,375,473,152   7 NTFS / exFAT / HPFS
/dev/sdc2       2,375,475,200 2,436,737,023    61,261,824  83 Linux




Drive: sdd _____________________________________________________________________


Disk /dev/sdd: 160.0 GB, 160041885696 bytes
256 heads, 63 sectors/track, 19381 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdd1                   1 4,294,967,295 4,294,967,295  ee GPT


/dev/sdd1 ends after the last sector of /dev/sdd


GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1           2,048       616,447       614,400 Windows Recovery Environment (Windows)
/dev/sdd2         616,448       821,247       204,800 EFI System partition
/dev/sdd3         821,248     1,083,391       262,144 Microsoft Reserved Partition (Windows)
/dev/sdd4       1,083,392   312,580,095   311,496,704 Data partition (Windows/Linux)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        70f24e13-d6a9-4e06-a796-6cfe4f951a91   ext4       
/dev/sda2        45397cb8-6313-45d1-a376-cb31f40d5161   ext4       
/dev/sdb1        6C668A156689DFE6                       ntfs       1TBVolume
/dev/sdc1        7AD0E6EDD0E6AF17                       ntfs       2TBVolume
/dev/sdc2        47aab5c3-8e8e-4874-8016-22081ed5abd4   ext4       Storage
/dev/sdd1        6C802DD5802DA714                       ntfs       Récupération
/dev/sdd2        4C32-756C                              vfat       
/dev/sdd4        76C44337C442F93F                       ntfs       
/dev/sde         FA6C-A83E                              vfat       WINDOWS


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext4       (rw)
/dev/sde         /media/t/WINDOWS         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)




=========================== sda1/boot/grub/grub.cfg: ===========================


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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi


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
set root='hd0,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  70f24e13-d6a9-4e06-a796-6cfe4f951a91
else
  search --no-floppy --fs-uuid --set=root 70f24e13-d6a9-4e06-a796-6cfe4f951a91
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=countdown
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --verbose --interruptible 10 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-70f24e13-d6a9-4e06-a796-6cfe4f951a91' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  70f24e13-d6a9-4e06-a796-6cfe4f951a91
    else
      search --no-floppy --fs-uuid --set=root 70f24e13-d6a9-4e06-a796-6cfe4f951a91
    fi
    linux    /boot/vmlinuz-3.17.1-031701-generic root=UUID=70f24e13-d6a9-4e06-a796-6cfe4f951a91 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.17.1-031701-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-70f24e13-d6a9-4e06-a796-6cfe4f951a91' {
    menuentry 'Ubuntu, with Linux 3.17.1-031701-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.17.1-031701-generic-advanced-70f24e13-d6a9-4e06-a796-6cfe4f951a91' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  70f24e13-d6a9-4e06-a796-6cfe4f951a91
        else
          search --no-floppy --fs-uuid --set=root 70f24e13-d6a9-4e06-a796-6cfe4f951a91
        fi
        echo    'Loading Linux 3.17.1-031701-generic ...'
        linux    /boot/vmlinuz-3.17.1-031701-generic root=UUID=70f24e13-d6a9-4e06-a796-6cfe4f951a91 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.17.1-031701-generic
    }
    menuentry 'Ubuntu, with Linux 3.17.1-031701-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.17.1-031701-generic-recovery-70f24e13-d6a9-4e06-a796-6cfe4f951a91' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  70f24e13-d6a9-4e06-a796-6cfe4f951a91
        else
          search --no-floppy --fs-uuid --set=root 70f24e13-d6a9-4e06-a796-6cfe4f951a91
        fi
        echo    'Loading Linux 3.17.1-031701-generic ...'
        linux    /boot/vmlinuz-3.17.1-031701-generic root=UUID=70f24e13-d6a9-4e06-a796-6cfe4f951a91 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.17.1-031701-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  70f24e13-d6a9-4e06-a796-6cfe4f951a91
    else
      search --no-floppy --fs-uuid --set=root 70f24e13-d6a9-4e06-a796-6cfe4f951a91
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  70f24e13-d6a9-4e06-a796-6cfe4f951a91
    else
      search --no-floppy --fs-uuid --set=root 70f24e13-d6a9-4e06-a796-6cfe4f951a91
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
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


=============================== sda1/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=70f24e13-d6a9-4e06-a796-6cfe4f951a91 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=45397cb8-6313-45d1-a376-cb31f40d5161 /home           ext4    defaults        0       2
--------------------------------------------------------------------------------


=================== sda1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sdd2


00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 09 00  |........?....h..|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 6c 75 32 4c 4e  4f 20 4e 41 4d 45 20 20  |..)lu2LNO NAME  |
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
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 45 72  |..............Er|
000001b0  72 2e 20 64 69 73 71 75  65 ff 0d 0a 50 72 65 73  |r. disque...Pres|
000001c0  73 65 7a 20 75 6e 65 20  74 6f 75 63 68 65 20 70  |sez une touche p|
000001d0  6f 75 72 20 72 65 64 82  6d 61 72 72 65 72 0d 0a  |our red.marrer..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 ba 01 00 00 55 aa  |..............U.|
00000200


Unknown BootLoader on sde


00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 e6 07  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 b0 f0 00 0d 3c 00 00  00 00 00 00 02 00 00 00  |.....<..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 3e a8 6c fa 4e  4f 20 4e 41 4d 45 20 20  |..)>.l.NO NAME  |
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
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 45 72  |..............Er|
000001b0  72 2e 20 64 69 73 71 75  65 ff 0d 0a 50 72 65 73  |r. disque...Pres|
000001c0  73 65 7a 20 75 6e 65 20  74 6f 75 63 68 65 20 70  |sez une touche p|
000001d0  6f 75 72 20 72 65 64 82  6d 61 72 72 65 72 0d 0a  |our red.marrer..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 ba 01 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages: ===============================


xz: (stdin): Compressed data is corrupt
cat: /tmp/BootInfo-uxhB9KqG/Tmp_Log: No such file or directory



```
> **oldfred said:**
> Post Summary report from Boot-Repair. Then we can suggest a boot stanza. Otherwise we are just guessing.
[http://paste.ubuntu.com/10488130/](http://paste.ubuntu.com/10488130/)

apparently the two are quite similar.

---

### Post by oldfred on 2015-03-01
As suspected you have Windows in UEFI boot mode on sdd and Ubuntu in BIOS boot mode on sda.
Grub then cannot boot Windows. Grub can only boot systems installed in the same boot mode as you have to reboot to switch modes. Or you can only boot from UEFI menu.

You also show grub in MBR of sda. But sda is shown as gpt partitioned. So I do not think you can boot from grub in sda, without having a bios_grub partition for BIOS boot with gpt partitioning. 
Is UEFI boot you have to have gpt partitioning and an efi partition.

Are you actually booting from sdb or sdc? Those show still as MBR(msdos) partitioned.

---

### Post by tatsujb on 2015-03-01
> **oldfred said:**
> 

Are you actually booting from sdb or sdc? Those show still as MBR(msdos) partitioned.
neither. those are just NTFS formatted, i kept the partitioning as is because they are rather full and moving the data to ext4 would require an incredible amount of shimmying on the same drive.

so the good news is I can boot windows just by using the motherboard's boot menu on boot?

EDIT : thinking about reinstalling ubuntu in UEFI mode, good or bad idea?

also why is it my ubuntu liveCD won't work in UEFI mlode?

---

### Post by oldfred on 2015-03-01
If you have UEFI hardware, you should be able to select to boot Windows from UEFI boot menu.
Some systems do require you to turn on/off UEFI and/or CSM/BIOS mode to boot system installed in that mode. Others auto switch, but you still have to boot from UEFI boot menu or one time boot key on a reboot.

You should also be able to boot flash drive or DVD, but if secure boot is on, you may have to also turn on other settings to allow any other device to boot. Even with secure boot off, some require you to set a password to open other settings that you need to change. Never lose that password if you have to have it.

If you are changing or using UEFI best to have all systems in UEFI boot mode and have all drives with gpt partitioning. But you can transition as you update or change configurations.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

With multiple drives, many suggest disconnecting other drives, so you have a clean install to that one drive only. You can partition in advance and use Something Else, but I found even then Ubuntu would use another drive's efi partition. I then copied boot files back to efi partition on same drive.

---

