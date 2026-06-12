---
title: "Can't boot ubuntu after installing Win-7"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by Honey_HR on 2010-08-22
Hi, I ve ubuntu and windows 7 both.and both are installed in diffrent drives. and works perfectly, but due to some reasons i ve to reinstall windows 7. and after iinstalling windows, i did not show me any boot choice menu for Ubuntu !!  
Please help me guys, I am waiting for your answers.
 
Regards

---

### Post by jcolyn on 2010-08-22
Windows has to be installed first then Ubuntu..

---

### Post by wilee-nilee on 2010-08-22
It doesn't matter in what order the OS are installed. Post the bootscript in my signature to confirm your set-up in code tags as described.

---

### Post by Honey_HR on 2010-08-22
> **wilee-nilee said:**
> It doesn't matter in what order the OS are installed. Post the bootscript in my signature to confirm your set-up in code tags as described.
Hellop sir here is the result below of bootscript :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

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

/dev/sda1    *             63   206,017,559   206,017,497   7 HPFS/NTFS
/dev/sda2         206,028,800   780,710,804   574,682,005   7 HPFS/NTFS
/dev/sda3         780,711,936   813,842,795    33,130,860  83 Linux
/dev/sda4         813,844,478 1,953,521,663 1,139,677,186   f W95 Ext d (LBA)
/dev/sda5         821,659,648 1,334,888,447   513,228,800   7 HPFS/NTFS
/dev/sda6       1,334,890,496 1,953,521,663   618,631,168   7 HPFS/NTFS
/dev/sda7         813,844,480   821,659,647     7,815,168  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BEB87426B873DB7B                       ntfs                                     
/dev/sda2        52A01921A0190D5B                       ntfs       New Volume                    
/dev/sda3        06aab75b-9d7c-4fd7-8ef7-a1650a5d348b   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        2ABC2136BC20FE47                       ntfs       New Volume                    
/dev/sda6        30C628B0C62877EC                       ntfs       New Volume                    
/dev/sda7        44c601ae-b45e-43b3-943c-3b3be0f3eaf8   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/BEB87426B873DB7B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 06aab75b-9d7c-4fd7-8ef7-a1650a5d348b
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 06aab75b-9d7c-4fd7-8ef7-a1650a5d348b
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
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 06aab75b-9d7c-4fd7-8ef7-a1650a5d348b
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=06aab75b-9d7c-4fd7-8ef7-a1650a5d348b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 06aab75b-9d7c-4fd7-8ef7-a1650a5d348b
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=06aab75b-9d7c-4fd7-8ef7-a1650a5d348b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 06aab75b-9d7c-4fd7-8ef7-a1650a5d348b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=06aab75b-9d7c-4fd7-8ef7-a1650a5d348b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 06aab75b-9d7c-4fd7-8ef7-a1650a5d348b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=06aab75b-9d7c-4fd7-8ef7-a1650a5d348b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 06aab75b-9d7c-4fd7-8ef7-a1650a5d348b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 06aab75b-9d7c-4fd7-8ef7-a1650a5d348b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set beb87426b873db7b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=44c601ae-b45e-43b3-943c-3b3be0f3eaf8 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 408.4GB: boot/grub/core.img
 402.3GB: boot/grub/grub.cfg
 408.9GB: boot/initrd.img-2.6.32-21-generic
 409.5GB: boot/initrd.img-2.6.32-24-generic
 408.9GB: boot/vmlinuz-2.6.32-21-generic
 409.2GB: boot/vmlinuz-2.6.32-24-generic
 409.5GB: initrd.img
 408.9GB: initrd.img.old
 409.2GB: vmlinuz
 408.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  7a 30 61 15 6d 53 77 d2  7b 25 9b 2c b5 73 73 75  |z0a.mSw.{%.,.ssu|
00000010  83 de aa af 14 c9 3e a6  db dd b2 b7 5d 1b 46 69  |......>.....].Fi|
00000020  e6 fb ac 76 0b de 89 5f  36 99 77 1c 66 f6 62 85  |...v..._6.w.f.b.|
00000030  fe cc 30 3f c0 6e 6a 95  4b 55 53 54 f5 aa 45 63  |..0?.nj.KUST..Ec|
00000040  6f b8 75 f7 c8 fa 6c d4  34 7d 68 8f e7 2b d3 67  |o.u...l.4}h..+.g|
00000050  98 ac 82 6b 07 a5 ae 9e  9b 79 d3 c1 1e 9a b7 27  |...k.....y.....'|
00000060  f8 76 59 3e 85 77 84 72  b4 e5 9e 57 4c 78 ef 33  |.vY>.w.r...WLx.3|
00000070  18 30 7d e6 cf eb f5 53  fd 3f 9e b1 e0 1b 44 69  |.0}....S.?....Di|
00000080  d8 89 5a 0d f2 2e 4b 01  7a 3c 10 9b a9 15 a7 12  |..Z...K.z<......|
00000090  be 83 47 2a 89 27 c4 48  33 20 4a 70 3c d9 d8 51  |..G*.'.H3 Jp<..Q|
000000a0  51 b8 b8 86 5d b3 7c 5e  c7 4a af 56 06 0c 45 55  |Q...].|^.J.V..EU|
000000b0  f1 28 19 03 fb 49 b5 ca  15 c1 fa af 17 c6 64 d2  |.(...I........d.|
000000c0  30 27 0b 98 be c0 9d 5f  8d ae 68 c6 a0 3c fc 66  |0'....._..h..<.f|
000000d0  6e 8a 60 93 d8 ad 8f 6d  d5 eb 3d c6 b6 75 c6 33  |n.`....m..=..u.3|
000000e0  74 75 af 37 e3 be 1f 7d  f7 cc 56 e7 38 25 dd 6b  |tu.7...}..V.8%.k|
000000f0  9d 7c d9 1c 87 30 4c 30  7c a8 48 08 45 d6 fd 50  |.|...0L0|.H.E..P|
00000100  94 aa 5a cc f7 46 a5 ca  19 fd a9 09 8c 89 09 d4  |..Z..F..........|
00000110  de fa ac ce 93 fc ba 2a  2e b1 5c 54 a2 56 94 7d  |.......*..\T.V.}|
00000120  59 f1 f2 b0 86 a9 54 54  af ff e1 7f c7 8a ae 5d  |Y.....TT.......]|
00000130  57 56 71 8b 7b a5 a7 a4  e9 d3 24 62 fb 0e d8 eb  |WVq.{.....$b....|
00000140  b3 09 49 9c b4 cb f3 dc  59 a8 84 1f fb ca af e0  |..I.....Y.......|
00000150  f7 ea 26 91 bc 18 d4 0c  04 11 2f c2 50 28 7f 7d  |..&......./.P(.}|
00000160  53 6f e6 73 0b 0e 89 7f  b2 97 db ec b4 bb aa bf  |So.s............|
00000170  2e 4d 90 c8 fe 6a b2 f9  40 b8 f5 5f 5b 8b 52 45  |.M...j..@.._[.RE|
00000180  74 79 f2 f1 e4 4b 41 49  e9 3f b7 d3 59 c7 7a 73  |ty...KAI.?..Y.zs|
00000190  a6 c8 d6 6d 56 10 c1 94  7a 0f 84 80 3b 3e 3d ff  |...mV...z...;>=.|
000001a0  a8 92 af dd 4a ab d8 84  f8 96 25 cf 29 cf 58 a3  |....J.....%.).X.|
000001b0  27 1a ff 66 9d 1e cf 2a  fa bf 7b 5b e5 53 00 fe  |'..f...*..{[.S..|
000001c0  ff ff 07 fe ff ff 02 40  77 00 00 40 97 1e 00 fe  |.......@w..@....|
000001d0  ff ff 05 fe ff ff 57 82  0e 1f ab 95 df 24 00 00  |......W......$..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Please give me any solution

---

### Post by oldfred on 2010-08-22
Someone else just had /grldr in their windows partition and grub would not see the windows to add it.

I would delete the /grldr and then in Ubuntu run 

sudo update-grub

---

### Post by wilee-nilee on 2010-08-23
So if you can get the /grldr removed I don't know anything about this part sorry,  but the person in post 5 is most likely to help you. If you get it removed you can reload grub from a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Grub is the Ubuntu bootloader that will let you choose the OS to boot. the /grldr reference is in the boot dir files in sda1 in the script if you look.

---

### Post by xaliqen on 2010-08-23
If you need to restore GRUB selection at boot, then you can try one of the [Super GRUB]("http://www.supergrubdisk.org/") disks.

[This documentation]("http://www.supergrubdisk.org/wiki/Howto_Fix_Grub") may also come in handy.

---

### Post by Eng.Khalid on 2010-08-23
I've the same problem ....

I can access only win7 I don't want to lost my data on ubuntu 

so is there any way to do that ???

---

### Post by wilee-nilee on 2010-08-23
> **Eng.Khalid said:**
> I've the same problem ....

I can access only win7 I don't want to lost my data on ubuntu 

so is there any way to do that ???

Start your own thread as these boot problems are different per person.

Post the boot script in my signature in code tags as described in the new thread.

---

### Post by xaliqen on 2010-08-23
Eng.Khalid -- You could also try the Super Grub disks I mentioned.  One of their main purposes is to restore the GRUB operating system selection menu at startup.

EDIT: Be sure to use the Super Grub disk appropriate for the GRUB you want to install or modify (in this case, it would be GRUB2).  Apparently, Super Grub may not auto-detect everything just yet.  So, be sure to understand which version of GRUB you need ahead of time (most recent distributions will use GRUB2).

---

### Post by wilee-nilee on 2010-08-24
> **xaliqen said:**
> Eng.Khalid -- You could also try the Super Grub disks I mentioned.  One of their main purposes is to restore the GRUB operating system selection menu at startup.

EDIT: Be sure to use the Super Grub disk appropriate for the GRUB you want to install or modify (in this case, it would be GRUB2).  Apparently, Super Grub may not auto-detect everything just yet.  So, be sure to understand which version of GRUB you need ahead of time (most recent distributions will use GRUB2).

I would take oldfred's word on the /grldr boot problem you are trying to force something that isn't going to work.

This line shows a problem it is highlighted.
 Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       **/grldr** /ntldr /NTDETECT.COM

---

### Post by Eng.Khalid on 2010-08-24
this is my thread link :
[http://ubuntuforums.org/showthread.php?p=9759438#post9759438](http://ubuntuforums.org/showthread.php?p=9759438#post9759438)

I've posted my boot info plz need help

---

