---
title: "Issues w/ 11.10 and 10.10; boot repair doesn't work"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by melkins on 2012-01-31
I've recently tried to install Ubuntu along side my Windows Vista Ultimate x86 OS. I tried both of 11.10 and 10(?) and both could not install the boot loader. It would not let me select any of the dva/xxx options. I also had the same issue with the Mint OS.

So, I re-installed 11.10 and following the directions I found, downloaded and installed boot repair. The first time I tried, boot repair never got past the "scanning system...this will take a few minutes" dialog. I closed it, tried again and the same thing happened. I restarted the computer and tried again. This time it worked; the boot repair screen came up and I selected Recommended Repairs. After some time it stated that the issues was fixed. I restarted the computer and the screen to choose OSs came up. I chose Ubuntu and.... blinking cursor for as long as I'm willing to wait. I hit esc. A screen comes up that I think says it's cancelling processes. Then it hangs up. If I hit the enter key the Ubuntu screen comes up like it's loading, but it never does. It goes through this same thing if I choose the Ubuntu Recover option as well.

I've tried going back with the Live CD again and trying boot repair again, but it keeps getting stuck on the 'scanning system' thing again.

Is my computer allergic to Linux, or what?!?! I haven't found anything with anyone having the same issues except with the grub thing. Any ideas? Thanks for any suggestions.
Matt
System:
AMD 64x2 5200
ASUS M2NBP-VM CSM
ZOTAC ZT-84GED2M-HSL GeForce 8400 GS
I'm blanking on the HDDs; they're older; SATA 1.5GB type

---

### Post by bogan on 2012-01-31
Hi!, **melkins**.

You Posted:>  I'm blanking on the HDDs; they're older; SATA 1.5GB type[I]If that is not a typo, please tell us how well Windows Vista Ultimate runs from a 1.5GB hard drive.

[/I]Chao!, **bogan**[I].
[/I]

---

### Post by melkins on 2012-01-31
[QUOTE=bogan;11654672]Hi!, **melkins**.

You Posted:[I]If that is not a typo, please tell us how well Windows Vista Ultimate runs from a 1.5GB hard drive.

I've had no problems or errors with the drives or running Vista.

---

### Post by darkod on 2012-01-31
The hard driveS??? More than one? You are not running raid are you?

---

### Post by melkins on 2012-01-31
No, I'm not running RAID. One drive is for the OS and programs and the other is for music files. In one of my installation attempts, I did try to load it on the other drive; I had the same result.

---

### Post by Quackers on 2012-01-31
Have you tried the nomodeset boot option?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by darkod on 2012-01-31
The blinking cursor might be video driver issue, but that doesn't explain not installing the bootloader (grub). Sometimes grub fails installing on fakeraid but people keep trying to install with the standard cd and not the alternate one.
But on a single drive the grub install rarely fails.

If grub installs but ubuntu doesn't boot correctly, that's another matter. The first thing to try with nvidia card would be to try the nomodeset boot parameter as suggested above.

---

### Post by melkins on 2012-01-31
I haven't tried the nomodeset boot option. I'll read up on it and try it when I get home. Thanks.

---

### Post by darkod on 2012-02-01
If you still don't get anywhere, follow the link in my signature to run the boot info script and post the results here. It's explained in the link.
It will show more details about your system and boot process.

---

