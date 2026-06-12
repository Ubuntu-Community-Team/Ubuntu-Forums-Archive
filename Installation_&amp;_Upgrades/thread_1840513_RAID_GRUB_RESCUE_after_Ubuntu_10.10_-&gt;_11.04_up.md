---
title: "RAID GRUB RESCUE after Ubuntu 10.10 -&gt; 11.04 upgrade"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by masho95 on 2011-09-07
It was suggested under my other thread to post a new thread with the word RAID in it to get help from users with RAID experience. Trying to get my 4 RAID drives with Windows 7 back into the boot loader!

[Other thread]("http://ubuntuforums.org/showthread.php?t=1840359")

So to start off I'm a complete Linux newb, and I originally installed Ubuntu 10.10 to learn a little more about it. 

I have a laptop and a desktop. Both computers had Ubuntu 10.10 installed on them. On the laptop Ubuntu was installed in a dual boot configuration on a single partitioned hard drive. On my desktop Ubuntu had it's own separate drive. I have 4 other hard drives 1 TB each running in a RAID 10 setup. I upgraded from 10.10 -> 11.04 on my laptop first and it went off without any problem.

When I upgraded 10.10 -> 11.04 on my desktop all hell broke loose. I choose all the same options as the laptop upgrade, but it didn't work out as well, lol. I think the problem originated at the end of the upgrade when it asks you about the boot configuration. I chose the first option which was something like "use the manufacturers boot blah blah". When the computer restarted it went through the POST and I was left at a "grub rescue>" prompt. I messed around with a program called Rescatux. I think what I ended up doing was installing a MBR to the sde drive which is my separate hard drive for Ubuntu. I changed the boot order in my BIOS to the separate drive with Ubuntu first and now it will boot into Ubuntu fine but it has no boot loader.

My question and probably complicated is, how do I restore it to the way it was before? With the GRUB2 boot loader and the option to boot into Windows 7 (on my four hard drives in RAID 10 setup) along with the option of booting into Ubuntu 11.04 on the separate drive?? I have a boot script text file output that was generated from the Rescatux program. Should I post the output to this thread? Not even sure what's in the text file.

Thank you in advance for any help restoring my system to a working condition (mainly Windows 7)

