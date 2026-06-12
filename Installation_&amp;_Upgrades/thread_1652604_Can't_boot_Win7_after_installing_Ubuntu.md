---
title: "Can't boot Win7 after installing Ubuntu"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by WhiteLion on 2010-12-25
This might sound like the usual problem, but it isn't. I had win 7 installed, decided to install ubuntu on this desktop computer. I had a windows partition, and a few other partitions, one with a wubi install of windows that I never used, so I decided to delete it, while installing ubuntu 10.10. I had free unallocated space for installing ubuntu, which was contiguous to the partition of the wubi install of ubuntu, so I decided to merge them, I did all this in gparted while installing ubuntu 10.10, 2gb swap, then 15gb root and all that remained to home. Everything worked out fine (of course I never touched the win7 partition). After reboot grub doesn't show win 7, so I thought I'll just add it to grub, followed a few tutorials on this forum, but nothing worked. 
Then I remembered that the partition which I deleted to merge with the ubuntu partition, was an Active partition, and soon found out that my win7 partition was not active! (this is probably because I installed win 7 while I had still win vista, so that active partition was where vista was). So now a ~100mb apparently unallocated partition was the active partition (win 7 hidden boot partition?), and trying the Startup repair of win 7 cd doesn't work, tried bootrec /fixboot, successfully, but bootrec /rebuildbcd can't find any Windows installation, even after setting the win7 partition as active with DiskPart.
I don't know if this is the right place to post this, as this is almost entirely a windows problem, but I just wanted to have Ubuntu working alongside Windows (I use a lot adobe's sw, which runs sadly only on windows, otherwise I would use only ubuntu).
Please let me know what can I do! Thank you!

---

### Post by Rubi1200 on 2010-12-25
Hi and welcome to the forums :)

The best thing to do right now is the following:

Boot the computer with a LiveCD choosing to try not install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Copy/paste the contents from the text file that is generated and post it back here.

The results will tell us what is where and make offering solutions easier.

Thanks.

---

### Post by WhiteLion on 2010-12-26
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Boot the computer with a LiveCD choosing to try not install Ubuntu.


