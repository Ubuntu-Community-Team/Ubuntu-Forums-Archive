---
title: "Ubuntu will not boot after installation"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by Albundy213 on 2010-06-24
Hello All,

I searched for this but I didn't have any luck. Please help me.

_Problem-PC automatically boots into a black screen with blinking cursor. No message or nothing_

I have 4 HD. Primary drive has Windows Vista, Secondary no OS installed. Sata1 HD Ubuntu 10.04, Sata2 Windows 7. Prior to installing windows 7 all was perfect but once I did it, grub got all screwed up. The only way I can boot into grub is if I manually select my Sata1 which has Ubuntu on it and only then it allows me to select Linux or Windows OS. How can I change that so it can boot up normally as before? I'm assuming that grub was installed in the primary drive which has vista on it, but once I installed windows 7 it got deleted and when I tried reinstalling Ubuntu, the grub was not installed in the primary drive. Just a guess. Please help, I'm loosing my mind trying to fix this.

Thanks

---

### Post by sikander3786 on 2010-06-24
Hi.

You will have to reinstall grub I think.

Was ubuntu booting fine before windows 7 got installed?

You have ubuntu on your primary drive and windows 7 on the slave? You have 2 physical drives? On which drive did you install grub? Please post back.

Regards.

---

### Post by darkod on 2010-06-24
Did you reinstall ubuntu just to get grub2 back? There is a way just to reinstall grub2, you shouldn't reinstall the whole OS just for that. Depending how you reinstalled ubuntu, you might have two parallel installations now, because it doesn't automatically overwrite the old one unless you tell it to.
If you can boot fine when you select the sata1, why don't you just make that disk first in the boot order in BIOS? Then you will always boot from it.

---

### Post by Albundy213 on 2010-06-24
---SIK
I tried reinstalling grub2 via Synaptic Package Manager and it installed without any errors. It asked me on what drive I wanted grub to install and I choose the HDD that has Ubuntu on it which is my Sata1(not primary nor slave). Prior to installing Windows 7, Ubuntu did boot up correctly but I recall having the same problem the first time I upgraded from 9.10 to 10.04 but I used the testdisk feature and I fixed the problem. Ubuntu is on my Sata1 drive which is third in the HDD list last time I checked my BIOS. Vista is on my Primary and Slave has no OS installed. W7 is on Sata2 I have 4 physical drives.

---darkod
Yes I reinstalled a fresh copy of Ubuntu 10.04 because I couldn't get it to work so I figured reinstalling a new copy would fix it but it didn't. I reinstalled Ubuntu from the live disk. I believe it did overwrite the old one because when step 4 or 5 not sure it asked what drive I wanted to install it on and it showed my I currently had Ubuntu 10 on it and it will erase everything on it and reinstall the new copy over it. I attempted to change my boot order from BIOS but by default it has my Primary drive as the first boot option and it will not let me change it. I attempted to change the HDD boot option order and even disabled to the Primary drive and I still get the black screen with cursor. 

Could it be that grub was installed in my primary drive and once windows 7 installed onto my Sata2 drive it overwrote something on the primary drive causing this issue?

---

### Post by darkod on 2010-06-24
Run the boot info script from my signature and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Also tell us which disk is your IDE Primary that is first in the boot order, like is it /dev/sda, /dev/sdc, etc.

---

### Post by Albundy213 on 2010-06-24
IDE Primary is /dev/sda

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb5 and 
                       looks at sector 286527 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdb5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdd1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sde1 and 
                       looks at sector 286527 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   619,080,839   619,080,777   7 HPFS/NTFS
