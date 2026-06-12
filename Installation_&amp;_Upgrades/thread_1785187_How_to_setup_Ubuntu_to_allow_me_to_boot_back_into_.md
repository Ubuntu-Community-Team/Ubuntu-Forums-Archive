---
title: "How to setup Ubuntu to allow me to boot back into Windows 7"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by void.pointer on 2011-06-17
I just installed Ubuntu 11.04 via USB drive. I have 3 disks on my system. Two are 1TB drives and are actual real drives, labeled sda and sdb. sda is where I installed Ubuntu (on its own drive). I also made sure that GRUB was assigned to sda during setup.

The 3rd drive isn't really a physical drive, it's a stripped RAID. My BIOS has Intel raid support, and I have 2 500GB drives that form one 1TB drive, and that's the one that Windows 7 is installed on. How do I setup GRUB to allow me to boot back into Windows 7?

---

### Post by Quackers on 2011-06-17
Welcome to UF.
From your Ubuntu desktop please open a terminal and run ```
sudo update-grub
``` and watch to see if the Windows Loader is recognised as grub.cfg is run.
If it is, reboot and try to boot Windows.

---

### Post by void.pointer on 2011-06-18
> **Quackers said:**
> Welcome to UF.
From your Ubuntu desktop please open a terminal and run ```
sudo update-grub
``` and watch to see if the Windows Loader is recognised as grub.cfg is run.
If it is, reboot and try to boot Windows.

Thanks for the help. Unfortunately it didn't seem to detect it. Here is the output:


```
robert@bob-linux:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
done
```

What can I do at this point? I tried going into my HDD device priority in my BIOS settings to put my RAID setup at the top so it would boot into windows first, but it said it failed to boot. I don't know if that's an issue with intel's RAID or if my Windows partition somehow got corrupted.

---

### Post by void.pointer on 2011-06-18
I wonder if the Intel RAID is messing things up. I don't think GRUB is recognizing the RAID setup, which is why it can't boot Windows. After reading around, people have installed dmraid to see if that can help. I might try that. In the meantime, I'm open to any suggestions you guys have. I took a leap of faith and installed Ubuntu to try linux, and I'm really starting to regret it now with all the trouble I'm having.

---

### Post by Rubi1200 on 2011-06-18
Although dmraid is on the CD for some reason it appears not to install on disk.

I suggest you run these commands:

```
sudo apt-get install dmraid

sudo dmraid -r

sudo dmraid -ay
```

You may still have to run update-grub afterwards too.

Hope this helps.

---

### Post by void.pointer on 2011-06-18
> **Rubi1200 said:**
> Although dmraid is on the CD for some reason it appears not to install on disk.

I suggest you run these commands:

```
sudo apt-get install dmraid

sudo dmraid -r

sudo dmraid -ay
```

You may still have to run update-grub afterwards too.

Hope this helps.

I did as you suggested but grub doesn't seem to recognize Windows even still. Here is the output:


```
robert@bob-linux:/usr/share/doc/dmraid$ sudo dmraid -r
/dev/sdd: isw, "isw_chhdebaadd", GROUP, ok, 976773166 sectors, data@ 0
/dev/sdc: isw, "isw_chhdebaadd", GROUP, ok, 976773166 sectors, data@ 0
robert@bob-linux:/usr/share/doc/dmraid$ sudo dmraid -ay
RAID set "isw_chhdebaadd_MyRaid" was activated
RAID set "isw_chhdebaadd_MyRaid1" was activated
robert@bob-linux:/usr/share/doc/dmraid$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
done
```

The good news is that after I ran this, my RAID drive shows up in Places >> Computer and I can browse the files (even my Windows folder), so I know the partition isn't corrupted. Now to just be able to boot from it...

Do I need to restart before I run update-grub?

UPDATE: Restarting didnt help.

UPDATE2:

Just out of curiosity I wanted to run fdisk to list my current drives. After running dmraid as you instructed I get different results. There seems to be some errors but I don't quite understand what it is reporting. The output is below:


