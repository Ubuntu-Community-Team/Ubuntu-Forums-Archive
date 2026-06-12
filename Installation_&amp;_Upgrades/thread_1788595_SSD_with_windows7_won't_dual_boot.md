---
title: "SSD with windows7 won't dual boot"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by mske on 2011-06-22
I built this computer with a Gigabyte motherboard, i3 processor, 8Gb ram, 64Gb SSD, and 1.5Tb HDD. Loaded Windows 7 to the SSD... repartitioned the drives and loaded Ubuntu 11.04.
The start menu comes up to select Windows 7 or Ubuntu... when I select Ubuntu I get a screen which reads:

Windows failed to start. A recent hardware or software change might be the cause. To Fix the problem:
1. Insert your windows installation disc and restart your computer.
2. Choose your language settings, and the click "Next"
3. Click "Repair your computer."

if you do not have this disc, contact your sys admin or manufacturer for assistance.

   File: \ubuntu\winboot\wubildr.mbr

   Status: 0xc0000098

   Info: The selected entry could not be loaded because the application is missing or corrupt.

****************

This screen continues to come up. I tried to load Ubuntu with Wubi but it would not install... I have now installed it from a DVD but the load screen keeps putting me back to the screen above. I can't load from the Windows CD it won't recognize it even if I change the bios setting.

Windows 7 seems to be running fine... and Ubuntu seems to have loaded fine... so how can I get my Windows boot screen to go and load Ubuntu as my OS?

Help!

---

### Post by oldfred on 2011-06-23
I do not know wubi. But those that do will need you to run the boot script from a Ubuntu liveCD. If you installed directly in windows download Ubuntu and install to a liveCD or USB. Then you can run this script from the liveCD or liveUSB.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Wubi is a version that installs inside the windows NTFS partition and uses the windows boot loader to boot. It is intended primarily for windows users who want an extended trial of Ubuntu without partitioning.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
how to fix those Wubi installation breakages without going crazy Rubi1200 Dec 2010
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by mske on 2011-06-23
reposting boot script below with correct formating

---

### Post by srs5694 on 2011-06-23
It looks as if you're using a UEFI-based system, although I'm not 100% sure of that -- there are some inconsistencies in the results of the Boot Info Script. (These could be the result of disks being re-used from an earlier non-UEFI installation, though.) UEFI changes a lot of the ground rules for booting and dual-booting a computer. Most importantly, you need to use different boot loaders than you'd use on a BIOS-based computer. AFAIK, the Windows BCD tool can't redirect the boot process to another EFI boot loader, so you can't use it to boot Linux. Instead, you're doing to have to use your firmware's boot options to locate a Linux boot loader. If Ubuntu installed the way it should have, you should be able to find an Ubuntu UEFI boot loader, probably in the EFI/ubuntu directory on the EFI System Partition (ESP) -- /dev/sda1. When you tell the firmware to boot it, you should be able to get into Ubuntu, and perhaps redirect to Windows, too. Unfortunately, Ubuntu's UEFI support is still pretty bleeding-edge, and it doesn't work correctly for everybody, so you may need to make some significant changes.

Be aware that the Boot Info Script provides little in the way of UEFI diagnostics, although some of the data it provides are useful for both BIOS and UEFI systems. Manually looking for files in the ESP (/dev/sda1) can provide useful information. In particular, look for what subdirectories exist in the EFI directory of that partition, and what files with .efi extensions exist in each of those directories. Those .efi files are your installed UEFI boot loaders.

Finally, please follow oldfred's request and use [noparse]```
[/noparse] and [noparse]
```[/noparse] tags when posting text-mode program output in the future. Your Boot Info Script output is much harder to read without that, and I for one am not going to look for the sorts of details in the reformatted text that results when those tags are omitted.

---

### Post by oldfred on 2011-06-23
It seems wubi requires windows to be booting from the MBR. Or it does not work with UEFI for now.

[https://bugs.launchpad.net/wubi/+bug/694242](https://bugs.launchpad.net/wubi/+bug/694242)

---

### Post by mske on 2011-06-24
reposted  with correct format
 
```

