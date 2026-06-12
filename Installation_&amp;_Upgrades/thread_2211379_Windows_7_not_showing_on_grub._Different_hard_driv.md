---
title: "Windows 7 not showing on grub. Different hard drive."
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by RobotSpaceTime on 2014-03-15
I'm running Ubuntu 13.10 on a different hard drive than my Windows 7. I can get both to load if I go to BIOS and tell it to boot from one or the other. I feel like I am SO close to getting this to work. I want the GRUB menu to show me Ubuntu and Windows 7 on the same screen. Here is Boot Info Script's summary:  ```
 Boot Info Script 0.61      [1 April 2012]



============================= Boot Info Summary: ===============================


 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 2048.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg


sdb3: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10
    Boot files:        /etc/fstab


sdb4: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb5: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       976,895       974,848 EFI System partition
/dev/sdb2         976,896     2,930,687     1,953,792 Data partition (Linux)
/dev/sdb3       2,930,688    18,554,879    15,624,192 Data partition (Linux)
/dev/sdb4      18,554,880 2,623,680,511 2,605,125,632 Data partition (Linux)
/dev/sdb5   2,623,680,512 2,639,306,751    15,626,240 Swap partition (Linux)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        EEFACD30FACCF63D                       ntfs       
/dev/sdb1        4CA8-0F5B                              vfat       
/dev/sdb2        af3f3151-9cbc-4e8a-ad67-59b9fbb513ba   ext4       
/dev/sdb3        7185e576-49d5-4866-9644-cc8972273b14   ext4       
/dev/sdb4        22a11510-102b-40c1-b172-31d92ab3a97c   ext4       
/dev/sdb5        a2ce4746-fb88-4659-9d07-f2236dd600ec   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sdb1        /boot/efi                vfat       (rw)
/dev/sdb2        /boot                    ext4       (rw)
/dev/sdb3        /                        ext4       (rw,errors=remount-ro)
/dev/sdb4        /home                    ext4       (rw)
/dev/sr0         /media/schrader/UDF Volume udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,uhelper=udisks2)




============================= sdb2/grub/grub.cfg: ==============================


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
set default="1"


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
insmod part_gpt
insmod ext2
set root='hd1,gpt3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt3 --hint-efi=hd1,gpt3 --hint-baremetal=ahci1,gpt3  7185e576-49d5-4866-9644-cc8972273b14
else
  search --no-floppy --fs-uuid --set=root 7185e576-49d5-4866-9644-cc8972273b14
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-7185e576-49d5-4866-9644-cc8972273b14' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd1,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
    else
      search --no-floppy --fs-uuid --set=root af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
    fi
    linux    /vmlinuz-3.11.0-18-generic.efi.signed root=UUID=7185e576-49d5-4866-9644-cc8972273b14 ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.11.0-18-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-7185e576-49d5-4866-9644-cc8972273b14' {
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-advanced-7185e576-49d5-4866-9644-cc8972273b14' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
        else
          search --no-floppy --fs-uuid --set=root af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /vmlinuz-3.11.0-18-generic.efi.signed root=UUID=7185e576-49d5-4866-9644-cc8972273b14 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-recovery-7185e576-49d5-4866-9644-cc8972273b14' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
        else
          search --no-floppy --fs-uuid --set=root af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /vmlinuz-3.11.0-18-generic.efi.signed root=UUID=7185e576-49d5-4866-9644-cc8972273b14 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-7185e576-49d5-4866-9644-cc8972273b14' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
        else
          search --no-floppy --fs-uuid --set=root af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /vmlinuz-3.11.0-12-generic root=UUID=7185e576-49d5-4866-9644-cc8972273b14 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-7185e576-49d5-4866-9644-cc8972273b14' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd1,gpt2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
        else
          search --no-floppy --fs-uuid --set=root af3f3151-9cbc-4e8a-ad67-59b9fbb513ba
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /vmlinuz-3.11.0-12-generic root=UUID=7185e576-49d5-4866-9644-cc8972273b14 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-12-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if sleep --verbose --interruptible 10 ; then
    set timeout=0
  fi
fi
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


=================== sdb2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




=============================== sdb3/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=7185e576-49d5-4866-9644-cc8972273b14 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=af3f3151-9cbc-4e8a-ad67-59b9fbb513ba /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=4CA8-0F5B  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda4 during installation
UUID=22a11510-102b-40c1-b172-31d92ab3a97c /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a2ce4746-fb88-4659-9d07-f2236dd600ec none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sdb3: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-ba06jqgA/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-ba06jqgA/Tmp_Log: No such file or directory



```

Let me know if you need any other information, and I thank you in advance for your assistance.

---

### Post by QIII on 2014-03-15
If you installed each with the other drive unplugged (which I recommend), GRUB will not contain a selection for Win 7 until it is updated.

Set your BIOS/EFI to boot first from your Ubuntu drive and restart.

When you get to Ubuntu, issue the following command in the terminal:

```
sudo update-grub
```

and see if that doesn't fix it for you.

---

### Post by RobotSpaceTime on 2014-03-15
Still having the issue.
I did install each OS with the other drive unplugged. I just noticed in the file I posted at the top it says > [COLOR=#000000][FONT=Ubuntu Mono] => Windows is installed in the MBR of /dev/sda.
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] => No boot loader is installed in the MBR of /dev/sdb.[/FONT][/COLOR]. After some Googling and re-installing Grub2 I am still getting the "No boot loader installed" when I run that Boot Info Summary program. And I did remember to ```
sudo update-grub
```. Any other ideas?

---