```
robert@bob-linux:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00089928

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      487424   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              61      121602   976272385    5  Extended
/dev/sda5              61         548     3905536   82  Linux swap / Solaris
/dev/sda6             548       37021   292967424   83  Linux
/dev/sda7           37021      121602   679397376   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa9aaa9aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3ee124f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976764928    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/dm-0: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0xf3ee124f

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1      121602   976764928    7  HPFS/NTFS

Disk /dev/dm-1: 1000.2 GB, 1000207286272 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-1p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-1p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/dm-1p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

```

---

### Post by Rubi1200 on 2011-06-18
Hi,

let's take a closer look at where everything is by seeing the output of the boot script:

From within the working Ubuntu install:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by void.pointer on 2011-06-18
> **Rubi1200 said:**
> Hi,

let's take a closer look at where everything is by seeing the output of the boot script:

From within the working Ubuntu install:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Here are the contents of RESULTS.txt as you requested:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/mapper/isw_chhdebaadd_MyRaid.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

isw_chhdebaadd_MyRaid1: ________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   mount: unknown filesystem type ''
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       976,895       974,848  83 Linux
/dev/sda2             978,942 1,953,523,711 1,952,544,770   5 Extended
/dev/sda5             978,944     8,790,015     7,811,072  82 Linux swap / Solaris
/dev/sda6           8,792,064   594,726,911   585,934,848  83 Linux
/dev/sda7         594,728,960 1,953,523,711 1,358,794,752  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,953,531,903 1,953,529,856   7 NTFS / exFAT / HPFS

/dev/sdc1 ends after the last sector of /dev/sdc

Drive: isw_chhdebaadd_MyRaid _____________________________________________________________________

Disk /dev/mapper/isw_chhdebaadd_MyRaid: 1000.2 GB, 1000210694144 bytes
255 heads, 63 sectors/track, 121602 cylinders, total 1953536512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_chhdebaadd_MyRaid1              2,048 1,953,531,903 1,953,529,856   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/isw_chhdebaadd_MyRaid1 541C6EAB1C6E8836                       ntfs       Main
/dev/sda1        70840aff-c252-4e4d-afbe-8903c0e73094   ext2       
/dev/sda5        38f7b626-0af0-4591-a2b0-68d066217405   swap       
/dev/sda6        85369040-62d1-47d1-a503-9e8ecb75f8cc   ext4       
/dev/sda7        473046ea-86dc-4e08-b837-c4418eb1224e   ext4       
/dev/sdb1        6290B69790B67161                       ntfs       Storage
/dev/sdc                                                isw_raid_member 
/dev/sdd                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_chhdebaadd_MyRaid
isw_chhdebaadd_MyRaid1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/dm-1        /media/Main              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /boot                    ext2       (rw)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 85369040-62d1-47d1-a503-9e8ecb75f8cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
set locale_dir=($root)/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
	linux	/vmlinuz-2.6.38-8-generic root=UUID=85369040-62d1-47d1-a503-9e8ecb75f8cc ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=85369040-62d1-47d1-a503-9e8ecb75f8cc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.387785912 = 0.416381952    grub/core.img                                  2
   0.385347366 = 0.413763584    grub/grub.cfg                                  2
   0.023766518 = 0.025519104    initrd.img-2.6.38-8-generic                   55
   0.010767937 = 0.011561984    vmlinuz-2.6.38-8-generic                      20

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 85369040-62d1-47d1-a503-9e8ecb75f8cc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
set locale_dir=($root)/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
	linux	/vmlinuz-2.6.38-8-generic root=UUID=85369040-62d1-47d1-a503-9e8ecb75f8cc ro   quiet splash vt.handoff=7
	initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/vmlinuz-2.6.38-8-generic root=UUID=85369040-62d1-47d1-a503-9e8ecb75f8cc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 70840aff-c252-4e4d-afbe-8903c0e73094
	linux16	/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=85369040-62d1-47d1-a503-9e8ecb75f8cc /               ext4    errors=remount-ro 0       1
