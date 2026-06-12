---
title: "Did something wrong, very wrong installing BURG"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2010-09-05
Thought BURG would be cool so I installed it. Something is very wrong. (See attached photos) all I get is the 1st photo, **BURG version 1.98+20100623-1+karmic**. If I tab I get photo 2. 

At this point I'd be happy just to restore GRUB2 & forget BURG but I can't even boot to any OS. I haven't had Ubuntu on this PC for long so maybe the best, or simplest option, would be to re-install Ubuntu- which would rewrite grub2.

Please advise.

Ubuntu 10.04 amd64 w/ Windows 7 Home Premium 64bit

---

### Post by oldfred on 2010-09-05
You probably just need to reinstall grub to the MBR.

But to know exactly what is where.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

To reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by linux18 on 2010-09-05
put in your live cd (any live cd)

if ubuntu is your only os:

in a terminal type sudo grub-install /dev/sda && sudo update-grub

---

### Post by GARoss on 2010-09-05
Thanks. I cannot boot into Ubuntu at all. With the install CD I can boot to the Try Ubuntu desktop.

I can boot Win 7 by typing grub> **exit** then enter key.

I have Ubuntu 10.04 amd64 w/ Windows 7 Home Premium 64bit installed on separate HDDs (there's 3 HDDs total). I'm not sure which section Ubuntu is installed. Would sudo grub-install /dev/**sda** && sudo update-grub still be correct?

---

### Post by linux18 on 2010-09-05
take out every non-ubuntu HDD, then run the commands, unless you mean partitions, in which case show a screenshot with gparted or post the boot info script

---

### Post by GARoss on 2010-09-05
Thanks,
I checked & Ubuntu is installed on sda1. So in a terminal, do I type *sudo grub-install /dev/sda**[COLOR="Red"]1[/COLOR]** && sudo update-grub* or as you originally said, *sudo grub-install /dev/sda && sudo update-grub*?

---

### Post by linux18 on 2010-09-05
sda1 or sda, it doesn't matter because if no number is specified it defaults to sda1

---

### Post by oldfred on 2010-09-05
Unless you are using some other boot loader you do not want to install grub to a partition like sda1. You install grub to sda, sdb or sdc and it is usually better to have grub's boot loader in the MBR of the same drive as the Ubuntu install. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by GARoss on 2010-09-05
> **linux18 said:**
> sda1 or sda, it doesn't matter because if no number is specified it defaults to sda1

Tried it both ways from the Live CD but it cannot find the file. It says it doesn't exist. I suspect it's because I cannot access grub from the LIVE CDs terminal & I cannot figure out how to navigate to it from the terminal.

---

### Post by linux18 on 2010-09-05
type df into a trminal and post that

---

### Post by oldfred on 2010-09-05
When you reinstall  from a liveCD you have to let grub know where it is installed by mounting the partition grub is in. If you post the boot info script results I can give you specific instructions. Otherwise the links I have posted or:

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by GARoss on 2010-09-05
> **oldfred said:**
> Unless you are using some other boot loader you do not want to install grub to a partition like sda1. You install grub to sda, sdb or sdc and it is usually better to have grub's boot loader in the MBR of the same drive as the Ubuntu install. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Thanks oldfred, but, I cannot boot into Ubuntu at the moment to do as you suggested. All I get is what is seen in photo 1. I can boot into Win7 by typing in "exit" into the grub> line. 

I can boot to the Ubuntu's live cd desktop. From there I can use Nautilus to navigate to my folders in Ubuntu 10.04 to view & edit. I don't know if I can get to the installed folders using the terminal that's in the live cd or not.

---

### Post by wilee-nilee on 2010-09-06
You can run the bootscript from the live cd.

---

### Post by GARoss on 2010-09-06
Sorry I can keep up. I appreciate your help.:)

I've been typing from my Mac & had my PC off. Rebooting liveCD now.

All I want to do is to fix the broken grub from the liveCD if possible. Be back soon.

---

### Post by GARoss on 2010-09-06
> **linux18 said:**
> type df into a trminal and post that

ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1995400     53356   1942044   3% /
none                   1990156       392   1989764   1% /dev
/dev/sr0                702610    702610         0 100% /cdrom
/dev/loop0              670592    670592         0 100% /rofs
none                   1995400       104   1995296   1% /dev/shm
tmpfs                  1995400        12   1995388   1% /tmp
none                   1995400        88   1995312   1% /var/run
none                   1995400         4   1995396   1% /var/lock
none                   1995400         0   1995400   0% /lib/init/rw
ubuntu@ubuntu:~$

---

### Post by GARoss on 2010-09-06
> **oldfred said:**
> When you reinstall  from a liveCD you have to let grub know where it is installed by mounting the partition grub is in. If you post the boot info script results I can give you specific instructions. Otherwise the links I have posted or:

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Here's RESULTS.txt

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/burg.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   146,303,954   146,303,892  83 Linux
/dev/sda2         562,724,881   586,099,394    23,374,514   5 Extended
/dev/sda5         562,724,883   586,099,394    23,374,512  82 Linux swap / Solaris
/dev/sda3         146,303,955   562,724,819   416,420,865   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   145,211,534   145,211,472   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 300.1 GB, 300090728448 bytes
16 heads, 63 sectors/track, 581463 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   586,114,703   586,114,641   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a5429f48-a054-40f2-9a0b-90d5ca53d572   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        53146EFC3E6DA0D6                       ntfs       Video Storage 2               
/dev/sda5        d22a5588-e21c-44e3-9679-04d5598e5536   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8878AC7578AC63A2                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        AE24A22624A1F20F                       ntfs       Video Storage 1               
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found
error: /dev/sdi: No medium found
error: /dev/sdj: No medium found
error: /dev/sdk: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=a5429f48-a054-40f2-9a0b-90d5ca53d572 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=a5429f48-a054-40f2-9a0b-90d5ca53d572 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a5429f48-a054-40f2-9a0b-90d5ca53d572 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=a5429f48-a054-40f2-9a0b-90d5ca53d572 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a5429f48-a054-40f2-9a0b-90d5ca53d572 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a5429f48-a054-40f2-9a0b-90d5ca53d572 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a5429f48-a054-40f2-9a0b-90d5ca53d572
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 8878ac7578ac63a2
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a5429f48-a054-40f2-9a0b-90d5ca53d572 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d22a5588-e21c-44e3-9679-04d5598e5536 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  38.8GB: boot/grub/core.img
  13.1GB: boot/grub/grub.cfg
  38.8GB: boot/initrd.img-2.6.32-21-generic
  38.9GB: boot/initrd.img-2.6.32-22-generic
  38.9GB: boot/initrd.img-2.6.32-23-generic
  38.7GB: boot/vmlinuz-2.6.32-21-generic
    .5GB: boot/vmlinuz-2.6.32-22-generic
   1.5GB: boot/vmlinuz-2.6.32-23-generic
  38.9GB: initrd.img
  38.9GB: initrd.img.old
   1.5GB: vmlinuz
    .5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  90 37 75 05 00 00 00 01  |.........7u.....|
000001c0  01 00 07 0f ff ff 3f 00  00 00 51 66 ef 22 00 00  |......?...Qf."..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 b0 aa 64 01 00 00  |............d...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh sdi sdj sdk

---

### Post by GARoss on 2010-09-06
> **oldfred said:**
> When you reinstall  from a liveCD you have to let grub know where it is installed by mounting the partition grub is in. If you post the boot info script results I can give you specific instructions. Otherwise the links I have posted or:

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

This fix it! I'll mark it solved. Thanks to all that replied. :popcorn:

---

