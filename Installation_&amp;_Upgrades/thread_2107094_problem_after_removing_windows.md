---
title: "problem after removing windows"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by nosmokenofire on 2013-01-21
Hi,

I have finally got round to getting rid of windows, after a couple of years on a dual boot without using it, and needing the extra space on my hard drive.

I followed these instructions: [https://help.ubuntu.com/community/HowToRemoveWindows#Deleting_the_Windows_Partition](https://help.ubuntu.com/community/HowToRemoveWindows#Deleting_the_Windows_Partition)

With the space left by windows I created a primary partition ext4 (as instructed), my initial Ubuntu installation is on an extended partition. All went ok until I tried to boot into the new partion where I had copied and pasted. No luck, I only seem to be able to boot into the old installation.

The idea was to transfer my Ubuntu installation to the new primary partition, format the extended partition and use the freed up disk space.

I tried this to sort it out: [https://help.ubuntu.com/community/BootPartition ]("https://help.ubuntu.com/community/Boot-Repair#Using_Boot-Repair")but to no avail... I still only seem to be able to boot into the extended partition.

Any help would be greatly appreciated.
Alistair.

---

### Post by darkod on 2013-01-21
First of all, what is the purpose of this? Ubuntu works just fine from logical partition so you don't need to move it just because of that. If you have enough space on the root partition you can keep it as it is and use the new partition as data storage.

If you still want to move root to the new partition, how did you copy it? You simply opened Nautilus and copied? I am not sure whether that copies all hidden files and whether it keeps permissions. When I copied my root partition I did it from live mode and using terminal.
Then, even if it was copied correctly, did you change the root partition UUID in /etc/fstab and reinstalled grub2 to work with the new partition? You can try that first.

Open the /etc/fstab in the new partition and check if the UUID is correct. You can see all UUIDs in terminal with:
sudo blkid

Then, run update-grub which should detect the new partition and list it as additional OS at the bottom of the list. You don't need to do this but it's a better approach before deleting yuor old root to check if the new one works. It's easy to get rid of the old one later. When you run update-grub does it detect the new root?

Post the output of the new /etc/fstab, the blkid and update-grub outputs so we can see them.

In general it's very easy to move the root partition, you just have to do the couple of things mentioned above.

---

### Post by nosmokenofire on 2013-01-21
Thanks darko, in answer to your question: I copied and pasted in gparted from a live cd, as per the tutorial i followed.

here are the results of  "sudo blkid"
```
/dev/sda1: UUID="173e9a2b-77f5-4b6b-a12d-065fbc84d489" TYPE="ext4" 
/dev/sda2: UUID="0bb3944a-1c51-4079-9f5f-55a94b6d9ec4" TYPE="ext4" 
/dev/sda5: UUID="173e9a2b-77f5-4b6b-a12d-065fbc84d489" TYPE="ext4" 
/dev/sda6: UUID="135ba135-19c6-4bb8-bc5b-bd81ebd7cd49" TYPE="swap" 
```sda1 is the new partition (with copied and pasted files) ans sda5 is the original Ubuntu installation.

here is the contents of /etc/fstab :
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=135ba135-19c6-4bb8-bc5b-bd81ebd7cd49 none            swap    sw              0       0
```when I run "update-grub" i get:
```
grub-mkconfig: You must run this as root
```many thanks for your help.

ps All I wanted to do was to get rid of windows and use the space. Maybe the best is that I just create data storage and leave the root alone...

---

### Post by nosmokenofire on 2013-01-21
If it helps I also ran the bootinfoscript from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and got this:
             ```
   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *      2,050,048    99,090,431    97,040,384  83 Linux
/dev/sda2               2,048     2,050,047     2,048,000  83 Linux
/dev/sda4          99,635,130   156,301,311    56,666,182   5 Extended
/dev/sda5          99,635,193   154,850,534    55,215,342  83 Linux
/dev/sda6         154,861,568   156,301,311     1,439,744  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        173e9a2b-77f5-4b6b-a12d-065fbc84d489   ext4       
/dev/sda2        0bb3944a-1c51-4079-9f5f-55a94b6d9ec4   ext4       
/dev/sda5        173e9a2b-77f5-4b6b-a12d-065fbc84d489   ext4       
/dev/sda6        135ba135-19c6-4bb8-bc5b-bd81ebd7cd49   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
else
  search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Vista (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-64700DE6700DBFB2' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  64700DE6700DBFB2
    else
      search --no-floppy --fs-uuid --set=root 64700DE6700DBFB2
    fi
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=135ba135-19c6-4bb8-bc5b-bd81ebd7cd49 none            swap    sw              0       0
UUID=0bb3944a-1c51-4079-9f5f-55a94b6d9ec4    /boot    ext4    defaults    0    2
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   7.265533447 = 7.801307136    boot/grub/grub.cfg                             1
  20.774414062 = 22.306357248   boot/initrd.img-2.6.32-31-generic              2
  24.021598816 = 25.792995328   boot/initrd.img-2.6.38-11-generic-pae          3
  26.184570312 = 28.115468288   boot/initrd.img-3.0.0-17-generic-pae           5
   1.696289062 = 1.821376512    boot/initrd.img-3.2.0-32-generic-pae           3
  24.329101562 = 26.123173888   boot/initrd.img-3.5.0-17-generic               3
  26.320758820 = 28.261699584   boot/initrd.img-3.5.0-18-generic              10
  18.352539062 = 19.705888768   boot/initrd.img-3.5.0-19-generic              17
  15.035644531 = 16.144400384   boot/initrd.img-3.5.0-21-generic              56
  10.480106354 = 11.252928512   boot/initrd.img-3.5.0-22-generic              22
  18.512557983 = 19.877707776   boot/vmlinuz-2.6.32-31-generic                 1
  23.415470123 = 25.142169600   boot/vmlinuz-2.6.38-11-generic-pae             2
   3.421897888 = 3.674234880    boot/vmlinuz-3.0.0-17-generic-pae             46
  26.224399567 = 28.158234624   boot/vmlinuz-3.2.0-32-generic-pae              2
  16.347621918 = 17.553125376   boot/vmlinuz-3.5.0-17-generic                  3
  19.697204590 = 21.149712384   boot/vmlinuz-3.5.0-18-generic                  2
  16.439392090 = 17.651662848   boot/vmlinuz-3.5.0-19-generic                  2
   6.878906250 = 7.386169344    boot/vmlinuz-3.5.0-21-generic                  3
  24.012073517 = 25.782767616   boot/vmlinuz-3.5.0-22-generic                  3

============================= sda2/grub/grub.cfg: ==============================

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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
else
  search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
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
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    menuentry 'Ubuntu (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
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

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.132575989 = 0.142352384    grub/grub.cfg                                  1

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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
else
  search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    menuentry 'Ubuntu (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.32-31-generic
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=135ba135-19c6-4bb8-bc5b-bd81ebd7cd49 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  53.888111591 = 57.861919232   boot/grub/grub.cfg                             1
  67.306637287 = 72.269951488   boot/initrd.img-2.6.32-31-generic              2
  70.553822041 = 75.756589568   boot/initrd.img-2.6.38-11-generic-pae          3
  72.716793537 = 78.079062528   boot/initrd.img-3.0.0-17-generic-pae           5
  48.228512287 = 51.784970752   boot/initrd.img-3.2.0-32-generic-pae           3
  70.861324787 = 76.086768128   boot/initrd.img-3.5.0-17-generic               3
  72.852982044 = 78.225293824   boot/initrd.img-3.5.0-18-generic              10
  64.884762287 = 69.669483008   boot/initrd.img-3.5.0-19-generic              17
  61.567867756 = 66.107994624   boot/initrd.img-3.5.0-21-generic              56
  57.012329578 = 61.216522752   boot/initrd.img-3.5.0-22-generic              22
  65.044781208 = 69.841302016   boot/vmlinuz-2.6.32-31-generic                 1
  69.947693348 = 75.105763840   boot/vmlinuz-2.6.38-11-generic-pae             2
  49.954121113 = 53.637829120   boot/vmlinuz-3.0.0-17-generic-pae             46
  72.756622791 = 78.121828864   boot/vmlinuz-3.2.0-32-generic-pae              2
  62.879845142 = 67.516719616   boot/vmlinuz-3.5.0-17-generic                  3
  66.229427814 = 71.113306624   boot/vmlinuz-3.5.0-18-generic                  2
  62.971615314 = 67.615257088   boot/vmlinuz-3.5.0-19-generic                  2
  53.411129475 = 57.349763584   boot/vmlinuz-3.5.0-21-generic                  3
  70.544296741 = 75.746361856   boot/vmlinuz-3.5.0-22-generic                  3
  57.012329578 = 61.216522752   initrd.img                                    22
  57.012329578 = 61.216522752   initrd.img.old                                22
  70.544296741 = 75.746361856   vmlinuz                                        3
  70.544296741 = 75.746361856   vmlinuz.old                                    3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ba 18 16 f8 42 e6 ef 5d  11 f9 70 ed b4 9a 9b de  |....B..]..p.....|
00000010  3b 2d ed cd 3c 79 32 53  98 75 79 af 94 76 ec f0  |;-..<y2S.uy..v..|
00000020  9d 8f 56 79 d2 b8 55 20  c5 c2 d7 8b 8a 3e 9f 64  |..Vy..U .....>.d|
00000030  7a d3 e4 96 a1 5a 41 59  d3 67 86 2e 52 62 6b f7  |z....ZAY.g..Rbk.|
00000040  06 a6 8f 0b 19 9c 12 34  78 ef 9e d6 4f 74 9f 8c  |.......4x...Ot..|
00000050  78 dc 3e 8b 36 9b ba a1  17 c0 48 44 73 0b aa e1  |x.>.6.....HDs...|
00000060  2b af e6 31 31 ea ec 84  90 5d c8 bc 1c f4 90 ab  |+..11....]......|
00000070  35 94 3d 3f e3 20 ad b0  13 29 f9 34 f0 f4 38 2d  |5.=?. ...).4..8-|
00000080  c4 8b 63 c2 43 8b 34 46  7d 80 42 33 e3 37 c5 e3  |..c.C.4F}.B3.7..|
00000090  5f 8b 33 9b cc 04 56 81  15 9b c1 21 c2 79 b3 84  |_.3...V....!.y..|
000000a0  17 4c 78 de 54 78 9f 5c  c4 1e a6 58 34 3d ad df  |.Lx.Tx.\...X4=..|
000000b0  35 6f ba 30 7e 29 f7 44  4b e0 25 91 da 5b 0d cb  |5o.0~).DK.%..[..|
000000c0  97 0f 35 8b b9 4a 06 2d  23 24 f6 5e c4 12 cb e4  |..5..J.-#$.^....|
000000d0  38 30 79 be ee a3 67 bb  6f f7 27 4d 2f ca 8e c8  |80y...g.o.'M/...|
000000e0  52 6c 82 b7 92 50 db fb  91 f5 e5 ea d5 12 f8 16  |Rl...P..........|
000000f0  1d 54 9b c7 4e 29 c0 fd  9f 71 45 2b d9 a4 59 c6  |.T..N)...qE+..Y.|
00000100  ba be d8 89 13 0e fe 4a  03 1b a1 6f 7c 83 3c ed  |.......J...o|.<.|
00000110  37 78 b6 d1 f4 49 5b b6  03 56 96 14 2f 22 70 5f  |7x...I[..V../"p_|
00000120  b2 95 25 e7 df e0 3d b3  8a 6b 96 63 f5 07 00 7e  |..%...=..k.c...~|
00000130  d3 26 8c dd 9d 5a 0b 67  9e 84 e9 13 db 47 06 d4  |.&...Z.g.....G..|
00000140  35 35 42 49 27 df df 95  46 cc 35 35 35 c2 99 74  |55BI'...F.555..t|
00000150  6a e7 bc 6d 9d da 9d b6  4f b1 77 59 1e a7 a3 d9  |j..m....O.wY....|
00000160  43 a3 af bf 0e ed 5e 1e  9e ec 0b 23 46 41 fb 39  |C.....^....#FA.9|
00000170  97 1d d9 fb 12 fb bb 6b  d1 c0 8b 0a 8b 70 2d 36  |.......k.....p-6|
00000180  3c 0a f3 5f 6a e5 d1 74  cb 27 b0 d8 10 4f 9d 72  |<.._j..t.'...O.r|
00000190  ef 5b b5 92 7a 91 c3 b3  f6 5e d3 a0 3d b5 c7 f0  |.[..z....^..=...|
000001a0  2e ad 62 bf 13 58 f5 65  12 cd 98 82 4e 0d 1a 14  |..b..X.e....N...|
000001b0  f8 53 cb 9f e8 d5 70 1d  18 26 69 52 7e 91 00 fe  |.S....p..&iR~...|
000001c0  ff ff 83 fe ff ff 3f 00  00 00 ee 84 4a 03 00 fe  |......?.....J...|
000001d0  ff ff 05 fe ff ff 2d 85  4a 03 19 23 16 00 00 00  |......-.J..#....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by darkod on 2013-01-21
I don't know what they wanted to do with the tutorial you followed, but I wouldn't copy the partition with Gparted like they told you to do. if you notice the blkid results, the UUID of sda1 and sda5 is the same now because you copied the whole partition. The UUID should be unique.

Another thing that's confusing me, is that you seem to be using a separate /boot partition (sda2), but there is no /boot/grub/core.img file in either sda5 or sda2. There should be one otherwise grub2 can't work. I'm confused how is it working for you at all.

Actually I noticed now that you have /boot in fstab of sda1, but not in the current fstab of sda5. If you want to copy your system you should copy it as it is. You shouldn't try to change it to using separate /boot if you are not using it now. I suggest to comment out (put the # symbol at the front of the line) the line about the /boot in fstab of sda1.

After that you can try making grub2 boot from sda1 with:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If that doesn't work, have your ubuntu cd at hand so you can boot in live mode and fix things back.

---

### Post by nosmokenofire on 2013-01-21
Darko,

I'm far from an expert and I think that I may be out of my depth here. The fact is that I'm an amateur ubuntu fiddler and having succesfully followed instructions from this forum and other sources on the web in order to play about with things, I thought that by following the instructions I found, all would go to plan...
> Another thing that's confusing me, is that you seem to be using a  separate /boot partition (sda2), but there is no /boot/grub/core.img  file in either sda5 or sda2. There should be one otherwise grub2 can't  work. I'm confused how is it working for you at all.This is a probably a result of  my following these instructions: [https://help.ubuntu.com/community/BootPartition]("https://help.ubuntu.com/community/Boot-Repair") in trying to fix my problem.
 > I suggest to comment out (put the # symbol at the front of the line) the line about the /boot in fstab of sda1.I don't actually know what you mean by this...

thanks.

---

### Post by darkod on 2013-01-21
From your bootinfo results you posted:
> =============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=135ba135-19c6-4bb8-bc5b-bd81ebd7cd49 none            swap    sw              0       0
UUID=0bb3944a-1c51-4079-9f5f-55a94b6d9ec4    /boot    ext4    defaults    0    2
--------------------------------------------------------------------------------


The last line is an entry for /boot which you can see from the mount point used. If you open the file and put # at the front of the line, the rest of the line is ignored. That way you can do temporary tests and later remove the # if you need to. This will make the line active again without needing to remember or retype the whole line.

If you compare this /etc/fstab on sda1 with the one on sda5 (down in the bootinfo results) you will see that the /boot entry does not exist in your original installation on sda5. Like you said, you probably selected a wrong option in boot-repair which added that entry in fstab. I think it should be safe to disable it by putting # at front and saving the changed file, because it doesn't exist on sda5.

Are you interested to do it again and make it right this time? :)

---

### Post by nosmokenofire on 2013-01-21
Some more information that may (or may not help).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230429&d=1358784366[/IMG]
Attached is a snapshot from GParted. You will see that the *unused* disk space is identical for sda1 and sda5 even though I simply copied from sda5 to sda1. If I open GParted in a live cd boot this is not the case, it displays the disk space *used* as identical...



[IMG]http://ubuntuforums.org/home/alistair/Desktop/Screenshot from 2013-01-21 17:00:19.png[/IMG][IMG]http://ubuntuforums.org/home/alistair/Desktop/Screenshot from 2013-01-21 17:00:19.png[/IMG]

---

### Post by nosmokenofire on 2013-01-21
> Are you interested to do it again and make it right this time?

Yes I am! I'll do what you say and let you know.

Thanks

---

### Post by darkod on 2013-01-21
The same UUID on sda1 and sda5 is definitely confusing things, you can see they both have / mount point which should be impossible.

Here is what I would do, under the assumption you still haven't deleted anything on sda5 and it still has your full installation. So, continue only if you haven't started deleting things from sda5.

1. Boot the cd in live mode and open Gparted. In live mode sda1 shouldn't be mounted (there will be no keys symbol next to it).
2. Delete both sda1 and sda2. Create one single big ext4 partition from that space. Don't forget to click the green button in Gparted to execute your changes. The new partition should be called sda1 again.
3. Open terminal (this is still in live mode) and copy the files/folders from the root partition (not the whole partition in Gparted like last time). For this purpose we will create few temporary mount points but don't worry. This is live mode and when you reboot the mount points are gone, but the results of your work will still be there. So, don't mind the names I will use for the mount points.
```
sudo mkdir /mnt/oldroot
sudo mkdir /mnt/newroot
sudo mount /dev/sda5 /mnt/oldroot
sudo mount /dev/sda1 /mnt/newroot
cd /mnt/oldroot
sudo cp -ax * /mnt/newroot/
sudo umount /mnt/oldroot
sudo umount /mnt/newroot
```

In the above commands I made the assumption the new partition created will be sda1 again. You can see the command to mount it at /mnt/newroot. If the partition is sda2, etc, use that instead.

When that process finishes you will have everything copied keeping ownership and permissions, but sda1 will have its own UUID that was created when creating the partition and formatting it as ext4.

Now you can reboot without the cd and boot your normal ubuntu which is sda5. Let us know when you reach this far, there will be few more simple things to do to finish everything off. We just want to be sure sda5 still boots fine after all this.

---

### Post by nosmokenofire on 2013-01-21
message removed

---

### Post by nosmokenofire on 2013-01-21
Darko,

I followed all of the instructions as described but when I tried to reboot I got this message instead of GRUB: ```
error: no such partition 
grub rescue> 
```help!!!

---

### Post by darkod on 2013-01-21
Ok, no problem. As I said, the grub files looked weird.

No problem, easily fixable. First the shortest way. At the rescue prompt, execute one by one these commands:
```
insmod part_msdos
insmod ext2
set root=(hd0,msdos5)
linux /vmlinuz root=/dev/sda5
initrd /initrd.img
boot
```

If that boots your ubuntu on sda5, let us know before you reboot. If you reboot you will have to do the same to load it.

If it doesn't work, don't worry, there are other procedures to fix it.

---

### Post by nosmokenofire on 2013-01-21
darko,

All went well until I tried to execute the fourth line: 
```
linux /vmlinuz root=/dev/sda5
```at which point I got an error message: ```
command unknown 'linux'
``` or something like that.

Thanks again for your help.
Alistair

---

### Post by darkod on 2013-01-21
OK, second option. From live mode in terminal:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart without the cd and see if you get a repaired grub.

---

### Post by nosmokenofire on 2013-01-21
That worked well, grub is back and I'm booted into sda5.

what next?

---

### Post by darkod on 2013-01-21
OK. Now boot the working ubuntu from sda5, open terminal and run:
sudo update-grub

That should detect the "new" 12.10 on sda1 and add it at the bottom. The entry in the grub menu will be like "Ubuntu 12.10 on /dev/sda1". After running the above command, restart and if the new entry for sda1 is there try booting it.

Check if it works and boots OK.

---

### Post by nosmokenofire on 2013-01-21
That went fine in the terminal, as you said it detected the new version on sda1, but when it comes to booting I get 2 versions in grub just "Ubuntu" and "Ubuntu 12.10" and two versions of advanced options one of which has a long list of Ubuntu (Ithink with different kernal version) all with "on /dev/sda1" after each one.
No matter what I try to boot into I seem to end up in the sda5 version.

---

### Post by darkod on 2013-01-21
Sorry, my mistake. We didn't change the fstab on sda1 after copying. It still has the same UUID as sda5.

Boot your sda5 (the entry that says only Ubuntu, first on top), then first in terminal run again:
sudo blkid

Note down the UUID string for sda1. Be careful, there are lots of letters and numbers.

After that open the fstab from sda1 for editing:
```
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/fstab
```

When it opens with Gedit, in the line where / is defined replace the UUID= string with the sda1 uuid. Save and close the file. Reboot and try booting the Ubuntu on /dev/sda1 entry.

When it boots, to check which partition is mounted as / you can do in terminal:
df -h

That will tell you which partition is mounted as /. It should be /dev/sda1.

---

### Post by nosmokenofire on 2013-01-22
I have got as far as opening ftab from sda1 in gedit. The entire line reads: ```
/ was on /dev/sda5 during installation
UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 /               ext4
```do I just modify the UUID number or do I also change the first bit so that it reads something about /dev/sda1?

Sorry about the hesitation, I just don't want to mess things up.

Thanks.

---

### Post by darkod on 2013-01-22
Just the UUID string. The line above is only a comment, you can see the # in front. Just so you know that your new root is sda1, you can change the sda5 to sda1, but in reality it doesn't affect anything. It's purely informational.

---

### Post by nosmokenofire on 2013-01-22
done all that and still no luck. I'm still only able to boot into the sda5 installation. I tried a
 sudo update-grub   to see if that sorted it out, but no...

any ideas?

PS I should only need to select one of the two Ubuntu options on the main menu of grub right? no need to go into advanced options? I tried the two and on each it is sda5 that ends up mounted...

---

### Post by darkod on 2013-01-22
Correct, no need to go into advanced options. You either select the main Ubuntu at the top, or the Ubuntu on /dev/sda1 which is towards the bottom.

It should have worked. Can you confirm the UUID you changed is correct in the /etc/fstab which is on /dev/sda1?

Those are the only steps you need to do. Just copy and change the UUID in fstab. Double check the values just in case.

---

### Post by nosmokenofire on 2013-01-22
I double checked the numbers it is all right. would the line ```
errors=remount-ro
``` after the UUID number make any difference? Just wondering...

incidently I only have in grub "Ubuntu" or "Ubuntu 12.10". I do not have "Ubuntu on /dev/sda1" unless I go into advanced options.

---

### Post by darkod on 2013-01-22
Oh, I didn't understand that. Then go into advanced and try to boot the "on /dev/sda1" option with the highest kernel number, if it shows the kernel numers like 3.5.0-XX.

If it boots, in terminal check again with df -h which partition is mounted as root.

---

### Post by nosmokenofire on 2013-01-22
done that: root is still /dev/sda5 ...

If we cannot find a solution would another option be to reformat dev/sda1 unstall Ubuntu onto it from cd and then copy all of the necessary files and folders from within one of the two installations?

or maybe I could just format as data storage and continue with ubuntu on /dev/sda5. With this option: when sda5 is full, will ubuntu automatically start stocking files in the data storage partition, without me needing to do anything? are there any downsides to having data storage on a different partition to the root?

Lots of questions.
Thanks again for your time and help.

---

### Post by darkod on 2013-01-22
OK, at this point it's becoming the twilight zone. :) It doesn't make any sense.

I think the boot process might be totally confused, we only did the quick repair earlier. I was planning to suggest a full grub2 purge and reinstallation once you move to using sda1, but it seems to keep using only sda5 according to what you say. Lets make a last attempt to see some details, and we can reinstall grub2 later.

Boot your normal ubuntu from sda5, open terminal and post the output of:
```
sudo mount /dev/sda1 /mnt
cat /mnt/etc/fstab
sudo blkid
sudo umount /mnt
```

Lets make sure the UUID is fine. The only thing remaining after that will be a full grub2 reinstall. The situation with core.img is still confusing for me.

---

### Post by nosmokenofire on 2013-01-22
Here you go```
alistair@alistair-laptop:~$ cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a787b565-5217-4912-8cdf-64832572624d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=135ba135-19c6-4bb8-bc5b-bd81ebd7cd49 none            swap    sw              0       0
alistair@alistair-laptop:~$ sudo blkid
/dev/sda1: UUID="a787b565-5217-4912-8cdf-64832572624d" TYPE="ext4" 
/dev/sda5: UUID="173e9a2b-77f5-4b6b-a12d-065fbc84d489" TYPE="ext4" 
/dev/sda6: UUID="135ba135-19c6-4bb8-bc5b-bd81ebd7cd49" TYPE="swap"
```

---

### Post by darkod on 2013-01-22
I would reinstall grub2 completely, just to take it out of the way.

From your sda5 ubuntu booted, in terminal:
```
sudo apt-get remove --purge grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda
```

That should completely remove and reinstall grub2, creating new config files. After that is done, reboot and see if the boot menu looks little different. Try booting both the primary ubuntu, and the one on /dev/sda1 which should appear in the main list now, not under the Advanced option.

---

### Post by nosmokenofire on 2013-01-22
help, in the terminal I get a blue screen with a choice of where to install grub. something like this
```
Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;            
           &#9474; GRUB install devices:                                 &#9474;            
           &#9474;                                                       &#9474;            
           &#9474;    [ ] /dev/sda (80026 MB; Hitachi_HTS541680J9SA00)   &#9474;            
           &#9474;    [ ] - /dev/sda5 (28270 MB; /)                      &#9474;            
           &#9474;                                                       &#9474;            
           &#9474;                                                       &#9474;            
           &#9474;                        <Ok>                           &#9474;            
           &#9474;                                                       &#9474;            
           &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
``` the only problem is that I am not able to select anything and when I press enter it tells me that I have selceted to not install grub... what do I do?

---

### Post by nosmokenofire on 2013-01-22
here is the message I get after that:> You chose not to install GRUB to any devices. If you continue, the boot   &#9474;  
 &#9474; loader may not be properly configured, and when this computer next        &#9474;  
 &#9474; starts up it will use whatever was previously in the boot sector. If      &#9474;  
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474;  
 &#9474; unable to load modules or handle the current configuration file.          &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you are already using a different boot loader and want to carry on     &#9474;  
 &#9474; doing so, or if this is a special environment where you do not need a     &#9474;  
 &#9474; boot loader, then you should continue anyway. Otherwise, you should       &#9474;  
 &#9474; install GRUB somewhere.                                                   &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Continue without installing GRUB?       

---

### Post by nosmokenofire on 2013-01-22
it was space bar i needed to hit.

---

### Post by darkod on 2013-01-22
Yeah, in the text menus you use Space bar to mark an item as selected.

How does it work after reinstalling it? You did select /dev/sda in that menu, right? Not the partition sda5.

---

### Post by nosmokenofire on 2013-01-22
still nothing. Grub looks exactly the same as before and both options take me to sda5...

---

### Post by darkod on 2013-01-22
Can you run the bootinfoscript again and post the results like in did in one of your first posts?

Lets see how it looks like now, but I don't like it. :) The version on sda5 seems to be working just fine, but why the hell it doesn't wanna load sda1.

---

### Post by nosmokenofire on 2013-01-22
here you go```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 136230409 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 72 for .
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    99,633,151    99,631,104  83 Linux
/dev/sda4          99,635,130   156,301,311    56,666,182   5 Extended
/dev/sda5          99,635,193   154,850,534    55,215,342  83 Linux
/dev/sda6         154,861,568   156,301,311     1,439,744  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a787b565-5217-4912-8cdf-64832572624d   ext4       
/dev/sda5        173e9a2b-77f5-4b6b-a12d-065fbc84d489   ext4       
/dev/sda6        135ba135-19c6-4bb8-bc5b-bd81ebd7cd49   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
else
  search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    menuentry 'Ubuntu (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic--173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.32-31-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a787b565-5217-4912-8cdf-64832572624d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=135ba135-19c6-4bb8-bc5b-bd81ebd7cd49 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.161777496 = 17.353576448   boot/grub/grub.cfg                             1
   5.283409119 = 5.673017344    boot/initrd.img-2.6.32-31-generic              1
   5.408683777 = 5.807529984    boot/initrd.img-2.6.38-11-generic-pae          1
   5.456825256 = 5.859221504    boot/initrd.img-3.0.0-17-generic-pae           2
   5.480857849 = 5.885026304    boot/initrd.img-3.2.0-32-generic-pae           1
   5.200740814 = 5.584252928    boot/initrd.img-3.5.0-17-generic               1
   5.130424500 = 5.508751360    boot/initrd.img-3.5.0-18-generic               1
   5.271053314 = 5.659750400    boot/initrd.img-3.5.0-19-generic               1
   5.345275879 = 5.739446272    boot/initrd.img-3.5.0-21-generic               2
   5.083564758 = 5.458436096    boot/initrd.img-3.5.0-22-generic               1
   5.410995483 = 5.810012160    boot/vmlinuz-2.6.32-31-generic                 2
   5.423282623 = 5.823205376    boot/vmlinuz-2.6.38-11-generic-pae             1
   5.232002258 = 5.617819648    boot/vmlinuz-3.0.0-17-generic-pae              1
   5.138462067 = 5.517381632    boot/vmlinuz-3.2.0-32-generic-pae              1
   5.154232025 = 5.534314496    boot/vmlinuz-3.5.0-17-generic                  1
   5.357360840 = 5.752422400    boot/vmlinuz-3.5.0-18-generic                  1
   5.224548340 = 5.609816064    boot/vmlinuz-3.5.0-19-generic                  1
   5.365173340 = 5.760811008    boot/vmlinuz-3.5.0-21-generic                  1
   5.415954590 = 5.815336960    boot/vmlinuz-3.5.0-22-generic                  1
   5.083564758 = 5.458436096    initrd.img                                     1
   9.503543854 = 10.204352512   initrd.img.old                                22
   5.415954590 = 5.815336960    vmlinuz                                        1
   5.415954590 = 5.815336960    vmlinuz.old                                    1

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
else
  search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-21-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-21-generic ...'
        linux    /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-19-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-19-generic ...'
        linux    /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.2.0-32-generic-pae ...'
        linux    /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.0.0-17-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 3.0.0-17-generic-pae ...'
        linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.38-11-generic-pae-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.38-11-generic-pae ...'
        linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-advanced-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-2.6.32-31-generic-recovery-173e9a2b-77f5-4b6b-a12d-065fbc84d489' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
        else
          search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
        fi
        echo    'Loading Linux 2.6.32-31-generic ...'
        linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-2.6.32-31-generic
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  173e9a2b-77f5-4b6b-a12d-065fbc84d489
    else
      search --no-floppy --fs-uuid --set=root 173e9a2b-77f5-4b6b-a12d-065fbc84d489
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a787b565-5217-4912-8cdf-64832572624d' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
    else
      search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
    fi
    linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-a787b565-5217-4912-8cdf-64832572624d' {
    menuentry 'Ubuntu (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-21-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-21-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-21-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-21-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-19-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-19-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-19-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic-pae (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.2.0-32-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-32-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.0.0-17-generic-pae (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-17-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-3.0.0-17-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-11-generic-pae-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.38-11-generic-pae
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.32-31-generic-root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset-a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-2.6.32-31-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro recovery nomodeset
        initrd /boot/initrd.img-2.6.32-31-generic
    }
    menuentry 'Ubuntu 12.10 (12.10) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-22-generic--a787b565-5217-4912-8cdf-64832572624d' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  a787b565-5217-4912-8cdf-64832572624d
        else
          search --no-floppy --fs-uuid --set=root a787b565-5217-4912-8cdf-64832572624d
        fi
        linux /boot/vmlinuz-3.5.0-22-generic root=UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-22-generic
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=173e9a2b-77f5-4b6b-a12d-065fbc84d489 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=135ba135-19c6-4bb8-bc5b-bd81ebd7cd49 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  66.080944538 = 70.953873920   boot/grub/grub.cfg                             1
  67.306637287 = 72.269951488   boot/initrd.img-2.6.32-31-generic              2
  70.553822041 = 75.756589568   boot/initrd.img-2.6.38-11-generic-pae          3
  72.716793537 = 78.079062528   boot/initrd.img-3.0.0-17-generic-pae           5
  48.228512287 = 51.784970752   boot/initrd.img-3.2.0-32-generic-pae           3
  70.861324787 = 76.086768128   boot/initrd.img-3.5.0-17-generic               3
  72.852982044 = 78.225293824   boot/initrd.img-3.5.0-18-generic              10
  64.884762287 = 69.669483008   boot/initrd.img-3.5.0-19-generic              17
  61.567867756 = 66.107994624   boot/initrd.img-3.5.0-21-generic              56
  57.012329578 = 61.216522752   boot/initrd.img-3.5.0-22-generic              22
  65.044781208 = 69.841302016   boot/vmlinuz-2.6.32-31-generic                 1
  69.947693348 = 75.105763840   boot/vmlinuz-2.6.38-11-generic-pae             2
  49.954121113 = 53.637829120   boot/vmlinuz-3.0.0-17-generic-pae             46
  72.756622791 = 78.121828864   boot/vmlinuz-3.2.0-32-generic-pae              2
  62.879845142 = 67.516719616   boot/vmlinuz-3.5.0-17-generic                  3
  66.229427814 = 71.113306624   boot/vmlinuz-3.5.0-18-generic                  2
  62.971615314 = 67.615257088   boot/vmlinuz-3.5.0-19-generic                  2
  53.411129475 = 57.349763584   boot/vmlinuz-3.5.0-21-generic                  3
  70.544296741 = 75.746361856   boot/vmlinuz-3.5.0-22-generic                  3
  57.012329578 = 61.216522752   initrd.img                                    22
  57.012329578 = 61.216522752   initrd.img.old                                22
  70.544296741 = 75.746361856   vmlinuz                                        3
  70.544296741 = 75.746361856   vmlinuz.old                                    3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ba 18 16 f8 42 e6 ef 5d  11 f9 70 ed b4 9a 9b de  |....B..]..p.....|
00000010  3b 2d ed cd 3c 79 32 53  98 75 79 af 94 76 ec f0  |;-..<y2S.uy..v..|
00000020  9d 8f 56 79 d2 b8 55 20  c5 c2 d7 8b 8a 3e 9f 64  |..Vy..U .....>.d|
00000030  7a d3 e4 96 a1 5a 41 59  d3 67 86 2e 52 62 6b f7  |z....ZAY.g..Rbk.|
00000040  06 a6 8f 0b 19 9c 12 34  78 ef 9e d6 4f 74 9f 8c  |.......4x...Ot..|
00000050  78 dc 3e 8b 36 9b ba a1  17 c0 48 44 73 0b aa e1  |x.>.6.....HDs...|
00000060  2b af e6 31 31 ea ec 84  90 5d c8 bc 1c f4 90 ab  |+..11....]......|
00000070  35 94 3d 3f e3 20 ad b0  13 29 f9 34 f0 f4 38 2d  |5.=?. ...).4..8-|
00000080  c4 8b 63 c2 43 8b 34 46  7d 80 42 33 e3 37 c5 e3  |..c.C.4F}.B3.7..|
00000090  5f 8b 33 9b cc 04 56 81  15 9b c1 21 c2 79 b3 84  |_.3...V....!.y..|
000000a0  17 4c 78 de 54 78 9f 5c  c4 1e a6 58 34 3d ad df  |.Lx.Tx.\...X4=..|
000000b0  35 6f ba 30 7e 29 f7 44  4b e0 25 91 da 5b 0d cb  |5o.0~).DK.%..[..|
000000c0  97 0f 35 8b b9 4a 06 2d  23 24 f6 5e c4 12 cb e4  |..5..J.-#$.^....|
000000d0  38 30 79 be ee a3 67 bb  6f f7 27 4d 2f ca 8e c8  |80y...g.o.'M/...|
000000e0  52 6c 82 b7 92 50 db fb  91 f5 e5 ea d5 12 f8 16  |Rl...P..........|
000000f0  1d 54 9b c7 4e 29 c0 fd  9f 71 45 2b d9 a4 59 c6  |.T..N)...qE+..Y.|
00000100  ba be d8 89 13 0e fe 4a  03 1b a1 6f 7c 83 3c ed  |.......J...o|.<.|
00000110  37 78 b6 d1 f4 49 5b b6  03 56 96 14 2f 22 70 5f  |7x...I[..V../"p_|
00000120  b2 95 25 e7 df e0 3d b3  8a 6b 96 63 f5 07 00 7e  |..%...=..k.c...~|
00000130  d3 26 8c dd 9d 5a 0b 67  9e 84 e9 13 db 47 06 d4  |.&...Z.g.....G..|
00000140  35 35 42 49 27 df df 95  46 cc 35 35 35 c2 99 74  |55BI'...F.555..t|
00000150  6a e7 bc 6d 9d da 9d b6  4f b1 77 59 1e a7 a3 d9  |j..m....O.wY....|
00000160  43 a3 af bf 0e ed 5e 1e  9e ec 0b 23 46 41 fb 39  |C.....^....#FA.9|
00000170  97 1d d9 fb 12 fb bb 6b  d1 c0 8b 0a 8b 70 2d 36  |.......k.....p-6|
00000180  3c 0a f3 5f 6a e5 d1 74  cb 27 b0 d8 10 4f 9d 72  |<.._j..t.'...O.r|
00000190  ef 5b b5 92 7a 91 c3 b3  f6 5e d3 a0 3d b5 c7 f0  |.[..z....^..=...|
000001a0  2e ad 62 bf 13 58 f5 65  12 cd 98 82 4e 0d 1a 14  |..b..X.e....N...|
000001b0  f8 53 cb 9f e8 d5 70 1d  18 26 69 52 7e 91 00 fe  |.S....p..&iR~...|
000001c0  ff ff 83 fe ff ff 3f 00  00 00 ee 84 4a 03 00 fe  |......?.....J...|
000001d0  ff ff 05 fe ff ff 2d 85  4a 03 19 23 16 00 00 00  |......-.J..#....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by darkod on 2013-01-22
It all looks right, but it still doesn't work. I don't know what to say, sorry. It looks like you have some confusion which might be a result of doing upgrades instead of clean installs. According to the kernels you have present, you did a number of upgrades from one version to the next. Some things might not have been upgraded correctly but I don't know enough to find them.

For example, the grub2 version reported is 1.99 while 12.10 comes with 2.00 and since we did a purge/reinstall, it should have been replacd with 2.00 regardless what the previous version was. But that didn't happen.

As a final attempt, you can try doing the recommended repair of boot-repair. Do it from live mode. The instructions are here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Maybe the program can find something I can't and fix it.

---

### Post by nosmokenofire on 2013-01-22
I'll try that.

If that doesn't work would another option be to reformat dev/sda1 install Ubuntu onto it from  cd and then copy all of the necessary files and folders from within one  of the two installations?

or maybe I could just format as data storage and continue with ubuntu on  /dev/sda5. Question: With this option when /dev/sda5 is full, will ubuntu  automatically start stocking files in the data storage partition,  without me needing to do anything? are there any downsides to having  data storage on a different partition to the root? Advantages?

---

### Post by darkod on 2013-01-22
No, it doesn't start to fill it automatically and that can be an issue, you have to watch out for the free space on sda5 (root).

The benefit is that any data on another partition is safe if you want to format sda5 and do a new clean install. I have a separate /home partition where alll Home folders are by default, and i am doing clean installs formatting the root partition. I never do upgrades. All user data is sitting there in the /home partition and you are free to format /. Of course, you lose programs and some settings that are not in /home, but i think that's a small price to pay since clean install is always better than upgrade.
Also, there are ways to export the list of software that you installed with apt-get and run a command in the new installation to install the same software/packages, their updated versions (if they exist).

The bad side is that you will have to copy things there yourself (I mean on /dev/sda1). As mentioned, it's not done automatically. There are many things to help you, like creating symlinks which means something like a folder in realite linked to another folder on another location/partition. So, for example, inside your Home folder you can have the Documents, Music, Pictures, etc folders symlinked to folders on sda1, and the way you are using them is perfectly the same, only the actual files are kept on sda1. In such case, sda1 will be used automatically because of the symlink. I haven't used something similar, but some forum members use it like that, for example oldfred. You should be able to find tutorials on Google about symlinking.

There are few options. You have to decide what you want to do. On another hand, what you tried by copying root should be plain and simple in reality, only it didn't turn out like that for you.

---

### Post by nosmokenofire on 2013-01-22
It worked!

I am currently calling from /dev/sda1 ! Boot repair seems to have sorted it out. Now the first "Ubuntu" option in Grub takes me straight into /dev/sda1 and it looks identical to my original install on /dev/sda5 ;)

Are there any checks that I can run to make sure that everything is alright? Are you willing to help me with the next steps?

I am really grateful for your time, Darko... I'd buy you a box of chocolates if you lived round the corner:p

Alistair

---

### Post by darkod on 2013-01-22
I think where I messed up was trying to save you from typing a full chroot procedure to enter into sda1 and do it from within. That's why it kept a reference to sda5 all the time.

I'm not aware on any special checks you need to make. Gparted and the df -h command can tell you which partition is mounted as root, and if that's sda1, then that's it. They will also tell you the free space on the root partition which should be much bigger compared to when you were using sda5.

Just remember, if you continue working with sda1 now, after making changes those changes will no longer be in sda5, so sda5 will become like your "old" root. You need to continue working only with sda1, and if you are happy after a while, you can think about formatting sda5 and using it as some sort of storage.

---

### Post by nosmokenofire on 2013-01-22
Darko,
All seems to be in order now. Both with df -h and in GParted checks the mount point is sda1. In GParted sda1 is now flagged as boot...

You got me thinking about the "fresh install vs update" question. I may look into it in the future.

When I get round to formating the rest of the drive how do I go about it? Can I format the whole sda4 extended partition (which contains sda5 and sda6 (linux-swap)) in order to extend sda1 into unallocated space, or do I need to keep an extended partition with a linux-swap partition?

Another thing: what started all this mess was this wiki [https://help.ubuntu.com/community/HowToRemoveWindows#Deleting_the_Windows_Partition](https://help.ubuntu.com/community/HowToRemoveWindows#Deleting_the_Windows_Partition) with these instructions 
> 
[LIST]
[*]create a new partition using the space left by the deleted primary partition (see Creating a New Partition below),
[*]if  the new partition is smaller than the main Linux partition, resize the  latter to fit the former (but only if the latter is not so full that  data would be lost),
[*]copy  the data of the old partition to the new one (click on the old  partition; Ctrl-C; click on the new partition; Ctrl-V; click Edit ->  Apply) (had it been possible, resizing the old partition would also have  involved copying and would have taken just as long),
[*]reinstall GRUB2 to the new partition (see [Grub2#Reinstalling GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2")), and
[*]boot into the new partition (see Reboot below) and make sure everything works as normal.
[/LIST]
 somewhat misleading don't you think? Should I try to contact the last contributer to the article, to say it is not that simple?

Anyway I'll flag this thread as solved. You are a genius...
All the best.

---

### Post by darkod on 2013-01-22
You can't format the whole sda4 as it is because the swap (sda6) is inside and mounted while ubuntu is running. Swap gets mounted even in live mode, to speed up working from the cd. And it's better that you keep swap.

You can format sda5 since it does not get mounted by default, even when ubuntu is running from the hdd. After that you can use it as you wish.

If you prefer to join the space, you can do something like this from live mode:
1. Boot live mode and open Gparted. Swap will be mounted and sda6 and sda4 will have the key symbol (can't operate on them).
2. Right-click sda6 and select Swapoff. The key symbols are gone from both.
3. Delete sda6, sda5, then sda4.
4. Create one new primary swap partition at the End of the unallocated space, with the same size as the current. It's very important to create it at the end so that you can expand sda1. Click the green button in Gparted to do the changes.
5. The new swap partition will have new UUID. Check it in terminal with sudo blkid and open sda1/etc/fstab and replace the UUID of swap with the new one. Save and close.

After that the computer should boot OK. You will have to use Gparted again from live mode to expand sda1 into the rest of the unallocated space. You can do it another time, or after you create the new swap in the above procedure.

But before resizing root you should make a full backup. These operations can sometimes go wrong, as simple as they may look.

---