/dev/sda1       /boot           ext2    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=473046ea-86dc-4e08-b837-c4418eb1224e /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=38f7b626-0af0-4591-a2b0-68d066217405 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.579192162 = 4.916870144    boot/grub/core.img                             2
   4.576753616 = 4.914251776    boot/grub/grub.cfg                             2
   4.215172768 = 4.526007296    boot/initrd.img-2.6.38-8-generic              55
   4.202174187 = 4.512050176    boot/vmlinuz-2.6.38-8-generic                 20
   4.215172768 = 4.526007296    initrd.img                                    55
   4.202174187 = 4.512050176    vmlinuz                                       20

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  00 00 00 00 0b 10 00 00  00 00 00 00 77 f1 b9 05  |............w...|
00000010  5a ae 5b d5 92 38 7a 41  a6 49 c6 ac 5a aa ea b3  |Z.[..8zA.I..Z...|
00000020  01 00 00 00 00 00 00 00  64 00 00 00 00 00 00 00  |........d.......|
00000030  0c 10 00 00 00 00 00 00  5d eb 86 77 07 96 42 09  |........]..w..B.|
00000040  2d 58 7f 43 84 c3 de 93  a2 b2 4c 3c 01 00 00 00  |-X.C......L<....|
00000050  00 00 00 00 64 00 00 00  00 00 00 00 0d 10 00 00  |....d...........|
00000060  00 00 00 00 cc 74 ed 1c  42 82 4c 74 f5 4d 6c 45  |.....t..B.Lt.MlE|
00000070  ab 9e 01 4e fb 90 21 e3  01 00 00 00 00 00 00 00  |...N..!.........|
00000080  64 00 00 00 00 00 00 00  0e 10 00 00 00 00 00 00  |d...............|
00000090  50 10 dc ea f9 60 a6 aa  65 98 8e 45 b4 84 01 bc  |P....`..e..E....|
000000a0  7f e3 97 3e 01 00 00 00  00 00 00 00 64 00 00 00  |...>........d...|
000000b0  00 00 00 00 0f 10 00 00  00 00 00 00 05 72 ce ea  |.............r..|
000000c0  a4 5b fc 72 f9 24 11 40  9f 3f ad d2 7a fa d8 18  |.[.r.$.@.?..z...|
000000d0  01 00 00 00 00 00 00 00  64 00 00 00 00 00 00 00  |........d.......|
000000e0  10 10 00 00 00 00 00 00  2b cb 93 9e c3 d6 a7 0b  |........+.......|
000000f0  8d 56 59 41 ab 91 78 1a  91 fb 71 e5 01 00 00 00  |.VYA..x...q.....|
00000100  00 00 00 00 64 00 00 00  00 00 00 00 11 10 00 00  |....d...........|
00000110  00 00 00 00 02 cb eb 4c  0b f3 3a b3 52 f5 84 45  |.......L..:.R..E|
00000120  93 6c cb 93 e5 cd a2 9f  01 00 00 00 00 00 00 00  |.l..............|
00000130  64 00 00 00 00 00 00 00  12 10 00 00 00 00 00 00  |d...............|
00000140  4c 33 2e 2c 38 8a f5 00  4b c5 40 4c 86 96 97 23  |L3.,8...K.@L...#|
00000150  59 80 ea e1 01 00 00 00  00 00 00 00 64 00 00 00  |Y...........d...|
00000160  00 00 00 00 13 10 00 00  00 00 00 00 da 76 b8 52  |.............v.R|
00000170  91 1f 8c 18 40 3c 32 41  9e c5 d8 b0 3b 72 a8 a2  |....@<2A....;r..|
00000180  01 00 00 00 00 00 00 00  64 00 00 00 00 00 00 00  |........d.......|
00000190  14 10 00 00 00 00 00 00  23 a4 3f ad d4 96 f3 5b  |........#.?....[|
000001a0  b2 5e 6f 46 bd e9 2f b3  f2 36 1d 6e 01 00 00 00  |.^oF../..6.n....|
000001b0  00 00 00 00 64 00 00 00  00 00 00 00 15 10 00 00  |....d...........|
000001c0  00 00 00 00 af 26 b0 c3  cf 57 da 53 c0 62 c4 45  |.....&...W.S.b.E|
000001d0  81 de 76 10 bc ef d7 f5  01 00 00 00 00 00 00 00  |..v.............|
000001e0  64 00 00 00 00 00 00 00  16 10 00 00 00 00 00 00  |d...............|
000001f0  47 99 ed 9f 02 d5 cd d5  9c 2e 1b 10 93 97 08 00  |G...............|
00000200

Unknown BootLoader on sda2

00000000  b3 fd b3 9f b3 fd b3 fd  54 fd b3 fd fd 54 57 37  |........T....TW7|
00000010  2a f9 81 30 a9 83 d4 82  4f 1f 1f 1f 6c 1f 6c 1f  |*..0....O...l.l.|
00000020  6c 1f 42 0b 6c 42 42 42  0b 42 42 42 c5 42 42 0f  |l.B.lBBB.BBB.BB.|
00000030  c5 0f c5 42 42 42 42 42  42 42 42 42 6c 0b 6c 6c  |...BBBBBBBBBl.ll|
00000040  6c 6c 6c 7f 6c 6c c0 6c  0e c0 7f 0e c0 0e c0 0e  |lll.ll.l........|
00000050  37 0e ec 37 0e ec ec 37  2e fd ec ec 2e ec fd fd  |7..7...7........|
00000060  fd 2e 37 fd ec ec ec fd  ec fd ec fd 9f fd fd ec  |..7.............|
00000070  9f fd ec fd fd 2e fd 9f  ec fd fd fd fd fd fd fd  |................|
00000080  fd fd 9f fd 2e fd 9f fd  b3 fd b3 fd b3 fd b3 9f  |................|
00000090  b3 b3 b3 b3 b3 fd b3 a3  b3 b3 b3 b3 b3 b3 fd b3  |................|
000000a0  b3 b3 b3 b3 fd b3 9f 95  b3 57 54 fd b3 fd 54 fd  |.........WT...T.|
000000b0  54 fd 54 37 c4 a8 81 30  a9 83 82 82 4f f7 1f c0  |T.T7...0....O...|
000000c0  1f 6c 1f 6c 0b 6c 1f 42  1f 42 0b 6c c5 42 c5 42  |.l.l.l.B.B.l.B.B|
000000d0  42 42 c5 c5 42 c5 c5 c5  c5 42 c5 42 42 42 6c 42  |BB..B....B.BBBlB|
000000e0  6c 42 6c 0b 6c 0b 6c 6c  7f 7f c0 0e 6c 7f 37 6c  |lBl.l.ll....l.7l|
000000f0  7f c0 0e 37 0e ec ec ec  ec 37 fd 0e fd ec 9f fd  |...7.....7......|
00000100  ec fd ec 2e 37 fd fd 2e  fd fd 2e ec fd ec 2e 37  |....7..........7|
00000110  2e ec 9f fd ec 9f 2e 9f  fd 9f ec fd fd fd fd fd  |................|
00000120  a3 fd fd fd fd fd fd fd  fd fd fd fd fd b3 fd b3  |................|
00000130  9f b3 fd b3 b3 9f b3 fd  54 b3 b3 b3 b3 b3 b3 b3  |........T.......|
00000140  fd b3 54 b3 fd b3 b3 b3  b3 b3 b3 fd b3 b3 b3 fd  |..T.............|
00000150  54 b3 fd b3 9f b3 9f 3d  c4 a8 81 d7 a9 83 d4 67  |T......=.......g|
00000160  4f 6c 1f 6c 1f 6c 1f 6c  1f 6c 42 1f 42 42 6c 42  |Ol.l.l.l.lB.BBlB|
00000170  42 42 42 42 c5 0f c5 c5  c5 c5 c5 42 42 c5 42 42  |BBBB.......BB.BB|
00000180  0f 42 42 6c 0b 6c 1f 6c  6c 1f 6c 1f 6c 7f 7f 6c  |.BBl.l.ll.l.l..l|
00000190  c0 7f 6c 0e 0e 7f 0e ec  ec ec ec 0e ec 0e ec 9f  |..l.............|
000001a0  0e 9f fd 0e fd ec fd fd  fd fd 37 fd ec ec ec fd  |..........7.....|
000001b0  0e fd fd fd fd 9f fd ec  fd ec fd ec 2e fd 00 ee  |................|
000001c0  33 3c 82 27 84 23 02 00  00 00 00 30 77 00 00 27  |3<.'.#.....0w..'|
000001d0  85 23 05 fe ff ff 02 30  77 00 00 b0 ec 22 00 00  |.#.....0w...."..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc1



========= Devices which don't seem to have a corresponding hard drive: =========

sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
hexdump: /dev/sdc1: No such file or directory
hexdump: /dev/sdc1: No such file or directory

```

