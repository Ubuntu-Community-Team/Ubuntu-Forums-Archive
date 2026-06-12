---
title: "Grub not running after installing fro dual boot"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by crosland on 2011-06-16
Hi, I have a desktop Windows PC with three hard drives. Having successfully installed Ubuntu on a laptop I used the same CD image to boot Ubuntu on my desktop machine. All seemed well so I selected the option to install alongside the existing OS. I left the choice of drive as presented by the installer (it was the largest one) and asked for an 80G partition for Ubuntu. The installation went well but when the machine was restarted it just booted straight into Windows. No sign of the bootloader menu. I'm guessing the BIOS doesn't look at the drive where Ubuntu is installed, and the installer did not put the bootloader on the Windows boot drive. The Windows drive is too small to install Ubuntu there.

How do I fix this so that I can dual boot, or alternatively how do I get rid of Ubuntu and reclaim the 80G for Windows?

Thanks,

Andrew

---

### Post by oldfred on 2011-06-16
Welcome to the forums.

Have you tried booting from the other drives?

This will show us what is installed where, you can run from LiveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by crosland on 2011-06-16
Thanks for your help. I was able to boot Ubuntu by changing the HDD boot order in the BIOS, but still no grub.

Output from the shell script below.

Andrew

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid c155d8a8-f080-46a9-af05-78803ca30ee1 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /BOOT.INI /NTLDR /NTDETECT.COM

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   312,560,639   312,560,577   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    16,370,234    16,370,172  1b Hidden W95 FAT32
/dev/sdb2    *     16,370,235    62,990,864    46,620,630   7 NTFS / exFAT / HPFS
/dev/sdb3          63,006,930   156,280,319    93,273,390   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   315,448,721   315,448,659   7 NTFS / exFAT / HPFS
/dev/sdc2         315,449,342   488,396,799   172,947,458   5 Extended
/dev/sdc5         315,449,344   485,779,455   170,330,112  83 Linux
/dev/sdc6         485,781,504   488,396,799     2,615,296  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        867C284E7C283B77                       ntfs       BACKUP
/dev/sdb1        E8D2-E752                              vfat       BACKUP
/dev/sdb2        EEF89047F8901047                       ntfs       OS
/dev/sdb3        4AD01179D0116C87                       ntfs       APPS
/dev/sdc1        629C5CDE9C5CADF3                       ntfs       DATA
/dev/sdc5        c155d8a8-f080-46a9-af05-78803ca30ee1   ext4       
/dev/sdc6        40d87c7a-4399-40d8-9db8-e9b5748d2e2a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb3        /media/APPS              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons 
C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..." 
--------------------------------------------------------------------------------

================================ sdb2/BOOT.INI: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
--------------------------------------------------------------------------------

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root c155d8a8-f080-46a9-af05-78803ca30ee1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root c155d8a8-f080-46a9-af05-78803ca30ee1
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root c155d8a8-f080-46a9-af05-78803ca30ee1
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c155d8a8-f080-46a9-af05-78803ca30ee1 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root c155d8a8-f080-46a9-af05-78803ca30ee1
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=c155d8a8-f080-46a9-af05-78803ca30ee1 ro single 
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
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root c155d8a8-f080-46a9-af05-78803ca30ee1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root c155d8a8-f080-46a9-af05-78803ca30ee1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root e8d2-e752
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos2)'
    search --no-floppy --fs-uuid --set=root EEF89047F8901047
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

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=c155d8a8-f080-46a9-af05-78803ca30ee1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=40d87c7a-4399-40d8-9db8-e9b5748d2e2a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 174.552005768 = 187.423789056  boot/grub/core.img                             1
 180.614028931 = 193.932836864  boot/grub/grub.cfg                             1
 151.078342438 = 162.219134976  boot/initrd.img-2.6.38-8-generic               1
 174.550273895 = 187.421929472  boot/vmlinuz-2.6.38-8-generic                  1
 151.078342438 = 162.219134976  initrd.img                                     1
 174.550273895 = 187.421929472  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by oldfred on 2011-06-16
What do you mean by no grub. If you can boot then grub2's boot loader is working.

If do prefer to have the boot loader for a system on the same drive as the system when you have more than one drive. So I would install grub2's boot loader to sdc.

If you can boot you can do this, then change BIOS to boot sdc.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck /dev/sdc
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