### Post by melkins on 2012-02-01
Well, things got more interesting. I tried the nomodeset to no avail. When I ran the code, it said it couldn't find the device. I went back in to Windows and couldn't find Ubuntu anywhere. I thought it had installed, but I guess something happened the last time I tried to install it. I tried re-installing through Windows, restarted the machine, and the same thing happened. I went into Windows and Ubuntu was no where to be found. So, this time I rebooted the machine with the Live CD in the drive to install. I chose the first option which was to erase any previous version of Ubuntu and do a clean install (the Live CD, I think, detected a previous version because the default option was to update Ubuntu). So I went through the process and it was going well; no fatal errors showed up this time. It went all the way through and then had me reboot. I could almost smell the sweet aroma of success :D. Then it rebooted and I was greeted with grub rescue prompt :confused:.
So, I don't have a Windows recovery disk because it's and Enterprise edition of Ultimate I had gotten from the university I went to. I'm going to get an Ultimate Boot CD to try and fix the windows part of it. I've read some articles about how to fix this, and I'm going to give them a try. Any links or suggestions?
I found this article: [https://sites.google.com/site/easylinuxtipsproject/grub](https://sites.google.com/site/easylinuxtipsproject/grub)
It seems pretty straight forward. I just hope I can find what device Ubuntu is installed on. It seems like that would be easy (sdb), but in my case it hasn't been showing up at all in the past.
Thanks for your patience with me. This is my first foray into anything Linux and so I know I'm probably missing some obvious things. Thanks for your continued help.
Matt

---

### Post by darkod on 2012-02-01
The grub rescue might refer to the previous partition. You don't need the Ultimate Boot CD, you can do everything with the ubuntu cd. Boot into live mode and post the output of:
sudo fdisk -l (small L)

---

### Post by melkins on 2012-02-01
Here is the fdisk output:
Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?   218129509  1920119918   850995205   72  Unknown
/dev/sda2   ?   729050177  1273024900   271987362   74  Unknown
/dev/sda3   ?   168653938   168653938           0   65  Novell Netware 386
/dev/sda4      2692939776  2692991410       25817+   0  Empty

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   759554049   379776993+   7  HPFS/NTFS/exFAT
/dev/sdb2       759556094   976771071   108607489    5  Extended
/dev/sdb5       971012096   976771071     2879488   82  Linux swap / Solaris
/dev/sdb6       965249024   970999807     2875392   82  Linux swap / Solaris
/dev/sdb7       959485952   965232639     2873344   82  Linux swap / Solaris
/dev/sdb8       759556096   953722879    97083392   83  Linux
/dev/sdb9       953724928   959481855     2878464   82  Linux swap / Solaris

Partition table entries are not in disk order

If I'm reading this right, it looks like there is some previous partitions from when I installed Ubuntu before. Any suggestions on how I should proceed?

---

### Post by melkins on 2012-02-01
Also, is my latest install on sdb5? How would I get rid of the old ones, since they never showed up on the windows side?

---

### Post by melkins on 2012-02-01
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 860763496 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda: ___________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   759,554,049   759,553,987   7 NTFS / exFAT / HPFS
/dev/sdb2         759,556,094   976,771,071   217,214,978   5 Extended
/dev/sdb5         971,012,096   976,771,071     5,758,976  82 Linux swap / Solaris
/dev/sdb6         965,249,024   970,999,807     5,750,784  82 Linux swap / Solaris
/dev/sdb7         959,485,952   965,232,639     5,746,688  82 Linux swap / Solaris
/dev/sdb8         759,556,096   953,722,879   194,166,784  83 Linux
/dev/sdb9         953,724,928   959,481,855     5,756,928  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda         4680A83480A82C7D                       ntfs       
/dev/sdb1        80C85F25F4974A14                       ntfs       
/dev/sdb5        ed4bd6bf-e699-4e6b-8aa4-df70e9337cf8   swap       
/dev/sdb6        81b43105-adae-43eb-aead-e567b8697d11   swap       
/dev/sdb7        7e3f4b62-3d7b-4d93-8a1a-46e96b40ce09   swap       
/dev/sdb8        5a3d16e7-df30-4411-9ecb-37f08fa110b7   ext4       
/dev/sdb9        547d90d2-8e28-49d5-af4b-9a40af0db9db   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda         /media/4680A83480A82C7D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb8        /media/5a3d16e7-df30-4411-9ecb-37f08fa110b7 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=10 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS=Windows /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sdb8/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos8)'
search --no-floppy --fs-uuid --set=root 5a3d16e7-df30-4411-9ecb-37f08fa110b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos8)'
  search --no-floppy --fs-uuid --set=root 5a3d16e7-df30-4411-9ecb-37f08fa110b7
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 5a3d16e7-df30-4411-9ecb-37f08fa110b7
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5a3d16e7-df30-4411-9ecb-37f08fa110b7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 5a3d16e7-df30-4411-9ecb-37f08fa110b7
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=5a3d16e7-df30-4411-9ecb-37f08fa110b7 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 5a3d16e7-df30-4411-9ecb-37f08fa110b7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos8)'
    search --no-floppy --fs-uuid --set=root 5a3d16e7-df30-4411-9ecb-37f08fa110b7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 80C85F25F4974A14
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

