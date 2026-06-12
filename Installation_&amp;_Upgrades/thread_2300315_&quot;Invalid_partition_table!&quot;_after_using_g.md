---
title: "&quot;Invalid partition table!&quot; after using gparted"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by hansmc2 on 2015-10-25
I just used gparted to change and resize partitions on my disk. It finished successfully and it does not give any errors, but when I reboot I just get "Invalid partition table!". 

I have kubuntu 14.04 installed on the hard disk along with windows 7. I also have kubuntu 14.04 on a sub drive. That was how I was running gparted.

I rebooted to the live kubuntu and opened gparted again and removed a basic partition from after a extended partition. After that I rebooted again still get the error but gparted still seems to read the partitions on the disk fine. 

I copied off the following information encase it might be helpful. I do not know what kind of tools can fix the partition table, or why gparted seems to have no trouble with it. I have a Dell Latitude E6430 laptop. Thanks

kubuntu@kubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA ST320LT007-9ZV14 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      2048s       121964543s  121962496s  primary   ntfs
 3      121966592s  618995711s  497029120s  extended
 5      121972736s  193818623s  71845888s   logical   ext4
 7      193820672s  200058879s  6238208s    logical   linux-swap(v1)
 6      200060928s  618993663s  418932736s  logical   ext4

kubuntu@kubuntu:~$ sudo fdisk -l -u /dev/sda

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa43fc883

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   121964543    60981248    7  HPFS/NTFS/exFAT
/dev/sda3       121966592   618995711   248514560    5  Extended
/dev/sda5       121972736   193818623    35922944   83  Linux
/dev/sda6       200060928   618993663   209466368   83  Linux
/dev/sda7       193820672   200058879     3119104   82  Linux swap / Solaris

Partition table entries are not in disk order
kubuntu@kubuntu:~$

---

### Post by oldfred on 2015-10-25
You swap is wrong.
It either is sda7 but then the extended partition must be larger to include it.
Or it is sda2 or sda4 which are remaining primary partitions and is not then inside the extended partition.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt


 
To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by hansmc2 on 2015-10-25
Thanks for the info and links. I am working on it right now. Fixparts keeps saying "Warning: 0xEE partition doesn't start on sector 1. This can cause problems in some OSes", but it does not give me any way to fix it. I think I will change all the partitions to primary and see if that fixes the problem. I wanted to do that any way, but gparted does not allow it as far as I can see. I also notices that none of the partitions are marked as boot partitions so that might be a issue.

Edit One: Changed all partitions to primary and saved and rebooted, but computer still says "Invalid partition table!" on start up.

Edit Two: Here is what the new partitions look like. The warning that bios is giving me may be a little misleading. It seems to me that we would need to set one of these partitions as a boot partition?
 
kubuntu@kubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA ST320LT007-9ZV14 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start       End         Size        Type     File system     Flags
 1      2048s       121964543s  121962496s  primary  ntfs
 2      121972736s  193818623s  71845888s   primary  ext4
 4      193820672s  200058879s  6238208s    primary  linux-swap(v1)
 3      200060928s  618993663s  418932736s  primary  ext4

kubuntu@kubuntu:~$ sudo fdisk -l -u /dev/sda

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa43fc883

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   121964543    60981248    7  HPFS/NTFS/exFAT
/dev/sda2       121972736   193818623    35922944   83  Linux
/dev/sda3       200060928   618993663   209466368   83  Linux
/dev/sda4       193820672   200058879     3119104   82  Linux swap / Solaris

Partition table entries are not in disk order
kubuntu@kubuntu:~$

**Edit Three: **I tried setting both the fist (windows 7) and the second (kubuntu 14.04) partitions as the boot partitions. On reboot they both say:
error: no such partition
Entering rescue mode . . .
grub rescue> _

Does this indicate that the partition table is fine and I just messed up grub?

---

### Post by yancek on 2015-10-25
>  It seems to me that we would need to set one of these partitions as a boot partition?
 
 
Only windows needs that.  It isn't necessary to mark a Linux system as active/bootable but you do need that for windows so mark sda1 as bootable/active.  You changed the partitions which also changed the UUIDs which are used in Grub.  Probably the simplest thing to do at this point is to get the bootinfoscript or bootrepair and run it, with boot repair just select the option to Create BootInfo Summary and post the output or a link to it here.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by LostFarmer on 2015-10-25
> Does this indicate that the partition table is fine and I just messed up grub?                                                                                              
 grub is messed up and maybe more.