/dev/sda2         619,080,840   625,137,344     6,056,505   5 Extended
/dev/sda5         619,080,903   625,137,344     6,056,442  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *         16,065   156,296,384   156,280,320   f W95 Ext d (LBA)
/dev/sdb5              16,128   156,296,384   156,280,257   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   468,738,047   468,736,000  83 Linux
/dev/sdc2         468,740,094   488,396,799    19,656,706   5 Extended
/dev/sdc5         468,740,096   488,396,799    19,656,704  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8C3CAC2B3CAC126E                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        90f0be56-7415-4efd-a4f2-8fd08190721e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        7C7865CF786588AA                       ntfs       New Volume                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        acd99d09-a1d1-45f3-84da-06632ee364a6   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        96832f1a-432c-42ef-a913-e7e1818988b1   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        7A82AC8582AC4809                       ntfs       Tango                         
/dev/sdd: PTTYPE="dos" 
/dev/sde1        55D123D9E79ABF54                       ntfs       OneTouch 4                    
/dev/sde: PTTYPE="dos" 
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sde1        /media/OneTouch 4        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
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
search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=acd99d09-a1d1-45f3-84da-06632ee364a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=acd99d09-a1d1-45f3-84da-06632ee364a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8c3cac2b3cac126e
	chainloader +1
}
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
UUID=acd99d09-a1d1-45f3-84da-06632ee364a6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=96832f1a-432c-42ef-a913-e7e1818988b1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  68.8GB: boot/grub/core.img
  68.8GB: boot/grub/grub.cfg
  68.9GB: boot/initrd.img-2.6.32-22-generic-pae
  68.8GB: boot/vmlinuz-2.6.32-22-generic-pae
  68.9GB: initrd.img
  68.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  8a bc de 7d 65 91 e6 ea  1b 4d f8 37 12 ee d4 1b  |...}e....M.7....|
