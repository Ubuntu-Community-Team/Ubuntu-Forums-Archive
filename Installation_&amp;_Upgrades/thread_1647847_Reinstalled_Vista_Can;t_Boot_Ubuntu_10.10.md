---
title: "Reinstalled Vista Can;t Boot Ubuntu 10.10"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by MrStRNGE on 2010-12-17
So i did my re installation of Vista which i do every year or so and i got that done all fine no problems
But lately i was having fun with Ubuntu (way faster than vista so i've been using it to play mine craft etc)
so i'm a bit of a newbie in terms of Ubuntu
But after doing so my Dual Boot disappeared and i couldn't get back to my Ubuntu
I've been looking for solutions for about a half hour now and none of them brought it back
It's Installed to my D:\ drive with all 80GB's allocated to the Ubuntu partition
I don't want to have it installed over cause that's where i backed up my important files from Vista (My work OS... no it wasn't a very good OS for work but you got to make do with what you got)
I tried using the USB i installed Ubuntu on first to copy and paste the files back over to vista but Ubuntu's security wouldn't let me
And vista can;t even see the D:\ drive any more

So unless anyone knows how to break through Ubuntu's security to retrieve those files through Vista and i reinstall 10.10
Can anyone help me get the Dual Boot?
(no i wasn't using the Vista Dual boot i was using Linux's GNU grub whatever it was called i remember seeing GNU in it i remember that)
(and also both OS's are 32 bit if that helps anyone... my laptop is also a HP Pavillion DX6000)

---

### Post by Quackers on 2010-12-17
The Vista re-install probably over-wrote grub in the mbr. You will need to re-install grub to the mbr of the drive. Have a look here

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by wilee-nilee on 2010-12-18
Ubuntu installed in D sounds wubiesque to me.;)

Op can you give us a posting of the readout of running this command in the terminal from a Ubuntu live cd.
```
sudo fdisk -lu
```

---

### Post by MrStRNGE on 2010-12-18
> **Quackers said:**
> The Vista re-install probably over-wrote grub in the mbr. You will need to re-install grub to the mbr of the drive. Have a look here

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I tried following this but it think i did it wrong still not boot loader
and this is what terminal said to me

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf82ae629

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   219174794   109587366    7  HPFS/NTFS
/dev/sda2       219174795   234436544     7630875    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd439

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   149843967    74920960   83  Linux
/dev/sdb2       149846014   156301311     3227649    5  Extended
/dev/sdb5       149846016   156301311     3227648   82  Linux swap / Solaris

Disk /dev/sdc: 8054 MB, 8054636032 bytes
248 heads, 62 sectors/track, 1023 cylinders, total 15731711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb0eb409

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3447419926  1019098920   933323145+  66  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1010, 16, 43) logical=(224207, 211, 13)
Partition 1 has different physical/logical endings:
     phys=(906, 97, 3) logical=(66278, 135, 23)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?        2573        2573           0   72  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(101, 116, 32) logical=(0, 41, 32)
Partition 2 has different physical/logical endings:
     phys=(370, 114, 47) logical=(0, 41, 31)
Partition 2 does not end on cylinder boundary.

Partition table entries are not in disk order
```

---

### Post by Quackers on 2010-12-18
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by MrStRNGE on 2010-12-18
Roger that

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   219,174,794   219,174,732   7 HPFS/NTFS
/dev/sda2         219,174,795   234,436,544    15,261,750   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   149,843,967   149,841,920  83 Linux
/dev/sdb2         149,846,014   156,301,311     6,455,298   5 Extended
/dev/sdb5         149,846,016   156,301,311     6,455,296  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AE20EC1720EBE3F5                       ntfs       OS                            
/dev/sda2        E854B1F354B1C51A                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        797d0e2b-2c28-412f-93f7-a5c4cc05d5fa   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        28bedc3b-2e20-4360-80d4-05e0cf2c9956   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         E4C6-FBBA                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 797d0e2b-2c28-412f-93f7-a5c4cc05d5fa
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 797d0e2b-2c28-412f-93f7-a5c4cc05d5fa
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 797d0e2b-2c28-412f-93f7-a5c4cc05d5fa
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=797d0e2b-2c28-412f-93f7-a5c4cc05d5fa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 797d0e2b-2c28-412f-93f7-a5c4cc05d5fa
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=797d0e2b-2c28-412f-93f7-a5c4cc05d5fa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 797d0e2b-2c28-412f-93f7-a5c4cc05d5fa
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=797d0e2b-2c28-412f-93f7-a5c4cc05d5fa ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 797d0e2b-2c28-412f-93f7-a5c4cc05d5fa
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=797d0e2b-2c28-412f-93f7-a5c4cc05d5fa ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 797d0e2b-2c28-412f-93f7-a5c4cc05d5fa
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 797d0e2b-2c28-412f-93f7-a5c4cc05d5fa
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set ae20ec1720ebe3f5
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
UUID=28bedc3b-2e20-4360-80d4-05e0cf2c9956 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  17.4GB: boot/grub/grub.cfg
  64.7GB: boot/initrd.img-2.6.35-22-generic
  64.8GB: boot/initrd.img-2.6.35-23-generic
  17.5GB: boot/vmlinuz-2.6.35-22-generic
  17.8GB: boot/vmlinuz-2.6.35-23-generic
  64.8GB: initrd.img
  64.7GB: initrd.img.old
  17.8GB: vmlinuz
  17.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 02 02  |.X.SYSLINUX.. ..|
00000010  02 00 00 00 00 f8 00 00  11 00 04 00 00 00 00 00  |................|
00000020  e0 0b f0 00 ff 0e 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ba fb c6 e4 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 40 cc 59 00  66 ba 00 00 00 00 bb 00  |}.f.@.Y.f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Anything else?

---

### Post by Quackers on 2010-12-18
Is your bios set to boot from the first hard drive? Try setting it to boot from the second drive. What happens then?

---

### Post by MrStRNGE on 2010-12-18
i was looking for it earlier but didn't see the second hard drive in the BIOS i'll check once more

---

### Post by MrStRNGE on 2010-12-18
Put the C:\ drive (also known as the Notebook Hardrive) on the Bios down to the Lowest priority and Ubuntu still didn't come up just windows back again to say hello
Every other option was all USB or my Disc Drive and the Network Adapter

I don't Mind reinstalling Ubuntu 10.10 in the D:/ Drive i just want to get my Files back out of it's Documents folder but being able to start up Ubuntu again would be nice

---

### Post by Quackers on 2010-12-18
How many drives has your notebook? One?
The boot script output reports that you have 2 hard drives. Is one a usb hard drive? That would be one of the usb options in bios.

---

### Post by MrStRNGE on 2010-12-18
It has 2 physical hard drives i don't know if it was in the BIOS pre Ubuntu
But Windows can no longer see D as a hardrive maybe that has something to do with it
Ubuntu is hidden and the BIOS can't find it

---

### Post by Quackers on 2010-12-18
Very curious.
If the notebook has 2 hard drives and the bios is only seeing one of them there is a problem somewhere. Unless you have a raid array, but I didn't see any indication of that in the boot script.

---

### Post by MrStRNGE on 2010-12-18
Maybe there is one in windows causing that to happen?
wouldn't even know how to check

---

### Post by wilee-nilee on 2010-12-18
> **Quackers said:**
> Very curious.
If the notebook has 2 hard drives and the bios is only seeing one of them there is a problem somewhere. Unless you have a raid array, but I didn't see any indication of that in the boot script.

Probably not relevant but wasn't there a HP version of the dell data safe. You knows HP own firmware.

---

### Post by wilee-nilee on 2010-12-18
> **MrStRNGE said:**
> Maybe there is one in windows causing that to happen?
wouldn't even know how to check

There is a per-session boot key prompt that might show the second sdb drive, mine is f12, yours may be different. The prompt is used (as if) you were gong to the bios at powering on.

---

### Post by Quackers on 2010-12-18
The boot script says that one hard drive is 120GB and the other is 80GB. This would be most unusual for a twin drive laptop. Could you please boot from the Live cd again and select "try ubuntu" and go to System > Admin > gparted and when the program has scanned the discs post a screenshot of the first screen.
Then near the top right of gparted you will see a box that says /dev/sda with a little down arrow next to it. Please click on the down arrow and the option to choose /dev/sdb should be there. Select that option and post a screenshot of that screen as well please.

---

### Post by MrStRNGE on 2010-12-18
Yeah i thought the size difference was Odd too
but I've seen the with my own eyes when i was cleaning the dust out one day
i can even tell you that the 2 drives are right beside the mouse pad
C:/ to the left hand D:/ to the right hand side

---

### Post by Quackers on 2010-12-18
Well, at least we know that gparted can see both drives :-) And the boot script!
Did you see wilee-nilee's suggestion a couple of posts up - about the per-session boot choice? F12 on his. Does your laptop have that feature?

---

### Post by Quackers on 2010-12-18
Actually, while you are in gparted and in the /dev/sdb screen will you right-click on the sdb1 partition and select "manage flags" and then check the box for "boot", then apply the change.  It could be the reason why your bios doesn't see sdb.

---

### Post by MrStRNGE on 2010-12-18
i don't remember such an option but i will take a look

---

### Post by Quackers on 2010-12-18
See one post above yours first :-)

---

### Post by MrStRNGE on 2010-12-18
A Little late but i've been using The LiveCD anyway so i'll see what this does

---

### Post by MrStRNGE on 2010-12-18
It didn't add an entry into the BIOS for the second hard drive
And i even did boot device (F9 For me) and it just said 
CD DRIVE
USB Hard Drive (Live CD)
Notebook Hard Drive (vista)

---

### Post by MrStRNGE on 2010-12-18
If only ubuntu could ignore it's own security like it did to windows :p

---

### Post by Quackers on 2010-12-18
I'm not ignoring you, I'm thinking :-)

---

### Post by MrStRNGE on 2010-12-18
Mis understanding 
When you go to copy and paste files from a windows OS documents and setting folder
Ubuntu is unaffected by any widnows security protocall
When ubuntu tries to take from Ubuntu
(in this case me trying to recover files from an inaccessible OS Partition from the Live CD version it was installed off of)
It goes "Nope sorry can't do that"

---

### Post by Quackers on 2010-12-18
If you were booting previously using grub and all that has changed is that you've re-installed vista, then previously grub must have been installed in the mbr of sda.
I presume that grub stopped appearing as soon as you re-installed Vista?

---

### Post by MrStRNGE on 2010-12-18
Yes Sir
Vista had lost it;s edge just had to sharpen it a little
by reinstalling
I had installed Ubuntu about 2 weeks before
And i always Used GRUB to start it up

---

### Post by Quackers on 2010-12-18
Then all I can suggest is to try installing grub to the mbr of sda.
From the live cd desktop try these commands in a terminal. We'll try the short way first :-)
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If you copy/paste one line at a time to the terminal and press enter after each line please.

---

### Post by MrStRNGE on 2010-12-18
Said installation finished no errors reported

---

### Post by Quackers on 2010-12-18
Try rebooting please, without the cd in.
It may boot to Ubuntu and it may not. If nothing boots at all will you reboot to the Live cd please.

---

### Post by MrStRNGE on 2010-12-18
Victory!
That one worked!
now on to puttting my files back to where they belong
Thanks for the help!

---

### Post by Quackers on 2010-12-18
So grub re-appeared, excellent. Did you try booting both systems? All is well? Excellent :-)
If you are happy can you mark the thread as solved please, using the Thread Tools near the top of the forum. Thanks.

---

### Post by wilee-nilee on 2010-12-18
> **Quackers said:**
> So grub re-appeared, excellent. Did you try booting both systems? All is well? Excellent :-)
If you are happy can you mark the thread as solved please, using the Thread Tools near the top of the forum. Thanks.
I wondered about that had a 4 gig thumb with the first partition a W7 load for install with their loader and the second Ubuntu if I switched the boot flags I would get the one it was on.

---