> Edit One: Changed all partitions to primary and saved and rebooted, but  computer still says "Invalid partition table!" on start up.
> **Edit Three: **I tried setting both the fist (windows 7) and the  second (kubuntu 14.04) partitions as the boot partitions. On reboot they  both say:
error: no such partition
Entering rescue mode . . .
grub rescue> _It looks like you have a least 2 problems.  ist-- you have MS Windows boot loader or some other (not grub) install in sda so it needs the boot flag.  When you put the boot flag on the linux partition , it tries to boot with grub but when you changed partitions it can not find the next step. (reinstall grub, normally sda but can be done on the linux partition)  
problem #2-- you have grub installed on your win 7 partition , you will have to rewrite win7 boot loader code in its VBR,  when you put the boot flag it also ran grub, it should have booted Win7.

there are several commands that need to be ran to verify the above but I do not have the time at the moment .

---

### Post by oldfred on 2015-10-25
I had to check on what oxEE partition is. Only if also gpt partitioned with the very much not recommended hybrid partitioning. Sometime required with Mac and an older Windows install.

That is only for a protective MBR with gpt partitioning where the MBR has just one partition saying the MBR has a gpt partition. That is to prevent old MBR(msdos) tools from overwriting a gpt partition table. The gpt partition table does normally start at sector 1. With MBR the partition table is inside the MBR.

Best to use 3 primary partitions, and have swap in a logical partition. Then if in future you need another partition, you at least have the extended partition to hold more logical partitions. But unless planning well, you may still have to move partitions around.

---

### Post by hansmc2 on 2015-10-26
I turned boot flag off on all partitions and used the boot-repair tool. After that I had the grub menu with a working link to ubuntu. However, boot-repair did not add a link to Windows 7. So I turned on the boot flag on /dev/sda1 and rerun boot-repair with the same results. So now the only thing left to do is get a line/link on grub for windows. I have tried a few things I found on the forms here, but nothing has worked yet. Bellow is the output from boot info script ([http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)).

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   121,964,543   121,962,496   7 NTFS / exFAT / HPFS
/dev/sda2         121,972,736   200,058,879    78,086,144  83 Linux
/dev/sda3         200,060,928   618,993,663   418,932,736  83 Linux
/dev/sda4         618,993,664   625,141,759     6,148,096  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mmcblk0p1   6352-5317                              vfat       
/dev/sda1        34EE4C35EE4BEE24                       ntfs       OSDisk
/dev/sda2        385b88a0-6eda-49dd-8940-10b58ad31204   ext4       
/dev/sda3        d7bdd967-ba54-4f0f-8a37-399c58b31238   ext4       
/dev/sda4        f5737bb0-e09f-46de-b128-5932fc643c5d   swap       
/dev/sr0                                                iso9660    IPC

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /home                    ext4       (rw)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
else
  search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