00000010  fa 93 bf ba 61 03 f2 67  9a b8 b5 03 b8 53 c8 7d  |....a..g.....S.}|
00000020  7e 8e bf 80 0d ec b2 d7  e4 1e c3 73 d7 05 e8 fb  |~..........s....|
00000030  76 fb da 4b 09 48 b6 4f  8a 59 b5 f8 ce 8a 95 98  |v..K.H.O.Y......|
00000040  d2 b6 68 52 e4 07 e4 76  5e 6c 5c 75 d6 87 9a fd  |..hR...v^l\u....|
00000050  e1 b2 ba 91 d8 1c 53 f3  72 cc 0a e5 d1 1f 05 4f  |......S.r......O|
00000060  82 bf 7f 66 bf 47 52 63  7d 1b 99 ff dc e0 7d d4  |...f.GRc}.....}.|
00000070  f5 c6 43 bf c5 ef 2a ec  e1 72 cc 65 0c be 2a 7e  |..C...*..r.e..*~|
00000080  b0 c9 a8 ef da 1b a5 0b  fe bb e3 8d 84 e6 8e 39  |...............9|
00000090  4e 53 2f e4 d6 24 1b c8  62 1f 29 37 e3 fb 12 23  |NS/..$..b.)7...#|
000000a0  dd 30 36 17 3f 72 89 14  d3 34 aa de 5a a1 8e 84  |.06.?r...4..Z...|
000000b0  9d b0 1a 3f ee dc 3b ce  a7 f9 18 77 9c 8b f9 e8  |...?..;....w....|
000000c0  ca b3 f2 f6 a0 86 40 08  d7 dd d7 ce ca bf e7 8e  |......@.........|
000000d0  70 98 ad eb cb 2b 72 b5  22 67 7d 67 f6 f2 26 d3  |p....+r."g}g..&.|
000000e0  b1 7c f0 6e 62 a0 24 e1  1e 0c 50 6f 1b 20 79 94  |.|.nb.$...Po. y.|
000000f0  d0 25 2d 64 1d 61 a5 5c  2e 61 c5 f2 ee 84 c1 5d  |.%-d.a.\.a.....]|
00000100  45 64 de 21 a3 cc d4 9d  af f0 79 3a f6 29 47 2e  |Ed.!......y:.)G.|
00000110  14 28 f9 1b 52 1a 4e a6  2c b7 3a c7 04 2c 44 82  |.(..R.N.,.:..,D.|
00000120  7c ec 98 e4 07 b7 26 06  8a 00 6e 7c 80 fa b8 ef  ||.....&...n|....|
00000130  91 e8 10 1f 24 04 e5 eb  df 8d 11 cc 3e 8a ad 17  |....$.......>...|
00000140  8c 86 2f 28 fe 16 72 ee  1e 13 43 66 3f 31 58 8a  |../(..r...Cf?1X.|
00000150  f2 27 61 2f 92 83 9f b2  b6 b5 98 74 e8 4f c2 7a  |.'a/.......t.O.z|
00000160  96 1e 54 bf 2e 4a 2f f2  f5 d8 73 ca cf ec 4e 8e  |..T..J/...s...N.|
00000170  d3 05 d3 3c 3e 01 fd ed  d3 16 47 f0 0f 2f 51 ea  |...<>.....G../Q.|
00000180  3a ac 13 f4 f3 96 34 73  3c b5 a2 bb fe 4e aa 89  |:.....4s<....N..|
00000190  9e aa 0b 73 81 7e fc b9  46 7c 93 f1 df f6 e8 9c  |...s.~..F|......|
000001a0  5a 34 43 76 91 5d 3e a5  99 f2 b1 3f a7 46 76 ec  |Z4Cv.]>....?.Fv.|
000001b0  d3 94 ab 3c 1e de f5 50  00 ef fe 8e 0f b3 00 01  |...<...P........|
000001c0  01 01 07 fe ff ff 3f 00  00 00 c1 a5 50 09 00 00  |......?.....P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdd1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdf sdg 
```

---

### Post by darkod on 2010-06-24
OK, if your BIOS limits you to boot from /dev/sda, from live mode do this:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should sort it out.

You have some remains of XP boot files on /dev/sda1, your vista partition. I'm not sure if they can get in the way when trying to boot vista, probably not.

Were you running XP together with vista? If all works out after reinstalling grub2 with the above commands, just leave it as it is for the time being.

---

### Post by Albundy213 on 2010-06-24
Darko,

I followed the steps you provided and I did get confirmation that grub was installed with 0 errors but it did not work. I rebooted and still get the black screen with blinking cursor. I just don't understand what could be the problem. I can manually boot up my primary drive and grub does load up and allows me to select whatever OS but how can it work automatically?

---

### Post by darkod on 2010-06-24
Are you sure you are booting from /dev/sda?

---

### Post by Albundy213 on 2010-06-24
I'm almost certain i'm booting from /dev/sda. Is there a command I can run to confirm that?

---

### Post by darkod on 2010-06-24
> **Albundy213 said:**
> I'm almost certain i'm booting from /dev/sda. Is there a command I can run to confirm that?

Not really. Alternative you can install grub2 to all of the other three disks, so regardless from which you boot, we will see if it helped.

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
sudo grub-install --root-directory=/mnt/ /dev/sdc
sudo grub-install --root-directory=/mnt/ /dev/sdd
sudo grub-install --root-directory=/mnt/ /dev/sde

---

### Post by Albundy213 on 2010-06-25
I did as you said and installed grub2 to the other disks but I'm still getting the same black screen with blinking cursor. If I reinstall Ubuntu, will that make any difference? I don't get it, if grub is installed on all hard disk, then what is causing it to boot up into that black screen?

---

### Post by wilee-nilee on 2010-06-25
> **Albundy213 said:**
> I did as you said and installed grub2 to the other disks but I'm still getting the same black screen with blinking cursor. If I reinstall Ubuntu, will that make any difference? I don't get it, if grub is installed on all hard disk, then what is causing it to boot up into that black screen?

Since you have tried some fixes post the bootscript again there is a link in my sig to it.

---

### Post by darkod on 2010-06-25
If you have a usb hdd connected try booting without it to see if it helps.

---

### Post by Albundy213 on 2010-06-25
--darkod, I disconnected my usb hdd and I'm still getting the black screen.

Here is the new bootscript
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /mnt/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /mnt/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /mnt/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd5 and 
                       looks at sector 286527 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdd5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sde1 and 
                       looks at sector 286527 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   468,738,047   468,736,000  83 Linux
/dev/sda2         468,740,094   488,396,799    19,656,706   5 Extended
/dev/sda5         468,740,096   488,396,799    19,656,704  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   619,080,839   619,080,777   7 HPFS/NTFS
/dev/sdc2         619,080,840   625,137,344     6,056,505   5 Extended
/dev/sdc5         619,080,903   625,137,344     6,056,442  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *         16,065   156,296,384   156,280,320   f W95 Ext d (LBA)
/dev/sdd5              16,128   156,296,384   156,280,257   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             63 1,465,144,064 1,465,144,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        acd99d09-a1d1-45f3-84da-06632ee364a6   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        96832f1a-432c-42ef-a913-e7e1818988b1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7A82AC8582AC4809                       ntfs       Tango                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8C3CAC2B3CAC126E                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        90f0be56-7415-4efd-a4f2-8fd08190721e   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1: PTTYPE="dos" 
/dev/sdd5        7C7865CF786588AA                       ntfs       New Volume                    
/dev/sdd: PTTYPE="dos" 
/dev/sde1        55D123D9E79ABF54                       ntfs       OneTouch 4                    
/dev/sde: PTTYPE="dos" 
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sde1        /media/OneTouch 4        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
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
search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=acd99d09-a1d1-45f3-84da-06632ee364a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=acd99d09-a1d1-45f3-84da-06632ee364a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set acd99d09-a1d1-45f3-84da-06632ee364a6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 8c3cac2b3cac126e
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
# / was on /dev/sdc1 during installation
UUID=acd99d09-a1d1-45f3-84da-06632ee364a6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=96832f1a-432c-42ef-a913-e7e1818988b1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  68.8GB: boot/grub/core.img
  68.8GB: boot/grub/grub.cfg
  68.9GB: boot/initrd.img-2.6.32-22-generic-pae
  68.8GB: boot/vmlinuz-2.6.32-22-generic-pae
  68.9GB: initrd.img
  68.8GB: vmlinuz

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader  on sdd1

00000000  8a bc de 7d 65 91 e6 ea  1b 4d f8 37 12 ee d4 1b  |...}e....M.7....|
00000010  fa 93 bf ba 61 03 f2 67  9a b8 b5 03 b8 53 c8 7d  |....a..g.....S.}|
00000020  7e 8e bf 80 0d ec b2 d7  e4 1e c3 73 d7 05 e8 fb  |~..........s....|
00000030  76 fb da 4b 09 48 b6 4f  8a 59 b5 f8 ce 8a 95 98  |v..K.H.O.Y......|
00000040  d2 b6 68 52 e4 07 e4 76  5e 6c 5c 75 d6 87 9a fd  |..hR...v^l\u....|
00000050  e1 b2 ba 91 d8 1c 53 f3  72 cc 0a e5 d1 1f 05 4f  |......S.r......O|
00000060  82 bf 7f 66 bf 47 52 63  7d 1b 99 ff dc e0 7d d4  |...f.GRc}.....}.|
00000070  f5 c6 43 bf c5 ef 2a ec  e1 72 cc 65 0c be 2a 7e  |..C...*..r.e..*~|
00000080  b0 c9 a8 ef da 1b a5 0b  fe bb e3 8d 84 e6 8e 39  |...............9|
00000090  4e 53 2f e4 d6 24 1b c8  62 1f 29 37 e3 fb 12 23  |NS/..$..b.)7...#|
000000a0  dd 30 36 17 3f 72 89 14  d3 34 aa de 5a a1 8e 84  |.06.?r...4..Z...|
000000b0  9d b0 1a 3f ee dc 3b ce  a7 f9 18 77 9c 8b f9 e8  |...?..;....w....|
000000c0  ca b3 f2 f6 a0 86 40 08  d7 dd d7 ce ca bf e7 8e  |......@.........|
000000d0  70 98 ad eb cb 2b 72 b5  22 67 7d 67 f6 f2 26 d3  |p....+r."g}g..&.|
000000e0  b1 7c f0 6e 62 a0 24 e1  1e 0c 50 6f 1b 20 79 94  |.|.nb.$...Po. y.|
000000f0  d0 25 2d 64 1d 61 a5 5c  2e 61 c5 f2 ee 84 c1 5d  |.%-d.a.\.a.....]|
00000100  45 64 de 21 a3 cc d4 9d  af f0 79 3a f6 29 47 2e  |Ed.!......y:.)G.|
00000110  14 28 f9 1b 52 1a 4e a6  2c b7 3a c7 04 2c 44 82  |.(..R.N.,.:..,D.|
00000120  7c ec 98 e4 07 b7 26 06  8a 00 6e 7c 80 fa b8 ef  ||.....&...n|....|
00000130  91 e8 10 1f 24 04 e5 eb  df 8d 11 cc 3e 8a ad 17  |....$.......>...|
00000140  8c 86 2f 28 fe 16 72 ee  1e 13 43 66 3f 31 58 8a  |../(..r...Cf?1X.|
00000150  f2 27 61 2f 92 83 9f b2  b6 b5 98 74 e8 4f c2 7a  |.'a/.......t.O.z|
00000160  96 1e 54 bf 2e 4a 2f f2  f5 d8 73 ca cf ec 4e 8e  |..T..J/...s...N.|
00000170  d3 05 d3 3c 3e 01 fd ed  d3 16 47 f0 0f 2f 51 ea  |...<>.....G../Q.|
00000180  3a ac 13 f4 f3 96 34 73  3c b5 a2 bb fe 4e aa 89  |:.....4s<....N..|
00000190  9e aa 0b 73 81 7e fc b9  46 7c 93 f1 df f6 e8 9c  |...s.~..F|......|
000001a0  5a 34 43 76 91 5d 3e a5  99 f2 b1 3f a7 46 76 ec  |Z4Cv.]>....?.Fv.|
000001b0  d3 94 ab 3c 1e de f5 50  00 ef fe 8e 0f b3 00 01  |...<...P........|
000001c0  01 01 07 fe ff ff 3f 00  00 00 c1 a5 50 09 00 00  |......?.....P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdf sdg 
```

---

### Post by darkod on 2010-06-25
How did the ubuntu disk become /dev/sda from /dev/sdc?

Also, look at this mess on the vista partition:

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR=Red]/ntldr /NTDETECT.COM /boot/grub/core.img[/COLOR]

