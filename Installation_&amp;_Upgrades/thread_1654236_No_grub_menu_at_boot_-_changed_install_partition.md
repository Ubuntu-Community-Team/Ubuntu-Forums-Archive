---
title: "No grub menu at boot - changed install partition"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by Yumi on 2010-12-28
Have a dual boot with XP on sdb1. Reinstalled Maverick as it developed some problems due to updates during the Beta phase.

Decided to move the program installation to sdb5 as this is a smaller partition and to keep sdb2 for data only.

Ubuntu works fine and comes up again if I do a "Restart". However, after I "Shutdown" I only get the grub> prompt.

/boot/grub is on sdb5. If I type "sudo grub" in the terminal I get "sudo: grub: command not found"

My guess is that the MBR has to be changed. But how to?

Michael

---

### Post by karthick87 on 2010-12-28
The right command is,but it wont solve your problem i guess.
```
sudo update-grub
```
Boot using a live ubuntu cd and post the results of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code (#) tags.

---

### Post by amsterdamharu on 2010-12-28
When in the grub2 command mode type the following command:
```
search --file /boot/grub/ext2.mod
```This should give you hd0,7 (0,7 is an example you might have different values)

Then type the following commands (replace 0,7 with the values you got from the first command) In this I use root=[COLOR=Red]/dev/sdb5[/COLOR]  that is where Ubuntu was installed. I am just guessing here you can try  1 through 12, the wrong one gives you a kernel panic so you have to  retry another one like /dev/sdb4:
```
insmod ext2
set root='(hd0,7)'
linux /boot/vmlinuz(press tab to autocomplete or get a list) root=/dev/[COLOR=Red]sdb5[/COLOR]
initrd /boot/initrd(press tab, make sure the initrd has the same version number as vmlinuz)
boot
```

When you're booted in Ubuntu you have to re install grub and update the grub menu but we need the output of the boot info script to advice you on how to do that.

---

### Post by Yumi on 2010-12-28
Thanks for the suggestions.

The script when executed sits there after a > and is blinking like it is working. Maybe takes a long time?

Before I posted I did a reinstall and am running my ubuntu installation. Have no Disk but installed from USB stick which is very slow. Installing from it works but "try Ubuntu" does not work after over an hour waiting.

I am reluctant to shut down to get to the grub menu. Is there a way to execute the search --file /boot/grub/ext2.mod within the runnin ubuntu? Looked in Nautilus and /boot/grub/ext2.mod is there. But I need the value of hd0.X

Michael

---

### Post by amsterdamharu on 2010-12-28
```
Is there a way to execute the search --file /boot/grub/ext2.mod within the runnin ubuntu?
```

No not really, these are grub commands. Both the terminal and grub usually have a black screen where you can type stuff but they are totally different. The grub command is sort of an inter active start my operating system command line and the terminal is the started operating system.
From grub command you could type commands to start Windows if it's there and working.

Now to go back to the very first replies, could you post the output of the boot info script?

I don't have a working google right now but it should be easy to find.

---

### Post by Yumi on 2010-12-28
This time it executed. The result.txt is
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    78,139,391    78,137,344   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    58,605,119    58,605,057   7 HPFS/NTFS
/dev/sdb2          58,605,120   132,809,354    74,204,235  83 Linux
/dev/sdb3         132,809,479   156,296,384    23,486,906   5 Extended
/dev/sdb5    *    136,761,345   156,296,384    19,535,040  83 Linux
/dev/sdb6         132,809,481   136,745,279     3,935,799  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        39155031306755DB                       ntfs       Michael Mobile Data           
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AECCB208CCB1CB3B                       ntfs       WINXP                         
/dev/sdb2        c759bb55-f0b3-4547-adf4-c5b8c668a5ed   ext3       Ubuntu Data                   
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        225fbc22-3896-4a9b-b90d-6783c119071a   ext3                                     
/dev/sdb6        dda5b86f-4d26-4d96-8b60-7c988eaf2945   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/Michael Mobile Data fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/c759bb55-f0b3-4547-adf4-c5b8c668a5ed ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/WINXP             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\Arldr="DOS¹€ŸßÏä"


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 225fbc22-3896-4a9b-b90d-6783c119071a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 225fbc22-3896-4a9b-b90d-6783c119071a
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 225fbc22-3896-4a9b-b90d-6783c119071a
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=225fbc22-3896-4a9b-b90d-6783c119071a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 225fbc22-3896-4a9b-b90d-6783c119071a
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=225fbc22-3896-4a9b-b90d-6783c119071a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 225fbc22-3896-4a9b-b90d-6783c119071a
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=225fbc22-3896-4a9b-b90d-6783c119071a ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 225fbc22-3896-4a9b-b90d-6783c119071a
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=225fbc22-3896-4a9b-b90d-6783c119071a ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 225fbc22-3896-4a9b-b90d-6783c119071a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 225fbc22-3896-4a9b-b90d-6783c119071a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set aeccb208ccb1cb3b
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=dda5b86f-4d26-4d96-8b60-7c988eaf2945 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  73.1GB: boot/grub/core.img
  73.1GB: boot/grub/grub.cfg
  73.2GB: boot/initrd.img-2.6.35-22-generic
  73.2GB: boot/initrd.img-2.6.35-24-generic
  73.1GB: boot/vmlinuz-2.6.35-22-generic
  73.1GB: boot/vmlinuz-2.6.35-24-generic
  73.2GB: initrd.img
  73.2GB: initrd.img.old
  73.1GB: vmlinuz
  73.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  9a 43 26 30 1c fb c8 37  42 7f dc 8e 8b c8 41 fa  |.C&0...7B.....A.|
00000010  2f 40 2b 3d fb 98 1c e9  11 c6 9a 74 ea 4a ce 02  |/@+=.......t.J..|
00000020  eb 0d 55 04 49 9b 32 02  3d cd 59 c2 0d 24 49 ce  |..U.I.2.=.Y..$I.|
00000030  6c 22 80 6e c0 07 b8 e4  55 9c f5 4a 9c d0 ae 14  |l".n....U..J....|
00000040  2e 75 aa 5e 58 89 22 aa  25 8e ac d7 14 8d af 31  |.u.^X.".%......1|
00000050  29 ea fb 9e fc 4d 8c 1a  ac 0b 20 f5 0d f4 3a cb  |)....M.... ...:.|
00000060  f3 b7 7c 38 7c f5 a8 65  94 90 23 18 38 e7 26 ff  |..|8|..e..#.8.&.|
00000070  b0 e9 a3 ae 41 78 82 c2  9e c0 ed df 99 35 07 62  |....Ax.......5.b|
00000080  3b 1b ae bc bc 8f 1f f0  6a bc a4 ee 52 6d 67 b6  |;.......j...Rmg.|
00000090  b1 67 e9 53 67 d1 6f 59  d3 74 87 57 14 68 f7 b9  |.g.Sg.oY.t.W.h..|
000000a0  3c b1 7d 9c f1 86 f5 37  90 0c b0 d2 03 05 79 e8  |<.}....7......y.|
000000b0  05 84 f1 e5 33 06 96 5a  2d 2d ed 02 3b 6d b2 a8  |....3..Z--..;m..|
000000c0  d0 89 02 94 b2 14 34 05  bf b7 53 f8 5c ee 2c af  |......4...S.\.,.|
000000d0  c2 86 dd 5b 89 ee 1f de  2b 84 4d ba 80 7d d5 61  |...[....+.M..}.a|
000000e0  e5 8c 10 2c c2 de 51 ab  bb 23 df ab a2 25 6e 43  |...,..Q..#...%nC|
000000f0  7f 2b 5b eb 44 ef 75 53  dd a4 75 a6 d8 e0 7d e9  |.+[.D.uS..u...}.|
00000100  bc dd a1 82 33 e5 41 2e  61 d3 1d 70 b3 11 15 08  |....3.A.a..p....|
00000110  dc 1f 57 f5 0a 12 ff b2  bf ef de a7 c5 6f 2f 34  |..W..........o/4|
00000120  18 6f 74 c5 23 af f4 43  de 50 b4 2b 38 94 49 99  |.ot.#..C.P.+8.I.|
00000130  de 6f f4 6d 99 84 bd ce  47 dd ef 59 7c c2 ec d0  |.o.m....G..Y|...|
00000140  bb d0 77 4d b3 ab e9 60  be b7 44 a8 50 6a 0e 3f  |..wM...`..D.Pj.?|
00000150  ab 9d ce 4c 16 3e 16 89  b7 df d9 f2 6e 42 d3 18  |...L.>......nB..|
00000160  3f 7d c8 34 05 25 4a f6  8a 78 9d 50 b5 18 82 2a  |?}.4.%J..x.P...*|
00000170  0b 72 79 c3 70 6f d9 64  61 d6 d3 c4 a7 00 c3 60  |.ry.po.da......`|
00000180  7d 33 71 33 44 db 1d db  50 f1 a6 db 51 85 40 54  |}3q3D...P...Q.@T|
00000190  a3 73 7e 20 62 dc 6f fe  d8 1b 7a c9 aa c1 69 c8  |.s~ b.o...z...i.|
000001a0  74 40 94 52 23 01 50 78  8d 79 ab f0 14 f2 6b 42  |t@.R#.Px.y....kB|
000001b0  a7 b8 8b 90 bd 7a 0f d7  c0 e3 9c 3d cf 48 80 fe  |.....z.....=.H..|
000001c0  ff ff 83 fe ff ff fa 4c  3c 00 c0 14 2a 01 00 fe  |.......L<...*...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 38 0e 3c 00 00 00  |..........8.<...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by amsterdamharu on 2010-12-28
You can run the update-grub command to see if it re creates the grub.cfg (in /boot/grub)
```
sudo update-grub
```

