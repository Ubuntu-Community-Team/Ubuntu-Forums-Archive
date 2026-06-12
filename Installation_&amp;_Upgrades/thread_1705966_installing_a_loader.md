---
title: "installing a loader"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by bob321 on 2011-03-13
hello,

so I've finished installing ubuntu. I had xp for a while and have installed seven yesterday.
There is a problem with the loader because it automatically logs in with seven.
I'd like to change the loader so that I can choose between xp, seven and ubuntu when it starts.
This is really messy. I have 3 hard drives, and it seems that each one  holds a piece of something. I would want only one disk to contain all  that is related to the systems, the other 2 are only for data and likely  to be removed. From what I saw during the installation process, I have a  disk sda that contains data, and maybe grub, a disk sdb that contains  the 3 OSes, and a disk sdc that may contain the seven loader. I don't  know whether the seven installation, which I did only yesterday,  triggered the creation of a windows loader to choose between xp and  seven, but I wasn't asked this during the boot.

Please help me to clean this situation so that everything works and is properly lined up.

Thanks

---

### Post by kansasnoob on 2011-03-13
Using an Ubuntu live CD or USB please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by bob321 on 2011-03-13
hello,

here it is :


Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   286,722,047   286,720,000   7 HPFS/NTFS
/dev/sdb2    *    344,805,439   488,394,751   143,589,313   7 HPFS/NTFS
/dev/sdb3         286,724,094   344,805,375    58,081,282   5 Extended
/dev/sdb5         286,724,096   288,675,839     1,951,744  82 Linux swap / Solaris
/dev/sdb6         288,677,888   300,394,495    11,716,608  83 Linux
/dev/sdb7         300,396,544   344,805,375    44,408,832  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 3,907,024,064 3,907,024,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        5C38FB8B38FB6286                       ntfs       WD                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        60E8B570E8B544D6                       ntfs                                     
/dev/sdb2        384CD74B4CD70314                       ntfs       System
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        7685b1a8-59ea-4c0a-99b2-d75d54fe99ff   swap                                     
/dev/sdb6        e339f209-bb4b-4e57-876a-b2b0d17e2e0b   ext4                                     
/dev/sdb7        069330ae-88c3-41d3-a102-8293f131928f   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        9E34497534495207                       ntfs       Samsung                 
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        04F02993F0298BCC                       ntfs       Seagate                  
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set e339f209-bb4b-4e57-876a-b2b0d17e2e0b
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set e339f209-bb4b-4e57-876a-b2b0d17e2e0b
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set e339f209-bb4b-4e57-876a-b2b0d17e2e0b
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=e339f209-bb4b-4e57-876a-b2b0d17e2e0b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set e339f209-bb4b-4e57-876a-b2b0d17e2e0b
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=e339f209-bb4b-4e57-876a-b2b0d17e2e0b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set e339f209-bb4b-4e57-876a-b2b0d17e2e0b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set e339f209-bb4b-4e57-876a-b2b0d17e2e0b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 384cd74b4cd70314
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 9e34497534495207
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=e339f209-bb4b-4e57-876a-b2b0d17e2e0b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb7 during installation
UUID=069330ae-88c3-41d3-a102-8293f131928f /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=7685b1a8-59ea-4c0a-99b2-d75d54fe99ff none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 149.0GB: boot/grub/core.img
 149.0GB: boot/grub/grub.cfg
 149.2GB: boot/initrd.img-2.6.32-28-generic
 149.1GB: boot/vmlinuz-2.6.32-28-generic
 149.2GB: initrd.img
 149.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  58 7e 27 54 b3 b6 3f 10  52 98 46 4d f7 b0 46 fd  |X~'T..?.R.FM..F.|
