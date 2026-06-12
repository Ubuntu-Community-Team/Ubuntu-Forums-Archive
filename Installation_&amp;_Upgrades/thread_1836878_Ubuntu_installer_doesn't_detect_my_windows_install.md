---
title: "Ubuntu installer doesn't detect my windows installation/HDD partitions"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by Daniel090 on 2011-08-31
Well hello everyone i hope you can help me with my problem:

Yesterday i installed Ubuntu via Wubi over Windows, i mean using a virtual partition, but it had a couple of very annoying bugs so i decided to create an actual partition for the dual boot.
 I Downloaded Ubuntu from Ubuntu.com and burnt the ISO, I assumed the installation "wizard" would give me the option create a partition. [I should mention that my PC wouldn't boot with the CD, so i had to choose the option "Help me Boot from CD"]
 I got to the step on the installation where i had to allocate the drive space, the option to install alongside Windows was there, I chose "something else" instead and it opened the partition manager, it showed my partitions [C: drive, and the occult recovery partitions]. 
I didn't feel comfortable with the partition manager so i exited the installation and booted Windows 7 [64bit] to create a partition, my disk was fragmented so i had to defragment it to create a partition of the size that i wanted [27GB]
After the process  of defragmentation was done, i created the partition using the Windows Disk Manager, and formated it as NTFS.
Until then everything was OK, i Booted Ubuntu from the CD, clicked on "Install Ubuntu 11.04" on the UI, and when i got to the step where i had to allocate drive space, the option to install it alongside Windows
 [I dont really remember what the option was exactly ] was missing and there was a message saying "This computer has no detected operative systems, What would you like to do?".
[IMG]http://i873.photobucket.com/albums/ab299/Daniel_93LDU/Screenshot-1.png[/IMG]
 so i clicked "Something Else" and my partitions didn't show, it just shows my HDD.
[IMG]http://i873.photobucket.com/albums/ab299/Daniel_93LDU/Screenshot.png[/IMG]

So i gave up on the installation and went back to Windows 7 to install it via Wubi, on a virtual partition, so then i could migrate it to an actual partition, when the process was done i booted Ubuntu and the installation process gave me the error "No root filesystem defined".

Sorry if i overdid the post, but im extremely frustrated and this is the only thing i can do.
PD: I'm running on a Toshiba laptop

---

### Post by Quackers on 2011-08-31
Welcome to UF :-)
Firstly can you inform as to how many primary partitions you now have on the system?
If unsure you can post a screenshot of your Windows Disk Management screen.

---

### Post by oldfred on 2011-08-31
From liveCD post this using terminal, so we can see how man partitions you have:

```
sudo fdisk -lu
```Many Windows 7 computers use all 4 primary partitions that is allowed under MBR(msdos) formating. Windows uses 2, a hidden system boot/recovery & the main install. The vendor does a recovery partition which is an image of you hard drive to restore your computer to the way it was when purchased, erasing everything since. And often just another Utility partition to use all 4 and prevent you from easily installing anything else. Microsoft likes it and the Vendor likes it as users do not call about installs of stuff they cannot script for a help desk.

You need a repairCD or USB flash drive for every operating system you have installed (and maybe a couple of other repairCDs).
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


If you have made a lot of changes you may not want to restore Win7 with the recovery disks unless eventually you sell it. But you should make the set of recovery DVDs as that is the only way to totally restore it.
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Daniel090 on 2011-08-31
The command "sudo fdisk -lu"
gave me this
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a502fc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2         3074048   869947540   433436746+   7  HPFS/NTFS
/dev/sda3       932866048   976784129    21959041   17  Hidden HPFS/NTFS

---

### Post by oldfred on 2011-08-31
That says you can create a sda4 as an extended partition and install many logical partitions for Ubuntu. If creating the partitions manually you have to shrink win7 and that is best done with win7's MMC. Then use gparted in Ubuntu liveCD to create partitions.