---

### Post by Rubi1200 on 2011-06-18
Thanks for posting the results.

I want to be cautious with this situation because there are a couple of things I am concerned about.

First, a question; do you really need sda1 as a separate /boot partition?

What worries me though is this:

sdc1:

> Mounting failed:   mount: unknown filesystem type

and this also:

> /dev/sdc1 ends after the last sector of /dev/sdc

I will send a message to forum member srs5694, who knows more about disk and partition problems, asking him to comment.

Meantime, please be patient and wait for one of us to post again.

Thanks.

---

### Post by void.pointer on 2011-06-18
> **Rubi1200 said:**
> Thanks for posting the results.

I want to be cautious with this situation because there are a couple of things I am concerned about.

First, a question; do you really need sda1 as a separate /boot partition?

What worries me though is this:

sdc1:



and this also:



I will send a message to forum member srs5694, who knows more about disk and partition problems, asking him to comment.

Meantime, please be patient and wait for one of us to post again.

Thanks.

Well I followed the instructions I found to create 4 partitions on my 1 hard drive for my Ubuntu install. It really pisses me off that Ubuntu messed up my Windows installation.

---

### Post by srs5694 on 2011-06-18
From your description, you have four physical disks -- the two 1 TB drives and two 500 GB drives. The two 500 GB drives are configured into a motherboard software RAID array for Windows, and you can't access those drives.