Boot Script Info:
```
  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Testdisk is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdf.
 => Testdisk is installed in the MBR of /dev/mapper/isw_dahgaaided_myraid.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       isw_raid_member
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type 'isw_raid_member'

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

isw_dahgaaided_myraid1: ________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type 'isw_raid_member'
mount: unknown filesystem type ''

isw_dahgaaided_myraid2: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type 'isw_raid_member'
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 2,936,010,751 2,935,803,904   7 NTFS / exFAT / HPFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848 2,936,010,751 2,935,803,904   7 NTFS / exFAT / HPFS

/dev/sdb2 ends after the last sector of /dev/sdb

Drive: sde _____________________________________________________________________

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               2,048   293,048,319   293,046,272  83 Linux
/dev/sde2         293,050,366   312,580,095    19,529,730   5 Extended
/dev/sde5         293,050,368   312,580,095    19,529,728  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  32     7,821,311     7,821,280   b W95 FAT32


Drive: isw_dahgaaided_myraid _____________________________________________________________________

Disk /dev/mapper/isw_dahgaaided_myraid: 751.6 GB, 751619407872 bytes
255 heads, 63 sectors/track, 91379 cylinders, total 1468006656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_dahgaaided_myraid1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_dahgaaided_myraid2            206,848 2,936,010,751 2,935,803,904   7 NTFS / exFAT / HPFS

/dev/mapper/isw_dahgaaided_myraid2 ends after the last sector of /dev/mapper/isw_dahgaaided_myraid

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda                                                isw_raid_member 
/dev/sdb2                                               isw_raid_member 
/dev/sdc                                                isw_raid_member 
/dev/sdd                                                isw_raid_member 
/dev/sde1        58808144-aad3-4fb3-939b-39f48fad4654   ext4       
/dev/sde5        dbe63fe0-381f-4c7c-b15e-6c06f5ef5731   swap       
/dev/sdf1        602F-9D79                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_dahgaaided_myraid
isw_dahgaaided_myraid-0
isw_dahgaaided_myraid1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sde1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdf1        /media/602F-9D79         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sde1/boot/grub/grub.cfg: ===========================

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
set root='(hd4,msdos1)'
search --no-floppy --fs-uuid --set=root 58808144-aad3-4fb3-939b-39f48fad4654
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd4,msdos1)'
search --no-floppy --fs-uuid --set=root 58808144-aad3-4fb3-939b-39f48fad4654
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 58808144-aad3-4fb3-939b-39f48fad4654
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=58808144-aad3-4fb3-939b-39f48fad4654 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 58808144-aad3-4fb3-939b-39f48fad4654
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=58808144-aad3-4fb3-939b-39f48fad4654 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 58808144-aad3-4fb3-939b-39f48fad4654
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=58808144-aad3-4fb3-939b-39f48fad4654 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 58808144-aad3-4fb3-939b-39f48fad4654
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=58808144-aad3-4fb3-939b-39f48fad4654 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 58808144-aad3-4fb3-939b-39f48fad4654
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root 58808144-aad3-4fb3-939b-39f48fad4654
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sde1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde1 during installation
UUID=58808144-aad3-4fb3-939b-39f48fad4654 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=dbe63fe0-381f-4c7c-b15e-6c06f5ef5731 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sde1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 124.157890320 = 133.313519616  boot/grub/core.img                             1
 124.204124451 = 133.363163136  boot/grub/grub.cfg                             1
   2.253883362 = 2.420088832    boot/initrd.img-2.6.35-22-generic              2
   3.523090363 = 3.782889472    boot/initrd.img-2.6.38-11-generic              2
 124.181774139 = 133.339164672  boot/vmlinuz-2.6.35-22-generic                 1
   2.485664368 = 2.668961792    boot/vmlinuz-2.6.38-11-generic                 1
   3.523090363 = 3.782889472    initrd.img                                     2
   2.253883362 = 2.420088832    initrd.img.old                                 2
   2.485664368 = 2.668961792    vmlinuz                                        1
 124.181774139 = 133.339164672  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sdb2

00000000  5c 24 20 45 33 c9 41 8b  d7 48 8b 4c 24 30 e8 a5  |\$ E3.A..H.L$0..|
00000010  4b 7d ff 8b 4e 50 41 81  ff 00 00 00 80 75 09 83  |K}..NPA......u..|
00000020  f9 ff 0f 84 68 49 2e 00  41 8b c7 99 f7 f9 8b c8  |....hI..A.......|
00000030  8b 46 58 0f af c8 48 63  d1 48 8d 0d b2 4f 53 ff  |.FX...Hc.H...OS.|
00000040  e8 5b 06 7d ff 48 8b f8  48 8b 4e 38 48 8d 05 0d  |.[.}.H..H.N8H...|
00000050  97 5c ff 80 39 00 48 c7  44 24 28 00 00 00 00 48  |.\..9.H.D$(....H|
00000060  89 7c 24 20 45 8b cf 45  33 c0 4c 8b 7c 24 30 49  |.|$ E..E3.L.|$0I|
00000070  8b d7 4c 8b d8 ff 10 8b  d8 89 5c 24 20 45 8b cd  |..L.......\$ E..|
00000080  4d 8b c6 33 d2 48 8b cf  e8 2b 4b 7d ff 4d 8b 47  |M..3.H...+K}.M.G|
00000090  08 33 d2 49 8b cf e8 85  44 7d ff 4c 8b 47 08 33  |.3.I....D}.L.G.3|
000000a0  d2 48 8b cf e8 77 44 7d  ff 2b eb 44 03 eb 66 90  |.H...wD}.+.D..f.|
000000b0  85 ed 7f 08 41 8b c4 e9  90 01 00 00 8b 4e 2c 8b  |....A........N,.|
000000c0  46 50 3b c8 0f 8d f0 00  00 00 66 0f 1f 44 00 00  |FP;.......f..D..|
000000d0  4c 8b 5e 30 48 8b 56 40  44 8b 46 2c 44 8b 4e 50  |L.^0H.V@D.F,D.NP|
000000e0  45 2b c8 49 8b 03 49 8b  cb ff 90 28 01 00 00 44  |E+.I..I....(...D|
000000f0  8b d8 45 85 db 0f 85 a8  00 00 00 48 8b 4e 38 48  |..E........H.N8H|
00000100  8b 56 40 44 8b 4e 2c 48  8d 05 5a 96 5c ff 80 39  |.V@D.N,H..Z.\..9|
00000110  00 45 33 c0 4c 8b d8 ff  10 48 8b d8 48 8d 7e 48  |.E3.L....H..H.~H|
00000120  48 8b d3 48 8b cf e8 e5  04 7d ff 48 8b 43 08 89  |H..H.....}.H.C..|
00000130  46 54 c6 46 62 01 8b 46  54 3b e8 7d 3b 48 8b 0f  |FT.Fb..FT;.};H..|
00000140  89 6c 24 20 45 8b cd 4d  8b c6 33 d2 e8 67 4a 7d  |.l$ E..M..3..gJ}|
00000150  ff 8b 46 54 2b c5 89 46  54 48 8b 0f 8b 46 54 89  |..FT+..FTH...FT.|
00000160  44 24 20 45 33 c9 4c 8b  c1 8b d5 e8 48 4a 7d ff  |D$ E3.L.....HJ}.|
00000170  41 8b c4 e9 d4 00 00 00  48 8b 0f 89 44 24 20 45  |A.......H...D$ E|
00000180  8b cd 4d 8b c6 33 d2 e8  2c 4a 7d ff 8b 46 54 2b  |..M..3..,J}..FT+|
00000190  e8 c7 46 54 00 00 00 00  44 2b e5 41 8b c4 e9 a9  |..FT....D+.A....|
000001a0  00 00 00 8b 46 2c 41 03  c3 89 46 2c 8b 4e 2c 8b  |....F,A...F,.N,.|
000001b0  46 50 3b c8 0f 8c 16 ff  ff ff 48 8b 4e 38 48 8b  |FP;.......H.N8H.|
000001c0  56 40 44 8b 4e 50 48 8b  46 48 4c 8d 15 9f 95 5c  |V@D.NPH.FHL....\|
000001d0  ff 80 39 00 48 c7 44 24  28 00 00 00 00 48 89 44  |..9.H.D$(....H.D|
000001e0  24 20 45 33 c0 4d 8b da  41 ff 12 8b d8 c7 46 2c  |$ E3.M..A.....F,|
000001f0  00 00 00 00 3b eb 7c 1f  48 8b 4e 48 89 5c 24 20  |....;.|.H.NH.\$ |
00000200

Unknown BootLoader on isw_dahgaaided_myraid2



=============================== StdErr Messages: ===============================

unlzma: Decoder error
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/mapper/isw_dahgaaided_myraid2: No such file or directory
hexdump: /dev/mapper/isw_dahgaaided_myraid2: No such file or directory
```