Lets try this. Boot your hdd ubuntu, you said you can boot it with some procedure, and then open the vista partition and move (not delete) the ntldr, ntdetect.com and /boot/grub/core.img files to your ubuntu home folder for example.

After moving these files, and if you are booted into the hdd ubuntu, also do:

sudo grub-mkdevicemap
sudo update-grub

Restart and see how it goes.
Also you should check if the ubuntu disk, now called /dev/sda, the 250GB disk is first in hdd boot options in BIOS.
And if the /dev/sde disk, One Touch, is usb hdd, keep it disconnected until you sort this out, just in case. It's in the results again.

Let us know how it went.

---

### Post by Albundy213 on 2010-06-25
I followed your instructions and that darn black screen is still there. Could it be a file in my primary drive that needs deletion in order for grub to kick in. As I mentioned before, if I manually boot up any of my hdd, grub automatically kicks in.

I didn't notice the changing of the disk name until you mentioned it and I looked back at my original bootscript sure enough it did change. I didn't change anything in the BIOS. All I've been doing is following the instructions given to me. I have a few questions.
1) Will reinstalling Ubuntu fix this?
2) How can I wipe everything out that Ubuntu installed in order to have windows boot up normally?
3) How can I remove grub from all my other hdd in order to redo the installation?

Thanks