Your /etc/fstab points to a wrong root partition, I guess passing the value in the grub menu solved it instead of getting a kernel panic. You should change it though.

press alt + F1, type "sudo gedit /etc/fstab" (no quotes) and click run.
Replace the line:
```
/dev/sda5       /               ext3    errors=remount-ro 0       1
```
with:
```
UUID=225fbc22-3896-4a9b-b90d-6783c119071a      /               ext3    errors=remount-ro 0       1
```

---

### Post by Yumi on 2010-12-28
```
sudo update-grub
```
generated a new grub.cfg file in /boot/grub/

Edited fstab as you suggested.

Am to nervous to try it out and shutdown the computer. Will finish my days work and then see tomorrow morning. :confused:

Thank you very much for the quick help. Sounded very professional.

Michael

---

### Post by amsterdamharu on 2010-12-28
It's great that it worked. 

If you have the commands written down you should be able to boot the same way next time; that is if the menu don't show and it boots without the need of user input.

---

### Post by Yumi on 2010-12-28
Changed situation. This morning I am faced with

```
error: out of disk
grub rescue>
```

I tried the commands from further up but some are not accepted under grub rescue, some just do nothing.

Looked at the manual and tried "**insmod /boot/grub/normal.mod**" but it just repeads the error: out of disk, grub resucue> message. No return to the normal grub promt.

---

### Post by amsterdamharu on 2010-12-28
Can you set your BIOS to boot from the second harddisk?

---

### Post by Yumi on 2010-12-28
The second HD sda is an external USB HD. But I have 10.10 on a USB stick and booted from there. Took 2 hours! and now it does not react to my USB keyboard nor my USB mouse. If I do a hard reset it will take another 2 hours to get Ubuntu off the stick again.

Correction: It reacts to mouse and keyboard but no mouse pointer on the screen. Still managed to open a terminal window and am able to write

---

### Post by Yumi on 2010-12-29
How many times can a man install
before he . . . . . 

I deleted all Ubuntu related Partitions and recreated new ones incl. formating the space. Then reinstalled from USB stick and everything work well. Never found out why and what malfunctioned.

Michael

---

### Post by theozzlives on 2010-12-29
> **Yumi said:**
> How many times can a man install
before he . . . . . 

I deleted all Ubuntu related Partitions and recreated new ones incl. formating the space. Then reinstalled from USB stick and everything work well. Never found out why and what malfunctioned.

Michael

Sometimes you just gotta do it. It sucks but it fixed your problem. Ever since DOS, at times I just had to backup my stuff and start over fresh.

---

