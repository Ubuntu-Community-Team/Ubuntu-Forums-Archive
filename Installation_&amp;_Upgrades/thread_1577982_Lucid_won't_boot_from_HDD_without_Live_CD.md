---
title: "Lucid won't boot from HDD without Live CD"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by knightysmith on 2010-09-19
Hi all, 

I have managed to install Ubuntu 10.40 LTS over the weekend and I have got it working... sort of.

My only remaining issue is that I am unable to boot into the Hard Drive where Ubuntu is installed unless I boot from the Live CD and select 'Boot from first hard disk'.

I have checked to make sure my boot priority sequence is correct, and it is, but without the Live CD, if I try to boot I get to the 'load operating system' screen and nothing would happen from there, just a blinking cursor.

I am not dual booting, but I do have 3 internal drives. I have made sure that the drive I am trying to boot to is in fact the drive that Ubuntu has been installed on. I also checked to see if Grub was installed which it didn't appear to be, but has since been installed.

My basic cpecs are:
Processor: AMD Phenom II 550 DualCore 3
Video Card: Gigabyte ATI HD5450 512MB
MOBO: Gigabyte GA-770T-USB3

Irritating! Any suggestions would be greatly appreciated.

Thank you!

---

### Post by presence1960 on 2010-09-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by knightysmith on 2010-09-20
Okay no probs. Here it is (thanks!):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

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
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   224,827,391   224,825,344  83 Linux
/dev/sdc2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sdc5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F49634DE9634A2D2                       ntfs       WD 1.0TB                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C468509868508AD6                       ntfs       Astone                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0c1dc4c1-4875-42d2-81be-93d1ee0d7db8   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        e2acf452-4072-4acf-ac5d-d80405e8d3f1   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Ubuntu 10.04.1 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda1        /media/WD 1.0TB          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 0c1dc4c1-4875-42d2-81be-93d1ee0d7db8
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 0c1dc4c1-4875-42d2-81be-93d1ee0d7db8
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
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 0c1dc4c1-4875-42d2-81be-93d1ee0d7db8
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0c1dc4c1-4875-42d2-81be-93d1ee0d7db8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 0c1dc4c1-4875-42d2-81be-93d1ee0d7db8
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0c1dc4c1-4875-42d2-81be-93d1ee0d7db8 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 0c1dc4c1-4875-42d2-81be-93d1ee0d7db8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 0c1dc4c1-4875-42d2-81be-93d1ee0d7db8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=0c1dc4c1-4875-42d2-81be-93d1ee0d7db8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=e2acf452-4072-4acf-ac5d-d80405e8d3f1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
  36.7GB: boot/grub/grub.cfg
  30.2GB: boot/initrd.img-2.6.32-24-generic
  30.3GB: boot/vmlinuz-2.6.32-24-generic
  30.2GB: initrd.img
  30.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  f3 28 a0 d7 6e 87 5b 0c  05 1d 31 4d 11 65 ad d6  |.(..n.[...1M.e..|
00000010  3d 23 3d 7b d5 6f 4b ea  fd b2 54 d4 20 90 f8 50  |=#={.oK...T. ..P|
00000020  6a ff 08 03 41 bf da c9  10 b3 a5 63 0c 1b 1d f1  |j...A......c....|
00000030  21 b4 f7 65 a8 56 08 ba  b1 37 47 a3 6d 7d fe 99  |!..e.V...7G.m}..|
00000040  b3 2c d7 8a d2 68 5d 41  5f ca 08 43 68 9c d3 7f  |.,...h]A_..Ch...|
00000050  e2 76 00 1b 5f 44 e4 73  9c 9f cc 35 c0 5e ed df  |.v.._D.s...5.^..|
00000060  c4 57 b6 fa 71 7d ad fa  8b 61 80 fd bf 8f 6b b4  |.W..q}...a....k.|
00000070  05 d0 fa 34 70 c8 e4 03  79 1b 4c 2e c6 18 3e 9d  |...4p...y.L...>.|
00000080  2d 3f af cd 95 8f b7 7f  b9 bb c9 c4 40 cd 9e 9c  |-?..........@...|
00000090  9e b7 8c f7 33 b2 34 c1  3f bd dc 64 f3 86 27 6c  |....3.4.?..d..'l|
000000a0  3c 3a 32 ca 81 0e 96 30  9d 7a 99 de 3c ac f9 c5  |<:2....0.z..<...|
000000b0  98 78 d0 cc 51 b8 04 f7  18 e3 7c f0 2e f5 55 5a  |.x..Q.....|...UZ|
000000c0  d3 fd 89 69 28 a0 8c 34  a6 c7 b7 31 10 46 83 de  |...i(..4...1.F..|
000000d0  78 cb e1 1d fd 53 97 10  fb e4 43 e2 5b e8 92 8b  |x....S....C.[...|
000000e0  b2 ec b6 da e4 60 26 78  c4 5d 60 c2 26 9d f8 de  |.....`&x.]`.&...|
000000f0  7d bf e5 57 db 83 02 dc  c4 38 35 0c de 21 11 aa  |}..W.....85..!..|
00000100  84 83 27 85 f5 62 e0 bc  54 93 3e b4 d7 c5 60 02  |..'..b..T.>...`.|
00000110  89 2b 52 3c 99 e1 0b 34  15 bd 11 1e c6 6c 9f 08  |.+R<...4.....l..|
00000120  50 86 d4 de 96 89 e1 67  31 00 9f 5a 1b 45 b2 ff  |P......g1..Z.E..|
00000130  0e ba 3a 9b cd 71 b8 ea  7d 17 61 dc 79 1a 82 a5  |..:..q..}.a.y...|
00000140  4c 06 b6 fa a8 2c 30 7d  80 68 7d 1e d8 14 66 50  |L....,0}.h}...fP|
00000150  06 ba 81 86 3f ad 1d 6d  1e 45 d5 92 89 bf 08 67  |....?..m.E.....g|
00000160  12 a8 fa 03 84 9c 11 ab  73 1c 6f dc 81 73 de ba  |........s.o..s..|
00000170  87 21 62 ea 75 18 2f 8a  36 25 f2 21 0a 94 fd 3b  |.!b.u./.6%.!...;|
00000180  a2 fa 84 f4 2b 54 3a 6a  0a 1f 4d a9 70 82 58 54  |....+T:j..M.p.XT|
00000190  f1 2e 96 7b 80 a1 09 28  75 1d 6e 0c de 74 3f 36  |...{...(u.n..t?6|
000001a0  27 5b ad 43 90 e4 f2 7f  ea d0 51 64 fb 0d 3e f1  |'[.C......Qd..>.|
000001b0  d0 ab 14 82 f1 dc 65 c9  d3 8e ec 0c a8 31 00 fe  |......e......1..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by knightysmith on 2010-09-20
something else randomly:

if i boot to one of the other 2 HDD's Ubuntu loads fine (no menus or anything, just straight in). but I am 100% sure that the install is not on this hard drive.

does help/hinder/banish me from forums?

---

### Post by presence1960 on 2010-09-20
Boot the ubuntu live cd/usb. Go to the desktop. Open a terminal and run ```
sudo mount /dev/sdc1 /mnt
``` This will mmount your ubuntu root partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdc
``` This will put GRUB 2 on the MBR of sdc.

Reboot without live cd/usb. Go into BIOS and set sdc (120 GB) as first hard disk to boot in the hard disk boot order. Save changes to CMOS and continue booting into ubuntu.

Boot to ubuntu. When the desktop loads open a terminal and run ```
sudo dpkg-reconfigure grub-pc
``` Hit enter at each window until you get to the window where you can choose where GRUB is located. Use the space bar to deselect sda and sdb if they are selected. Use the space bar to select sdc if unselected. Tab down to OK. This will ensure any grub-pc updates are installed to sdc instead of sda or sdb.

---

### Post by knightysmith on 2010-09-21
hi guys, all sorted thanks.

@presence1960 that didnt work exactly for me, but it did identify some grub issues. i followed a tutorial for installing grub2 and from there got my situation fixed.

i really appreciate your help. glad i crossed over from the dark side.

thanks again.

---