Hi, thanks for the help! I ran the boot info script in Ubuntu, not the live cd (I've read in the instructions "Boot into any Linux based operating system"). Is it ok? If not I'll do it on the live cd.

PS: this entry in grub is the one I added manually, following instructions of this forum, win 7 is on sda3:
### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

2ndPS: sdb is just a backup disk, there are no win installations there (and never were).

Here is the result, and thanks again!

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Boot/BCD /Windows/System32/winload.exe /wubildr.mbr 
                       /wubildr

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

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
28 heads, 40 sectors/track, 1744218 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          1,312       273,279       271,968  82 Linux swap / Solaris
/dev/sda2           3,907,582   922,685,966   918,778,385   f W95 Ext d (LBA)
Extended  partition  linking to another extended partition
/dev/sda5           3,907,584    33,202,175    29,294,592  83 Linux
/dev/sda6          33,204,224   409,591,807   376,387,584  83 Linux
/dev/sda7         409,603,887   922,685,903   513,082,017   7 HPFS/NTFS
/dev/sda3         922,685,967 1,045,567,103   122,881,137   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   956,285,189   956,285,127   7 HPFS/NTFS
/dev/sdb2         956,285,190   976,768,064    20,482,875   f W95 Ext d (LBA)
/dev/sdb5         956,285,253   976,768,064    20,482,812   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2: PTTYPE="dos" 
/dev/sda3        70C4DA75C4DA3CD2                       ntfs                                     
/dev/sda5        8d00537c-4e54-4d2f-bc68-31d84370271a   ext4                                     
/dev/sda6        d127b20e-9ed8-4600-aee5-31b1d593449c   ext4                                     
/dev/sda7        01C9CA761C81F380                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        42341D2B341D2387                       ntfs       My Book                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        460A-5191                              vfat       BACKUP                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sda7        /media/01C9CA761C81F380  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/70C4DA75C4DA3CD2  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/BACKUP            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8d00537c-4e54-4d2f-bc68-31d84370271a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 8d00537c-4e54-4d2f-bc68-31d84370271a
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8d00537c-4e54-4d2f-bc68-31d84370271a
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=8d00537c-4e54-4d2f-bc68-31d84370271a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8d00537c-4e54-4d2f-bc68-31d84370271a
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=8d00537c-4e54-4d2f-bc68-31d84370271a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8d00537c-4e54-4d2f-bc68-31d84370271a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8d00537c-4e54-4d2f-bc68-31d84370271a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8d00537c-4e54-4d2f-bc68-31d84370271a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=8d00537c-4e54-4d2f-bc68-31d84370271a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8d00537c-4e54-4d2f-bc68-31d84370271a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 8d00537c-4e54-4d2f-bc68-31d84370271a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=8d00537c-4e54-4d2f-bc68-31d84370271a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=d127b20e-9ed8-4600-aee5-31b1d593449c /home           ext4    defaults        0       2
/dev/sda1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   4.3GB: boot/grub/core.img
   8.9GB: boot/grub/grub.cfg
   3.6GB: boot/initrd.img-2.6.35-22-generic
   3.7GB: boot/initrd.img-2.6.35-24-generic
   5.4GB: boot/vmlinuz-2.6.35-22-generic
   5.4GB: boot/vmlinuz-2.6.35-24-generic
   3.7GB: initrd.img
   3.6GB: initrd.img.old
   5.4GB: vmlinuz
   5.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  00 4d 00 1e 43 a6 00 5a  ad 28 12 10 00 9c 0f 08  |.M..C..Z.(......|
00000010  00 00 1a 00 1e f2 4f be  72 82 a6 00 1e b6 11 00  |......O.r.......|
00000020  00 d1 00 1e 00 75 28 5e  1d 79 53 10 00 20 87 14  |.....u(^.yS.. ..|
00000030  00 00 78 00 1e 02 35 00  42 0b 48 07 10 00 ff 16  |..x...5.B.H.....|
00000040  08 00 00 6f 00 0f 76 a0  96 08 00 75 11 10 00 6e  |...o..v....u...n|
00000050  19 00 00 02 44 00 0f 09  14 82 34 2f 3f 80 10 00  |....D.....4/?...|
00000060  b2 1b 00 00 45 00 0f 00  b5 f7 87 60 46 f9 0f 00  |....E......`F...|
00000070  00 f7 1d 00 00 b9 01 00  00 38 58 6a a8 00 b5 00  |.........8Xj....|
00000080  bc 0c 02 ec 13 80 bd 87  c4 c4 c9 01 4b 05 1d 66  |............K..f|
00000090  0b 00 20 00 cf 00 29 00  07 00 8b 00 52 02 00 d0  |.. ...).....R...|
000000a0  00 1e 00 0c f2 00 03 00  51 81 0e ff ff fd 00 05  |........Q.......|
000000b0  01 01 18 09 ab 80 14 81  03 05 80 30 0c 80 01 8d  |...........0....|
000000c0  80 01 2a 99 80 01 36 80  40 3d 80 01 15 ff 01 06  |..*...6.@=......|
000000d0  00 e6 02 00 80 00 43 49  00 4d 5f 41 63 74 73 41  |......CI.M_ActsA|
000000e0  73 20 53 70 61 72 65 00  5d 65 73 00 63 72 69 70  |s Spare.]es.crip|
000000f0  74 69 6f 6e 40 00 00 54  68 65 20 8c 10 20 80 61  |tion@..The .. .a|
00000100  73 73 6f 63 69 61 01 10  00 20 69 6e 64 69 63 61  |ssocia... indica|
00000110  74 00 65 73 20 77 68 69  63 68 00 20 65 6c 65 6d  |t.es which. elem|
00000120  65 6e 74 80 73 20 63 61  6e 20 73 01 28 00 20 6f  |ent.s can s.(. o|
00000130  72 20 72 65 70 6c a0 61  63 65 20 74 80 26 6f 00  |r repl.ace t.&o.|
00000140  02 00 72 20 61 67 67 72  65 67 45 00 1c 64 06 19  |..r aggregE..d..|
00000150  2e 20 20 81 36 66 08 61  63 74 00 14 61 74 20 61  |.  .6f.act..at a|
00000160  c3 04 20 01 25 6f 70 65  72 80 16 80 37 00 20 22  |.. .%oper...7. "|
00000170  68 6f 74 20 73 74 00 61  6e 64 62 79 22 20 6d 40  |hot st.andby" m@|
00000180  6f 64 65 20 69 73 80 0a  65 00 63 69 66 69 65 64  |ode is..e.cified|
00000190  20 6f 8c 6e 20 c0 1e 04  22 20 62 79 05 18 00 20  | o.n ..." by... |
000001a0  62 61 73 69 73 2e 00 40  00 41 4d 45 4e 44 c0 00  |basis..@.AMEND..|
000001b0  54 00 00 00 4c 4f 43 41  4c 45 00 00 00 47 72 6f  |T...LOCALE...Gro|
000001c0  75 70 00 9e 66 81 53 c6  00 01 58 40 8a 80 03 41  |up..f.S...X@...A|
000001d0  5b 5a 38 40 50 4c c0 00  82 5e 59 00 02 00 70 72  |[Z8@PL...^Y...pr|
000001e0  65 66 3a 41 46 42 4d c3  0f 00 0e 44 8d 4e c2 05  |ef:AFBM....D.N..|
000001f0  80 3f 66 65 72 65 c6 6e  00 40 00 42 72 65 73 02  |.?fere.n.@.Bres.|
00000200

---

### Post by amsterdamharu on 2010-12-26
```
sda7: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   
```

Looks like Windows is found but not put in the grub.cfg, could you try the following command?

```
sudo update-grub
cat /boot/grub/grub.cfg | grep indo
```

Then post the output of it here?

---

### Post by WhiteLion on 2010-12-26
> **amsterdamharu said:**
> 
```
sudo update-grub
cat /boot/grub/grub.cfg | grep indo
```Then post the output of it here?

Output:
### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
### END /etc/grub.d/11_Windows ###

Edit: by the way, sda7 is not where windows 7 is, it's a storage partition I use, there are only common files, there isn't any OS installed

---

### Post by amsterdamharu on 2010-12-26
So is there a Windows in the menu when you boot?

---

### Post by WhiteLion on 2010-12-26
> **amsterdamharu said:**
> So is there a Windows in the menu when you boot?

Grub doesn't show up at all when I power on the pc, it goes straight to Ubuntu.

---

### Post by amsterdamharu on 2010-12-26
Try holding down the shift key to show the menu.

---

### Post by presence1960 on 2010-12-26
```
============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
[COLOR="Red"]partition #6 for (,msdos6)/boot/grub.[/COLOR]
=> Windows is installed in the MBR of /dev/sdb
```

GRUB is looking to the wrong partition that is why you don't get a GRUB menu. It should be pointing to partition #5 (sda5).

You can save the ubuntu installation by boot ing from the Live CD/USB. Choose try ubuntu without installing. When the desktop loads open a terminal and run ```
sudo mount /dev/sda5 /mnt
```This will mount your ubuntu root partition. Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
``` This will put GRUB on the MBR and pointing to the correct partition. 

As far as windows you may need to reinstall because if you installed windows 7 with Vista your windows 7 boot files were combined with Vista's. When you removed Vista you removed the files necessary to boot 7.
I am only ok with windows, but if meierfra is around he may be able to save your windows without reinstalling.

Your sda3 is a system reserved for windows 7. But if sda7 is your windows partition, which it probably is because you installed 7 after Vista it will never boot because a sole windows OS needs to be a primary partition. sda7 is logical. This makes a lot of sense because the default behavior for windows when installing a second windows OS is to make the new OS in a logical partition.

---

### Post by IWantFroyo on 2010-12-26
You have to back up your Windows 7, then erase your entire disk. Partition and install Ubuntu, then do the same with Windows. If you just put Linux in, it sometimes tends to corrupt some of the important Windows stuff. Just a precaution for people who have used their Windows system to save big programs before deciding to use Ubuntu.

---

### Post by presence1960 on 2010-12-26
```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
28 heads, 40 sectors/track, 1744218 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 1,312 273,279 271,968 82 Linux swap / Solaris
/dev/sda2 3,907,582 922,685,966 918,778,385 f W95 Ext d (LBA)
[COLOR="Red"]Extended partition linking to another extended partition[/COLOR]
/dev/sda5 3,907,584 33,202,175 29,294,592 83 Linux
/dev/sda6 33,204,224 409,591,807 376,387,584 83 Linux
/dev/sda7 409,603,887 922,685,903 513,082,017 7 HPFS/NTFS
/dev/sda3 922,685,967 1,045,567,103 122,881,137 7 HPFS/NTFS
```

The red above is probably not a good sign!

I would back up any important data, format and partition the disk the way you want it. Install windows first then reinstall ubuntu.

---

### Post by WhiteLion on 2010-12-27
> **amsterdamharu said:**
> Try holding down the shift key to show the menu.

Ok, did that and the Grub menu doesn't have win7.

> **presence1960 said:**
> 
Your sda3 is a system reserved for windows 7. But if sda7 is your windows partition, which it probably is because you installed 7 after Vista it will never boot because a sole windows OS needs to be a primary partition. sda7 is logical. This makes a lot of sense because the default behavior for windows when installing a second windows OS is to make the new OS in a logical partition.

Ubuntu is running just fine, the problem is with windows 7. When I uninstalled Vista Win7 was still running fine, but now I'm afraid I formatted the active partition where Win7 had it's boots files, so I don't know how to repair it, as Win7 recovery doesn't work. _Sda3 is where win7 is installed_, there is nothing in sda7!
Thanks to each of you for the help so far, I would really like to recover win7, I can't use adobe's products, particularly lightroom, without it.

PS: I'm going to be on vacation for the next few days, probably won't have access to internet.

---

### Post by WhiteLion on 2010-12-27
> **IWantFroyo said:**
> You have to back up your Windows 7, then erase your entire disk. Partition and install Ubuntu, then do the same with Windows. If you just put Linux in, it sometimes tends to corrupt some of the important Windows stuff. Just a precaution for people who have used their Windows system to save big programs before deciding to use Ubuntu.

If I use this last case resort, should I install first Windows or Ubuntu? Because presence1960 suggested first Win than Ubuntu.

---

### Post by wilee-nilee on 2010-12-27
> **WhiteLion said:**
> If I use this last case resort, should I install first Windows or Ubuntu? Because presence1960 suggested first Win than Ubuntu.

Windows first is preferred.:)

---

### Post by amsterdamharu on 2010-12-27
Strange that the boot info script says that win7 boot sector is found on sda7 and winXP boot sector is found on sda3.

Anyway, you can see the content of sda3 and know that it's Windows 7.

You say there is no Windows 7 in the boot menu but the output of the commands you posted show a menu entry for Windows 7. Did you mean there is no working menu entry for Windows 7?

You can add the entry manually by doing the following:
press alt + F2, type "gksu gedit" and click run.
Open the file /etc/grub.d/40_custom and change the content of the file to:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Microsoft Windows 7 (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 70C4DA75C4DA3CD2
    drivemap -s (hd0) ${root}
    chainloader +1
}
```Now execute the following command:
```
sudo update-grub
```Now when you reboot you should definitely have a windows 7 entry in the menu.

---

### Post by vnoeal on 2010-12-31
I'm new to this forum. I have the same problem that I can't boot my Window 7 after installing Ubuntu 10.10. I installed Ubuntu 10.10 over windows 7 and in the boot menu I can see both OS. I don't have any hassles booting Ubuntu and its working fine. I can't boot Windows 7, I think I have some problem with my boot record. Found below my Boot info script. Please help me.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 276980464 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   104,859,647   104,857,600   7 HPFS/NTFS
/dev/sda2         104,859,648   209,717,247   104,857,600   7 HPFS/NTFS
/dev/sda3         209,717,304   263,639,622    53,922,319   7 HPFS/NTFS
/dev/sda4         263,641,086   312,576,704    48,935,619   5 Extended
/dev/sda5         283,209,948   312,576,704    29,366,757  bc Acronis BackUp
/dev/sda6         263,641,088   282,277,887    18,636,800  83 Linux
/dev/sda7         282,279,936   283,209,727       929,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BE7ED7067ED6B67D                       ntfs                                     
/dev/sda2        DCAEC24DAEC21FBE                       ntfs       DATA STORE                    
/dev/sda3        6E64046C640438FB                       ntfs       BAKEUPS                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        B305-089D                              vfat       ACRONIS SZ                    
/dev/sda6        73248553-b766-40a1-94d4-dba86dd1a2b4   ext4                                     
/dev/sda7        e0c44820-9068-4e31-a4ca-d199b3dda6a8   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 73248553-b766-40a1-94d4-dba86dd1a2b4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 73248553-b766-40a1-94d4-dba86dd1a2b4
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 73248553-b766-40a1-94d4-dba86dd1a2b4
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=73248553-b766-40a1-94d4-dba86dd1a2b4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 73248553-b766-40a1-94d4-dba86dd1a2b4
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=73248553-b766-40a1-94d4-dba86dd1a2b4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 73248553-b766-40a1-94d4-dba86dd1a2b4
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=73248553-b766-40a1-94d4-dba86dd1a2b4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 73248553-b766-40a1-94d4-dba86dd1a2b4
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=73248553-b766-40a1-94d4-dba86dd1a2b4 ro single 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 73248553-b766-40a1-94d4-dba86dd1a2b4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 73248553-b766-40a1-94d4-dba86dd1a2b4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set be7ed7067ed6b67d
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=73248553-b766-40a1-94d4-dba86dd1a2b4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=e0c44820-9068-4e31-a4ca-d199b3dda6a8 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/core.img
 140.1GB: boot/grub/grub.cfg
 136.1GB: boot/initrd.img-2.6.35-22-generic
 136.1GB: boot/initrd.img-2.6.35-24-generic
 141.8GB: boot/vmlinuz-2.6.35-22-generic
 141.8GB: boot/vmlinuz-2.6.35-24-generic
 136.1GB: initrd.img
 136.1GB: initrd.img.old
 141.8GB: vmlinuz
 141.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  42 84 7b 91 77 08 8c bf  ea 29 8f 7a be bc 53 ff  |B.{.w....).z..S.|
00000010  5b 05 49 0e 27 89 d0 7d  dd 29 34 be a7 b6 57 fb  |[.I.'..}.)4...W.|
00000020  32 9b 28 dc a3 0b ef f8  a9 b3 a2 60 95 48 ca d2  |2.(........`.H..|
00000030  5b 94 74 bd 22 7b 82 9c  a3 cd a0 2a 7d ed 35 37  |[.t."{.....*}.57|
00000040  20 ae a7 d0 66 6a b3 9b  97 16 0a cf 0e 3d a8 3c  | ...fj.......=.<|
00000050  0d 82 8e d5 9e 9b 05 a9  cd 2c 34 a3 78 50 65 b8  |.........,4.xPe.|
00000060  12 e0 19 35 61 1d f1 c7  87 0b 5e 20 c6 cf ac 03  |...5a.....^ ....|
00000070  7d 88 bb b3 ec 52 5b ac  34 73 bb ec 7c dd eb 2a  |}....R[.4s..|..*|
00000080  11 72 02 95 a1 7a 13 5f  04 6b 89 60 9d 63 94 32  |.r...z._.k.`.c.2|
00000090  63 32 3d 46 fe 51 61 41  b9 ee eb dd 7f 5c 51 64  |c2=F.QaA.....\Qd|
000000a0  5b 60 cc 6e 82 58 18 13  ee 3d 81 32 67 81 13 43  |[`.n.X...=.2g..C|
000000b0  ea 89 6c f9 e0 c8 60 97  88 21 05 d0 f3 d5 95 58  |..l...`..!.....X|
000000c0  ed 99 a6 34 3f 8c e1 ab  6c 94 0e c2 96 99 5d 85  |...4?...l.....].|
000000d0  90 6b bb 20 1f 94 86 6d  e6 c6 bb b1 11 3d 22 1a  |.k. ...m.....=".|
000000e0  77 37 cd 8c a7 18 7f f9  e2 26 61 90 ab d2 11 5a  |w7.......&a....Z|
000000f0  aa 96 61 51 77 1c ae 51  96 71 3c dd ce df 8f 2c  |..aQw..Q.q<....,|
00000100  85 f9 e0 56 c3 ae 0b 79  66 5a 92 f5 df 00 d3 f3  |...V...yfZ......|
00000110  ed 9e 8e 5d 69 95 c4 30  4e 23 6b 4f 4e d9 7f 3a  |...]i..0N#kON..:|
00000120  ee 43 db 27 39 36 d4 81  67 a8 f7 74 9d 98 bd ae  |.C.'96..g..t....|
00000130  52 e5 e8 4f 25 43 8c cc  03 fc 7b e4 91 4c 90 c8  |R..O%C....{..L..|
00000140  30 d0 d8 18 2f af bc 4e  38 e2 1b 79 d7 35 e4 03  |0.../..N8..y.5..|
00000150  c8 41 06 7c b0 cb 7f 97  76 8d dd a0 d0 db f1 fb  |.A.|....v.......|
00000160  28 b7 be 3d 82 a8 24 37  71 18 7a 1a a4 13 11 40  |(..=..$7q.z....@|
00000170  7d f9 6f e0 73 8b b6 83  81 09 f2 5a f3 9f e5 04  |}.o.s......Z....|
00000180  cf 21 8c f3 fd e5 a0 50  58 ba 53 d4 0a 43 57 c7  |.!.....PX.S..CW.|
00000190  08 8d cc a2 18 e3 2e 6d  f8 1a e6 f6 cf 1b ca 83  |.......m........|
000001a0  67 28 5f 3d 24 8e eb 9f  f9 09 42 4b 6b fd bf 83  |g(_=$.....BKk...|
000001b0  b3 0d 63 e4 b1 7a e8 1e  9c d1 d6 18 57 ba 00 01  |..c..z......W...|
000001c0  c1 ff bc fe ff ff de 98  2a 01 e5 19 c0 01 00 fe  |........*.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 60 1c 01 00 00  |...........`....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by WhiteLion on 2011-01-01
> **amsterdamharu said:**
>  Now when you reboot you should definitely have a windows 7 entry in the menu.
Yes, I could see it, but then windows couldn't find his boot files, so in the end I formatted everything and re-installed win and ubuntu, so now everything is working fine. 
Thanks to each of you ubuntu fine users for the help, I really appreciate it.

to vnoeal: you should probably start your own thread, otherwise it becomes too chaotic.

---

### Post by presence1960 on 2011-01-01
> **WhiteLion said:**
> Yes, I could see it, but then windows couldn't find his boot files, so in the end I formatted everything and re-installed win and ubuntu, so now everything is working fine. 
Thanks to each of you ubuntu fine users for the help, I really appreciate it.

to vnoeal: you should probably start your own thread, otherwise it becomes too chaotic.

```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
28 heads, 40 sectors/track, 1744218 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 1,312 273,279 271,968 82 Linux swap / Solaris
/dev/sda2 3,907,582 922,685,966 918,778,385 f W95 Ext d (LBA)
[COLOR="Red"]Extended partition linking to another extended partition[/COLOR]
/dev/sda5 3,907,584 33,202,175 29,294,592 83 Linux
/dev/sda6 33,204,224 409,591,807 376,387,584 83 Linux
/dev/sda7 409,603,887 922,685,903 513,082,017 7 HPFS/NTFS
/dev/sda3 922,685,967 1,045,567,103 122,881,137 7 HPFS/NTFS
```

That was probably the best thing to do because your partition table was messed up.

---