It seems a little strange that your boot flag is on sda1, and is unknown?? Boot flag is usually on a 100MB boot/recovery NTFS partition or the main NTFS Windows partition depending on where the boot files are. Windows can only boot the partition with the boot flag, grub does not use a boot flag.

Post this to see your entire configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Daniel090 on 2011-09-01
```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       43905023 sectors, but according to the info from 
                       fdisk, it has 43918081 sectors.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   869,947,540   866,873,493   7 NTFS / exFAT / HPFS
/dev/sda3         869,949,440   932,866,047    62,916,608   f W95 Extended (LBA)
/dev/sda5         869,951,488   932,866,047    62,914,560   7 NTFS / exFAT / HPFS
/dev/sda4         932,866,048   976,784,129    43,918,082  17 Hidden NTFS / HPFS

/dev/sda4 ends after the last sector of /dev/sda

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        E202520F0251E8D5                       ntfs       TOSHIBA System Volume
/dev/sda2        92F253A5F2538BFB                       ntfs       Local Disc
/dev/sda4        1A6655F16655CE5F                       ntfs       HDDRECOVERY
/dev/sda5        48C09827C0981D6E                       ntfs       Local Disc

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)



```

---

### Post by YesWeCan on 2011-09-01
> **Daniel090 said:**
> After the process  of defragmentation was done, i created the partition using the Windows Disk Manager, and formated it as NTFS.
Ubuntu cannot be installed to an NTFS file system, it needs to be a linux file system such as ext4. Try deleting the partition to leave empty space on the disk. The Ubuntu installer should show that unallocated space in its partitioner and you can tell it to make root and swap partitions there.

---

### Post by Daniel090 on 2011-09-01
> **YesWeCan said:**
> Ubuntu cannot be installed to an NTFS file system, it needs to be a linux file system such as ext4. Try deleting the partition to leave empty space on the disk. The Ubuntu installer should show that unallocated space in its partitioner and you can tell it to make root and swap partitions there.
I already tried that and it didn't work

---