---

### Post by YesWeCan on 2011-09-07
Hi there.
I haven't read your previous thread yet. Can you boot anything at the moment?

After a quick glance it seems to me what you want to end up with is Ubuntu and Grub on the 160GB sde drive and your Windows RAID10 to be totally untouched by linux. This way you can boot the RAID directly if you need to but you can boot either Ubuntu or Windows via Grub on sde.

So my first question is what happens when you tell your bios to boot sde first?

---

### Post by YesWeCan on 2011-09-07
Your RAID consists of 4 drives but only 2 are being shown by bootinfoscript. I think it should be showing sd[abcd] and sde and a dm device isw_dahgaaided_myraid.

Then it also reports that volume isw_dahgaaided_myraid2 ends beyond the last sector of the array. This is because the array is only half detected.

---

### Post by masho95 on 2011-09-07
> **YesWeCan said:**
> Hi there.
I haven't read your previous thread yet. Can you boot anything at the moment?

After a quick glance it seems to me what you want to end up with is Ubuntu and Grub on the 160GB sde drive and your Windows RAID10 to be totally untouched by linux. This way you can boot the RAID directly if you need to but you can boot either Ubuntu or Windows via Grub on sde.

So my first question is what happens when you tell your bios to boot sde first?

Correct, it's the way I had it set up before. The boot loader would give me the option to boot to Windows or Ubuntu on the sde drive. Telling BIOS to boot to the sde drive first will give me the GRUB2 loader and I can load Ubuntu fine. If I try booting to the RAID array that's when I'm left with the grub rescue> prompt. The boot script shows sda0, sda1, sdb0, and sdb1. Since it's in RAID 10 setup only 2 drives are technically used with the other two as mirrors for backup.

