---
title: "Grub rescue no such device"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by yusuo85 on 2011-02-17
Ive just installed ubuntu 10.10 onto a old pc that has windows 7 already running.
Ive kept it on a seperate hard drive but when installed all i get is "grub rescue - no such device (and then a long number)
ive tried installing lilo and restoring the mbr of sda (windows drive) but ubuntu resides on the second drive i use (sdb)
Now restoring the mbr has allowed me to boot back into windows but doesnt give me the option to boot into ubuntu, how do i get this working so I can dual boot,

---

### Post by drs305 on 2011-02-17
I would recommend you download and run the boot info script from the following link. Post the contents of the RESULTS.txt the script generates and we will be able to see your boot status and make informed suggestions.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

It may be as simple as changing the BIOS boot order of your drives, but the RESULTS.txt will tell us.

---

### Post by Kirboosy on 2011-02-17
You are going to have to reinstall grub

Look at [this page]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Now did you pull the ubuntu drive in order to boot Windows 7? If you remove the drive on grub without updating it, it will go into rescue mode.

---

### Post by yusuo85 on 2011-02-17
nope drive is still in the system just ran lilo and set it to recreate a mbr on sda, never touched the drive

Ill run the script as soon as i get a chance

One more thing would i have to install grub to sda (windows drive) or sdb (ubuntu drive)

---

### Post by yusuo85 on 2011-02-17
edited post above with additional question

---

### Post by Kirboosy on 2011-02-17
Was GRUB detecting Windows 7 initially? 

I would highly recommend running that bootscript tool as soon as you can. :)

---

### Post by yusuo85 on 2011-02-17
grub wasnt detecting anything, i turned on the pc and all i got was grub rescue, i dont know what it may of been detecting. i had to use the livecd to replace windows mbr

---

### Post by presence1960 on 2011-02-17
Run the boot info script as drs305 suggested. this will show us your set up & boot process which will eliminate guessing and all this back & forth.

Here is how:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by yusuo85 on 2011-02-17
Heres the results.txt              

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Lilo is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.1 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   156,246,015   156,039,168   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    76,210,175    76,208,128  83 Linux
/dev/sdb2          76,212,222    78,163,967     1,951,746   5 Extended
/dev/sdb5          76,212,224    78,163,967     1,951,744  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        A4D09B0BD09AE33A                       ntfs       System Reserved               
/dev/sda2        88DCA3AADCA3914C                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4824feaa-41b0-43ae-bd95-3177a6e086f4   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        28e6d983-342a-442b-ba9b-0730e4771df8   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set 4824feaa-41b0-43ae-bd95-3177a6e086f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 4824feaa-41b0-43ae-bd95-3177a6e086f4
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
	search --no-floppy --fs-uuid --set 4824feaa-41b0-43ae-bd95-3177a6e086f4
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4824feaa-41b0-43ae-bd95-3177a6e086f4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 4824feaa-41b0-43ae-bd95-3177a6e086f4
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=4824feaa-41b0-43ae-bd95-3177a6e086f4 ro single 
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
	search --no-floppy --fs-uuid --set 4824feaa-41b0-43ae-bd95-3177a6e086f4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 4824feaa-41b0-43ae-bd95-3177a6e086f4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a4d09b0bd09ae33a
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
UUID=28e6d983-342a-442b-ba9b-0730e4771df8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  34.5GB: boot/grub/core.img
  25.9GB: boot/grub/grub.cfg
  32.4GB: boot/initrd.img-2.6.35-22-generic
  34.5GB: boot/vmlinuz-2.6.35-22-generic
  32.4GB: initrd.img
  34.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  92 6e df 77 9f f9 1e 63  93 bb 69 f9 2f 4b 94 3c  |.n.w...c..i./K.<|
