---
title: "Grub2, Windows 7, Headaches..."
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by c0rsana on 2010-09-15
Alright, here's my problem...
My original system was a 20 GB ubuntu partition and a 100 GB windows 7 partition, the grub in working order and all that. After a while, I decided to get rid of the ubuntu partitions and install a smaller partition of LinuxMint (Extremely similar, with some ups and downs of it's own...)

Now, even after I tried the solution [here]("http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/"), the computer boots directly into Mint without a second thought.

My windows 7 drive is on /dev/sda3, and it's worked before.

Any suggestions?

---

### Post by ronparent on 2010-09-15
Open a terminal in Mint and write:

> sudo update-grub

---

### Post by c0rsana on 2010-09-15
Still boots with the same result.

The underscore appears in the tope left corner, blinks, the screen goes black for a second, the underscore blinks for a few more seconds, then it starts in Mint as usual. :\

---

### Post by c0rsana on 2010-09-15
Think I must have had the wrong partition for windows. In an attempt to get back into windows, I went into the startup manager and changed the default system to "Windows 7" {

Now, whenever I start the computer normally, it runs the memory test test... *Knocks head against wall repeatedly*

I ran```
sudo fdisk -l /dev/sda
``` and it looks as if the windows partition is on /dev/sda3. I put (hd0,3) in for the drive, and that apparently runs the memory test...

---

### Post by wilee-nilee on 2010-09-15
Is the mint install using grub-legacy or grub2? If it is grub legacy you need to reload the OS with grub2 and  boot it to run, this will chainload the mint to grub.gfg
```
sudo update-grub
```

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Really before you do anything post the bootscript in my signature in code tags as described, this will give us the lowdown of your setup.

---

### Post by c0rsana on 2010-09-15
Here's what was in the RESULTS.txt:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 9 Isadora
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    293,187,582   312,580,095    19,392,514   5 Extended
/dev/sda5         293,187,584   311,654,399    18,466,816  83 Linux
/dev/sda6         311,656,448   312,580,095       923,648  82 Linux swap / Solaris
/dev/sda3                  63   293,187,552   293,187,490   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2048 MB, 2048728064 bytes
64 heads, 63 sectors/track, 992 cylinders, total 4001422 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            245     3,999,743     3,999,499   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       a7b51583-cacf-7347-99e8-6a2bd1f76558   ext2       casper-rw                     
/dev/sda1: PTTYPE="dos" 
/dev/sda3        4E4891F94891DFCF                       ntfs                                     
/dev/sda5        91981583-6f68-4d38-bace-95415c2ae621   ext4                                     
/dev/sda6        13ea0135-845a-467d-be62-356a43f071e4   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AE9A-A577                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda5        /media/91981583-6f68-4d38-bace-95415c2ae621 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/loop1       /media/casper-rw         ext2       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=91981583-6f68-4d38-bace-95415c2ae621 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=91981583-6f68-4d38-bace-95415c2ae621

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Linux Mint 9 Isadora, kernel 2.6.32-21-generic
uuid		91981583-6f68-4d38-bace-95415c2ae621
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=91981583-6f68-4d38-bace-95415c2ae621 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-21-generic

title		Linux Mint 9 Isadora, kernel 2.6.32-21-generic (recovery mode)
uuid		91981583-6f68-4d38-bace-95415c2ae621
kernel		/boot/vmlinuz-2.6.32-21-generic root=UUID=91981583-6f68-4d38-bace-95415c2ae621 ro  single
initrd		/boot/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		91981583-6f68-4d38-bace-95415c2ae621
kernel		/boot/grub/core.img

title		Linux Mint 9 Isadora, memtest86+
uuid		91981583-6f68-4d38-bace-95415c2ae621
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
title Windows 7 Ultimate
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="2"
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 91981583-6f68-4d38-bace-95415c2ae621
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 91981583-6f68-4d38-bace-95415c2ae621
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 91981583-6f68-4d38-bace-95415c2ae621
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5)" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 91981583-6f68-4d38-bace-95415c2ae621
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=91981583-6f68-4d38-bace-95415c2ae621 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda5) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 91981583-6f68-4d38-bace-95415c2ae621
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=91981583-6f68-4d38-bace-95415c2ae621 ro single  splash vga=786
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows 7 Ultimate Edition&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 91981583-6f68-4d38-bace-95415c2ae621
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 91981583-6f68-4d38-bace-95415c2ae621
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=91981583-6f68-4d38-bace-95415c2ae621 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=13ea0135-845a-467d-be62-356a43f071e4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 152.4GB: boot/grub/core.img
 157.4GB: boot/grub/grub.cfg
 157.4GB: boot/grub/menu.lst
 152.8GB: boot/initrd.img-2.6.32-21-generic
 152.5GB: boot/vmlinuz-2.6.32-21-generic
 152.8GB: initrd.img
 152.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  19 f1 3f 44 e3 7f bc f8  8b ab d8 ef 9b 6e 6a fc  |..?D.........nj.|