---

### Post by YesWeCan on 2011-09-07
> **masho95 said:**
> Since it's in RAID 10 setup only 2 drives are technically used with the other two as mirrors for backup.
Not really...all 4 drives are being used all the time and all four should be detected separately as well as the RAID device. It is only detecting 2 drives and a RAID device of 752GB instead of 2000GB.

I suspect a problem in your BIOS setup. If you boot into the BIOS do all 4 drives show as RAID enabled and members of a RAID10?

In Ubuntu you can list the individual dmraid devices using
[COLOR="DarkSlateBlue"]sudo dmraid -s[/COLOR]

---

### Post by masho95 on 2011-09-08
> **YesWeCan said:**
> Not really...all 4 drives are being used all the time and all four should be detected separately as well as the RAID device. It is only detecting 2 drives and a RAID device of 752GB instead of 2000GB.

I suspect a problem in your BIOS setup. If you boot into the BIOS do all 4 drives show as RAID enabled and members of a RAID10?

In Ubuntu you can list the individual dmraid devices using
[COLOR="DarkSlateBlue"]sudo dmraid -s[/COLOR]

Oops thought I responded to your post! I get this back from the dmraid command:

```
*** Group superset isw_dahgaaided
--> Active Superset
name   : isw_dahgaaided_myraid
size   : 2936013312
stride : 128
type   : raid01
status : ok
subsets: 2
devs   : 4
spares : 0

```

Looks like it is showing 4 devices.

---

### Post by YesWeCan on 2011-09-08
I see.
Would you post
sudo dmraid -b
sudo dmraid -r
I'm just reviewing the dmraid man page: [http://linuxmanpages.com/man8/dmraid.8.php](http://linuxmanpages.com/man8/dmraid.8.php)

---

### Post by masho95 on 2011-09-08
sudo dmraid -b
```
/dev/sde:    312581808 total, "WD-WMAV32240678"
/dev/sdd:   1953525168 total, "S246J9BZC08991"
/dev/sdc:   1953525168 total, "S246J9BZC08992"
/dev/sdb:   1953525168 total, "S246J9BZC08988"
/dev/dm-2:       204800 total, "N/A"
/dev/dm-1:   1468006656 total, "N/A"
/dev/dm-0:   1468006664 total, "N/A"
/dev/sda:   1953525168 total, "S246J9BZC08994"

```

sudo dmraid -r
```
/dev/sdd: isw, "isw_dahgaaided", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdc: isw, "isw_dahgaaided", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdb: isw, "isw_dahgaaided", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sda: isw, "isw_dahgaaided", GROUP, ok, 1953525166 sectors, data@ 0

```

---

### Post by YesWeCan on 2011-09-08
Well that all seems to look good. I don't understand why bootinfoscript didn't show two of the drives but I guess that's my problem. ;)

Try 
[COLOR="DarkSlateBlue"]sudo dmraid -ay[/COLOR]
to activate the array if it isn't already

Then see what
[COLOR="DarkSlateBlue"]sudo update-grub[/COLOR]
shows. See if it lists the Windows OS in the array. If it does then it has added it to its boot menu and you should be able to reboot and choose Windows.

---

### Post by masho95 on 2011-09-08
sudo update-grub

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

Is the output. It's not even seeing the Win 7 it seems.