The trouble I see is that only one of those two 500 GB drives is being detected by Linux (/dev/sdc), so it can't complete your RAID array. My best guess is that the drive may be on a different type of controller on the motherboard and Linux lacks drivers for it; however, if that were the case I'd be a bit surprised that Windows can assemble the disks into a coherent array, since my understanding is that motherboard-based software RAID is tied to disk controller chipsets. Nonetheless, it might be worth trying to move the cable of that drive from one connector to another, if you've got more than four on your motherboard.

---

### Post by SACHINVD on 2011-06-18
You can add windows entry manually to /boot/grub/grub.cfg

---

### Post by Quackers on 2011-06-18
Which hard drive (or raid set) is set as first boot device in your bios?
I would definitely check the connection for /dev/sdd (the second of the two raid drives) with your motherboard. Yo do have 4 SATA ports on the MB?

---

### Post by void.pointer on 2011-06-18
Don't worry about it. I no longer need help with this because I reinstalled Windows 7 and I will never ever ever go back to Linux again.

Ubuntu has, yet again, seriously ****** up my system and it pisses me off that I was even dumb enough to think it would be any different this time.

I appreciate everyone trying to help but Linux isn't for me.

---

### Post by Quackers on 2011-06-18
It seems a little unfair to blame Linux for your own lack of knowledge, but if that's how you want it, so be it.

---

### Post by Rubi1200 on 2011-06-18
void.pointer,
I am sorry you feel this way about what has happened.

However, I want to ask whether you tried following the advice posted by srs5694 and Quackers to check the settings for the RAID motherboard?

Additionally, setting up RAID can be complicated on Ubuntu. But, this does not mean it cannot be done or that Ubuntu is to blame.

I don't know which guide you used to set this up originally, and you didn't provide a link, but perhaps you should consider asking first before following such guides.

The reason I say this is because separate boot partitions are rarely used nowadays so perhaps that guide was outdated.

In any event, if you decide at some point to reconsider, know that we will try and do our best to help you.

I wish you good luck whatever you decide.

---