00000010  ef a7 e4 6a 48 e6 eb d3  b7 63 ef 54 74 53 96 de  |...jH....c.TtS..|
00000020  7f 9f fc 39 7e 26 2d 80  7f 4f ad 4e f1 82 38 cf  |...9~&-..O.N..8.|
00000030  5f 51 ef 4d 49 af 4b 9d  b1 77 5f 99 4d a0 70 70  |_Q.MI.K..w_.M.pp|
00000040  31 d3 d6 af d9 42 dc 64  7f 7b a1 15 d3 07 af 93  |1....B.d.{......|
00000050  5f f0 c6 b0 76 eb f2 b7  9a 5b 9d 12 c4 be 5f 4e  |_...v....[...._N|
00000060  7d 7f 9f f5 ac 8b b8 5b  0d 8f 4f 51 ed ff 00 d6  |}......[..OQ....|
00000070  c5 6c 4c a5 77 be 9d 0c  a7 82 40 38 cf 5f 4f af  |.lL.w.....@8._O.|
00000080  bd 2c 51 c8 ac 09 dd d4  7f 9e b4 a4 ec 9f 9a b7  |.,Q.............|
00000090  e0 72 54 7f 17 ad be e7  fe 48 b3 26 4a 37 53 c5  |.rT......H.&J7S.|
000000a0  73 73 44 c6 53 ef f5 f5  fa 57 2c dd 95 ba bf cb  |ssD.S....W,.....|
000000b0  53 cd a8 d7 e3 7f 96 a5  ab 6b 47 90 a8 20 f5 f4  |S........kG.. ..|
000000c0  f7 fa d6 ca 69 8e 53 8f  eb f5 fe b5 9a 76 d5 19  |....i.S......v..|
000000d0  14 67 b0 96 11 b8 83 8f  a7 d7 8c e7 fa 53 ec e5  |.g...........S..|
000000e0  31 70 4e 3a f5 c1 ed db  9e 95 d3 06 af 7e ea cb  |1pN:.........~..|
000000f0  ef 3d 1c 3e ff 00 3f fe  44 d2 13 b3 0e 08 3c 7a  |.=.>..?.D.....<z|
00000100  7a ff 00 9e d4 07 24 81  c7 27 fc f7 ad 8f 7b 0f  |z.....$..'....{.|
00000110  b7 cb f4 89 25 15 94 de  b6 e9 6d 7f af b8 ef e6  |....%.....m.....|
00000120  f7 79 ad f2 f9 d8 46 97  0a 47 1c 60 74 3d 88 aa  |.y....F..G.`t=..|
00000130  5f 68 1b fb 75 cf f5 f5  ff 00 3f 4a 94 da d8 c4  |_h..u.....?J....|
00000140  d0 85 c3 e0 7f 20 7d 7d  ff 00 1a b8 10 64 75 ea  |..... }}.....du.|
00000150  3d 3d 7e 95 b4 5d d7 e7  ea 67 3e d7 f3 b5 bd 75  |==~..]...g>....u|
00000160  bf e0 6a 42 80 28 3c ff  00 90 3d aa 53 38 5e 0f  |..jB.(<...=.S8^.|
00000170  61 e8 7e 9e be d5 56 56  de cf b5 8e 1a ab 56 fb  |a.~...VV......V.|
00000180  3f ce c4 ab 2a b0 ce 7b  0e c7 bd 31 b0 49 f4 3f  |?...*..{...1.I.?|
00000190  e1 59 54 e9 f3 39 e3 1e  57 7b df 4e c4 0e 83 03  |.YT..9..W{.N....|
000001a0  af 5f 6f 43 ed 54 e6 8c  1e 39 3c 0f 4f 5f a5 63  |._oC.T...9<.O_.c|
000001b0  28 f3 3b de da 76 3a 68  ef f3 7f 91 9d 2f 00 fe  |(.;..v:h...../..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by drs305 on 2011-02-17
Probably the best way to set this up is to keep lilo on sda (Windows) and install Grub2 on sdb and have your BIOS boot sdb first. Then if Grub2 fails in the future, you can change the boot order back to sda and still boot Windows until you can repair Grub2.

To do this, boot the Ubuntu LiveCD, open a terminal, and run the following:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Do not use the partition number in the second command.

Then reboot, and during the initial boot enter your BIOS setup and have it look for your Ubuntu drive first (sdb).

If Windows doesn't appear in the menu, after you do a normal boot run:
```
sudo update-grub
```
This should locate Windows on sda and place an entry in the Grub2 menu (if it isn't already there).

---

### Post by yusuo85 on 2011-02-17
thanks for the quick reply, now this is where it gets tricky, my bios doesnt give me the option to boot different hdd's only primary hdd or cd drive

---

### Post by yusuo85 on 2011-02-17
solved, its a bit of a long winded way but it will do, i just have to go into the boot menu when turning on the pc by pressing f12, if i dont it will auto try and boot windows without even prompting me, as i said its a bit of a long winded way but it will do

---

### Post by drs305 on 2011-02-17
Make sure you have checked all the various options in BIOS. In mine for instance, there is a BOOT section but the hard drive selection listed under 'Drives' instead, which isn't intuitive at all.

You can run the same commands as I gave you earlier, only replace sdb with sda in the second command. So they would be:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

This should allow G2 to boot, but you lose the lilo backup. Should you need to reinstall lilo for some reason (i.e. the above doesn't work), from the LiveCD:
[LIST]
[*]To reinstall lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Just run those two commands, even though it will state lilo isn't fully installed.
[/LIST]

---

### Post by yusuo85 on 2011-02-17
thanks drs for all your help working as it should be now

---

