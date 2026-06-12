---
title: "Can't boot to XP after fresh install of Maverick on dual-boot system"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by Bearly Able on 2010-11-10
Hi,

When I first installed Ubuntu as a dual-boot (about 18 months ago), I had problems booting to XP, which were eventually solved for me in [this thread]("http://ubuntuforums.org/showthread.php?t=1060203"), which set Windows to boot Ubuntu, rather than the other way round.

I've just had to do a fresh install of Maverick, following a major problem, and I'm back to being unable to boot XP.  The error is different from before and I don't want to start guessing at what to do about it and screwing things up still further.

The GRUB menu lists Ubuntu first, then Windows XP.  If I choose XP, it takes me to my previous boot menu, with Windows as the first option.  However, selecting this gives  me ```
Windows could not start because the following file is missing or corrupt: 
<Windows root>\system32\ntoskml.exe
Please re-install a copy of the above file.
```

Windows and Ubuntu are on separate hard drives.  XP was fine until I re-installed Ubuntu.

I'd be most grateful for any assistance.

Lesley

---

### Post by sikander3786 on 2010-11-10
Hi.

Please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us better understand your current situation and thus help you accordingly. Please wrap the output with proper code tags # from the post menu.

Here are some workarounds, but most of them will require you re-install Grub2.

[http://www.computerhope.com/issues/ch000646.htm](http://www.computerhope.com/issues/ch000646.htm)

---

### Post by Bearly Able on 2010-11-10
Thanks for the speedy reply.  Here is the Boot Info Script results.  (sda is my Windows drive, sdb is my Ubuntu drive and sdc is an external hard drive with no OS.)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /grub.bin is trying to chain load 
                       sector #63 on boot drive #2
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/sda2          71,682,030   312,576,704   240,894,675   f W95 Ext d (LBA)
/dev/sda5          71,682,093   133,259,174    61,577,082   7 HPFS/NTFS
/dev/sda6         133,259,238   199,463,039    66,203,802   7 HPFS/NTFS
/dev/sda7         199,463,103   266,678,999    67,215,897   7 HPFS/NTFS
/dev/sda8         266,679,063   312,576,704    45,897,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   300,292,095   300,290,048  83 Linux
/dev/sdb2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sdb5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        127C3D347C3D13C7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4CBE3566D7F2CDE4                       ntfs                                     
/dev/sda6        ACABF83B1BD256E9                       ntfs                                     
/dev/sda7        024FF147EFA0A210                       ntfs                                     
/dev/sda8        132F8D1E942CCBC1                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        fbe434d4-356f-4c3a-8197-a29857247a08   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        85559c9e-8932-46da-84a5-aa81e4e79e5c   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        afee3d14-aa20-447f-850b-8b0ebe355c58   ext4       HD-PFU2                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/HD-PFU2           ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\grub.bin=" Ubuntu Grub Menu"

C:\grub.bin=" Ubuntu Grub Menu"


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
search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
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
	search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=fbe434d4-356f-4c3a-8197-a29857247a08 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=fbe434d4-356f-4c3a-8197-a29857247a08 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 127c3d347c3d13c7
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=85559c9e-8932-46da-84a5-aa81e4e79e5c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/core.img
  38.9GB: boot/grub/grub.cfg
   3.3GB: boot/initrd.img-2.6.35-22-generic
  77.4GB: boot/vmlinuz-2.6.35-22-generic
   3.3GB: initrd.img
  77.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  29 a1 4e e2 43 0d e5 e2  a1 91 3e 06 b3 83 32 35  |).N.C.....>...25|
