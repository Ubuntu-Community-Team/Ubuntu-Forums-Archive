---
title: "grub - error no such disk"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by ApEkV2 on 2010-03-05
Hello, I just installed 9.10 on a removable hard drive, and now it won't boot, get an error "no such disk".
I go into my bios and set the primary boot as my windows hard drive, it won't boot windows?
I get that error: no such disk, and then grub rescue command line.
Now I'm going on vacation tomorrow, and I won't be able to do anything I planned. I did run the boot info script, and here is the output.

It should have installed ubuntu on sdb which is my external harddrive. sda is my windows. Can someone help me out, I need it desperately!

[color=red]Can anyone tell me how to get my windows drive to boot, I don't care about Ubuntu at this point anymore[/color]

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=1430c6bd-07e5-48e9-9f9f-ac6135372759)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       20482875 sectors.. But according to the info from the 
                       partition table , it has 281844359 sectors.
    Mounting failed:
mount: /dev/sda3: can't read superblock

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9b3496e

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,715,903    30,713,856  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,715,904   343,292,984   312,577,081   7 HPFS/NTFS
/dev/sda3         343,292,985   625,137,344   281,844,360   f W95 Ext d (LBA)
/dev/sda5         343,293,048   625,137,344   281,844,297   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1499cbfd

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   846,737,954   846,737,892   7 HPFS/NTFS
/dev/sdb2         846,737,955   976,768,064   130,030,110   5 Extended
/dev/sdb5         846,738,018   971,370,224   124,632,207  83 Linux
/dev/sdb6         971,370,288   976,768,064     5,397,777  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 514 MB, 514850816 bytes
16 heads, 32 sectors/track, 1964 cylinders, total 1005568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     1,005,567     1,005,536   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        7242C0BC42C08677                       ntfs       OS                            
/dev/sda3        589E-2CF2                              vfat                                     
/dev/sda5        0D7201CA45B7815C                       ntfs       DATA                          
/dev/sdb1        DE34A4D834A4B545                       ntfs       FreeAgent Drive               
/dev/sdb5        1430c6bd-07e5-48e9-9f9f-ac6135372759   ext4                                     
/dev/sdb6        7f1ff0a3-df55-451b-9eb4-8f017255720e   swap                                     
/dev/sdc1        0BFE-1C4B                              vfat       STORE'N'GO                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb5        /media/1430c6bd-07e5-48e9-9f9f-ac6135372759 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/DATA              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1        /media/STORE'N'GO        vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,5)
search --no-floppy --fs-uuid --set 1430c6bd-07e5-48e9-9f9f-ac6135372759
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 1430c6bd-07e5-48e9-9f9f-ac6135372759
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1430c6bd-07e5-48e9-9f9f-ac6135372759 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,5)
	search --no-floppy --fs-uuid --set 1430c6bd-07e5-48e9-9f9f-ac6135372759
	linux	/boot/vmlinuz-2.6.31-20-generic-pae root=UUID=1430c6bd-07e5-48e9-9f9f-ac6135372759 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 3c98-ac5d
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 7242c0bc42c08677
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=1430c6bd-07e5-48e9-9f9f-ac6135372759 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=7f1ff0a3-df55-451b-9eb4-8f017255720e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 437.1GB: boot/grub/core.img
 437.1GB: boot/grub/grub.cfg
 434.1GB: boot/initrd.img-2.6.31-20-generic-pae
 434.0GB: boot/vmlinuz-2.6.31-20-generic-pae
 434.1GB: initrd.img
 434.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 10 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 39 3c 76 14  |........?...9<v.|
00000020  3b 8b 38 01 08 27 00 00  00 00 00 00 12 05 00 00  |;.8..'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f2 2c 9e 58 4e  4f 20 4e 41 4d 45 20 20  |..).,.XNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 00 fe  |@.^.s........_..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 49 9a cc 10 00 00  |......?...I.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by ApEkV2 on 2010-03-05
bump, and I'm not going to be on here for the next day, (10 hr drive yeeeaaaaa!)

