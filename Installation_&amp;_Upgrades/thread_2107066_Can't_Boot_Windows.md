---
title: "Can't Boot Windows"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by Shoalster on 2013-01-20
Is there a sure-fire way to fix this installation of ubuntu so I can boot windows xp also.    There are items I would like to get from windows before I completely wipe it out.  Since installing ubuntu my pc boots to it only. Here's the info if it means anything to someone but  I have no windows  CD  to run chkdsk.

---

### Post by Shoalster on 2013-01-21
Hmm.   Must be the holiday.

---

### Post by presence1960 on 2013-01-21
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script. Copy the contents of the RESULTS.txt file back here. Click the # sign in the toolbar and paste the contents in between the code tags. This will give whoever helps you a snapshot of what is on your computer at the moment. It will help troubleshoot your problem(s)

---

### Post by Shoalster on 2013-01-21
Every time I put the command line in terminal it says command not found. 
  Here is the command:      sudo ~/home/ubuntu/Desktop/bootinfoscript

---

### Post by presence1960 on 2013-01-22
> **Shoalster said:**
> Every time I put the command line in terminal it says command not found. 
  Here is the command:      sudo ~/home/ubuntu/Desktop/bootinfoscript

put the bootinfoscript file on desktop. Then run this command ```
sudo ~/Desktop/bootinfoscript
```

P.S make sure you extract the contents of the archive and then put the bootinfoscript on desktop.

---

### Post by Shoalster on 2013-01-22
Whew !  I'm stumped.    Nothing works.  Still  "command not found"    And as you can see from   the command line that I tried to enter the bootinfoscript is extracted.  When I right click the bootscript the properties show      /home/shoalster/Desktop.  Thus ,  my command line is:   sudo ~/home/shoalster/Desktop/bootinfoscript


shoalster@shoalster-EG194AA-ABA-A1250N:~$ sudo ~/home/shoalster/Desktop/bootinfoscript
[sudo] password for shoalster: 
sudo: /home/shoalster/home/shoalster/Desktop/bootinfoscript: command not found
shoalster@shoalster-EG194AA-ABA-A1250N:~$ sudo ~/Desktop/bootinfoscript
sudo: /home/shoalster/Desktop/bootinfoscript: command not found
shoalster@shoalster-EG194AA-ABA-A1250N:~$ sudo ~/home/shoalster/Desktop/bootinfoscript
sudo: /home/shoalster/home/shoalster/Desktop/bootinfoscript: command not found
shoalster@shoalster-EG194AA-ABA-A1250N:~$ 


I think it's time to give up on ever getting Windows back and just wipe the partition.

---

### Post by oldfred on 2013-01-23
I think presence1960 left out bash (I either forget sudo or bash myself, but when I get an error I just know it did something wrong and correct it.)

But it also depends on where you saved bootinfoscript. You can to an ls command to make sure you are in the folder with the boot script. You can also use tab after typing a few characters and it will complete line or complete as much as it can when similar names are in folder. So I typed sudo bash boo {tab}.

fred@A105-Precise:~$ ls boo*
bootinfoscript
fred@A105-Precise:~$ sudo bash bootinfoscript 
[sudo] password for fred: 

Boot Info Script 0.61      [1 April 2012]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/fred/".

---

### Post by Shoalster on 2013-01-23
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    16,798,319    16,798,257   c W95 FAT32 (LBA)
/dev/sda2    *     16,798,320   390,186,313   373,387,994   7 NTFS / exFAT / HPFS
/dev/sda3         390,189,054   488,396,799    98,207,746   5 Extended
/dev/sda5    *    392,235,008   462,733,465    70,498,458  83 Linux
/dev/sda6         482,240,512   488,396,799     6,156,288  82 Linux swap / Solaris
/dev/sda7         390,189,056   392,235,007     2,045,952  83 Linux
/dev/sda8         462,735,360   482,238,463    19,503,104  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        434A-83EF                              vfat       HP_RECOVERY
/dev/sda2        736ABB93784F2BEB                       ntfs       HP_PAVILION
/dev/sda5        0e9a55af-fe2b-4044-bf12-0f9522a81b8d   ext4       
/dev/sda6        2bbd2a6c-be3a-4589-8512-bca0ec2addc4   swap       
/dev/sda7        e36b5db6-81b7-452e-a832-392a32448fe8   ext4       
/dev/sda8        ab380a59-5ad4-48ab-bc41-51c773da92e7   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
 