Boot Info Script 0.60 from 17 May 2011
 
 
============================= Boot Info Summary: ===============================
 
=> Windows is installed in the MBR of /dev/sda.
=> Windows is installed in the MBR of /dev/sdb.
 
sda1: __________________________________________________________________________
 
File system: vfat
Boot sector type: Unknown
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: 
 
sda2: __________________________________________________________________________
 
File system: 
Boot sector type: -
Boot sector info: 
Mounting failed: mount: unknown filesystem type ''
 
sda3: __________________________________________________________________________
 
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe /wubildr 
/ubuntu/winboot/wubildr /wubildr.mbr 
/ubuntu/winboot/wubildr.mbr
 
sda4: __________________________________________________________________________
 
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 11.04
Boot files: /boot/grub/grub.cfg /etc/fstab
 
sda5: __________________________________________________________________________
 
File system: swap
Boot sector type: -
Boot sector info: 
 
sdb1: __________________________________________________________________________
 
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: 
 
sdb2: __________________________________________________________________________
 
File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files: 
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot Start Sector End Sector # of Sectors Id System
 
/dev/sda1 1 117,231,407 117,231,407 ee GPT
 
 
GUID Partition Table detected.
 
Partition Start Sector End Sector # of Sectors System
/dev/sda1 2,048 206,847 204,800 EFI System partition
/dev/sda2 206,848 468,991 262,144 Microsoft Reserved Partition (Windows)
/dev/sda3 468,992 65,357,823 64,888,832 Data partition (Windows/Linux)
/dev/sda4 65,357,824 81,750,015 16,392,192 Data partition (Windows/Linux)
/dev/sda5 81,750,016 89,980,927 8,230,912 Swap partition (Linux)
 
Drive: sdb _____________________________________________________________________
 
Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot Start Sector End Sector # of Sectors Id System
 
/dev/sdb1 2,048 1,471,385,599 1,471,383,552 7 NTFS / exFAT / HPFS
/dev/sdb2 1,471,385,600 1,882,791,935 411,406,336 83 Linux
 
 
"blkid" output: ________________________________________________________________
 
Device UUID TYPE LABEL
 
/dev/loop0 squashfs 
/dev/sda1 36A8-49FC vfat 
/dev/sda3 4EC0B92DC0B91BE1 ntfs 
/dev/sda4 97224a7b-745f-47c3-a4cc-5e7cfdcb2485 ext4 /
/dev/sda5 e99909d9-3468-43ab-87a6-1cc4fc57e3d6 swap 
/dev/sdb1 4C78809A78808484 ntfs Samsung 1.5Tb
/dev/sdb2 4bebe03f-fa5c-48d1-93b2-f826c9951bc9 ext4 /home
 
================================ Mount points: =================================
 
Device Mount_Point Type Options
 
/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sr0 /cdrom iso9660 (ro,noatime)
 
 
=========================== sda4/boot/grub/grub.cfg: ===========================
 
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
insmod efi_gop
insmod efi_uga
insmod video_bochs
insmod video_cirrus
}
 
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt4)'
search --no-floppy --fs-uuid --set=root 97224a7b-745f-47c3-a4cc-5e7cfdcb2485
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt4)'
search --no-floppy --fs-uuid --set=root 97224a7b-745f-47c3-a4cc-5e7cfdcb2485
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
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt4)'
search --no-floppy --fs-uuid --set=root 97224a7b-745f-47c3-a4cc-5e7cfdcb2485
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=97224a7b-745f-47c3-a4cc-5e7cfdcb2485 ro quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt4)'
search --no-floppy --fs-uuid --set=root 97224a7b-745f-47c3-a4cc-5e7cfdcb2485
echo 'Loading Linux 2.6.38-8-generic ...'
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=97224a7b-745f-47c3-a4cc-5e7cfdcb2485 ro single 
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt4)'
search --no-floppy --fs-uuid --set=root 97224a7b-745f-47c3-a4cc-5e7cfdcb2485
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt4)'
search --no-floppy --fs-uuid --set=root 97224a7b-745f-47c3-a4cc-5e7cfdcb2485
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
 
### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------
 
=============================== sda4/etc/fstab: ================================
 
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda4 during installation
UUID=97224a7b-745f-47c3-a4cc-5e7cfdcb2485 / ext4 errors=remount-ro 0 1
# /home was on /dev/sdb2 during installation
UUID=4bebe03f-fa5c-48d1-93b2-f826c9951bc9 /home ext4 defaults 0 2
# swap was on /dev/sda5 during installation
UUID=e99909d9-3468-43ab-87a6-1cc4fc57e3d6 none swap sw 0 0
--------------------------------------------------------------------------------
 
=================== sda4: Location of files loaded by Grub: ====================
 
GiB - GB File Fragment(s)
 
31.450332642 = 33.769537536 boot/grub/grub.cfg 1
32.296379089 = 34.677972992 boot/initrd.img-2.6.38-8-generic 2
31.895816803 = 34.247872512 boot/vmlinuz-2.6.38-8-generic 1
32.296379089 = 34.677972992 initrd.img 2
31.895816803 = 34.247872512 vmlinuz 1
 
======================== Unknown MBRs/Boot Sectors/etc: ========================
 
Unknown BootLoader on sda1
 
00000000 eb 58 90 4d 53 44 4f 53 35 2e 30 00 02 02 fe 19 |.X.MSDOS5.0.....|
00000010 02 00 00 00 00 f8 00 00 3f 00 ff 00 00 08 00 00 |........?.......|
00000020 00 20 03 00 01 03 00 00 00 00 00 00 02 00 00 00 |. ..............|
00000030 01 00 06 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00000040 80 00 29 fc 49 a8 36 4e 4f 20 4e 41 4d 45 20 20 |..).I.6NO NAME |
00000050 20 20 46 41 54 33 32 20 20 20 33 c9 8e d1 bc f4 | FAT32 3.....|
00000060 7b 8e c1 8e d9 bd 00 7c 88 4e 02 8a 56 40 b4 41 |{......|.N..V@.A|
00000070 bb aa 55 cd 13 72 10 81 fb 55 aa 75 0a f6 c1 01 |..U..r...U.u....|
00000080 74 05 fe 46 02 eb 2d 8a 56 40 b4 08 cd 13 73 05 |t..F..-.V@....s.|
00000090 b9 ff ff 8a f1 66 0f b6 c6 40 66 0f b6 d1 80 e2 |.....f...@f.....|
000000a0 3f f7 e2 86 cd c0 ed 06 41 66 0f b7 c9 66 f7 e1 |?.......Af...f..|
000000b0 66 89 46 f8 83 7e 16 00 75 38 83 7e 2a 00 77 32 |f.F..~..u8.~*.w2|
000000c0 66 8b 46 1c 66 83 c0 0c bb 00 80 b9 01 00 e8 2b |f.F.f..........+|
000000d0 00 e9 2c 03 a0 fa 7d b4 7d 8b f0 ac 84 c0 74 17 |..,...}.}.....t.|
000000e0 3c ff 74 09 b4 0e bb 07 00 cd 10 eb ee a0 fb 7d |<.t............}|
000000f0 eb e5 a0 f9 7d eb e0 98 cd 16 cd 19 66 60 80 7e |....}.......f`.~|
00000100 02 00 0f 84 20 00 66 6a 00 66 50 06 53 66 68 10 |.... .fj.fP.Sfh.|
00000110 00 01 00 b4 42 8a 56 40 8b f4 cd 13 66 58 66 58 |....B.V@....fXfX|
00000120 66 58 66 58 eb 33 66 3b 46 f8 72 03 f9 eb 2a 66 |fXfX.3f;F.r...*f|
00000130 33 d2 66 0f b7 4e 18 66 f7 f1 fe c2 8a ca 66 8b |3.f..N.f......f.|
00000140 d0 66 c1 ea 10 f7 76 1a 86 d6 8a 56 40 8a e8 c0 |.f....v....V@...|
00000150 e4 06 0a cc b8 01 02 cd 13 66 61 0f 82 75 ff 81 |.........fa..u..|
00000160 c3 00 02 66 40 49 75 94 c3 42 4f 4f 54 4d 47 52 |...f@Iu..BOOTMGR|
00000170 20 20 20 20 00 00 00 00 00 00 00 00 00 00 00 00 | ............|
00000180 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
000001a0 00 00 00 00 00 00 00 00 00 00 00 00 0d 0a 52 65 |..............Re|
000001b0 6d 6f 76 65 20 64 69 73 6b 73 20 6f 72 20 6f 74 |move disks or ot|
000001c0 68 65 72 20 6d 65 64 69 61 2e ff 0d 0a 44 69 73 |her media....Dis|
000001d0 6b 20 65 72 72 6f 72 ff 0d 0a 50 72 65 73 73 20 |k error...Press |
000001e0 61 6e 79 20 6b 65 79 20 74 6f 20 72 65 73 74 61 |any key to resta|
000001f0 72 74 0d 0a 00 00 00 00 00 ac cb d8 00 00 55 aa |rt............U.|
00000200

```