btw I will have everything just in case it turns out able to be solved. (laptop, live cd, super grub disk, exthdd)

---

### Post by presence1960 on 2010-03-05
Simple fix to get both OSs booting and working. First the problem: you let GRUB be installed to the internal disk's MBR instead of the MBR of the external disk. 

The solution: Boot the Ubuntu Live CD and choose "try ubuntu without any changes." When the desktop loads open a terminal (Applications > Accessories > Terminal) & run ```
sudo mount /dev/sdb5 /mnt
```This will mount your ubuntu root (/) partition. Next run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB 2 on MBR of external disk.

When complete you will now fix your MBR of internal disk to a windows MBR. Still from the ubuntu Live CD run in terminal ```
sudo apt-get install lilo
```This will install lilo to the Live Cd session. Ignore the warning. In terminal run ```
sudo lilo -M /dev/sda mbr
```This will fix the MBR of the internal disk. Reboot without the Live CD & the external disconnected. You should boot right to windows. If so reboot again with the external plugged in. Go into BIOS and make sure the external is set to boot before the internal disk. Usually this is accomplished in the Device boot priority. Select USB/Removable to boot before CD and hard disk. Save changes to CMOS and continue booting with the external plugged in. At the GRUB menu select Ubuntu. You should boot to Ubuntu.

When you boot without the external you boot to windows. When you boot with the external you get GRUB and can boot to Ubuntu.

Now you need to do one more thing so any GRUB updates go to the external. Boot into Ubuntu and run ```
sudo dpkg-reconfigure grub-pc
```Hit Enter at first windows until you get to the window where to choose to put GRUB. At this window use arrow keys to navigate to sda. if it is selected use spacebar to unselect it. Then use arrow keys to navigate to sdb. Use the space bar to select sdb. Hit Tab to navigate to OK and hit Enter. You are now set so that any updates to grub-pc (GRUB 2) go to the external disk instead of the internal disk.

FYI next time you install to an external disk you need to choose to put GRUB on the MBR of the external. You do this at the Ready to install window by clicking the Advanced button (see pic below). You then choose where to install GRUB, in your case if you only have one internal disk & the external you choose /dev/sdb from the drop down box.

---

### Post by kansasnoob on 2010-03-05
Boot with the external drive plugged in and exit to BIOS, make sure it's set to boot from CD first, USB second, and internal drive last. Then go ahead and boot into Ubuntu and run the following commands:

```
sudo grub-install /dev/sdb
```

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

```
sudo apt-get install lilo
```

That installs grub to sdb where it belongs and we're using Lilo only as a tool to restore a Windows readable mbr to sda. Then we just remove the package Lilo so it doesn't mess with things at some point later on (it shouldn't anyway but I like to play it safe).

---

### Post by ApEkV2 on 2010-03-06
Thank you guys very much for your replies.  
I will have to try to complete those steps once I muster up the confidence.
It seems the bios sometimes detects the external harddrive and sometimes it doesn't.
If I follow through with these steps, and restore the sda mbr, will I still be able to boot windows in the event the external harddrive isn't detected at startup?

You guys are great, pros imho.

@ presence, Aahh I've never even seen the advanced options. How did I miss that? Thanks though for pointing that out.

---

### Post by presence1960 on 2010-03-06
> **ApEkV2 said:**
> Thank you guys very much for your replies.  
I will have to try to complete those steps once I muster up the confidence.
It seems the bios sometimes detects the external harddrive and sometimes it doesn't.
If I follow through with these steps, and restore the sda mbr, will I still be able to boot windows in the event the external harddrive isn't detected at startup?

You guys are great, pros imho.

@ presence, Aahh I've never even seen the advanced options. How did I miss that? Thanks though for pointing that out.

If you install and use lilo to fix the MBR of internal (sda) your machine will boot right to windows when the external is unplugged or unrecognized.

---