[spybotsd] 
timeout.old=0 
 
--------------------------------------------------------------------------------

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /fastdetect /NoExecute=OptIn 
[spybotsd] 
timeout.old=3 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="4"

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
else
  search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
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
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
    else
      search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
    fi
    linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=0e9a55af-fe2b-4044-bf12-0f9522a81b8d ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-21-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-advanced-0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=0e9a55af-fe2b-4044-bf12-0f9522a81b8d ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-recovery-0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=0e9a55af-fe2b-4044-bf12-0f9522a81b8d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=0e9a55af-fe2b-4044-bf12-0f9522a81b8d ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=0e9a55af-fe2b-4044-bf12-0f9522a81b8d ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
    else
      search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
    else
      search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows NT/2000/XP (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-434A-83EF' {
    insmod part_msdos
    insmod fat
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  434A-83EF
    else
      search --no-floppy --fs-uuid --set=root 434A-83EF
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows XP Media Center Edition (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-736ABB93784F2BEB' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  736ABB93784F2BEB
    else
      search --no-floppy --fs-uuid --set=root 736ABB93784F2BEB
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=0e9a55af-fe2b-4044-bf12-0f9522a81b8d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2bbd2a6c-be3a-4589-8512-bca0ec2addc4 none            swap    sw              0       0
UUID=e36b5db6-81b7-452e-a832-392a32448fe8    /boot    ext4    defaults    0    2
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.5.0-17-generic               1
               =                boot/initrd.img-3.5.0-21-generic               1
               =                boot/vmlinuz-3.5.0-17-generic                  1
               =                boot/vmlinuz-3.5.0-21-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

============================= sda7/grub/grub.cfg: ==============================

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
set default="4"

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
else
  search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows NT/2000/XP (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-434A-83EF' {
    insmod part_msdos
    insmod fat
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  434A-83EF
    else
      search --no-floppy --fs-uuid --set=root 434A-83EF
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows XP Media Center Edition (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-736ABB93784F2BEB' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  736ABB93784F2BEB
    else
      search --no-floppy --fs-uuid --set=root 736ABB93784F2BEB
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
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

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/grub.cfg                                  1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos8'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
else
  search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ab380a59-5ad4-48ab-bc41-51c773da92e7' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
    else
      search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
    fi
    linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=ab380a59-5ad4-48ab-bc41-51c773da92e7 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-ab380a59-5ad4-48ab-bc41-51c773da92e7' {
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-advanced-ab380a59-5ad4-48ab-bc41-51c773da92e7' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
        else
          search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=ab380a59-5ad4-48ab-bc41-51c773da92e7 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-recovery-ab380a59-5ad4-48ab-bc41-51c773da92e7' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
        else
          search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=ab380a59-5ad4-48ab-bc41-51c773da92e7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-advanced-ab380a59-5ad4-48ab-bc41-51c773da92e7' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
        else
          search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=ab380a59-5ad4-48ab-bc41-51c773da92e7 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-recovery-ab380a59-5ad4-48ab-bc41-51c773da92e7' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
        else
          search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=ab380a59-5ad4-48ab-bc41-51c773da92e7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-ab380a59-5ad4-48ab-bc41-51c773da92e7' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
        else
          search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=ab380a59-5ad4-48ab-bc41-51c773da92e7 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-ab380a59-5ad4-48ab-bc41-51c773da92e7' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
        else
          search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=ab380a59-5ad4-48ab-bc41-51c773da92e7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
    else
      search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ab380a59-5ad4-48ab-bc41-51c773da92e7
    else
      search --no-floppy --fs-uuid --set=root ab380a59-5ad4-48ab-bc41-51c773da92e7
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows NT/2000/XP (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-434A-83EF' {
    insmod part_msdos
    insmod fat
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  434A-83EF
    else
      search --no-floppy --fs-uuid --set=root 434A-83EF
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows XP Media Center Edition (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-736ABB93784F2BEB' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  736ABB93784F2BEB
    else
      search --no-floppy --fs-uuid --set=root 736ABB93784F2BEB
    fi
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
    else
      search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
    fi
    linux /vmlinuz root=/dev/sda5
    initrd /initrd.img
}
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        linux /vmlinuz root=/dev/sda5
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        linux /vmlinuz root=/dev/sda5
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        linux /vmlinuz root=/dev/sda5
        initrd /initrd.img.old
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.5.0-17-generic--0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        linux /vmlinuz-3.5.0-17-generic root=/dev/sda5
        initrd /initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz-3.5.0-21-generic--0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        linux /vmlinuz-3.5.0-21-generic root=/dev/sda5
        initrd /initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        linux /vmlinuz root=/dev/sda5
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        linux /vmlinuz root=/dev/sda5
        initrd /initrd.img
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz--0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        linux /vmlinuz root=/dev/sda5
        initrd /initrd.img.old
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/vmlinuz.old--0e9a55af-fe2b-4044-bf12-0f9522a81b8d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        else
          search --no-floppy --fs-uuid --set=root 0e9a55af-fe2b-4044-bf12-0f9522a81b8d
        fi
        linux /vmlinuz.old root=/dev/sda5
        initrd /initrd.img.old
    }
}

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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=ab380a59-5ad4-48ab-bc41-51c773da92e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2bbd2a6c-be3a-4589-8512-bca0ec2addc4 none            swap    sw              0       0
/dev/disk/by-id/ata-HP_DVD_Writer_740r /mnt/ata-HP_DVD_Writer_740r auto nosuid,nodev,nofail,x-gvfs-show 0 0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.5.0-17-generic               2
               =                boot/initrd.img-3.5.0-21-generic               1
               =                boot/initrd.img-3.5.0-22-generic               1
               =                boot/vmlinuz-3.5.0-17-generic                  1
               =                boot/vmlinuz-3.5.0-21-generic                  1
               =                boot/vmlinuz-3.5.0-22-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 10 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 f0 00 3f 00 00 00  |........?...?...|
00000020  31 52 00 01 0c 20 00 00  00 00 00 00 02 00 00 00  |1R... ..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ef 83 4a 43 4e  4f 20 4e 41 4d 45 20 20  |..)..JCNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
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

### Post by oldfred on 2013-01-23
Windows shows in grub. What happens if you boot the install in sda2?

You do have two boot flags. Grub does not use boot flag and you are supposed to only have one boot flag on the primary NTFS partition that you use to boot Windows from. That is required if you reinstall the Windows boot loader.

Grub normally shows which install it is booting from, but yours says partition 72 which I do not think is correct. But you said it works, so I assume that is a bug in bootinfoscript.

Nothing stands out that I can see. It mounted the NTFS partition so it is not corrupt, it shows boot.ini and the normal boot files. Partition boot sector looks normal also.

Then often the issue is that you really need to run chkdsk and you need the XP install CD to do that or any other Windows repairCD as you can run chkdsk from just about any version. 

Sometimes users can get to a repair console by pressing f8 at just about the same time as the grub entry for Windows. Those that did get it to work said they tried several times and it was real quick.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
I have used a Windows 7 repair flash drive to run chkdsk on my XP. I have not tried anything else. Someone posted this:

       May be able to run chkdsk from Hiren's boot CD. (mini xp.)
Hiren's Boot CD, and do a chkdsk on the XP

---

### Post by Shoalster on 2013-01-23
I will work on the chkdsk angle.   I have a laptop with Windows 7 and  could maybe copy the Win 7 recovery disk over to a flash drive as my CD is not working .    When I boot the computer I have the options for Boot Menu ( ESC)  ,    Setup  ( F1 )    and System Recovery  ( F10 ).      The F10 never responds .     I'll play with it and F8 some and see if I get lucky.     Thanks.

---

### Post by oldfred on 2013-01-23
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by presence1960 on 2013-01-23
Thanks oldfred! Usually I copy and paste commands for this very reason. This time I typed it and I guess my mind and fingers did not work together.

---

