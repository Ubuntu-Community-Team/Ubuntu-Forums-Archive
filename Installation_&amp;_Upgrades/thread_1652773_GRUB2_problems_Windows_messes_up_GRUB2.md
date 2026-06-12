---
title: "GRUB2 problems: Windows messes up GRUB2"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by emanresu on 2010-12-25
Greetings,

I have a dualboot laptop (HP/Compaq nx 7300), XP and Ubuntu. I updated to 10.04 yesterday. I was able to run Ubuntu right after the upgrade. Restarted the computer and logged into XP. Restarted again and got this error msg:

"No module name found. Aborted. Press any key to exit"

Pressed a key and got:

"Non-system disk or disk error. Replace and strike any key when ready."

and then it goes back and forth between error msgs each time I press a key. Try as I might, I could get neither XP or Ubuntu to even show up, let alone boot. 

I've spent hours trying to figure things out, but I'm no expert, so my knowledge is incomplete and my solutions are lacking. This is what I've figured out so far:
I used Grub Super Disk(GSD) to get rid of the MBR or something, so I was finally able to boot XP. Once there I checked the web for possible solutions. Somewhere I saw that Windows was somehow screwing up GRUB2-based MBRs. I reinstalled 10.04 2x now and it didn't work. I didn't realize there was a change to GRUB at first (wasn't paying attention to the GRUB name at first), so i was looking for /boot/grub/menu.lst to see if I could fix that the first time I reinstalled. Didn't work, since there was no more /boot/grub/menu.lst. 

More searching about the issue and I've tried at least these
[2]("http://ubuntuforums.org/showthread.php?t=1581099") similar [suggestions]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202") and they don't work. 

Specifically, I tried:

```
sudo mkdir /media/sda7
sudo mount /dev/sda7 /media/sda7
sudo grub-install --root-directory=/media/sda7 /dev/sda

```

2X and the 2nd time I also added 

```
sudo update-grub
```

(I've seen "-grub" and "-grub2". Which should it be?)

At this point, after thinking I've "fixed" GRUB and the MBR and restarted the computer, I get a GRUB menu and can log onto either OS. But if I choose XP and restart after logging into XP, I get the same two error msgs that I start this post off with and GRUB is shot. I can use GSD and the tools there to get rid of MBR and at least get into XP or I can use LiveCD and start 10.04 after that, but that's a lot of work to do something that worked quite easily when I had 9.10 or .04 or whatever the previous version was. 

I found another thread that uses a script to diagnose problems. Here are the results from the boot_info_script055. ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    37,752,749    37,752,687   7 HPFS/NTFS
/dev/sda2          37,752,750    50,444,099    12,691,350   c W95 FAT32 (LBA)
/dev/sda3          50,444,100   119,652,119    69,208,020   c W95 FAT32 (LBA)
/dev/sda4         119,652,181   156,301,311    36,649,131   f W95 Ext d (LBA)
/dev/sda5         119,652,183   126,110,249     6,458,067  82 Linux swap / Solaris
/dev/sda6         126,110,313   141,821,819    15,711,507  83 Linux
/dev/sda7         141,821,952   156,301,311    14,479,360  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3A48F38E48F34763                       ntfs                                     
/dev/sda2        3751-5B7F                              vfat                                     
/dev/sda3        4642-1A54                              vfat                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f1475d8f-4b52-4c35-a3c8-edab8da59704   swap                                     
/dev/sda6        e2f2318f-641e-4526-8695-f72b84889dce   ext3                                     
/dev/sda7        1f8afdad-27a6-4989-8c78-8c621b1de31d   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)


================================ sda1/boot.ini: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


================================ sda2/boot.ini: ================================

[boot loader]

timeout=0

default=C:\CMDCONS\BOOTSECT.DAT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 1f8afdad-27a6-4989-8c78-8c621b1de31d
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 1f8afdad-27a6-4989-8c78-8c621b1de31d
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 1f8afdad-27a6-4989-8c78-8c621b1de31d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=1f8afdad-27a6-4989-8c78-8c621b1de31d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 1f8afdad-27a6-4989-8c78-8c621b1de31d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=1f8afdad-27a6-4989-8c78-8c621b1de31d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 1f8afdad-27a6-4989-8c78-8c621b1de31d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 1f8afdad-27a6-4989-8c78-8c621b1de31d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3a48f38e48f34763
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 3751-5b7f
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=1f8afdad-27a6-4989-8c78-8c621b1de31d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f1475d8f-4b52-4c35-a3c8-edab8da59704 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/core.img
  75.4GB: boot/grub/grub.cfg
  77.8GB: boot/initrd.img-2.6.32-24-generic
  77.7GB: boot/vmlinuz-2.6.32-24-generic
  77.8GB: initrd.img
  77.7GB: vmlinuz
```
This is what the boot info result looks like after I've booted XP and messed up GRUB and used GSD to get rid of MBR or whatever it does. I wrote this post logged into 10.04 using the LiveCD.

---

### Post by coffeecat on 2010-12-25
I see you have a HP laptop. Have a look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

From what you describe that seems likely to be your problem. Do you have any of:

> HP:  Credential Manager, Recovery Manager, ProtectTools, PC Angel, Backup and Recovery?

If so, disabling whichever is the offender may be the answer. Another link which describes the problem as well:

[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable]("http://www.chiark.greenend.org.uk/ucgi/%7Ecjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable")

---

### Post by emanresu on 2010-12-26
Thank you, coffeecat.

The 1st solution given in the sourceforge link says to look at the hexdump (whatever that is) of MBR before and after the screwup. Those are big files and this forum won't let me post a complete view of just one of those. Here is the difference in the two based on diff. 

> ubuntu@ubuntu:~/Desktop$ diff /media/4642-1A54/goodd.txt /media/4642-1A54/badd.txt
1178,1209c1178,1185
< 00004a00  a4 f3 8b 4d 7f 32 17 ad  a7 13 ac ff 8d dd d8 c9  |...M.2..........|
< 00004a10  38 72 3a 8e ff aa 40 fb  d8 77 37 70 23 b3 6f f2  |8r:...@..w7p#.o.|
< 00004a20  e3 71 f2 9d 5b ff 72 4c  ff a8 0e 8c 91 80 66 5b  |.q..[.rL......f[|
< 00004a30  3b d8 3f 29 ff 61 6d e6  7a 75 81 0e 0a e5 12 fb  |;.?).am.zu......|
< 00004a40  20 67 18 f6 e0 d6 50 4b  2e 0f 81 ee e7 0d ad 7c  | g....PK.......||
< 00004a50  c5 18 b2 2f 36 56 f7 7f  81 31 1f 15 67 a4 61 f1  |.../6V...1..g.a.|
< 00004a60  96 5f d9 01 2e 5d ee 44  c3 a7 6c 70 9f 55 29 a3  |._...].D..lp.U).|
< 00004a70  ac 6c 0f 8d 13 d6 e5 a0  0f 11 e5 ef 5e 41 08 b4  |.l..........^A..|
< 00004a80  a5 95 d8 80 1d 29 fe e3  8d 6f 15 c5 e4 53 81 41  |.....)...o...S.A|
< 00004a90  93 46 7e f9 c2 54 8a 58  49 72 41 be c2 bb 29 43  |.F~..T.XIrA...)C|
< 00004aa0  12 6e d0 9a 99 d0 8f 96  37 92 cc 33 bf 6e 25 36  |.n......7..3.n%6|
< 00004ab0  9c 1d ed 6c a9 54 97 77  0b da d4 3d 19 fb d5 b8  |...l.T.w...=....|
< 00004ac0  1b 2f f8 a0 1a bf c3 c7  53 ff d0 1b f2 2f 75 38  |./......S..../u8|
< 00004ad0  82 65 48 7d 33 b6 ac e1  2d e0 77 26 9e 90 a4 9a  |.eH}3...-.w&....|
< 00004ae0  2a d5 5e 87 25 5b a8 82  39 97 49 a3 28 2e 09 47  |*.^.%[..9.I.(..G|
< 00004af0  d5 53 f2 db 33 84 44 06  31 66 79 55 e6 48 27 81  |.S..3.D.1fyU.H'.|
< 00004b00  90 cf be f6 35 c9 00 7b  eb ec f9 91 de d7 2d b1  |....5..{......-.|
< 00004b10  d4 83 96 b0 84 3a b8 43  56 0d 03 ec 94 af ba 1c  |.....:.CV.......|
< 00004b20  1d d4 15 d7 65 06 c2 5b  5d 9c 93 91 6d 4b c9 b6  |....e..[]...mK..|
< 00004b30  0f 2c ba c7 06 2e 40 5f  e0 85 2c ff cc af ac 9e  |.,....@_..,.....|
< 00004b40  02 0d 64 96 2f fa d0 5c  8d af 06 28 91 81 8f 00  |..d./..\...(....|
< 00004b50  a3 4d 7c 1c 59 5c 2a 0f  55 33 e5 a0 96 0b 6d cb  |.M|.Y\*.U3....m.|
< 00004b60  e3 c7 9b 58 40 bf 32 ed  8d 4b a0 b6 73 ee e4 d2  |...X@.2..K..s...|
< 00004b70  dc a6 35 2d e6 fb 8b 4a  91 68 08 a4 5e bf 57 96  |..5-...J.h..^.W.|
< 00004b80  9b 5c 7b f8 34 aa eb da  a2 de 92 d7 1f 21 72 48  |.\{.4........!rH|
< 00004b90  ff 53 1b ef ef 41 78 55  f2 c8 32 da 17 2b d7 df  |.S...AxU..2..+..|
< 00004ba0  2a 6d c9 66 5c 0e a1 90  e5 86 81 1f f1 1b 22 43  |*m.f\........."C|
< 00004bb0  5a ee eb 57 c9 75 ad 74  e1 60 35 2d 4d 13 8d 7c  |Z..W.u.t.`5-M..||
< 00004bc0  75 90 c8 eb fc 52 f2 68  ae 94 87 c6 6f 93 a6 c9  |u....R.h....o...|
< 00004bd0  d1 a4 0d 31 1f 42 d8 cc  54 08 73 54 6b b5 84 de  |...1.B..T.sTk...|
< 00004be0  fa 28 33 f5 a8 e5 78 65  81 14 b3 b9 86 8e 86 4e  |.(3...xe.......N|
< 00004bf0  a6 a9 bf 5a f9 15 0d 70  eb e5 7a 48 0c 02 64 4c  |...Z...p..zH..dL|
---
> 00004a00  42 e8 e9 fe e9 31 9c b9  ae 3d 86 fd b1 55 3e e0  |B....1...=...U>.|
> 00004a10  ae 3d 86 fd b1 55 3e e0  1f 61 6b a6 b8 fe 0e ce  |.=...U>..ak.....|
> 00004a20  56 33 24 c5 b5 fb fa 62  67 97 da 00 72 0c 36 57  |V3$....bg...r.6W|
> 00004a30  d1 b2 14 fe e1 32 e9 dc  27 4d 6a f8 a6 81 a0 cf  |.....2..'Mj.....|
> 00004a40  d3 5e ed 28 40 de c9 8e  73 f2 06 eb 72 dc 32 fc  |.^.(@...s...r.2.|
> 00004a50  3f 38 f0 b5 ee 85 2c 52  1e 86 97 71 b3 ca e8 c1  |?8....,R...q....|
> 00004a60  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
> *


I have no idea how to interpret this. If someone else could tell me what this means, that'd be great.

---

### Post by coffeecat on 2010-12-26
What it is says is:

> You also might be able to determine the program by looking at a hexdump of the extended MBR.... without telling you how. My guess is that you'd convert the hex to ascii or unicode and hope to find a string that tells you what the responsible app is. Certainly with an output from diff, there has been a change and the problem must be as in that link. But what that link says before that is:

> See what happens if you disable or uninstall  programs  in Windows which might be writing to  extended MBR.I think that's the route I'd go. Have a look in your Windows startup applications. See if there is any that is listed in that link. Or perhaps some sort of utility that you don't really need. It's going to be a third-party app - not Microsoft - because vanilla Windows, whether XP, Vista or W7 doesn't do this. My preference would be to disable any possible app rather than uninstall it. 

Do you know how to disable startup programs in XP? If I remember correctly you run 'msconfig' from Start > Run, and then click on the Startup tab. You'll see all the garbage that HP has deemed fit to cause to be run at startup and you can disable anything you want by unticking the box. Windows will have a moan at you when you reboot, but the deselected item won't run anymore. I had more than one occasion to do this when using XP.

---

