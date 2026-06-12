---
title: "Dual-Boot bootloader question"
date: 2012-01-10
forum: Installation &amp; Upgrades
---

### Post by lonewolf1991 on 2012-01-10
Hello, 
I installed Ubuntu today on my computer alongside Windows. Ubuntu was given its own 80GB drive, while Windows is on a 3 Drive RAID0 array. During the installation, a message box popped up saying grub cannot be installed on drive "sda" and was asked to choose another one, to which I chose the Ubuntu harddrive. After the installation, I had to fix the windows bootloader to get into windows.

My question is, why was the windows bootloader affected, even though Ubuntu and Grub were installed on a separate drive? It's been really bugging me, as I really don't know if that can lead to data corruption.

---

### Post by oldfred on 2012-01-11
Welcome to the forums.

Did grub try to install to sda. But with RAID do you even boot from sda or really from the RAID partition?

I normally run this before & after every install so I know what is installed where. I also run it just to document system on every backkup.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by lonewolf1991 on 2012-01-11
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Grub2 (v1.99) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
 => Windows is installed in the MBR of /dev/mapper/nvidia_bbbddafe.

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

nvidia_bbbddafe1: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

nvidia_bbbddafe2: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848 1,465,188,351 1,464,981,504   7 NTFS / exFAT / HPFS

/dev/sdb2 ends after the last sector of /dev/sdb

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sde _____________________________________________________________________

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048   139,526,143   139,524,096  83 Linux
/dev/sde2         139,528,190   156,296,384    16,768,195   5 Extended
/dev/sde5         147,910,518   156,296,384     8,385,867  82 Linux swap / Solaris
/dev/sde6         139,528,192   147,908,607     8,380,416  82 Linux swap / Solaris


Drive: nvidia_bbbddafe _____________________________________________________________________

Disk /dev/mapper/nvidia_bbbddafe: 750.2 GB, 750177976320 bytes
255 heads, 63 sectors/track, 91203 cylinders, total 1465191360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/nvidia_bbbddafe1   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/nvidia_bbbddafe2            206,848 1,465,188,351 1,464,981,504   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/nvidia_bbbddafe1 A22CB79D2CB76AC5                       ntfs       System Reserved
/dev/mapper/nvidia_bbbddafe2 3C70BE6870BE2892                       ntfs       
/dev/sdb                                                nvidia_raid_member 
/dev/sde1        eb34fc23-6b51-474a-bec9-1bf385659e59   ext4       
/dev/sde5        9d4bd40e-b83e-498a-a2a9-12312d73a84b   swap       
/dev/sde6        c59e9530-34e3-4020-b7d7-51e8a0ed78ac   swap       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
nvidia_bbbddafe
nvidia_bbbddafe1
nvidia_bbbddafe2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sde1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sde1/boot/grub/grub.cfg: ===========================

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
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set=root eb34fc23-6b51-474a-bec9-1bf385659e59
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd3,msdos1)'
  search --no-floppy --fs-uuid --set=root eb34fc23-6b51-474a-bec9-1bf385659e59
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root eb34fc23-6b51-474a-bec9-1bf385659e59
	linux	/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=eb34fc23-6b51-474a-bec9-1bf385659e59 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-14-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root eb34fc23-6b51-474a-bec9-1bf385659e59
	echo	'Loading Linux 3.0.0-14-generic-pae ...'
	linux	/boot/vmlinuz-3.0.0-14-generic-pae root=UUID=eb34fc23-6b51-474a-bec9-1bf385659e59 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-14-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root eb34fc23-6b51-474a-bec9-1bf385659e59
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=eb34fc23-6b51-474a-bec9-1bf385659e59 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root eb34fc23-6b51-474a-bec9-1bf385659e59
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=eb34fc23-6b51-474a-bec9-1bf385659e59 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root eb34fc23-6b51-474a-bec9-1bf385659e59
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd3,msdos1)'
	search --no-floppy --fs-uuid --set=root eb34fc23-6b51-474a-bec9-1bf385659e59
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/nvidia_bbbddafe1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd4,msdos1)'
	search --no-floppy --fs-uuid --set=root A22CB79D2CB76AC5
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
--------------------------------------------------------------------------------

=============================== sde1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdd1 during installation
UUID=eb34fc23-6b51-474a-bec9-1bf385659e59 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=c59e9530-34e3-4020-b7d7-51e8a0ed78ac none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sde1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/initrd.img-3.0.0-14-generic-pae           2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic-pae              2
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1


Unknown BootLoader on sdb2



========= Devices which don't seem to have a corresponding hard drive: =========

sda 

=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by rockachu2 on 2012-01-11
Being not so good at grub, i have dealt with it numerous times.


Grub installs itself in two places: the mbr and in the partition you told it to install.
The mbr install links to the partition, so when you restored the windows boot loader, it overwrote the mbr and pointed it back at windows. 

On another note, if grub cannot load your windows partition for some reason, then windows won't appear on your list.


run:

> sudo update-grub

to regenerate the list of OS's just in case grub missed windows.

If it still doesn't work, then you'll have to ask someone who knows why grub isn't finding windows (oldfred may be a good choice).

---

### Post by oldfred on 2012-01-11
You have grub in sde. 

When you installed, it is best with multiple drives to use the manual install or Something Else and chose partitions. That same screen also then gives the combo box on which drive (do not use partition) to install to.

The script did not parse the RAID. You may want to install the mdadm drivers.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)
Software RAID w/mdadm driver
[https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html)
[https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.10/serverguide/C/advanced-installation.html)

---

### Post by lonewolf1991 on 2012-01-11
I see, so it actually didn't touch the windows drives. I have never used the manual install, mainly because I don't know which partitions I need and how big the partitions have to be for proper functionality.

---

### Post by Mark Phelps on 2012-01-12
If you have actual physical drives on which only Windows is installed, it's best to disconnect them when installing Ubuntu.  That prevents any accidental or unintentional installation of GRUB to the MBRs for those drive.

It's a simple matter when done to reconnect the Windows drives and run the update-grub command to rebuild the GRUB menu.

---

### Post by darkod on 2012-01-12
> **Mark Phelps said:**
> If you have actual physical drives on which only Windows is installed, it's best to disconnect them when installing Ubuntu.  That prevents any accidental or unintentional installation of GRUB to the MBRs for those drive.

It's a simple matter when done to reconnect the Windows drives and run the update-grub command to rebuild the GRUB menu.

I have to say I don't agree with this (sorry Mark :) ).

I support using the manual install because it gives you total control, especially in multi-disk environment. If you are unsure about partitioning or anything else, ask before you start. There is plenty of info on google even without asking.

I always think you should do OS installs (any type of OS) with all hardware present, including disks. The OS should detect all hardware it will need to work with.

On top of that, in this particular situation, unplugging RAID0 disks might get you in even bigger trouble, potentially. Don't forget that RAID0 is not fault redundant. How would your array react with disk(s) unplugged?

---