---

### Post by darkod on 2010-06-25
I'm still confused. When you say manually boot up my hdd, you mean probably selecting something like Quick Boot menu. But it should still work if BIOS boots it too.

I just noticed something, we can give it a shot. Grub2 doesn't use the boot flag, do /dev/sda1 doesn't have it enabled, but some BIOS have problems with that.

Boot your ubuntu the manual way, then confirm with:

sudo fdisk -l

that the disk names haven't changed again. They should be the same as in the last results file.

In that case open Gparted, select disk /dev/sda, the ubuntu disk, right-click /dev/sda1 and set a boot flag on it.

Also, if your vista disk is still /dev/sdc, you can install generic mbr on it with:

sudo apt-get install lilo
sudo lilo -M /dev/sdc mbr

After the first command there will be warning messages, just ignore them and execute the second command. That should bring up the windows bootloader if you select to boot from /dev/sdc.

---

### Post by Albundy213 on 2010-06-26
In order to boot I have to press F8 a million times once my bios info loads up in order to select the drive I want to boot.

I added the boot flag and no progress. 

I did notice after doing this ```
sudo apt-get install lilo
sudo lilo -M /dev/sdc mbr
```, grub did not appear and my original windows boot sequence came up, but I still get the black screen. I couldn't take it anymore so I went into windows 7 and reformated my ubutu hdd and reinstalled Ubuntu thinking it would work but nothing. I still get the darn black screen with blinking cursor. Could it be that my Windows 7 64x is causing some problems? My vista is 32 and ubuntu is also 32.