---

### Post by YesWeCan on 2011-09-08
What output did dmraid -ay give?

You should try to fix the RAID using Windows. Boot using your Windows install CD, do a repair.
Perhaps consult a Windows forum if you get stuck.

---

### Post by masho95 on 2011-09-09
sudo dmraid -ay

```
RAID set "isw_dahgaaided_myraid" already active
RAID set "isw_dahgaaided_myraid1" already active
RAID set "isw_dahgaaided_myraid2" was not activated

```

I've messed with so many partition programs (Rescatux, Boot-Repair, TestDisk) that I think it's beyond saving. I was able to get to a Windows command prompt by using the repair option on the Windows 7 CD. From there I was able to access the raid drives and pull off all the info to my 1 TB USB drive for saving stuff in times just like this! I think it may just be easier to wipe the four 1 TB raid drives and start fresh, especially since I have all the files that I could possibly want to save. I think I'm going to mess with it for just a little bit longer before I do the wipe. Since I can access all my files it seems savable I'm just at a complete loss on how to do it.

---

### Post by masho95 on 2011-09-09
> **YesWeCan said:**
> You should try to fix the RAID using Windows. Boot using your Windows install CD, do a repair.
Perhaps consult a Windows forum if you get stuck.

I've already tried using the Windows install CD and it doesn't even see the Windows install on the hard drives. Maybe cause the RAID drivers aren't loaded?

At one point I had the Windows repair give me the following information:

```

Repair details:
The following startup option will be repaired:
Name: {bootmgr}
Identifier: {9DEA862C-5CDD-4E70-ACC1-F32B344D4795}

The following startup options will be added:
Name: Windows 7 Professional (recovered)
Path: Windows
Windows Device: Partition = D:(1433498 MB)

Name: Windows Recovery Environment (recovered)
Path: Recovery \0659142d-13a7-11e0-95c6-eb5729f2c691\Winre.wim
Windows Device: Partition = D:(1433498 MB)

A copy of the current boot configuration data will be saved as C:\Boot\BCD.Backup.0002

```

When I click OK I then get the problem System Recovery Options - (BIG RED X inside a circle) Failed to save startup options.

---

### Post by masho95 on 2011-09-09
Oh yay! I finally got my computer to boot into Windows 7. But now the GRUB bootloader is gone and I can't get into my Ubuntu install. It looks like everything is working the way it's supposed to in Win 7. The RAID array looks good and the files seem intact. It's showing 944 GB of 1.36 TB free which looks right. Now to get Ubuntu up and running again! I really wish Ubuntu could run all the same programs as Win 7 because IMO it's vastly superior. Soooo much faster which I love.

---

### Post by YesWeCan on 2011-09-09
Presumably you repaired it using your Windows CD?
So your bios is set to boot the RAID now.
To boot Ubuntu you'll have to tell the bios to boot the Ubuntu drive.

What you probably do not want to do is install Grub to the RAID again.
What you probably want is to add a menu stanza to the /etc/grub.d/40_custom that will chainload Windows on the RAID (run update-grub after any changes).

Unfortunately, after some Googling I haven't found an example of this. What I have found are several reports that the Grub OS-prober program is broken when it comes to detecting Windows RAIDs which may explain why update-grub failed.

It is potentially as simple as chainloading the MBR boot code of one of the RAID disks but I'm guessing.
```
menuentry "Windows 7" {
	recordfail
	set root='(hd0,0)'
	chainloader +1
}
```

Or it might be more complicated - something of this form (details might be garbage - I'm making it up):
```
menuentry "Windows 7" {
	recordfail
	insmod raid
	insmod mdraid
	insmod part_msdos
	insmod ntfs
        insmod dm_nv
	set root='(isw_dahgaaided_myraid1)'
	chainloader +1
}
```

You might want to start a fresh thread with title like "How can I use Grub to boot my Windows RAID?" to get more specific support.

---

### Post by YesWeCan on 2011-09-09
Alternatively, you may be able to boot Ubuntu using the Windows boot-loader. A free program EasyBCD will set this up.

---

