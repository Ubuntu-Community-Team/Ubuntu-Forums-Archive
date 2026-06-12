---
title: "Precautions to take when upgrading windows on windows/kubuntu dualboot PC?"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by Istrebitel on 2010-05-31
Greetings.

I have a Vista/Kubuntu dualboot, with grub2 as my loader. Because i have read that Windows likes to ignore something else present on the system and overwrite everything with itself. So i installed Vista, then Kubuntu.

Now i want to upgrade my Vista to Win7. My question is - what should i do in order to keep my current dualboot intact (Grub2 as a loader, and kubuntu fully functional). 

I fear Win7 might even never ask me about keeping my kubuntu dualboot, just overwrite everything. 

PS: My bootinfoscript output
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sdi

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   468,738,047   468,736,000  83 Linux
/dev/sdb2         468,740,094   488,396,799    19,656,706   5 Extended
/dev/sdb5         468,740,096   488,396,799    19,656,704  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   488,394,751   488,392,704   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdi1                  63 2,930,272,064 2,930,272,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A42C6CD12C6C9FD2                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        35ec6054-3f59-4d91-a8f8-4cc0e3eee916   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        67209fde-281a-4b32-acfb-44dfa9c5bf6e   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        32C47895C4785D53                       ntfs       &#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1085;&#1099;&#1081; &#1040;&#1092;&#1077;&#1088;&#1080;&#1089;&#1090;
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        84983C23983C1660                       ntfs       &#1061;&#1091;&#1081; &#1042;&#1086;&#1076;&#1086;&#1074;&#1086;&#1079;&#1085;&#1099;&#1081;   
/dev/sdd: PTTYPE="dos" 
/dev/sdi1        7604309904305DF5                       ntfs       &#1057;&#1098;&#1077;&#1084;&#1085;&#1099;&#1081; &#1052;&#1086;&#1079;&#1075;&#1086;&#1089;&#1086;&#1089;
/dev/sdi: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 35ec6054-3f59-4d91-a8f8-4cc0e3eee916
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 35ec6054-3f59-4d91-a8f8-4cc0e3eee916
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
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 35ec6054-3f59-4d91-a8f8-4cc0e3eee916
insmod tga
if background_image /usr/share/images/grub/Sparkler.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 35ec6054-3f59-4d91-a8f8-4cc0e3eee916
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=35ec6054-3f59-4d91-a8f8-4cc0e3eee916 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 35ec6054-3f59-4d91-a8f8-4cc0e3eee916
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=35ec6054-3f59-4d91-a8f8-4cc0e3eee916 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 35ec6054-3f59-4d91-a8f8-4cc0e3eee916
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 35ec6054-3f59-4d91-a8f8-4cc0e3eee916
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set a42c6cd12c6c9fd2
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=35ec6054-3f59-4d91-a8f8-4cc0e3eee916 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=67209fde-281a-4b32-acfb-44dfa9c5bf6e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 227.7GB: boot/grub/core.img
 199.8GB: boot/grub/grub.cfg
 227.9GB: boot/initrd.img-2.6.32-22-generic-pae
 227.7GB: boot/vmlinuz-2.6.32-22-generic-pae
 227.9GB: initrd.img
 227.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  bd 2c 0e 8c 4e a9 a5 42  3e 0b 4c f3 2a 25 55 3d  |.,..N..B>.L.*%U=|