I'm listing my current script results.```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /mnt/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /mnt/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in 
    partition #1 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdd5 and 
                       looks at sector 286527 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdd5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   468,738,047   468,736,000  83 Linux
/dev/sda2         468,740,094   488,396,799    19,656,706   5 Extended
/dev/sda5         468,740,096   488,396,799    19,656,704  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   619,080,839   619,080,777   7 HPFS/NTFS
/dev/sdc2         619,080,840   625,137,344     6,056,505   5 Extended
/dev/sdc5         619,080,903   625,137,344     6,056,442  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *         16,065   156,296,384   156,280,320   f W95 Ext d (LBA)
/dev/sdd5              16,128   156,296,384   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6b30ca69-4565-45a0-a760-d84ef07861cf   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        02fb7bc2-e817-4973-80c8-1048199f2ec8   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7A82AC8582AC4809                       ntfs       Tango                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        8C3CAC2B3CAC126E                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        90f0be56-7415-4efd-a4f2-8fd08190721e   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1: PTTYPE="dos" 
/dev/sdd5        7C7865CF786588AA                       ntfs       New Volume                    
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 6b30ca69-4565-45a0-a760-d84ef07861cf
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
search --no-floppy --fs-uuid --set 6b30ca69-4565-45a0-a760-d84ef07861cf
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6b30ca69-4565-45a0-a760-d84ef07861cf
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6b30ca69-4565-45a0-a760-d84ef07861cf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6b30ca69-4565-45a0-a760-d84ef07861cf
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6b30ca69-4565-45a0-a760-d84ef07861cf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6b30ca69-4565-45a0-a760-d84ef07861cf
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6b30ca69-4565-45a0-a760-d84ef07861cf ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6b30ca69-4565-45a0-a760-d84ef07861cf
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=6b30ca69-4565-45a0-a760-d84ef07861cf ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6b30ca69-4565-45a0-a760-d84ef07861cf
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6b30ca69-4565-45a0-a760-d84ef07861cf
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=6b30ca69-4565-45a0-a760-d84ef07861cf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=02fb7bc2-e817-4973-80c8-1048199f2ec8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   8.7GB: boot/grub/core.img
  21.6GB: boot/grub/grub.cfg
   8.8GB: boot/initrd.img-2.6.32-21-generic
   8.9GB: boot/initrd.img-2.6.32-22-generic
    .1GB: boot/vmlinuz-2.6.32-21-generic
   8.8GB: boot/vmlinuz-2.6.32-22-generic
   8.9GB: initrd.img
   8.8GB: initrd.img.old
   8.8GB: vmlinuz
    .1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader  on sdd1