=============================== sdb8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=5a3d16e7-df30-4411-9ecb-37f08fa110b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb9 during installation
UUID=547d90d2-8e28-49d5-af4b-9a40af0db9db none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 410.444046021 = 440.710938624  boot/grub/core.img                             1
 410.444057465 = 440.710950912  boot/grub/grub.cfg                             1
 364.033195496 = 390.877667328  boot/initrd.img-3.0.0-12-generic               1
 448.317035675 = 481.376751616  boot/vmlinuz-3.0.0-12-generic                  1
 364.033195496 = 390.877667328  initrd.img                                     1
 448.317035675 = 481.376751616  vmlinuz                                        1

================================ sda/boot.ini: =================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader on sdb2

00000000  e4 e1 18 b2 83 5f 25 68  81 8b 26 46 83 d8 4d aa  |....._%h..&F..M.|
00000010  98 6a a8 49 49 a0 ee c2  d9 b3 6d a2 3a 5d 6a b6  |.j.II.....m.:]j.|
00000020  c9 06 8c 5a b3 fa c9 f3  f9 00 57 3a f3 b6 65 a8  |...Z......W:..e.|
00000030  56 ab 27 97 28 ae 11 3b  7d 90 e7 97 bc a1 de d8  |V.'.(..;}.......|
00000040  b5 d5 0a 77 52 f1 be c2  32 d9 9b 7e f1 e3 79 07  |...wR...2..~..y.|
00000050  32 cf ec a4 a6 1b c9 38  ca 17 1f d3 0c bd 71 1d  |2......8......q.|
00000060  82 0f 06 ca 4e d0 b5 9e  d9 75 46 3d a5 32 65 63  |....N....uF=.2ec|
00000070  ab 0d 44 f6 df e5 eb 17  2c b2 94 b4 8f 24 81 e7  |..D.....,....$..|
00000080  a4 2f 34 3c 95 10 a0 45  fd ce cf 9b 38 64 c7 86  |./4<...E....8d..|
00000090  6f b3 d9 52 7d 78 6a 95  6a a5 63 ae 43 0a 35 d2  |o..R}xj.j.c.C.5.|
000000a0  9d a8 b6 54 44 83 ef ee  ce 66 c9 c4 fc ed 86 e7  |...TD....f......|
000000b0  4b 21 79 46 21 96 a9 a2  59 10 ac 27 4b ca 07 a8  |K!yF!...Y..'K...|
000000c0  52 7e 10 ac 1a 28 70 7b  df b5 a0 82 0c 76 df d9  |R~...(p{.....v..|
000000d0  74 c3 0c 40 e1 17 9d d9  ad 15 83 b4 ab 07 b9 41  |t..@...........A|
000000e0  8d bc ce 0e 01 82 d2 fb  24 c7 67 1f f1 24 13 a7  |........$.g..$..|
000000f0  ee d8 8f fc 1d 79 eb 3b  fe 67 72 d6 19 eb 6e e1  |.....y.;.gr...n.|
00000100  0e f9 71 75 50 19 09 d7  a1 c9 34 06 88 2f b0 30  |..quP.....4../.0|
00000110  cf bb a9 01 34 e4 ca 8b  c8 25 dc 2e 2b 2b 3e f2  |....4....%..++>.|
00000120  da ac 42 85 ec fd 79 6f  f3 12 16 3f a8 d6 bb 0f  |..B...yo...?....|
00000130  14 09 cf 0c 36 b1 43 cd  1d 9f 08 66 eb 5e 6a 60  |....6.C....f.^j`|
00000140  4a ac e3 d2 d7 58 66 dc  c2 35 9a 29 bb fb 83 bc  |J....Xf..5.)....|
00000150  2f 03 dc e6 bd ce 6d 5e  ea a5 b2 85 05 08 98 b2  |/.....m^........|
00000160  a6 59 0d 24 77 a7 63 98  b7 55 ab d9 03 ab 2b 26  |.Y.$w.c..U....+&|
00000170  ff a3 bd 8f e7 93 c6 b6  36 0d 57 2c 15 64 cf dd  |........6.W,.d..|
00000180  a7 11 8e 1a a4 2f 49 7b  20 30 a1 57 ab 1e 09 6e  |...../I{ 0.W...n|
00000190  ea 22 f0 f4 3b 88 f7 f9  30 49 a2 49 78 45 a8 e6  |."..;...0I.IxE..|
000001a0  5f d3 4c 80 dd 7c 91 b8  32 9b 03 a8 7e 2a 3e 4d  |_.L..|..2...~*>M|
000001b0  d7 17 8f 60 c5 96 f4 0f  83 01 9c f5 a1 ab 00 fe  |...`............|
000001c0  ff ff 82 fe ff ff 02 90  9a 0c 00 e0 57 00 00 fe  |............W...|
000001d0  ff ff 05 fe ff ff f5 62  42 0c 0d fd 57 00 00 00  |.......bB...W...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
```

---

### Post by YannBuntu on 2012-02-02
Please could you run Boot-Repair, click "Advanced options", click the "Backup partition tables, bootsectors and logs":
[IMG]http://pix.toile-libre.org/upload/img/1326203507.png[/IMG]

then send me the ZIP by email (yannubuntu ATT gmail DOTcom).

If Boot-Repair does not start, please send me a ZIP (or TAR) of the /boot-sav folder which is in your XP partition.

---

### Post by melkins on 2012-02-02
Yannbuntu:
I just sent you that compressed boot/sav folder. I hope this helps. Any input on how I can get Boot Repair to help me would be great. Thanks.

---

### Post by YannBuntu on 2012-02-02
Please run Boot-Repair, click "Advanced options", go to "GRUB options" tab, tick the "FlexNet" option, then apply:
[IMG]http://pix.toile-libre.org/upload/original/1324245480.png[/IMG]
Reboot and check if it's better.

---

### Post by melkins on 2012-02-02
Thanks for your effort. I'm at work right now, but I'll give it a try at home this evening.

---

### Post by darkod on 2012-02-02
The focus here seems to be on boot-repair but I see few other things that raise some questions. Also, I would like to point out that boot repair is not always the one-click solution it seems to be, depending of your setup. If it doesn't detect it correctly, it can even mix up things further.

Anyway, my observations:
1. In your post #12 the results of fdisk show some errors in the partition table of /dev/sda. What is /dev/sda? The first two partitions seem not recognized correctly.

2. Look in the results of the boot info script, the boot files reported on /dev/sdb1. The OS is reported as XP, but on top of the standard XP boot files (ntldr, boot.ini,ntdetect.com), there are boot files from Vista/7 (bootmgr, boot/BCD, windows/system32/winload.exe). Of course, on top of all of this there is a wubi install inside sdb1 so it has its boot files on sdb1 too.

Having the wubi files is normal if you have it installed, but having two sets of windows boot files, for both XP and Vista/7, is definitely strange. Did you have two windows OSs together on the computer at any time?

To answer few previous questions, your latest install is not sdb5, you can see in the fdisk results that sdb5 is a swap partition. You have 4 swap partitions, for what ever reason. You latest and only ubuntu install seems to be sdb8. So even without boot-repair working, you can boot with the ubuntu cd in live mode, and try to repair grub2 in terminal with:

```
sudo mount /dev/sdb8 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```That will install new grub2 on the MBR of /dev/sdb. Of course, set in BIOS to boot from the 500GB disk, /dev/sdb, as first option. You might have broken grub on the other disk (the script results are not definitive about sda) and you might have sda as first option to boot from right now.

I would try this grub2 reinstall first. But the possible issue about the windows boot files on sdb1 remains even if grub2 starts working fine.

---

### Post by melkins on 2012-02-02
Thanks for your comments darkod. I think /dev/sda is my 300gb HDD. I'm not sure why it's in the sda position and not sdb; I had recently put the computer in a new case, so my maybe I switched the SATA cables by mistake. The 300gb HDD is just for files; no OS on it.
I don't know why the 500gb HDD is reading XP. I have never had XP on this machine. 
Thanks. I'm going to try the grub2 repair tonight.

---

### Post by YannBuntu on 2012-02-02
Hello Darkod,
thanks for helping. Your analysis is correct. Therefore, here is why i asked to try the FlexNet option: in Melkins's Boot-Repair log dated 31 Jan , Boot-Repair tried to reinstall the GRUB2 of sdb7 in sdb's MBR , which gave the following output:
```
/usr/sbin/grub-setup: warn: Sector 7 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1

```

I guess your proposition will give the same error.

Furthermore, Boot-Repair is a GPL software designed to help the Community, and to facilitate the work of helpers like you and me, so please if you have seen any situation where it "mix up things", please report it on [this thread]("http://ubuntuforums.org/showthread.php?p=10871917#post10871917") or on [its bug tracker]("https://bugs.launchpad.net/boot-repair").

---

### Post by darkod on 2012-02-02
> **melkins said:**
> Thanks for your comments darkod. I think /dev/sda is my 300gb HDD. I'm not sure why it's in the sda position and not sdb; I had recently put the computer in a new case, so my maybe I switched the SATA cables by mistake. The 300gb HDD is just for files; no OS on it.
I don't know why the 500gb HDD is reading XP. I have never had XP on this machine. 
Thanks. I'm going to try the grub2 repair tonight.

Doesn't matter if sda is for OS or data. I would be even more worried if my data disk shows first two partitions as unrecognized filesystem. If an OS breaks you can reinstall it at worst case. If data is lost, you can hardly retrieve it.

But I don't know what to suggest for sda. Maybe you have some strange partition type, but usually linux is very good at detecting all of them.

For example, today at work I did a disk backup with System Rescue CD of a disk when both Acronis and Ghost couldn't do it. Good old linux came to rescue. :)

Changing the order of sata cables does change the order of the letters, sdA, sdB, sdC, etc. But as long as you tell BIOS to boot from the 500GB disk it doesn't care if it's called sda or sdb.

---

### Post by melkins on 2012-02-02
Well, I tried to run boot repair again, and was still hanging up on the scanning system. Then I tried darkod's suggestion and received an error. Today I was reading about the secured remix cd and I thought I would try that...well that worked! It fixed it with the grub repair option. Now I have to figure out how to get Windows working again. It shows up on the menu, but every time I select it, it brings me back to the menu.
I appreciate your time and help. This being my first time using a Linux-based system, I am a little more than clueless. That being said, it's almost enjoyable dealing with these problems, compared to dealing with Windows issues. I look forward to getting more familiar with Ubuntu.
If you do have any suggestions for getting Vista back up and running, let me know. In the mean time I've got some more researching to do.

---

### Post by darkod on 2012-02-03
When you say it brings you back to the menu, what exactly happens? Look very carefully, because you have quite a mix there.
As I already mentioned, you seem to have a wubi install inside windows too. Usually you do not keep wubi inside windows, and install ubuntu on its own partition. You have one or the other (it can work with both, no problem).

So even when your boot process works, it would look like:
1. You first get the grub2 boot menu from the MBR. If you select ubuntu it should boot ubuntu.
2. If you select windows, then you get the windows bootloader which contains windows and wubi (ubuntu). If you select windows here, it should boot.
3. If you select wubi (ubuntu) you then get the grub2 from wubi (sort of virtual) which again will have options for ubuntu (wubi but it calls it only ubuntu) and windows. In your setup it might even have the option for your sdb8 ubuntu install, not 100% sure if it can detect it.

So, by having both wubi inside windows and ubuntu on its own partition, you are looking into up to three bootloaders depending what system you want to boot.

To start troubleshoot the windows boot, if you never had XP, try removing (not deleting) the three XP boot files from sdb1:
ntldr
boot.ini
ntdetect.com

Boot your ubuntu and move these files on another location, on a usb stick, in your ubuntu Home folder, etc. Maybe they are confusing the windows boot.

Then restart and select windows from the grub2 menu, see what happens.

---