#set_background_image "images/tile.png";

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-385b88a0-6eda-49dd-8940-10b58ad31204' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
    else
      search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
    fi
    linux    /boot/vmlinuz-3.13.0-66-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-66-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
    menuentry 'Ubuntu, with Linux 3.13.0-66-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-66-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-66-generic ...'
        linux    /boot/vmlinuz-3.13.0-66-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-66-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-66-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-66-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-66-generic ...'
        linux    /boot/vmlinuz-3.13.0-66-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-66-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-65-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-65-generic ...'
        linux    /boot/vmlinuz-3.13.0-65-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-65-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-65-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-65-generic ...'
        linux    /boot/vmlinuz-3.13.0-65-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-65-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-63-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-63-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-63-generic ...'
        linux    /boot/vmlinuz-3.13.0-63-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-63-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-63-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-63-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-63-generic ...'
        linux    /boot/vmlinuz-3.13.0-63-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-63-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-62-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-62-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-62-generic ...'
        linux    /boot/vmlinuz-3.13.0-62-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-62-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-62-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-62-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-62-generic ...'
        linux    /boot/vmlinuz-3.13.0-62-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-62-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-61-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-61-generic ...'
        linux    /boot/vmlinuz-3.13.0-61-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-61-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-61-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-61-generic ...'
        linux    /boot/vmlinuz-3.13.0-61-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-61-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-59-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-59-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-59-generic ...'
        linux    /boot/vmlinuz-3.13.0-59-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-59-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-59-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-59-generic ...'
        linux    /boot/vmlinuz-3.13.0-59-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-58-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-58-generic ...'
        linux    /boot/vmlinuz-3.13.0-58-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-58-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-58-generic ...'
        linux    /boot/vmlinuz-3.13.0-58-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-57-generic ...'
        linux    /boot/vmlinuz-3.13.0-57-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-57-generic ...'
        linux    /boot/vmlinuz-3.13.0-57-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-55-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-55-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-55-generic ...'
        linux    /boot/vmlinuz-3.13.0-55-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-55-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-55-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-55-generic ...'
        linux    /boot/vmlinuz-3.13.0-55-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-55-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-54-generic ...'
        linux    /boot/vmlinuz-3.13.0-54-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-54-generic ...'
        linux    /boot/vmlinuz-3.13.0-54-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-54-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /boot/vmlinuz-3.13.0-53-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /boot/vmlinuz-3.13.0-53-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-51-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-51-generic ...'
        linux    /boot/vmlinuz-3.13.0-51-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-51-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-51-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-51-generic ...'
        linux    /boot/vmlinuz-3.13.0-51-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-51-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-49-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-49-generic ...'
        linux    /boot/vmlinuz-3.13.0-49-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-49-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-49-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-49-generic ...'
        linux    /boot/vmlinuz-3.13.0-49-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-49-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-46-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-46-generic ...'
        linux    /boot/vmlinuz-3.13.0-46-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-46-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-46-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-46-generic ...'
        linux    /boot/vmlinuz-3.13.0-46-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-46-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /boot/vmlinuz-3.13.0-45-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /boot/vmlinuz-3.13.0-45-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-35-generic ...'
        linux    /boot/vmlinuz-3.13.0-35-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-35-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-35-generic ...'
        linux    /boot/vmlinuz-3.13.0-35-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-34-generic ...'
        linux    /boot/vmlinuz-3.13.0-34-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-34-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-34-generic ...'
        linux    /boot/vmlinuz-3.13.0-34-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-385b88a0-6eda-49dd-8940-10b58ad31204' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
        else
          search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=385b88a0-6eda-49dd-8940-10b58ad31204 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
    else
      search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  385b88a0-6eda-49dd-8940-10b58ad31204
    else
      search --no-floppy --fs-uuid --set=root 385b88a0-6eda-49dd-8940-10b58ad31204
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=385b88a0-6eda-49dd-8940-10b58ad31204 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=d7bdd967-ba54-4f0f-8a37-399c58b31238 /home           ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
#UUID=6a987d9a-2c4a-4398-8c0b-518c62182552 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-AVRyjnkU/Tmp_Log: No such file or directory


```

---

### Post by oldfred on 2015-10-26
You need the boot flag on the NTFS partition to run Windows repairs from your Windows repair CD or flash drive.
Grub only boots working Windows so best or easiest to always have a Windows repair disk as well as the Ubuntu live installer as a repair disk.

Structure looks normal, it sees NTFS partition ok and you show the boot files.
Boot-Repair updates should have found the Windows entry, but try this directly first.
sudo update-grub

If not you may need to use Windows repair disk. Or temporarily install Windows boot loader with Boot-Repair can see if f8 will get you into the internal repair console. Run the Windows repairs 3 times and then see if Windows boots ok on its own. Then restore grub and run the update-grub again to see if added to grub boot menu.

You may want to house clean kernels. I normally keep 2.
              
 Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove

sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
# command line way

 cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.13.0-{XX,XX,XX,XX,XX,XX}-generic
sudo apt-get purge linux-image-3.13.0-{54,55,57}-generic

---

### Post by yancek on 2015-10-26
There is no entry for windows in the grub.cfg file which is the menu you see on boot so you need to boot Ubuntu and run the command:  sudo update-grub
Watch the output to see if there is an entry for windows.  If so, reboot and try it.  If you don't see windows in the output try to run the command:  sudo os-prober
Watch the output, if you see a windows entry, run sudo updaate-grub again.

You have 27 different kernels for Ubuntu, you might want to remove some of them.

---

### Post by hansmc2 on 2015-10-26
Thanks for the instructions on how to clean up old kernels. I removed all but three.
  
Sudo update-grub and sudo os-prober did not find any windows install. Os-prober did not find any thing, so I was not sure it was working. Then I booted up to my windows install disk and after choosing a language choose the little repair link on the second page of the install wizard. The installer/repairer then pooped up a dialog box saying had found some error ask if it should fix and reboot, so I said Yes. After a reboot both update-grub and os-prober found the windows install and it now shows in the grub menu.
 
 Thanks everyone so much for your help.

---

### Post by yancek on 2015-10-27
You didn't give any specifics on which partitions you changed.  If you want to modify windows partitions, best to do it from windows and reboot and run chkdsk.  GParted usually works but still, if it is windows use the windows software.

---