00000010  1b 96 a0 2a 8d 59 e1 c4  07 a3 f6 58 c1 d0 c3 3a  |...*.Y.....X...:|
00000020  df e8 ad f8 29 53 f2 6d  f5 86 03 ed b9 0f 4e 6b  |....)S.m......Nk|
00000030  0e 3c 8f dd 43 43 24 37  f1 60 5f a5 06 6b 4f bc  |.<..CC$7.`_..kO.|
00000040  8d 69 8a 86 36 75 06 7c  c5 21 a9 35 09 c8 a3 f4  |.i..6u.|.!.5....|
00000050  a3 82 73 9c bf 0d 16 9e  0d cb 95 00 45 7c 35 bf  |..s.........E|5.|
00000060  fd c4 f5 83 73 8b 16 09  09 68 77 76 a6 92 51 dd  |....s....hwv..Q.|
00000070  21 98 34 ff c2 68 6d 3d  b8 95 ce 5c f2 71 8f 67  |!.4..hm=...\.q.g|
00000080  f5 06 2c cd 00 e8 21 96  34 34 56 3f 6f 40 f7 ba  |..,...!.44V?o@..|
00000090  a0 c5 a1 f7 58 e2 55 67  d0 24 a2 1b 5d a4 a6 ec  |....X.Ug.$..]...|
000000a0  34 7c 68 bb 51 1f bd f0  b1 91 db a8 f0 f8 6f 38  |4|h.Q.........o8|
000000b0  01 df 83 aa 5b d3 86 03  72 52 f7 a5 ba 81 22 83  |....[...rR....".|
000000c0  e9 4a 69 b3 c0 bf 2d 74  3c b9 50 0c 03 58 4d b4  |.Ji...-t<.P..XM.|
000000d0  64 1b 19 13 99 84 bd 19  6e 38 f8 99 05 27 3d 8a  |d.......n8...'=.|
000000e0  1e 5a 5e bb 55 1e cd d5  c9 f3 73 36 68 24 59 a2  |.Z^.U.....s6h$Y.|
000000f0  0b 9f be a1 ba 4a 5e 0b  f4 fc 68 71 d3 40 60 c3  |.....J^...hq.@`.|
00000100  5c 66 92 e0 0c 91 89 4e  3e c1 82 56 28 62 7a 41  |\f.....N>..V(bzA|
00000110  9c 20 bc 9f dd 23 f3 cd  e1 01 17 c4 42 2a cb 24  |. ...#......B*.$|
00000120  70 94 02 e1 c7 60 ef 01  35 46 3b 77 f3 bf 0f 44  |p....`..5F;w...D|
00000130  3d 86 81 37 52 0b 57 9b  91 0b db 64 5f ad 56 2c  |=..7R.W....d_.V,|
00000140  d6 3b a5 48 38 2a 49 18  12 b4 83 68 9a 09 7b 2e  |.;.H8*I....h..{.|
00000150  75 5a 3d 8a f8 57 99 eb  1f 58 e9 00 af 57 c1 78  |uZ=..W...X...W.x|
00000160  e1 5b 59 5d f4 0e de 82  30 80 4e a7 6d af 64 41  |.[Y]....0.N.m.dA|
00000170  92 c9 2e 5d 95 af fb 53  cd 4c 1e a5 b4 87 a3 51  |...]...S.L.....Q|
00000180  7e 4c 9b e4 68 5b a1 0b  1b 12 67 f4 7d 91 64 c9  |~L..h[....g.}.d.|
00000190  97 94 bd 6f 3d f3 b2 ac  63 65 7d 94 2b 23 fd 2c  |...o=...ce}.+#.,|
000001a0  e7 2d 84 f0 ab 5d 3a 51  a5 2f 83 f2 a8 27 77 5d  |.-...]:Q./...'w]|
000001b0  1c 2f b1 b0 c5 2b eb c3  b5 8b 77 ef db 96 00 fe  |./...+....w.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2010-11-10
Which drive is your bios set to boot from please?

---

### Post by Bearly Able on 2010-11-10
sda.  Ubuntu boots no problem - it's just XP.

---

### Post by Quackers on 2010-11-10
Do you have a Windows XP repair disc?
The ntoskrnl.exe error can be caused by several things including a misconfigured boot.ini, but why that should be the case I have no idea.
I think we could do with oldfred appearing, he'll know :-)

---

### Post by Bearly Able on 2010-11-10
Thanks for your replies.  I'm afraid I've never even heard of an XP repair disc, so I hope it won't prove vital!

---

### Post by oldfred on 2010-11-10
The script seems to have added some info, which I assume is the issue as the windows partition should not be referring to grub unless you have configured something non-standard:

```
My XP:
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
Your XP:
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /grub.bin is trying to chain load 
                       sector #63 on boot drive #2
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

```I would run the XP repairs, you may only need the fixboot but I am pasting the entire list:

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\


BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

---

### Post by Bearly Able on 2010-11-10
OK.  I have a Windows XP CD, although I've never tried using it to boot from.

When I installed 10.10, I installed it to the second hard drive (sdb) with default settings  i.e. it put GRUB wherever it wanted.  However, my original Ubuntu install was booting Ubuntu from Windows (see link in my first post).  Could this be why Windows is referencing GRUB?  I don't want to risk losing access to Ubuntu, as it's my main system, and as you'll have realised, I have very little understanding of what I'm doing here.

Thanks for your help.

---

### Post by oldfred on 2010-11-10
When you have the luxury of multiple drives I prefer to have the boot loader in the MBR of the same drive as the system and then set BIOS to boot the Ubuntu drive. That way if one drive fails you can still boot the other drive. (but you still should be able to boot CDs anyway)

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions
then set BIOS to boot sdb.

Then when you run the windows repairs you can let window install its boot loader to the MBR of sda.

---

### Post by Bearly Able on 2010-11-10
OK, if I understand you correctly, you're suggesting I have a boot loader on each drive, and use the BIOS to select the drive to boot from?  That's not a problem; I don't use XP very often anyway.

I'm pretty tired just now, so I think I'll leave it until morning to try.  I'll post back and let you know the results.

Thanks again for your help.

---

### Post by oldfred on 2010-11-10
You only need to use the BIOS in an emergency where the grub/Ubuntu drive failed. If you set BIOS to boot grub first, it will also let you boot the windows install on the first drive.

I have 3 drives and three boot loaders. Grub2's osprober finds all the systems and lets me boot any of them. Only if experimenting do I use BIOS to boot another drive.

---

### Post by Bearly Able on 2010-11-11
Yes, I realise GRUB *should* be able to load Windows, but in my original setup (same machine, same hard drives) it just wouldn't ([see original thread]("http://ubuntuforums.org/showpost.php?p=6681905&postcount=13")).  Perhaps I'll have more luck with GRUB2, but I'm not holding my breath.

I've followed your instructions to install GRUB to the Ubuntu drive and it seems to have gone smoothly.  I'm going to try changing the BIOS to boot that drive first and check it's OK before I try to repair Windows.

Thanks again.

---

### Post by Bearly Able on 2010-11-11
I've changed the boot order and Ubuntu is still booting fine.  I've had less success with XP.

At the Administrator Password prompt, I entered my XP password, but got a message saying it was incorrect.  I tried my husband's password, as he also has an Administrator account on XP, but it wouldn't accept that either.  Leaving it blank seemed to work and ```
FIXBOOT C:
``` apparently created a new boot sector, but then

```
COPY [CDDRIVE]:\I386\NTLDR C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM C:\
```
both gave me ```
Access is denied
```.
```
BOOTCFG /rebuild
``` resulted in ```
Error.  Failed to add the selected boot entry to the boot list
``` - presumably because the previous two commands failed.

I've followed the links in oldfred's post #8, but I still can't work out what to do next.  Please can anyone help?  Thank you.

---

### Post by oldfred on 2010-11-11
Since it is XP you can do just about all the repairs from Ubuntu or any linux repair CD. Both an advantage & a danger as you can then also damage XP from Linux.

The one thing you cannot do is to run chkdsk. Often that solves many issues in windows NTFS partitions. So I would try that first.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

---

### Post by Bearly Able on 2010-11-11
Thanks, oldfred.  Presumably I do that using the recovery console from the XP CD?  I don't understand how installing Ubuntu on a separate drive could cause these problems in XP, because it was fine right up until I did that.

---

### Post by Bearly Able on 2010-11-11
I've run chkdsk, which "found and fixed one or more errors on the volume".  I then ran the same commands as before to fix the boot sector, with exactly the same results/error messages as before.  Are we any further forward?

I've just thought: both times I ran FIXMBR C: it didn't give me any output, just returned me to the prompt.  Is this right?

---

### Post by oldfred on 2010-11-11
If you in BIOS set sda the windows drive to boot does windows boot or not boot?

If you boot the Ubuntu drive does both Ubuntu and XP boot?

The fixMBR should write the windows boot loader to the MBR. The fixboot should fix the boot sector of the XP partition. If both of those are good then the boot.ini, ntldr and ntdetect should be all that is required.

If you got chkdsk errors you need to rerun that until you get no errors. It does not fix all errors on one pass.

---

### Post by Bearly Able on 2010-11-11
Thanks for the advice about chkdsk - I didn't know that.  I'll run it again now.

I can boot Ubuntu from both sda and sdb, both of which are using GRUB.  I can't boot Windows from either.  In both cases, selecting Windows takes me to my "old" boot menu, and selecting Windows from there still gives the original error message:```
 Windows could not start because the following file is missing or corrupt: 
<Windows root>\system32\ntoskml.exe
Please re-install a copy of the above file.  
```

I don't know if it's any help, but I've run boot_info_script again:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /grub.bin is trying to chain load 
                       sector #63 on boot drive #2
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/sda2          71,682,030   312,576,704   240,894,675   f W95 Ext d (LBA)
/dev/sda5          71,682,093   133,259,174    61,577,082   7 HPFS/NTFS
/dev/sda6         133,259,238   199,463,039    66,203,802   7 HPFS/NTFS
/dev/sda7         199,463,103   266,678,999    67,215,897   7 HPFS/NTFS
/dev/sda8         266,679,063   312,576,704    45,897,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   300,292,095   300,290,048  83 Linux
/dev/sdb2         300,294,142   312,580,095    12,285,954   5 Extended
/dev/sdb5         300,294,144   312,580,095    12,285,952  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        127C3D347C3D13C7                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        4CBE3566D7F2CDE4                       ntfs                                     
/dev/sda6        ACABF83B1BD256E9                       ntfs                                     
/dev/sda7        024FF147EFA0A210                       ntfs                                     
/dev/sda8        132F8D1E942CCBC1                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        fbe434d4-356f-4c3a-8197-a29857247a08   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        85559c9e-8932-46da-84a5-aa81e4e79e5c   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        afee3d14-aa20-447f-850b-8b0ebe355c58   ext4       HD-PFU2                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/HD-PFU2           ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\grub.bin=" Ubuntu Grub Menu"

C:\grub.bin=" Ubuntu Grub Menu"


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
search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
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
	search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=fbe434d4-356f-4c3a-8197-a29857247a08 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=fbe434d4-356f-4c3a-8197-a29857247a08 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set fbe434d4-356f-4c3a-8197-a29857247a08
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 127c3d347c3d13c7
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
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=85559c9e-8932-46da-84a5-aa81e4e79e5c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/core.img
  39.3GB: boot/grub/grub.cfg
   3.3GB: boot/initrd.img-2.6.35-22-generic
  77.4GB: boot/vmlinuz-2.6.35-22-generic
   3.3GB: initrd.img
  77.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  29 a1 4e e2 43 0d e5 e2  a1 91 3e 06 b3 83 32 35  |).N.C.....>...25|
00000010  1b 96 a0 2a 8d 59 e1 c4  07 a3 f6 58 c1 d0 c3 3a  |...*.Y.....X...:|
00000020  df e8 ad f8 29 53 f2 6d  f5 86 03 ed b9 0f 4e 6b  |....)S.m......Nk|
00000030  0e 3c 8f dd 43 43 24 37  f1 60 5f a5 06 6b 4f bc  |.<..CC$7.`_..kO.|
00000040  8d 69 8a 86 36 75 06 7c  c5 21 a9 35 09 c8 a3 f4  |.i..6u.|.!.5....|
00000050  a3 82 73 9c bf 0d 16 9e  0d cb 95 00 45 7c 35 bf  |..s.........E|5.|
00000060  fd c4 f5 83 73 8b 16 09  09 68 77 76 a6 92 51 dd  |....s....hwv..Q.|
00000070  21 98 34 ff c2 68 6d 3d  b8 95 ce 5c f2 71 8f 67  |!.4..hm=...\.q.g|
00000080  f5 06 2c cd 00 e8 21 96  34 34 56 3f 6f 40 f7 ba  |..,...!.44V?o@..|
00000090  a0 c5 a1 f7 58 e2 55 67  d0 24 a2 1b 5d a4 a6 ec  |....X.Ug.$..]...|
000000a0  34 7c 68 bb 51 1f bd f0  b1 91 db a8 f0 f8 6f 38  |4|h.Q.........o8|
000000b0  01 df 83 aa 5b d3 86 03  72 52 f7 a5 ba 81 22 83  |....[...rR....".|
000000c0  e9 4a 69 b3 c0 bf 2d 74  3c b9 50 0c 03 58 4d b4  |.Ji...-t<.P..XM.|
000000d0  64 1b 19 13 99 84 bd 19  6e 38 f8 99 05 27 3d 8a  |d.......n8...'=.|
000000e0  1e 5a 5e bb 55 1e cd d5  c9 f3 73 36 68 24 59 a2  |.Z^.U.....s6h$Y.|
000000f0  0b 9f be a1 ba 4a 5e 0b  f4 fc 68 71 d3 40 60 c3  |.....J^...hq.@`.|
00000100  5c 66 92 e0 0c 91 89 4e  3e c1 82 56 28 62 7a 41  |\f.....N>..V(bzA|
00000110  9c 20 bc 9f dd 23 f3 cd  e1 01 17 c4 42 2a cb 24  |. ...#......B*.$|
00000120  70 94 02 e1 c7 60 ef 01  35 46 3b 77 f3 bf 0f 44  |p....`..5F;w...D|
00000130  3d 86 81 37 52 0b 57 9b  91 0b db 64 5f ad 56 2c  |=..7R.W....d_.V,|
00000140  d6 3b a5 48 38 2a 49 18  12 b4 83 68 9a 09 7b 2e  |.;.H8*I....h..{.|
00000150  75 5a 3d 8a f8 57 99 eb  1f 58 e9 00 af 57 c1 78  |uZ=..W...X...W.x|
00000160  e1 5b 59 5d f4 0e de 82  30 80 4e a7 6d af 64 41  |.[Y]....0.N.m.dA|
00000170  92 c9 2e 5d 95 af fb 53  cd 4c 1e a5 b4 87 a3 51  |...]...S.L.....Q|
00000180  7e 4c 9b e4 68 5b a1 0b  1b 12 67 f4 7d 91 64 c9  |~L..h[....g.}.d.|
00000190  97 94 bd 6f 3d f3 b2 ac  63 65 7d 94 2b 23 fd 2c  |...o=...ce}.+#.,|
000001a0  e7 2d 84 f0 ab 5d 3a 51  a5 2f 83 f2 a8 27 77 5d  |.-...]:Q./...'w]|
000001b0  1c 2f b1 b0 c5 2b eb c3  b5 8b 77 ef db 96 00 fe  |./...+....w.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 bb 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Bearly Able on 2010-11-11
I've run chkdsk again and there were no errors reported.

I tried again to fix the Windows boot sector.  I got the same "Access is denied" error messages, but this time I didn't get an error message when I ran BOOTCFG /rebuild.

The BIOS is still set to boot sda.  I get the GRUB menu with XP as before.  Selecting XP gets me my "old" boot menu, which now has two entries for XP, but I can't boot from either of them.  Both give me the original ntoskml.exe error message.

---

### Post by oldfred on 2010-11-11
Microsoft has this info. It could be hardware, mouse, keyboard or harddrive can also cause this. It looks like your boot.ini has the default line.

[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

But I would go thru all their suggestions.

You are not using the grub entries in boot.ini anymore, I assume. I would suggest deleting them.

C:\grub.bin=" Ubuntu Grub Menu"

C:\grub.bin=" Ubuntu Grub Menu"

If editing windows files like boot.ini
(Using nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.

I also do not understand why the fixboot, did not put the windows boot loader into sda?? Some of the fixes must not be working correctly. Therefore rerunning may make sense.

---