00000000  8a bc de 7d 65 91 e6 ea  1b 4d f8 37 12 ee d4 1b  |...}e....M.7....|
00000010  fa 93 bf ba 61 03 f2 67  9a b8 b5 03 b8 53 c8 7d  |....a..g.....S.}|
00000020  7e 8e bf 80 0d ec b2 d7  e4 1e c3 73 d7 05 e8 fb  |~..........s....|
00000030  76 fb da 4b 09 48 b6 4f  8a 59 b5 f8 ce 8a 95 98  |v..K.H.O.Y......|
00000040  d2 b6 68 52 e4 07 e4 76  5e 6c 5c 75 d6 87 9a fd  |..hR...v^l\u....|
00000050  e1 b2 ba 91 d8 1c 53 f3  72 cc 0a e5 d1 1f 05 4f  |......S.r......O|
00000060  82 bf 7f 66 bf 47 52 63  7d 1b 99 ff dc e0 7d d4  |...f.GRc}.....}.|
00000070  f5 c6 43 bf c5 ef 2a ec  e1 72 cc 65 0c be 2a 7e  |..C...*..r.e..*~|
00000080  b0 c9 a8 ef da 1b a5 0b  fe bb e3 8d 84 e6 8e 39  |...............9|
00000090  4e 53 2f e4 d6 24 1b c8  62 1f 29 37 e3 fb 12 23  |NS/..$..b.)7...#|
000000a0  dd 30 36 17 3f 72 89 14  d3 34 aa de 5a a1 8e 84  |.06.?r...4..Z...|
000000b0  9d b0 1a 3f ee dc 3b ce  a7 f9 18 77 9c 8b f9 e8  |...?..;....w....|
000000c0  ca b3 f2 f6 a0 86 40 08  d7 dd d7 ce ca bf e7 8e  |......@.........|
000000d0  70 98 ad eb cb 2b 72 b5  22 67 7d 67 f6 f2 26 d3  |p....+r."g}g..&.|
000000e0  b1 7c f0 6e 62 a0 24 e1  1e 0c 50 6f 1b 20 79 94  |.|.nb.$...Po. y.|
000000f0  d0 25 2d 64 1d 61 a5 5c  2e 61 c5 f2 ee 84 c1 5d  |.%-d.a.\.a.....]|
00000100  45 64 de 21 a3 cc d4 9d  af f0 79 3a f6 29 47 2e  |Ed.!......y:.)G.|
00000110  14 28 f9 1b 52 1a 4e a6  2c b7 3a c7 04 2c 44 82  |.(..R.N.,.:..,D.|
00000120  7c ec 98 e4 07 b7 26 06  8a 00 6e 7c 80 fa b8 ef  ||.....&...n|....|
00000130  91 e8 10 1f 24 04 e5 eb  df 8d 11 cc 3e 8a ad 17  |....$.......>...|
00000140  8c 86 2f 28 fe 16 72 ee  1e 13 43 66 3f 31 58 8a  |../(..r...Cf?1X.|
00000150  f2 27 61 2f 92 83 9f b2  b6 b5 98 74 e8 4f c2 7a  |.'a/.......t.O.z|
00000160  96 1e 54 bf 2e 4a 2f f2  f5 d8 73 ca cf ec 4e 8e  |..T..J/...s...N.|
00000170  d3 05 d3 3c 3e 01 fd ed  d3 16 47 f0 0f 2f 51 ea  |...<>.....G../Q.|
00000180  3a ac 13 f4 f3 96 34 73  3c b5 a2 bb fe 4e aa 89  |:.....4s<....N..|
00000190  9e aa 0b 73 81 7e fc b9  46 7c 93 f1 df f6 e8 9c  |...s.~..F|......|
000001a0  5a 34 43 76 91 5d 3e a5  99 f2 b1 3f a7 46 76 ec  |Z4Cv.]>....?.Fv.|
000001b0  d3 94 ab 3c 1e de f5 50  00 ef fe 8e 0f b3 00 01  |...<...P........|
000001c0  01 01 07 fe ff ff 3f 00  00 00 c1 a5 50 09 00 00  |......?.....P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf 
```

---

### Post by darkod on 2010-06-26
If the windows boot sequence was still giving you black screen, this has nothing to do with ubuntu from the start.

Also, I don't know how much experience you have with windows/linux, but don't try too many things especially if you don't understand them. For example, you have a swap partition /dev/sdc5 which has no business there. I didn't mention it before because other problems are more important. But it's curious how did it got there.

Can this be some ridiculous BIOS setting that it's trying to boot from somewhere else? You don't have special boot procedures set, right?

At this point of time, make windows work by itself, you didn't need to reinstall ubuntu. Once windows works, I'm 99% sure it will work fine next to ubuntu too.

Get your vista install dvd and try to repair the boot process. set the vista disk to be first in BIOS before that, this is very important because windows boot process depends on it. Boot with the dvd and follow the manual instructions here to make it boot:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once you have that working, let us know, don't try anything else, and post new results file after that change. Then we will consider what to do in that new situation.

---