00000010  09 a1 37 66 3f aa 00 53  a9 44 12 98 88 bb 18 50  |..7f?..S.D.....P|
00000020  49 c5 74 d2 75 be 6d f5  bb be 82 f5 2c f1 08 f9  |I.t.u.m.....,...|
00000030  c1 43 f2 f9 0b 85 20 f8  9c 19 46 04 fa 4a 2b 1d  |.C.... ...F..J+.|
00000040  ec 81 be 48 bd a2 30 ac  b3 3f c3 ab 64 ef 67 ac  |...H..0..?..d.g.|
00000050  18 f9 0e ad 6b d4 7f 77  23 f6 61 60 34 c9 1e 82  |....k..w#.a`4...|
00000060  7d f2 87 2e f8 11 df bb  60 7f 88 f8 7a db 57 dc  |}.......`...z.W.|
00000070  ec 21 9a df d1 9f 9f 7e  f0 21 e9 b6 7b 63 0b 07  |.!.....~.!..{c..|
00000080  4b a8 17 ae 43 8f c6 bc  f6 9b 77 ee ee a3 e7 6c  |K...C.....w....l|
00000090  0b cb e7 a1 2b 1d a3 c6  79 ca 86 7d 7a 38 c8 3b  |....+...y..}z8.;|
000000a0  c8 cf 23 b6 d7 a6 5a 80  87 59 0c f6 d5 f4 a6 18  |..#...Z..Y......|
000000b0  ec 52 b8 9d c1 16 97 b6  0d b4 48 8b ad af 5d 39  |.R........H...]9|
000000c0  9f 04 ff 64 d3 46 02 f7  d5 9d 7e 6f 07 6c a7 53  |...d.F....~o.l.S|
000000d0  2f 01 e7 db b5 f4 59 8b  87 b4 5d e0 ef da da ad  |/.....Y...].....|
000000e0  9b 96 09 5f 2c bd 77 0c  79 9b 3b 7f fc 7e 2f e9  |..._,.w.y.;..~/.|
000000f0  4e d3 9c 9b 03 cf af 99  fe 59 c4 0f 5a 56 11 bf  |N........Y..ZV..|
00000100  43 70 bb ad ef f5 52 ea  8d 95 12 e2 89 3b a3 5e  |Cp....R......;.^|
00000110  b1 be 83 5a f1 b5 43 72  b8 87 ad df 87 a4 88 f7  |...Z..Cr........|
00000120  f0 3c 2f e4 db 50 bf ba  3a 6e c5 7b 67 34 d5 bb  |.</..P..:n.{g4..|
00000130  1e df dc e3 f8 7d 5a 3c  2a 94 90 af 6e 57 c3 12  |.....}Z<*...nW..|
00000140  50 98 3f 38 db 2f 6f 96  9c 8d db 15 b4 73 da 37  |P.?8./o......s.7|
00000150  59 f7 f5 cb a6 d1 85 df  fd 31 73 ae e7 00 f9 af  |Y........1s.....|
00000160  bb f1 eb c6 73 f8 5e 62  18 ab f5 d2 eb be 68 63  |....s.^b......hc|
00000170  6e e5 61 e2 67 29 bc 5a  86 9d 60 9e 3d f8 7d 9c  |n.a.g).Z..`.=.}.|
00000180  db b1 6b 04 f9 7d 2c 59  34 f1 fc 0a 5f 9d 05 6a  |..k..},Y4..._..j|
00000190  bc 5c 45 ff 4f 1d 6c 0b  82 27 93 46 25 72 c9 77  |.\E.O.l..'.F%r.w|
000001a0  c4 3b c9 79 fe 52 eb 11  af bb 61 6a 0c 79 4b c2  |.;.y.R....aj.yK.|
000001b0  28 cf 02 19 d3 c2 eb c8  57 81 ce ac f2 0a 00 fe  |(.......W.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c8 19 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  19 01 00 20 0e 00 00 00  |........... ....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

I'm running off a flash drive turned live-CD with a small amount of memory currently, so just somehow running off my main hard disk would be helpful...

---

### Post by wilee-nilee on 2010-09-15
So as I suspected you have grub-legacy and grub2, there are others on the forum who are very good at this so standby so to speak.

---

### Post by c0rsana on 2010-09-15
Tried fixing it using the first of my 2 usb live cd's, with the second method here:
> [https://help.ubuntu.com/community/Gr...0from%20LiveCD](https://help.ubuntu.com/community/Gr...0from%20LiveCD)
Because the first method just wasn't mounting anything. Good thing I have a backup live disk >.<

Just not touching anything else at this point... *Steps slowly away from keyboard*

---

### Post by oldfred on 2010-09-15
I am not sure what you have done to get partitions in the order they are in. Win7 when separately installed has a hidden boot/recovery partition that has /bootmgr /Boot/BCD and then in the main install is only /Windows/System32/winload.exe.

Since you  only have the winload.exe file you must have overwritten the boot partition. Move the boot flag to sda3 so the windows repair disk will see the windows partition and run repairs to add the bootmgr & BCD  to sda3.

set boot flag on for sda3 (off for others)
sudo sfdisk -A3 /dev/sda

You should not have to run fixMBR and if you do you will have to use a liveCD to reinstall grub2.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by wilee-nilee on 2010-09-15
> **c0rsana said:**
> Tried fixing it using the first of my 2 usb live cd's, with the second method here:

Because the first method just wasn't mounting anything. Good thing I have a backup live disk >.<

Just not touching anything else at this point... *Steps slowly away from keyboard*

I think your in okay shape it just needs a knowledgeable helper, I fail in this area, amongst others.;) I missed the missing Windows boot files as well.

---

### Post by c0rsana on 2010-09-16
Ok, did everything in olffred's post.

The only 2 wierd things that came up:

When I ran BootRec.exe /FixBoot, it said "BootRec.exe is not a runnable program, batch file, etc..."

And now, when I start up, it goes to windows... But "BOOTMGR" is missing...

---

### Post by c0rsana on 2010-09-16
Scratch that, now only the BOOTMGR is missing. Press ctrl+alt+del to restart. >.<

And just noticed that when I run BootRec.exe /ScanOs, it detects 0 windows installations...

---

### Post by c0rsana on 2010-09-16
Nevermind that, I ran the given startup repair thing on the disk, and that found and fixed the problem. Solved! :D :D :D

---

