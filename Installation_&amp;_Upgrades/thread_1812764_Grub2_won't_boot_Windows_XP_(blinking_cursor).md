---
title: "Grub2 won't boot Windows XP (blinking cursor)"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by Matalius on 2011-07-26
Hey everyone.

I've done a lot of reading on this site and others, and can't seem to fix this problem. 

I originally had Ubuntu 10.04 installed on my netbook, and one day when I tried to boot it, it failed and gave an error message, something along the lines of "Unable to mount /dev/" and some other mounting errors; basically it couldn't find Ubuntu. I ignored this, and kept using XP, since I wasn't really using Ubuntu anyway. Finally, a couple days ago, I decided I'd reinstall Ubuntu to fix it. 

Before installing, I made a stupid mistake: I ran my recovery partition because I wasn't sure what it was (it was labeled Windows 2000/NT/XP). It wiped GRUB, and I couldn't boot into anything. So to fix it, I ran Ubuntu 11.04 from USB, wiped the old Ubuntu 10.04 partitions, and installed Ubuntu 11.04. It worked great, and I'm posting from it now.

However, even though GRUB sees Windows XP, I can't boot it. When I try, it gives me a blinking cursor, which will stay there until I turn the computer off. I can mount the partition in Ubuntu, and everything is still there, if that helps.

Here's the BootInfoScript:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   184,944,309   184,944,247   7 NTFS / exFAT / HPFS
/dev/sda2         302,246,910   312,496,379    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4         184,944,638   302,245,887   117,301,250   5 Extended
/dev/sda5         184,944,640   292,366,335   107,421,696  83 Linux
/dev/sda6         292,368,384   302,245,887     9,877,504  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1068E9EE68E9D310                       ntfs       
/dev/sda2        CCED-990E                              vfat       PE
/dev/sda5        387bedb7-61a0-46a7-b6ab-5c1e1e9cce10   ext4       
/dev/sda6        4d2aabde-5bbf-43cd-aa97-d4adbdbc10a7   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=600)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
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
search --no-floppy --fs-uuid --set=root 387bedb7-61a0-46a7-b6ab-5c1e1e9cce10
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 387bedb7-61a0-46a7-b6ab-5c1e1e9cce10
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 387bedb7-61a0-46a7-b6ab-5c1e1e9cce10
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=387bedb7-61a0-46a7-b6ab-5c1e1e9cce10 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 387bedb7-61a0-46a7-b6ab-5c1e1e9cce10
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=387bedb7-61a0-46a7-b6ab-5c1e1e9cce10 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 387bedb7-61a0-46a7-b6ab-5c1e1e9cce10
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=387bedb7-61a0-46a7-b6ab-5c1e1e9cce10 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 387bedb7-61a0-46a7-b6ab-5c1e1e9cce10
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=387bedb7-61a0-46a7-b6ab-5c1e1e9cce10 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
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
	search --no-floppy --fs-uuid --set=root 387bedb7-61a0-46a7-b6ab-5c1e1e9cce10
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 387bedb7-61a0-46a7-b6ab-5c1e1e9cce10
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 1068E9EE68E9D310
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root cced-990e
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
UUID=387bedb7-61a0-46a7-b6ab-5c1e1e9cce10 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4d2aabde-5bbf-43cd-aa97-d4adbdbc10a7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 128.322509766 = 137.785245696  boot/grub/core.img                             1
 100.618907928 = 108.038729728  boot/grub/grub.cfg                             1
 106.637950897 = 114.501627904  boot/initrd.img-2.6.38-10-generic              1
  89.356666565 = 95.945990144   boot/initrd.img-2.6.38-8-generic               1
  88.989566803 = 95.551819776   boot/vmlinuz-2.6.38-10-generic                 1
 128.320781708 = 137.783390208  boot/vmlinuz-2.6.38-8-generic                  1
 106.637950897 = 114.501627904  initrd.img                                     1
  89.356666565 = 95.945990144   initrd.img.old                                 1
  88.989566803 = 95.551819776   vmlinuz                                        1
 128.320781708 = 137.783390208  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  cd d5 71 48 03 dd 66 89  ba 2b 17 db 65 f0 30 32  |..qH..f..+..e.02|