00000010  3c b9 10 00 d0 5f 62 e3  c6 67 dc a9 5f 03 98 5d  |<...._b..g.._..]|
00000020  ff a1 0f ef e5 92 55 fd  e5 4e 36 94 55 24 c9 b7  |......U..N6.U$..|
00000030  af 4f 43 3e b8 20 16 24  a0 f0 ba e7 ad fb 8d 0e  |.OC>. .$........|
00000040  8b 98 1e d7 fb b8 79 45  96 1d eb 80 99 0b b9 64  |......yE.......d|
00000050  83 34 83 ed 7c f4 a2 da  5e dd f2 2f 52 85 6a 75  |.4..|...^../R.ju|
00000060  a3 2b 4d 10 a4 36 6d d4  56 7f ea 6b 4a bf ae 3f  |.+M..6m.V..kJ..?|
00000070  a9 77 eb fe 97 0b bf d4  64 2b 1c a1 a1 67 f0 98  |.w......d+...g..|
00000080  1e ec e5 00 47 10 11 10  e1 25 cb dc 7d 42 0d fe  |....G....%..}B..|
00000090  e5 ed da da 20 c1 f0 98  1f ff c8 6a 38 96 88 13  |.... ......j8...|
000000a0  e8 18 8b 2a 61 54 cb 8b  2e 4b da 79 bd cb bb d3  |...*aT...K.y....|
000000b0  0b f3 d5 68 e1 6f 8c ae  b3 6e 64 30 47 bb 7a 98  |...h.o...nd0G.z.|
000000c0  af 06 96 df 18 88 62 58  cf 51 f0 d0 d6 9f 13 76  |......bX.Q.....v|
000000d0  7e 3e ed ff 2d c5 04 c6  b7 04 6a d0 42 20 91 7f  |~>..-.....j.B ..|
000000e0  d2 2c 8c 97 3d d5 5a 02  3a 39 a7 33 df ef ab 88  |.,..=.Z.:9.3....|
000000f0  1c 93 b1 13 d0 e8 59 d4  77 92 a9 d9 4f 0a 97 b3  |......Y.w...O...|
00000100  2d d5 71 0d ca ee 5e 32  c5 10 41 5b ad 04 8e 5d  |-.q...^2..A[...]|
00000110  a1 01 76 d5 f7 7a 03 01  bb 2b 7e 53 16 11 4b c5  |..v..z...+~S..K.|
00000120  68 d1 fa 49 e5 94 08 e0  eb 6e 4c e5 f8 de 89 f9  |h..I.....nL.....|
00000130  8c 90 ab cc 87 f6 7b b7  ff 36 9d f3 83 09 8b e8  |......{..6......|
00000140  1e ec f6 a0 47 10 11 11  6d 27 aa de 6e e4 59 23  |....G...m'..n.Y#|
00000150  da d3 67 29 9e ce 54 5b  6b 9c 67 99 19 87 fc ec  |..g)..T[k.g.....|
00000160  64 7c 80 ce dd bd 1b 56  4c 31 4e 44 f8 b5 27 64  |d|.....VL1ND..'d|
00000170  b2 c7 cb c4 28 9a 29 4c  de 2e 2f bc 4f d7 af 1b  |....(.)L../.O...|
00000180  e4 fc 54 56 f7 de 31 9e  c9 67 cd de f3 38 ad 48  |..TV..1..g...8.H|
00000190  b6 da a8 6c b3 3f 0e 10  b9 c1 cd 67 86 1e 45 de  |...l.?.....g..E.|
000001a0  30 b7 fd 4a ac 09 0c bf  18 0a dc c8 d2 df 06 61  |0..J...........a|
000001b0  5e a7 09 a4 57 74 79 6b  d0 1a 8a 50 39 da 00 fe  |^...Wtyk...P9...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 2b 01 00 00  |............+...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 

```

---

### Post by Mark Phelps on 2010-06-01
> **Istrebitel said:**
> My question is - what should i do in order to keep my current dualboot intact (Grub2 as a loader, and kubuntu fully functional)

Basically, you can't.  Win7, like all other MS Windows OSs, will overwrite the MBR with its own code.  You can't control or prevent that.

You will have to boot from a Kubuntu LiveCD afterward and reinstall GRUB.

---

### Post by Istrebitel on 2010-06-02
Ah.... I see. I should look for that option in the boot menu of the cd where i choose language and try ubuntu/install ubuntu yes?

---

### Post by dtfinch on 2010-06-02
You don't want to reinstall Ubuntu, just grub.

There's instructions on several different ways to do it here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Or more specific to grub 2:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Yathi on 2010-06-02
I did the same thing today. Upgraded to windows 7 n then reinstalling grub2 back was a piece of cake. But i had set my c drive to mount automatically when i had installed ubuntu by setting a mount point. Now since i formatted my c drive to install windows 7, tat drive is not being mounted. How can i again set it to mount automatically?

---

### Post by Istrebitel on 2010-06-02
Erm, thank you it clears almost everything up.

Except for one thing, i have the first (set to be booted from in bios) drive used by windows. And grub was installed there automatically when i installed kubuntu. If i would understake the "simplest" method from [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD), should i then mount this drive (windows drive) to /mnt yes?
Or should i still mount kubuntu drive (in that case i suppose that i will install the grub into mbr of the other drive, not the one bios is booting my system from?)

Or should i just let windows disk have mbr with windows loader, and kubuntu disk with grub, and switch it in bios so the system is being booted from the disk where grub is?

---