00000010  ad 02 91 21 e4 7e be 57  c9 a4 0a 3a 32 a6 45 ea  |...!.~.W...:2.E.|
00000020  10 10 94 a7 69 fc d2 bf  ff ff bb f9 f9 64 54 03  |....i........dT.|
00000030  98 61 60 d8 f1 ab 85 95  86 96 78 02 3c 61 c1 4d  |.a`.......x.<a.M|
00000040  eb 1c 65 82 a5 07 06 93  99 76 d6 b4 24 30 28 79  |..e......v..$0(y|
00000050  41 9a 24 c3 43 24 0d 31  e4 12 68 34 a4 66 f0 14  |A.$.C$.1..h4.f..|
00000060  88 10 b6 b0 af dd d8 2d  7d 03 96 ef bc 6f dc a5  |.......-}....o..|
00000070  6d 15 b2 89 a4 28 b2 38  88 39 2c 79 2f 2c 46 c2  |m....(.8.9,y/,F.|
00000080  0e 26 2f bc 05 08 5a 42  5a 96 dd 79 e2 69 6c d0  |.&/...ZBZ..y.il.|
00000090  a1 8a ef da e9 58 f4 91  4b 4e 85 ab 94 12 41 74  |.....X..KN....At|
000000a0  4c c5 ac 1e 88 e7 8b 4e  09 44 ba 19 b0 9d b6 93  |L......N.D......|
000000b0  b4 3c 40 c3 71 34 ca 85  d3 09 b2 db 1e d6 a6 64  |.<@.q4.........d|
000000c0  97 e3 3f 53 42 d7 b9 d1  0f b1 7a f7 d7 0d fd 7b  |..?SB.....z....{|
000000d0  6e 1d 20 ac 67 a0 14 3a  73 7a 17 92 5a 16 e1 59  |n. .g..:sz..Z..Y|
000000e0  0b f0 f2 1f ba 7b 9c ed  ad 14 54 85 09 7b 38 b6  |.....{....T..{8.|
000000f0  0f 3e 83 dd 82 ab f9 ba  d9 ae bb f8 cb dd 95 7f  |.>..............|
00000100  21 bd 39 e0 71 49 6d cc  a5 46 50 21 2a fd 50 03  |!.9.qIm..FP!*.P.|
00000110  c4 0f 42 04 6c 20 48 44  5c 6d 4a 5a 13 f1 6c 86  |..B.l HD\mJZ..l.|
00000120  14 92 8e 3b a7 8d 6e 67  3e e8 3e 8c 19 3c c0 58  |...;..ng>.>..<.X|
00000130  30 63 1b 03 e1 f5 5c a5  cf 5f f3 7f ba 7f 8f 98  |0c....\.._......|
00000140  99 74 ff ff ff 6d a6 1b  24 72 ba 00 cc fe 95 38  |.t...m..$r.....8|
00000150  cd 24 44 38 f0 88 80 2e  1a 58 15 43 22 cf 00 42  |.$D8.....X.C"..B|
00000160  80 80 86 49 30 0a 08 40  f4 d1 6b 65 94 1e 2d 44  |...I0..@..ke..-D|
00000170  e1 a0 38 14 46 1a 08 40  05 3f bc 79 ff fb b0 64  |..8.F..@.?.y...d|
00000180  18 8e 07 37 65 53 8b 78  65 50 3f e9 5b ef 30 02  |...7eS.xeP?.[.0.|
00000190  e5 1c 25 85 50 4d e1 33  80 ee a5 70 34 b0 0b 95  |..%.PM.3...p4...|
000001a0  ae e6 02 58 2c 2d 2a fa  76 d5 85 9e 83 84 ec 47  |...X,-*.v......G|
000001b0  dd 98 2d 43 85 f8 e4 c3  e0 53 ad 54 01 14 00 fe  |..-C.....S.T....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c8 1d 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c8  1d 00 00 d0 b2 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by bob321 on 2011-03-13
Can I get some help on this please ?

---

### Post by bob321 on 2011-03-13
I tried to reinstall the grub.
I tried sudo mount /dev/sdb6 /mnt since I think sda6 is where / is installed.
Then sudo grub-install --root-directory=/mnt/ /dev/sdb6
The result is:
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

---

### Post by runeh76 on 2011-03-13
Click my signature **GRUB2**, there is everything what u wanna know.

Good luck!

---

### Post by ronparent on 2011-03-13
If you examine the results of the boot script you are installed on sdb6. The grub-install command you used is exactly correct. You now have the choice of changing the boot order in your bios to boot to the second drive where the boot loader is already written, or, to write a boot loader to sda. Note that the boot loader is written to the MBR of the disk and not to a partition.

If you want to write the boot loader to your current boot disk, the command is  sudo **grub-install --root-directory=/mnt/ /dev/sda**. Other wise enter your computers bios and change your current sdb so that drive is first to boot! Post if you still have problems.

---

### Post by bob321 on 2011-03-13
Okay, so I wrote sdb instead of sdb6.
Then I rebooted the computer.
It is still booting on 7.

According to the boot info script of post 3, it would appear that the computer is booting on sdc rather than sdb.
Can I remove (is it dangerous?) the loader of 7 from sdc so that grub is used (it is in sdb) ?

---

### Post by oldfred on 2011-03-13
I have 3 drives and have different boot loaders in each drive. With grub2 I really do not have to as it gives the choice to boot everything, but I experiment with alpha/beta or other installs and sometimes it is better just to leave my working Ubuntu's grub2 alone.

I prefer to have a different system on each drive and make it stand alone so is one drive has issues I can fully boot from the other.

Your win7 install is sdb1 but it put the (hidden in windows) boot/recovery partition in sdc1. Did you have sdc set as the boot drive in BIOS when you installed windows to sdb?

You can just change BIOS to boot grub2 from sdb.

Some food for thought. I install each new version of Ubuntu (rotate between them) on a different drive, windows is just on my sda. 
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

Windows also combines its boot into one unless you have hidden it or just had one drive plugged in during install. It literal moves the boot files to one partition. If you then uninstall that one the other is also broken.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