00000010  38 69 e2 43 a9 ea e5 ea  eb 22 96 17 ef 00 79 8e  |8i.C....."....y.|
00000020  a0 05 1e 3f a9 40 59 ef  c4 97 c0 d5 17 59 80 ef  |...?.@Y......Y..|
00000030  01 76 af 37 64 df 9c dc  80 ed 81 59 1a 17 00 21  |.v.7d......Y...!|
00000040  51 a8 9a 8b 0d 6c 90 bc  16 a0 ff 1b 19 69 17 7e  |Q....l.......i.~|
00000050  c3 25 41 6e ed 4a 68 89  1d 3b a6 0b 20 1a 28 17  |.%An.Jh..;.. .(.|
00000060  3f 90 e1 f1 5c 7d 09 00  09 59 12 dd 49 d4 f8 50  |?...\}...Y..I..P|
00000070  17 c3 a8 e4 1b 3b 23 91  d2 bd 1a 87 70 19 1e ca  |.....;#.....p...|
00000080  ff 17 f1 35 d0 06 1e d4  da e1 67 67 0e a4 79 f2  |...5......gg..y.|
00000090  b2 2f 17 5b d4 85 7a 81  08 f3 e9 96 c3 d6 d2 84  |./.[..z.........|
000000a0  9f 05 de 17 26 9c 4a 53  3a 63 51 60 99 ba 31 5a  |....&.JS:cQ`..1Z|
000000b0  38 6a 44 9e 17 fe 1b 22  02 3b b5 f5 1f 0d e9 09  |8jD....".;......|
000000c0  1c 6b bb e0 32 17 11 e2  a3 2a 02 d2 b6 fb 54 71  |.k..2....*....Tq|
000000d0  a8 dd 08 46 66 43 17 d0  44 cb 08 16 cb 6e 67 59  |...FfC..D....ngY|
000000e0  f2 f6 a3 5c 88 bf 19 17  fd 51 f3 70 4a 86 f7 20  |...\.....Q.pJ.. |
000000f0  3a e9 53 a5 44 46 8a c3  17 b3 95 8d b6 c2 78 c6  |:.S.DF........x.|
00000100  33 41 bb 5a bd 95 5e 9b  64 17 b6 59 c5 b3 a5 8b  |3A.Z..^.d..Y....|
00000110  fe 2f 71 69 f2 a9 79 b5  dd a7 17 c3 0f 1c 92 a5  |./qi..y.........|
00000120  e1 05 b1 58 48 32 ff 65  bb bf 9f 17 65 16 84 7f  |...XH2.e....e...|
00000130  ed 72 3d e6 c3 5c ad 9f  01 a7 d5 7f 17 b2 83 88  |.r=..\..........|
00000140  5c 73 0d 62 0b e6 5b c0  70 cc b0 93 5a 17 08 83  |\s.b..[.p...Z...|
00000150  00 27 d1 ae 57 a3 43 92  3d c2 a2 be 2b 01 17 da  |.'..W.C.=...+...|
00000160  62 00 b3 b2 fa 17 80 aa  da 5f d6 12 89 d7 ad 17  |b........_......|
00000170  4d c5 31 91 fa c9 b2 80  fb db 0f 29 57 2a 1c 28  |M.1........)W*.(|
00000180  17 0f f0 77 63 cd 2c 1b  83 45 fa 1f f1 a6 5e 3f  |...wc.,..E....^?|
00000190  ae 17 0e 66 03 a9 72 ac  f6 76 a3 ca 7b 04 a5 1c  |...f..r..v..{...|
000001a0  ca 6b 17 f5 81 94 9b 9e  01 30 70 be e8 8c 2c fb  |.k.......0p...,.|
000001b0  03 2e 98 17 28 1e 62 4f  0b 42 3a 57 9e 36 00 fe  |....(.bO.B:W.6..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 67 06 00 fe  |........... g...|
000001d0  ff ff 05 fe ff ff 59 22  67 06 a9 bd 96 00 00 00  |......Y"g.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

I tried using testdisk, and backing up the boot sector, as advised by another site, but the boot sector and backup were identical. 

So, can anyone please help? Thanks in advance.

PS. Does anyone know what the heck sda3 is? I seem to recall it being like 4 MB partition when I was installing Ubuntu. I didn't delete it for fear of it being important.

---

### Post by oldfred on 2011-07-26
The boot script is showing the normal XP boot files and normal  NTFS partition. But if you started to run recovery, did you let it complete or else it may have only copied part of XP back into its partition.

Sometimes running windows repairs fixes things, even when they look ok but do not work. Testdisk which you have done is one of the first things to try. 

The efi partition is for newer UEFI boot systems that are replacing the 25 year old BIOS system. It may have boot or other system files for your system if using UEFI.  But window XP only works with BIOS & MBR partitioning. UEFI requires gpt partitions. Apple Macs use an early version of EFI and gpt and create a partial MBR so windows will work. 

You may just need to run chkdsk. But these all all the common commands to repair XP:

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

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\.

---

### Post by Luke M on 2011-07-26
Are you sure that this XP installation works? You can try a different boot loader (e.g. plop boot manager), or re-install the Windows MBR to test.

---

### Post by Matalius on 2011-07-26
Thanks for the replies. I'm actually not sure if this XP installation works. I know it *used* to work, before I booted the recovery partition.

I actually didn't let the recovery do anything. When I booted it, it gave me a popup saying "Are you sure you want to do this? All partitions and data will be deleted." and I clicked "No." and exited. I haven't booted into Windows since. 

I think the only way I could boot into Windows is using my recovery dvd that came with the computer, but I don't have an external drive (damn netbooks). Unless you know a way to create a bootable USB drive from it?

Edit: Forgot to mention that I don't know how to repair the Windows MBR except for using the recovery dvd. Is there a way to do it within Ubuntu or using a live USB?

---

### Post by srs5694 on 2011-07-26
> **oldfred said:**
> The efi partition is for newer UEFI boot systems that are replacing the 25 year old BIOS system. It may have boot or other system files for your system if using UEFI.  But window XP only works with BIOS & MBR partitioning. UEFI requires gpt partitions.

A small correction: UEFI does *not* require GPT; it can work just fine with MBR. *Windows* under UEFI, though, *does* require GPT, so the two are often linked. This isn't really relevant to Matalius's problem, though, unless perhaps the EFI System Partition (ESP) on the disk has the wrong type code or is otherwise somehow relevant to the problem. I don't see any evidence of that, though. FWIW, I've heard of ESPs being present on netbooks before with no obvious reason. My suspicion is that they exist to support models other than the ones in which they're installed; that is, it's easier to just partition all the disks in one way at the factory, even though not every model uses every partition. That's just a suspicion, though.

[quote=Matalius]I think the only way I could boot into Windows is using my recovery dvd  that came with the computer, but I don't have an external drive (damn  netbooks). Unless you know a way to create a bootable USB drive from it?[/quote]

I've heard of tools to do this, and a Google turned up [this page](http://downloadsquad.switched.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/) and [this one,](http://www.techrepublic.com/article/solutionbase-boot-windows-xp-from-a-usb-flash-drive/5928902) among many others. Caveat: I've not tried the tools and techniques described on those pages; I'm just passing on a couple of results from my Web search, which was on the phrase "create bootable USB from Windows XP CD". Try your own Web search if you want more options.

---

### Post by oldfred on 2011-07-26
A couple of more links.

Copy Windows XP to usb
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)

You can install a windows boot loader from Ubuntu and most Linux repair Cds. But if grub is not booting windows installing the windows boot loader will not make any difference (grub just jumps to the PBR the same way the win boot loader does). And then you have to reinstall grub2's bootloader to boot again.

---

### Post by Matalius on 2011-07-27
> 
I've heard of tools to do this, and a Google turned up [this page](http://downloadsquad.switched.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/) and [this one,](http://www.techrepublic.com/article/solutionbase-boot-windows-xp-from-http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=20&m=Eee%20PC%201005HA&s=1&hashedid=9w41pJa96C4YVicF&os=8&no=1718a-usb-flash-drive/5928902) among many others. Caveat: I've not tried the tools and techniques described on those pages; I'm just passing on a couple of results from my Web search, which was on the phrase "create bootable USB from Windows XP CD". Try your own Web search if you want more options.

Thanks for this, but apparently my support dvd works the same way my recovery partition works: it will only wipe the hard drive (dvd also gives me the option to wipe a partition only) and restore to factory settings. So.. I'm kind of at a loss. I'm not sure how I can fix the MBR anymore.

---

### Post by srs5694 on 2011-07-27
Try searching for either emergency Windows XP recovery discs or regular retail discs online. IIRC, there are sites that offer recovery discs that are perfectly legal (Microsoft wants you to be able to do this sort of repair, after all!), although I'm not sure about retail installation discs (I've seen supposedly legal images of Windows 7 available, but not of XP). Something a friend or neighbor has will do fine, too.

---

### Post by Matalius on 2011-07-27
Ok, thanks. I think my father has an XP Pro disc somewhere. Can I use an XP Pro disc to repair XP Home?

---

### Post by srs5694 on 2011-07-27
> **Matalius said:**
> Ok, thanks. I think my father has an XP Pro disc somewhere. Can I use an XP Pro disc to repair XP Home?

I'm not sure. The more recent versions tend to be fussy about that, although you might be able to do something simple with it, or Microsoft might have been less strict with XP. It's worth a try....

---

### Post by Matalius on 2011-07-27
> **srs5694 said:**
> I'm not sure. The more recent versions tend to be fussy about that, although you might be able to do something simple with it, or Microsoft might have been less strict with XP. It's worth a try....

Alright, I'll give it a try. Thanks for all the help guys, I really appreciate it. I'll post again on how the attempt goes, but it'll probably be a couple days.

---

### Post by steve11911 on 2011-07-28
I have not had occasion (knock on wood) to try this tool:
Rescatux features:

    Fixes GRUB and GRUB2
    Regenerates Debian/Ubuntu grub menues
    Check and fix filesystems
    Fixes Windows MBR

[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

==========
sda 3 MAY be a small partition of mfgrs tools.I recently worked on an XP Dell machine with a FAT32 backup partition and a small FAT16 tools partition...about 4GB I think...

Since you can access the data from the XP install I would backup everything important before proceeding.

---

### Post by Matalius on 2011-07-29
> **steve11911 said:**
> I have not had occasion (knock on wood) to try this tool:
Rescatux features:

    Fixes GRUB and GRUB2
    Regenerates Debian/Ubuntu grub menues
    Check and fix filesystems
    Fixes Windows MBR

[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

==========
sda 3 MAY be a small partition of mfgrs tools.I recently worked on an XP Dell machine with a FAT32 backup partition and a small FAT16 tools partition...about 4GB I think...

Since you can access the data from the XP install I would backup everything important before proceeding.

Ooh, thanks. I will try this tonight. The Windows MBR portion is in beta right now, but I don't have much to lose anyway. If it breaks something, I'll just use the recovery partition. Good thing I can still access my Windows partition in Ubuntu.

---

### Post by Matalius on 2011-07-29
Alright, so I tried that Rescatux tool, and.. nothing. When I booted after I "restored" the Windows MBR, it said "MBR" in the corner and had a blinking cursor on the next line. 

When I used Rescatux it asked me what position the hard drive was. Wasn't sure what that meant, so I picked 1. After it failed to boot Windows, I tried again in position 2, and it said "MBR:1" with a blinking cursor instead. 

Rescatux works great in restoring GRUB though. 

I guess the next step is to use an external dvd drive and a Windows CD to get to the recovery console. Planning on doing that tonight.

---