---

### Post by mske on 2011-06-24
Okay... So since I tried to install Ubuntu with Wubi it setup a boot that is not compatible with my UEFI-based mother board. It looks like since I'm on a new system the quickest way for me to resolve this is to back out and start over again. I mean reformat my drives and re-install Windows and reload Ubuntu only this time from my DVD.
 
My focus in this project is to have a computer that can run either Windows 7 or Ubuntu OS's and load them quickly from my SSD. A friend gave me the following article, although it is written for Ubuntu-9.10 I think it should work for the 11.04 release:
[[COLOR=#0000cc]http://m.lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony[/COLOR]]("http://m.lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")

Can you tell me if there are any changes I should be looking at for the disk partitions?
 
Will I run into the same problem with the dual-boot if I do the DVD install?
 
Does the DVD install I downloaded (11.04, 64bit, ISO) automatically install the Grub utility for selecting an OS on the startup?
 
Thanks for all your help!

---

### Post by oldfred on 2011-06-24
Are you planning on staying with UEFI or change to BIOS? UEFI can work but has some issues with grub. srs5694 has posted specific advice for dual booting windows and Linux in several threads. 

Windows 7 will only boot gpt partitioning with UEFI. Ubuntu will work with MBR or gpt partitioning and with BIOS. Grub seems to install to UEFI on its own but has issues with dual booting where you have to manually change settings and files. around.

SSDs are a lot different than rotating drives, UEFI & BIOS, MBR and gpt are all issues that your link does not discuss. Only the general dual boot is probably ok. I would not use that link for your install now, too many things have changed.

A lot of these are to comments by srs5964 as he has done UEFI install. I assume he will be back to comment but read some of these recommendations so you can ask specific questions for your install. He will also have updates as his recommendations are for each user.

grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)
How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
Updates to second post below:
[http://ubuntuforums.org/showthread.php?t=1772310](http://ubuntuforums.org/showthread.php?t=1772310)
UEFI issues srs5694 post #58
[http://ubuntuforums.org/showthread.php?t=1719851&page=6](http://ubuntuforums.org/showthread.php?t=1719851&page=6)
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
Has chainload window efi grub entry:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Windows 7 64bit UEFI 2.x boot:
[http://www.insanelymac.com/forum/index.php?showtopic=186440](http://www.insanelymac.com/forum/index.php?showtopic=186440)
Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
[http://ubuntuforums.org/showthread.php?t=1746194](http://ubuntuforums.org/showthread.php?t=1746194)
Many links & discussion:
[http://ubuntuforums.org/showthread.php?t=1734677](http://ubuntuforums.org/showthread.php?t=1734677)

MaverickUefiSupport - Cd may not work, need USB 
[https://wiki.ubuntu.com/FoundationsTeam/Specs/MaverickUefiSupport](https://wiki.ubuntu.com/FoundationsTeam/Specs/MaverickUefiSupport)

---

### Post by mske on 2011-06-24
Thanks oldfred and srs5694... It will take me a while to go through all of this info and learn enough to ask some moderately intellegent questions. While I have been a computer user for years, both on Windows and Linux, I never really got into much on modifying boot scripts. 
 
I guess my next step is to look into the Ubuntu UEFI boot loader... Before I start over. I'll read more and look into that this weekend.
 
Learning more than I thought I would need too!

---

### Post by srs5694 on 2011-06-24
UEFI is definitely a different kettle of fish than BIOS. Theoretically and in the long run, UEFI has advantages over BIOS, particularly in a dual-boot environment:


[list]
[*]Windows can (and must!) boot from GPT on UEFI-based computers, but cannot boot from GPT on BIOS-based computers. This is significant because GPT has advantages over the older MBR partitioning scheme, including the ability to work with over-2TiB disks and elimination of the distinction between primary, extended, and logical partitions.
[*]UEFI does not rely on boot code in the hard disk's first sector (aka the MBR). This makes it much more robust against problems caused by one OS trashing another OS's boot loader.
[*]UEFI has a built-in boot loader, although it can only "boot" EFI applications, which must then load the OS kernel, so you still need OS-specific boot loaders. If your firmware is well designed, the built-in boot loader should be all you need to select your OS. I'm not sure how good most boards' UEFI user interfaces are, though; the ones I've seen haven't been stellar, but I've not seen the latest boards with flashy GUI interfaces.
[*]UEFI boot loaders reside in a FAT filesystem, which can (in theory) be easily modified from any OS or even from the firmware itself. This can make recovery from problems and installation of new boot loaders a snap.
[/list]


Unfortunately, most Linux distributions have UEFI support that ranges from abysmal to middling. The variety of and default configuration for the GRUB 2 that Ubuntu uses is pretty dreadful, in my experience; it works tolerably in some cases, but in others it leaves you with no console (text-mode login) or fails to boot the OS at all. I've had much better luck with [ELILO,](http://elilo.sourceforge.net/cgi-bin/blosxom) but installing it will take some effort. Also, ELILO can't chainload to another EFI boot loader, so you'll need to either rely on your firmware's boot selector or another boot loader, such as [rEFIt,](http://refit.sourceforge.net) to select a boot OS. Also, unforgivably, Ubuntu's installer *erases* the EFI System Partition (ESP), which is where EFI boot loaders live. Thus, if you install Windows and then install Ubuntu, you'll lose the ability to boot Windows. Somebody screwed up very badly on that one! (Recovery is possible, but it's another hoop to jump through. The easiest solution is to back up the ESP before you install Ubuntu, then restore it later. It's only a few MiB in size, so it won't strain your storage capacity, but it's a hassle you shouldn't have to deal with.) If you install Ubuntu first, it's likely to use FAT16 on the ESP, but Windows wants to see FAT32 there, so Windows gets confused and can't be installed. (The workaround is to back up the ESP, put a fresh FAT32 filesystem on it, and restore it.)

If your board supports it, booting in BIOS mode is the easier solution in the short term, since it's well-supported right now. This has drawbacks, though; you'll be limited by MBR issues in a dual-boot environment, and if and when UEFI support improves, you may be missing out on some features that could materialize in the future.

I'm starting to think that the best compromise may be to install Windows in UEFI mode, switch the firmware to BIOS mode, install Ubuntu, install ELILO (and rEFIt, if you like), and switch back to UEFI mode. You can then boot both Windows and Ubuntu in UEFI mode.

---

### Post by SantaP on 2012-09-21
Is there any way to install ubuntu desctop 64bit (say 12.04) on SSD in window 7 home prem 64bit? I have the same problem trying to install with Wubi. I have Asus XU31a with UEFI.

---

### Post by oldfred on 2012-09-21
I do not follow wubi, but I do not think it works with UEFI as it has to use the Windows boot loader to work and with UEFI the Windows boot loader is different.

Another alternative is just to put a full install into a USB flash drive. Since flash is somewhat slower especially compared to a SSD, you may want the lighter weight Lubuntu just so it does not load as much data. I do have full install of Ubuntu in a 8GB partition on my 16GB flash. A bit slow but functional.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

Also with UEFI and Windows you have to have gpt partitioning. Then it is not all that difficult to create a 10 to 25GB partition and install the 64bit version in UEFI mode.

---