### Post by YesWeCan on 2011-09-01
I just noticed this:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total [COLOR="red"]976773168[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   869,947,540   866,873,493   7 NTFS / exFAT / HPFS
/dev/sda3         869,949,440   932,866,047    62,916,608   f W95 Extended (LBA)
/dev/sda5         869,951,488   932,866,047    62,914,560   7 NTFS / exFAT / HPFS
/dev/sda4         932,866,048   [COLOR="red"]976,784,129[/COLOR]    43,918,082  17 Hidden NTFS / HPFS

[COLOR="Red"]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]
```
That'll probably be it. The partition table is corrupt.
What's in sda4 - it might have to be "rearranged"

---

### Post by srs5694 on 2011-09-01
YesWeCan's analysis is correct; whatever you used for partitioning created (or changed) /dev/sda4 in such a way that it's too big for the disk. The Linux libparted library, upon which the Ubuntu installer's partitioning tool is based, flakes out and reports as empty any disk that has even a tiny partition table problems (and sometimes non-problems, too), which is why this defect is causing the partition table to show up as empty.

If you created /dev/sda4 for Linux's use, or if it's otherwise empty, the best option is to delete it. You can do this with whatever you used to create it or with fdisk:


[list=1]
[*]Type "sudo fdisk /dev/sda" to launch fdisk into interactive mode.
[*]Type "d" to delete a partition. You'll be asked for a partition number. Type "4".
[*]Type "p" to view the partition table and verify that you're working on the correct disk and have deleted the correct partition (as determined by its start and end points). If something seems wrong, type "q" to quit without saving your changes.
[*]If everything seems fine, type "w" to save your changes.
[/list]


Once that partition is deleted, the Ubuntu installer should be able to handle the disk correctly. You can use it to create partitions, as described in various installation documents on the Web. (I don't happen to have any bookmarked, though.)

If /dev/sda4 contains valuable data, then it becomes trickier. You'll have to either resize it with a utility that can cope with its illegal size (I have no recommendations on that score) or back up its data, delete it, create a new partition in its place, and restore its data. Since it has a type of 0x17 ("Hidden NTFS / HPFS"), you'll have to unhide it before you can back it up from Windows.

One caution: Do not use Windows to create partitions for Linux! Recent versions of the Windows partitioning tools have a tendency to convert a disk to use Windows' "dynamic disks" feature, which is a Microsoft-only type of partitioning scheme. They typically do this if you try to create more than four partitions on a disk. If you use dynamic disks, it becomes much harder (perhaps even impossible) to install Linux on the disk. There are some tools, such as EASEUS, that claim to be able to undo the conversion to dynamic disk format, but I've never tested them, so I don't know how well they work. Your disk has *not* been converted to dynamic disk format, so you got lucky on that score. I mention this mainly to warn you off of a second attempt that might result in such a conversion, but also to warn off anybody else who might read this in the future.

---

### Post by oldfred on 2011-09-01
+1 on srs5694 suggestions and kudos to YesWeCan for seeing the partition error.

Another way, first backup partition table and then use sfdisk to repair it.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

sfdisk to fix extended beyond end -partition outside the disk! But requires some  math to calculate size to get end sector.
[http://ubuntuforums.org/showthread.php?t=1012825](http://ubuntuforums.org/showthread.php?t=1012825)

---

### Post by srs5694 on 2011-09-01
> **oldfred said:**
> +1 on srs5694 suggestions and kudos to YesWeCan for seeing the partition error.

Another way, first backup partition table and then use sfdisk to repair it.

You could do the same thing with fdisk -- delete the partition and then create a new one with the same start point and a legal end point. You'd have to be careful to check that the start point is identical *in sector values* (not just in cylinder values). Under some circumstances, fdisk uses cylinder values or rounds the values you give it, so you've got to be sure it doesn't change those values.

The trouble with this approach, whether you use fdisk or sfdisk, is that it doesn't resize the filesystem *inside* the partition. Thus, this partition resizing isn't a complete fix, unless the contained filesystem is small enough to fit on the disk (which may be the case, but we can't be sure without seeing some NTFS diagnostics).

The bottom line: If you try this, you should follow up by using CHKDSK to check the filesystem or perhaps using other tools to verify the validity of the filesystem or resize it to fit inside the partition. I'm not an expert on NTFS repair, so I can't offer more specific suggestions about how to fix this up.

---

### Post by Daniel090 on 2011-09-01
Ok srs5694, i did just as you said and it killed my windows installation, i recovered it, and then the Ubuntu installer recognized the disc properly, I created a 30 GB partition with the Ubuntu partition manager, and installed Ubuntu Successfully.
Now the problem is that, the Ubuntu Installer didnt install on the 30 GB partition I created, It installed on a  166 GB space Im not sure where it came from, I didn't think of that as a problem, i thought i would be able to shrink the Ubuntu partition and add up to the Windows partition, but apparently it installed in such way that it killed my Windows installation and i don't understand my partitions anymore.

here's the new disk information, please someone tell me what happened.

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000   7 NTFS / exFAT / HPFS
/dev/sda2           3,074,048   327,911,647   324,837,600  83 Linux
/dev/sda3         327,913,470   932,866,047   604,952,578   f W95 Extended (LBA)
/dev/sda5         869,951,488   932,866,047    62,914,560   7 NTFS / exFAT / HPFS
/dev/sda6         327,913,472   861,695,999   533,782,528  83 Linux
/dev/sda7         861,698,048   869,935,103     8,237,056  82 Linux swap / Solaris
/dev/sda4         932,866,048   976,771,071    43,905,024   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E202520F0251E8D5                       ntfs       TOSHIBA System Volume
/dev/sda2        8be6fb3c-7e45-47b8-94b7-fdd2b0cf9fcb   ext2       
/dev/sda4        1A6655F16655CE5F                       ntfs       HDDRECOVERY
/dev/sda5        3610C2F010C2B661                       ntfs       New Volume
/dev/sda6        cf395592-5899-494f-8940-5b44888a7f11   ext4       
/dev/sda7        c32040ad-f009-4b3e-9715-32acbc41b835   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/TOSHIBA System Volume fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/HDDRECOVERY       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Repair disc Windows 7 64-bit udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)


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
search --no-floppy --fs-uuid --set=root cf395592-5899-494f-8940-5b44888a7f11
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root cf395592-5899-494f-8940-5b44888a7f11
set locale_dir=($root)/boot/grub/locale
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root cf395592-5899-494f-8940-5b44888a7f11
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=cf395592-5899-494f-8940-5b44888a7f11 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root cf395592-5899-494f-8940-5b44888a7f11
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=cf395592-5899-494f-8940-5b44888a7f11 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root cf395592-5899-494f-8940-5b44888a7f11
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root cf395592-5899-494f-8940-5b44888a7f11
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root E202520F0251E8D5
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 1A6655F16655CE5F
    drivemap -s (hd0) ${root}
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
UUID=cf395592-5899-494f-8940-5b44888a7f11 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c32040ad-f009-4b3e-9715-32acbc41b835 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 240.495864868 = 258.230468608  boot/grub/core.img                             1
 184.547019958 = 198.155853824  boot/grub/grub.cfg                             1
 158.010044098 = 169.661992960  boot/initrd.img-2.6.38-8-generic               2
 240.494144440 = 258.228621312  boot/vmlinuz-2.6.38-8-generic                  1
 158.010044098 = 169.661992960  initrd.img                                     2
 240.494144440 = 258.228621312  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  53 97 9e 11 7a 69 50 f2  6e 35 52 c9 a6 3b 2d 4a  |S...ziP.n5R..;-J|
00000010  60 b3 12 8c d0 24 e2 79  d4 79 50 ba f6 5d 46 ec  |`....$.y.yP..]F.|
00000020  34 44 35 5f e9 03 50 bf  92 e0 17 05 51 3c 1e 68  |4D5_..P.....Q<.h|
00000030  b6 43 c6 1a e1 74 68 74  5a 95 44 bc 5c 50 f8 a2  |.C...thtZ.D.\P..|
00000040  dc 3f 8e 16 e3 f4 7e 4a  f8 bb c8 9e 42 97 62 e2  |.?....~J....B.b.|
00000050  5f 03 40 fc 60 25 a1 9c  a6 66 42 57 95 52 9f a7  |_.@.`%...fBW.R..|
00000060  52 8d 3a 5c 4f 21 ac 9d  6f 57 07 93 c9 cc ad 1e  |R.:\O!..oW......|
00000070  b7 05 29 28 0f 07 d9 e4  33 14 68 d5 e7 2d 91 b5  |..)(....3.h..-..|
00000080  c4 54 01 f1 3a 7c 7a 4f  f5 51 dc e9 61 74 8a 30  |.T..:|zO.Q..at.0|
00000090  43 21 95 2a 11 85 da 2c  84 9c e7 19 d0 4b 51 e7  |C!.*...,.....KQ.|
000000a0  51 94 8a 8c 98 2e 84 b6  c6 58 d0 25 66 8b 71 8c  |Q........X.%f.q.|
000000b0  af 48 cc af 5f 3b 50 d5  c1 31 38 99 4e 21 eb 24  |.H.._;P..18.N!.$|
000000c0  27 49 76 63 56 a1 a1 69  1d 2a 25 61 cc 61 2d 1c  |'IvcV..i.*%a.a-.|
000000d0  cf 53 e8 b5 0c 04 2d 40  d8 7b a0 59 05 28 b7 1a  |.S....-@.{.Y.(..|
000000e0  e6 22 94 c1 2e eb 89 15  c5 9a 55 8d 72 9f b4 16  |."........U.r...|
000000f0  95 4b 02 d3 0c f4 96 8f  1a d4 a8 73 0a 62 0a 6a  |.K.........s.b.j|
00000100  29 99 71 c9 bd 55 55 55  55 55 55 55 55 55 55 55  |).q..UUUUUUUUUUU|
00000110  55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  |UUUUUUUUUUUUUUUU|
*
00000150  55 55 55 55 55 55 55 55  00 0e 00 94 8b 4e 73 67  |UUUUUUUU.....Nsg|
00000160  e8 0c 14 0c 06 31 92 21  3d d3 17 eb 78 d4 c7 9c  |.....1.!=...x...|
00000170  ec 22 1b eb 18 48 cc a8  0f d1 e8 4c 21 6a aa 26  |."...H.....L!j.&|
00000180  d9 90 c5 09 90 7e 8a 43  c7 84 ae 0b d3 71 3a 8b  |.....~.C.....q:.|
00000190  1b c3 2b 48 c7 c8 28 f3  b1 33 48 6e 1b f0 d5 25  |..+H..(..3Hn...%|
000001a0  d4 e6 5c 2b 4d b5 00 ae  96 15 6b 5a 5d 3a f5 7c  |..\+M.....kZ]:.||
000001b0  fe 38 f4 2d a9 56 23 91  89 04 d6 d1 11 b9 00 fe  |.8.-.V#.........|
000001c0  ff ff 07 fe ff ff 02 d8  4e 20 00 00 c0 03 00 fe  |........N ......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 e0 d0 1f 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by YesWeCan on 2011-09-01
Here are my calcs for oldfred's suggestion. This will fix the partition table and the Ubuntu installer should work. But there is some risk of damaging the file system inside the sda4 as srs5694 points out.

When you run sudo sfdisk -d /dev/sda > PT.txt, the PT.txt should look like this:
```
/dev/sda1 : start=     2048, size=  3072000, Id=27, bootable
/dev/sda2 : start=  3074048, size=866873493, Id= 7
/dev/sda3 : start=869949440, size= 62916608, Id= f
/dev/sda5 : start=869951488, size= 62914560, Id= 7
/dev/sda4 : start=932866048, size= [COLOR="Red"]43918082[/COLOR], Id=17
```
The number in red is too big.
The total sectors on the disk are 976773168.
The start sector of sda4 is 932866048 so the maximum size of sda4 is
976773168 - 932866048 = 43907120

So the number in red has to be changed. You can use gedit to edit PT.txt so it looks like this:
```
/dev/sda1 : start=     2048, size=  3072000, Id=27, bootable
/dev/sda2 : start=  3074048, size=866873493, Id= 7
/dev/sda3 : start=869949440, size= 62916608, Id= f
/dev/sda5 : start=869951488, size= 62914560, Id= 7
/dev/sda4 : start=932866048, size= [COLOR="green"]43907120[/COLOR], Id=17
```
And then write the new PT back to the MBR
sudo sh -c "cat PT.txt | sfdisk /dev/sda"

The sda4 partition is too big by 10962 sectors = 5.6MB. This is a very small % of the total size so the odds are fair that cutting this off won't damage the file system. But there is no guarantee unless you find a way to see what % of the file system has been used.

---

### Post by oldfred on 2011-09-02
Partition sda2 was your windows install, but now it says it is ext2 format. Did you change that? ext2 is not used much now for anything. Either ext3 or ext4 is more common. You might use ext2 on a flash drive so you do not have the journal and reduce writes.

Ubuntu installed in sda6 and sda7 for swap. If you used one of the automatic installs it tries to shrink something and create new partitions. Did you use auto install or the Something else or manual install where you choose which partition to use for / and which to use for swap?

If all you did was change the partition table entry for sda2, you may be able to change it back to NTFS, but if you overwrote it with any data you most likely will not be able to recover a working windows as any system file overwritten will prevent it from working.

---

### Post by srs5694 on 2011-09-02
Daniel090,

It's very unclear to me precisely what each of the partitions on your disk actually is or how you got to the current state. The only thing that's clear is that Linux is installed in /dev/sda6 (with its swap space in /dev/sda7). /dev/sda6 is a 255 GiB (273 GB) partition. You say that Linux is installed in a 166 GB space, but the only such space that I see is /dev/sda2, which is 155 GiB (166 GB) in size. It holds a Linux ext2 filesystem, but it doesn't seem to hold any boot files or be referenced in the GRUB configuration files, so I don't think Linux is installed there.

You've got three NTFS (Windows) partitions:


[list]
[*]/dev/sda1, which is tiny (1.5 GiB). It's got its boot flag set, as it did in the output you posted in post #6, which makes me think it holds critical Windows boot files, with Windows itself stored elsewhere.
[*]/dev/sda5, which is 30 GiB in size, but that doesn't seem to hold any Windows boot files. My suspicion is that you intended to install Linux here but accidentally installed it in /dev/sda6 instead.
[*]/dev/sda4, which is 21 GiB in size. This is big enough to hold a Windows installation, and GRUB includes an entry to boot it, but GRUB seems to think it's a Windows Recovery Environment partition. If this is the same as the /dev/sda4 from your post #6 (and it does begin on the same sector), then I'm a bit doubtful that this is your Windows boot partition.
[/list]


Notably absent from this list is anything akin to post #6's /dev/sda2, which at that time held a number of critical Windows boot files. Therefore, I suspect that you've accidentally deleted your Windows partition in your attempt to install Linux. If so, I hope you've got good backups, because you're likely to have a hard time recovering otherwise. If you're very lucky, you might be able to get the partition back with the help of a low-level tool like TestDisk, but it's likely to have suffered enough damage that Windows won't boot.

It's hard to offer advice about what to do next because there are many possibilities in the abstract, but what will be possible, much less practical, for you now depends on factors such as whether you've got good backups, whether you're willing to start with a "blank slate" for both Windows and Linux, whether there are critical personal files on the disk that are in danger, and precisely what your goals are. I therefore recommend that you post back with this information.

---

### Post by srs5694 on 2011-09-02
> **oldfred said:**
> If all you did was change the partition table entry for sda2, you may be able to change it back to NTFS, but if you overwrote it with any data you most likely will not be able to recover a working windows as any system file overwritten will prevent it from working.

The Boot Info Script outputs in posts #6 and #13 indicate that /dev/sda2 changed in size (866,873,493 sectors to 324,837,600 sectors), and #13 indicates that it holds an ext2 filesystem. The latter determination is made by probing the data inside the partition, so it's not just the partition table's type code that's changed. In other words, the data has been altered. That said, some NTFS data structures almost certainly remain -- but I don't know if enough NTFS data remains to enable reconstructing the original filesystem. Even if that can be done, writing the ext2fs data in the new /dev/sda2 (and the data in /dev/sda6 and /dev/sda7, which overlap the old /dev/sda2) will almost certainly have trashed some files. Therefore, I'm not optimistic about recovering the old /dev/sda2 data except by restoring it from a backup or using a low-level tool like PhotoRec.

---

### Post by Daniel090 on 2011-09-02
Well It doesn't really matter if i lose the data on my Windows partition, i have all the important personal files backed up on a external HDD/CDs and what i dont have backed up can be found on the internet even if it would take quite a wile to re download.
My priority right now is getting rid of the Ubuntu partition and recovering/reinstalling windows to a partition of its original size [idk what it was right now but it can be figured out][ id say my priority is actually to get things like they where before this whole mess ].

---

### Post by srs5694 on 2011-09-02
The easiest way to recover everything is probably to wipe the partition table clean and then restore from backups (or re-install Windows). There are several ways to wipe the partition table clean. One is this, typed in a Terminal from the Ubuntu disc in "live CD" mode:

```

sudo parted /dev/sda mklabel msdos

```

The disk will then have *not partitions* defined, and you'll be able to re-install Windows from scratch and/or restore everything from backups, as if you'd replaced the disk with a new one.

A less drastic option would be to use fdisk, parted, GParted, or whatever to delete everything except /dev/sda6 and /dev/sda7. This will leave Linux installed, and you'll be able to re-install or restore Windows in the resulting blank space. After installing Windows, you'll probably have to re-install GRUB to get Linux booting again. Also, there are issues with where blank space exists on your disk right now and the size of the extended partition; you might need to move and/or resize partitions to get a clean Windows installation.

---

