---
title: "New install - coming to grub resuce - error no such device"
date: 2014-08-15
forum: Installation &amp; Upgrades
---

### Post by Danial on 2014-08-15
HI,

Thanks to everyone who reads thru these lines and my apology in advance if this has been answered earlier. I have checked about 15 page of post and did search to no avail. So here is my issue:

I have a dual boot (older) machine with Win7 and 12.04. Finally I decide to upgrade (unsuccessfully) to 14.04 LTS from within 12.04. After hours of downloading and going thru its process, I ended up to grub rescue prompt and that was it (I don't remember exact error message). So at that point, I decide to do a clean install from a live cd. I was prompted that 14.04 is installed and do you want to install  over it (or in that meaning). Which I choosed. The whole process went thru it hoops and brought me back to the grub rescue prompt; giving the "error no such device" and then the device id: 658321e8-89c6-xxxx-xxxx-xxxxxxxxxxxx. With my little knowledge, I thought that is is the drive id that grub can not locate. Anyway, back to live cd and I ran sudo blkid. Following is the result.

> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="NT-INT1" UUID="22E2B9C622334662" TYPE="ntfs" 
/dev/sdb1: UUID="d898c458-3a28-4abf-9a28-c34d356c0046" TYPE="swap" 
/dev/sdb2: UUID="66B8B439B8B40A17" TYPE="ntfs" 
/dev/sr0: LABEL="Ubuntu 14.04 LTS amd64" TYPE="iso9660" 
/dev/sdc1: UUID="3a7ce152-9022-42d2-8069-088a8ce8d58d" TYPE="swap" 
/dev/sdc2: UUID="38cf3b09-8e34-410c-ac5e-8c7c2375808e" TYPE="ext4" 
/dev/sdc3: UUID="5f2a8dfb-6c63-49f7-8480-c2204a4f746f" TYPE="ext4" 
/dev/sdc5: UUID="e8703383-5e2d-41fa-8ffc-e393207619ec" TYPE="ext4" 
/dev/sdc6: LABEL="Ganey" UUID="2c97211d-9eb8-4520-9ea7-c091e58b3a3b" TYPE="ext4" 
/dev/sdc7: LABEL="Tasaveer" UUID="846a0dc9-58ba-468d-9e19-1fc5b59715c4" TYPE="ext4" 
/dev/sdc8: LABEL="Kaghzat" UUID="b8aaa3ec-6996-486a-b9bb-aa3a954ff7c3" TYPE="ext4" 
/dev/sdc9: LABEL="Linux-doc" UUID="1d3711f4-d1cf-472d-b09b-f90667a033fa" TYPE="ext4" 
/dev/sdc10: LABEL="Temp" UUID="ce1aca59-ceda-4aef-8230-eb2996535daf" TYPE="ext4" 
/dev/sdc11: LABEL="Kachra" UUID="3f608fc3-eef3-4dfe-a755-5e83486bb0e5" TYPE="ext4" 
/dev/sdc12: LABEL="Win-apps" UUID="73E1719801BBE72A" TYPE="ntfs" 
/dev/sdc13: UUID="3c58de79-519a-4e2e-9244-b153deb7a78a" TYPE="ext4" 
ubuntu@ubuntu:~$ 

Evidently that id does not show up in blkid output nor I can see it in gparted. I do not know more about trouble shooting or what logs are needed to troubleshoot this. So I seek your guidance and steps I need to do to provide more specific information.

I appreciate, if some guru can walk me thru to resolve this issue.

Once again thanks for all your time and help in this regard.

Danial

---

### Post by oldfred on 2014-08-15
You have more than one hard drive, so you have 3 different MBR, each may have different boot loaders or old versions?
Best to have each system installed on a separate drive with its boot loader in the MBR of that drive. And then in BIOS set default to Ubuntu/grub drive.
Did you try booting from another drive?

Default installs, put grub2's boot loader into sda, as that is usually correct as most users only have one drive or BIOS is set to sda. But your BIOS may be booting anther drive by default, or grub may be auto installing to another drive.

Be very careful on any auto reinstall option. It overwrites the entire hard drive. Best to only use Something Else especially with multiple drives as that is the only install option that lets you choose which drive to install grub2's boot loader into.
       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You can run Boot-Repair and post the link for its report. But do not run auto fix as that just installs one grub to every MBR. Advanced options lets you choose install and drive to install boot loader into.
       
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Report will show each MBR and what boot loader is installed in it.

---

### Post by Danial on 2014-08-16
Fred,
Thanks so much for your time. I will run Boot-Repair and post the results here in short time.
Your help is very appreciated.

Danial

---

### Post by Danial on 2014-08-16
Fred,
Thanks so much for your time. I will run Boot-Repair and post the results here in short time.
Your help is very appreciated.

Danial

---

### Post by Danial on 2014-08-16
Fred,
Here is the output from Boot-Repair: (sure it is a long log)

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdc1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdc3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc12: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   398,283,479   398,283,417   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    10,233,404    10,233,342  82 Linux swap / Solaris
/dev/sdb2    *     10,233,405    78,156,224    67,922,820   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63    10,120,949    10,120,887  82 Linux swap / Solaris
/dev/sdc2    *     10,121,216    69,468,159    59,346,944  83 Linux
/dev/sdc3          69,468,160   180,248,575   110,780,416  83 Linux
/dev/sdc4         180,249,361   976,768,064   796,518,704   5 Extended
/dev/sdc5         180,249,363   285,716,024   105,466,662  83 Linux
/dev/sdc6         285,716,088   444,293,639   158,577,552  83 Linux
/dev/sdc7         444,293,703   602,871,254   158,577,552  83 Linux
/dev/sdc8         602,871,318   655,435,934    52,564,617  83 Linux
/dev/sdc9         655,435,998   708,000,614    52,564,617  83 Linux
/dev/sdc10        813,467,403   895,109,669    81,642,267  83 Linux
/dev/sdc11        895,109,733   915,335,504    20,225,772  83 Linux
/dev/sdc12        708,000,678   813,467,339   105,466,662   7 NTFS / exFAT / HPFS
/dev/sdc13        915,335,568   976,768,064    61,432,497  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        22E2B9C622334662                       ntfs       NT-INT1
/dev/sdb1        d898c458-3a28-4abf-9a28-c34d356c0046   swap       
/dev/sdb2        66B8B439B8B40A17                       ntfs       
/dev/sdc1        3a7ce152-9022-42d2-8069-088a8ce8d58d   swap       
/dev/sdc10       ce1aca59-ceda-4aef-8230-eb2996535daf   ext4       Temp
/dev/sdc11       3f608fc3-eef3-4dfe-a755-5e83486bb0e5   ext4       Kachra
/dev/sdc12       73E1719801BBE72A                       ntfs       Win-apps
/dev/sdc13       3c58de79-519a-4e2e-9244-b153deb7a78a   ext4       
/dev/sdc2        38cf3b09-8e34-410c-ac5e-8c7c2375808e   ext4       
/dev/sdc3        5f2a8dfb-6c63-49f7-8480-c2204a4f746f   ext4       
/dev/sdc5        e8703383-5e2d-41fa-8ffc-e393207619ec   ext4       
/dev/sdc6        2c97211d-9eb8-4520-9ea7-c091e58b3a3b   ext4       Ganey
/dev/sdc7        846a0dc9-58ba-468d-9e19-1fc5b59715c4   ext4       Tasaveer
/dev/sdc8        b8aaa3ec-6996-486a-b9bb-aa3a954ff7c3   ext4       Kaghzat
/dev/sdc9        1d3711f4-d1cf-472d-b09b-f90667a033fa   ext4       Linux-doc
/dev/sr0                                                iso9660    Ubuntu 14.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/ubuntu/66B8B439B8B40A17 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc2        /media/ubuntu/38cf3b09-8e34-410c-ac5e-8c7c2375808e ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc3        /media/ubuntu/5f2a8dfb-6c63-49f7-8480-c2204a4f746f ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc5        /media/ubuntu/e8703383-5e2d-41fa-8ffc-e393207619ec ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc2/boot/grub/grub.cfg: ===========================

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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  38cf3b09-8e34-410c-ac5e-8c7c2375808e
else
  search --no-floppy --fs-uuid --set=root 38cf3b09-8e34-410c-ac5e-8c7c2375808e
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
  set timeout=-1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-38cf3b09-8e34-410c-ac5e-8c7c2375808e' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  38cf3b09-8e34-410c-ac5e-8c7c2375808e
    else
      search --no-floppy --fs-uuid --set=root 38cf3b09-8e34-410c-ac5e-8c7c2375808e
    fi
    linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=38cf3b09-8e34-410c-ac5e-8c7c2375808e ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-38cf3b09-8e34-410c-ac5e-8c7c2375808e' {
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-advanced-38cf3b09-8e34-410c-ac5e-8c7c2375808e' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  38cf3b09-8e34-410c-ac5e-8c7c2375808e
        else
          search --no-floppy --fs-uuid --set=root 38cf3b09-8e34-410c-ac5e-8c7c2375808e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=38cf3b09-8e34-410c-ac5e-8c7c2375808e ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-24-generic-recovery-38cf3b09-8e34-410c-ac5e-8c7c2375808e' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  38cf3b09-8e34-410c-ac5e-8c7c2375808e
        else
          search --no-floppy --fs-uuid --set=root 38cf3b09-8e34-410c-ac5e-8c7c2375808e
        fi
        echo    'Loading Linux 3.13.0-24-generic ...'
        linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=38cf3b09-8e34-410c-ac5e-8c7c2375808e ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-24-generic
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
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  38cf3b09-8e34-410c-ac5e-8c7c2375808e
    else
      search --no-floppy --fs-uuid --set=root 38cf3b09-8e34-410c-ac5e-8c7c2375808e
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  38cf3b09-8e34-410c-ac5e-8c7c2375808e
    else
      search --no-floppy --fs-uuid --set=root 38cf3b09-8e34-410c-ac5e-8c7c2375808e
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sdc2)' --class windows --class os $menuentry_id_option 'osprober-chain-66B8B439B8B40A17' {
    insmod part_msdos
    insmod ntfs
    set root='hd2,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos2 --hint-efi=hd2,msdos2 --hint-baremetal=ahci2,msdos2  66B8B439B8B40A17
    else
      search --no-floppy --fs-uuid --set=root 66B8B439B8B40A17
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
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

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=38cf3b09-8e34-410c-ac5e-8c7c2375808e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=3a7ce152-9022-42d2-8069-088a8ce8d58d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc4

00000000  b6 b6 ff 29 a2 b0 3b f9  ec 05 fa ca 1d 29 7f 7f  |...)..;......)..|
00000010  a7 4f d9 43 ff d6 56 d7  f8 09 6c f9 bb 75 bd c4  |.O.C..V...l..u..|
00000020  17 16 03 a7 f1 72 3c 21  6f b7 fe 91 94 1c 07 f9  |.....r<!o.......|
00000030  5b 1e e9 6b 7d 70 2c c5  e7 b7 9a 5a fc f2 9c f6  |[..k}p,....Z....|
00000040  b7 d6 32 db e7 4f f6 ef  d7 1d 70 21 3c 78 23 d5  |..2..O....p!<x#.|
00000050  ac 1b 56 ed eb 58 26 6b  1b cd 7e 7f 90 5a fd 5b  |..V..X&k..~..Z.[|
00000060  ff 47 8e b1 b8 e8 74 ba  13 c5 f9 67 cb 9e d4 ad  |.G....t....g....|
00000070  e5 0e 22 3f c1 2b 88 99  ed 94 fe f0 49 fb f0 8d  |.."?.+......I...|
00000080  b9 63 c5 58 fe 10 f0 8d  63 26 b8 7c 22 b7 c7 95  |.c.X....c&.|"...|
00000090  b6 df 4d 63 f1 60 32 ff  f2 a1 28 e3 06 b1 82 70  |..Mc.`2...(....p|
000000a0  17 e2 ef c9 6c d6 32 c6  b1 90 ff c2 39 45 22 dd  |....l.2.....9E".|
000000b0  c6 38 9d 2c 56 e8 a7 cd  8c 12 7e 96 d6 ab 81 6d  |.8.,V.....~....m|
000000c0  6b 29 7c b4 9e 24 7e f8  91 42 78 ab 1e 83 94 ac  |k)|..$~..Bx.....|
000000d0  6b 1a df c4 68 34 0a 5f  db 96 c5 36 ec 06 fd 05  |k...h4._...6....|
000000e0  fa 68 a4 21 23 f3 34 9a  af aa 20 03 42 12 84 02  |.h.!#.4... .B...|
000000f0  29 20 09 09 60 12 eb 3b  78 e8 1c c9 17 70 ac 92  |) ..`..;x....p..|
00000100  20 9c 79 e3 d6 0b ac 9f  01 31 00 0f 80 9d 00 03  | .y......1......|
00000110  c0 57 c0 00 5d 3f f8 09  1c 00 3c f5 ff 3d 66 55  |.W..]?....<..=fU|
00000120  65 d3 e5 f0 12 58 00 78  09 4c 00 7c 04 a0 00 5e  |e....X.x.L.|...^|
00000130  02 7c 00 1f 01 25 00 0e  55 cb 88 be 12 bc a5 f5  |.|...%..U.......|
00000140  3e 02 55 00 1f 34 e2 5b  cd 0e 96 71 0a 18 36 d1  |>.U..4.[...q..6.|
00000150  e1 07 4b 7f 27 60 d9 95  59 5a 74 fd 95 b1 c4 6a  |..K.'`..YZt....j|
00000160  c1 37 ae 0f 35 f8 8c e9  f2 fe 23 8c 1b 32 97 ff  |.7..5.....#..2..|
00000170  8b bf 5f af de 03 0b 33  a8 b7 b8 86 a3 c0 42 c0  |.._....3......B.|
00000180  08 8c a1 66 28 78 41 ff  13 fc 05 6e fc bc d7 e5  |...f(xA....n....|
00000190  5c 38 36 f8 45 6a b8 1f  67 b2 28 7e 30 6d 5b b7  |\86.Ej..g.(~0m[.|
000001a0  2c 6b 1a b1 dd 2e 8f cf  c2 09 5a a5 fd bb 04 b6  |,k........Z.....|
000001b0  f7 eb 78 0f c0 44 80 0a  38 d3 58 cb 55 8e 00 fe  |..x..D..8.X.U...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 26 4b 49 06 00 fe  |..........&KI...|
000001d0  ff ff 05 fe ff ff 28 4b  49 06 cf b3 73 09 00 00  |......(KI...s...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-ZGKaezAR/Tmp_Log: No such file or directory
File descriptor 9 (/proc/27419/mounts) leaked on lvscan invocation. Parent PID 13778: bash
File descriptor 63 (pipe:[2173511]) leaked on lvscan invocation. Parent PID 13778: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-08-16__04h50 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity

=================== os-prober:
/dev/sdb2:Windows 7 (loader):Windows:chain
/dev/sdc2:Ubuntu 14.04 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="NT-INT1" UUID="22E2B9C622334662" TYPE="ntfs"
/dev/sdb1: UUID="d898c458-3a28-4abf-9a28-c34d356c0046" TYPE="swap"
/dev/sdb2: UUID="66B8B439B8B40A17" TYPE="ntfs"
/dev/sr0: LABEL="Ubuntu 14.04 LTS amd64" TYPE="iso9660"
/dev/sdc1: UUID="3a7ce152-9022-42d2-8069-088a8ce8d58d" TYPE="swap"
/dev/sdc2: UUID="38cf3b09-8e34-410c-ac5e-8c7c2375808e" TYPE="ext4"
/dev/sdc3: UUID="5f2a8dfb-6c63-49f7-8480-c2204a4f746f" TYPE="ext4"
/dev/sdc5: UUID="e8703383-5e2d-41fa-8ffc-e393207619ec" TYPE="ext4"
/dev/sdc6: LABEL="Ganey" UUID="2c97211d-9eb8-4520-9ea7-c091e58b3a3b" TYPE="ext4"
/dev/sdc7: LABEL="Tasaveer" UUID="846a0dc9-58ba-468d-9e19-1fc5b59715c4" TYPE="ext4"
/dev/sdc8: LABEL="Kaghzat" UUID="b8aaa3ec-6996-486a-b9bb-aa3a954ff7c3" TYPE="ext4"
/dev/sdc9: LABEL="Linux-doc" UUID="1d3711f4-d1cf-472d-b09b-f90667a033fa" TYPE="ext4"
/dev/sdc10: LABEL="Temp" UUID="ce1aca59-ceda-4aef-8230-eb2996535daf" TYPE="ext4"
/dev/sdc11: LABEL="Kachra" UUID="3f608fc3-eef3-4dfe-a755-5e83486bb0e5" TYPE="ext4"
/dev/sdc12: LABEL="Win-apps" UUID="73E1719801BBE72A" TYPE="ntfs"
/dev/sdc13: UUID="3c58de79-519a-4e2e-9244-b153deb7a78a" TYPE="ext4"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== /media/ubuntu/38cf3b09-8e34-410c-ac5e-8c7c2375808e/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 17 01:26 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr 11 10:51 00_header
-rwxr-xr-x 1 root root  6058 Apr 10 15:58 05_debian_theme
-rwxr-xr-x 1 root root 11608 Apr 11 10:51 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11 10:51 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12 12:31 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11 10:51 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11 10:51 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr 11 10:51 40_custom
-rwxr-xr-x 1 root root   216 Apr 11 10:51 41_custom
-rw-r--r-- 1 root root   483 Apr 11 10:51 README




=================== /media/ubuntu/38cf3b09-8e34-410c-ac5e-8c7c2375808e/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/ubuntu/66B8B439B8B40A17.
sdc2    : sdc,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /media/ubuntu/38cf3b09-8e34-410c-ac5e-8c7c2375808e.
sdc3    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/ubuntu/5f2a8dfb-6c63-49f7-8480-c2204a4f746f.
sdc5    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/ubuntu/e8703383-5e2d-41fa-8ffc-e393207619ec.
sdc6    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc6.
sdc7    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc7.
sdc8    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc8.
sdc9    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc9.
sdc10    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc10.
sdc11    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc11.
sdc12    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc12.
sdc13    : sdc,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc13.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    63 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA Maxtor 6Y200P0 (scsi)
Disk /dev/sda: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  204GB  204GB  primary  ntfs         boot


Model: ATA WDC WD400BB-60JK (scsi)
Disk /dev/sdb: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
1      32.3kB  5240MB  5239MB  primary  linux-swap(v1)
2      5240MB  40.0GB  34.8GB  primary  ntfs            boot


Model: ATA ST3500320AS (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  5182MB  5182MB  primary   linux-swap(v1)
2      5182MB  35.6GB  30.4GB  primary   ext4            boot
3      35.6GB  92.3GB  56.7GB  primary   ext4
4      92.3GB  500GB   408GB   extended
5      92.3GB  146GB   54.0GB  logical   ext4
6      146GB   227GB   81.2GB  logical   ext4
7      227GB   309GB   81.2GB  logical   ext4
8      309GB   336GB   26.9GB  logical   ext4
9      336GB   362GB   26.9GB  logical   ext4
12      362GB   416GB   54.0GB  logical   ntfs
10      416GB   458GB   41.8GB  logical   ext4
11      458GB   469GB   10.4GB  logical   ext4
13      469GB   500GB   31.5GB  logical   ext4



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:204GB:scsi:512:512:msdos:ATA Maxtor 6Y200P0;
1:32.3kB:204GB:204GB:ntfs::boot;

BYT;
/dev/sdb:40.0GB:scsi:512:512:msdos:ATA WDC WD400BB-60JK;
1:32.3kB:5240MB:5239MB:linux-swap(v1)::;
2:5240MB:40.0GB:34.8GB:ntfs::boot;

BYT;
/dev/sdc:500GB:scsi:512:512:msdos:ATA ST3500320AS;
1:32.3kB:5182MB:5182MB:linux-swap(v1)::;
2:5182MB:35.6GB:30.4GB:ext4::boot;
3:35.6GB:92.3GB:56.7GB:ext4::;
4:92.3GB:500GB:408GB:::;
5:92.3GB:146GB:54.0GB:ext4::;
6:146GB:227GB:81.2GB:ext4::;
7:227GB:309GB:81.2GB:ext4::;
8:309GB:336GB:26.9GB:ext4::;
9:336GB:362GB:26.9GB:ext4::;
12:362GB:416GB:54.0GB:ntfs::;
10:416GB:458GB:41.8GB:ext4::;
11:458GB:469GB:10.4GB:ext4::;
13:469GB:500GB:31.5GB:ext4::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sdb2 on /media/ubuntu/66B8B439B8B40A17 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc5 on /media/ubuntu/e8703383-5e2d-41fa-8ffc-e393207619ec type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc3 on /media/ubuntu/5f2a8dfb-6c63-49f7-8480-c2204a4f746f type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc2 on /media/ubuntu/38cf3b09-8e34-410c-ac5e-8c7c2375808e type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc6 on /mnt/boot-sav/sdc6 type ext4 (rw)
/dev/sdc7 on /mnt/boot-sav/sdc7 type ext4 (rw)
/dev/sdc8 on /mnt/boot-sav/sdc8 type ext4 (rw)
/dev/sdc9 on /mnt/boot-sav/sdc9 type ext4 (rw)
/dev/sdc10 on /mnt/boot-sav/sdc10 type ext4 (rw)
/dev/sdc11 on /mnt/boot-sav/sdc11 type ext4 (rw)
/dev/sdc12 on /mnt/boot-sav/sdc12 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc13 on /mnt/boot-sav/sdc13 type ext4 (rw)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc10 sdc11 sdc12 sdc13 sdc2 sdc3 sdc4 sdc5 sdc6 sdc7 sdc8 sdc9 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu_dma_latency cuse disk dri ecryptfs fb0 fd fd0 full fuse fw0 hidraw0 hidraw1 hidraw2 hpet input kmsg kvm libmtp-1-3 log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdc sdc1 sdc10 sdc11 sdc12 sdc13 sdc2 sdc3 sdc4 sdc5 sdc6 sdc7 sdc8 sdc9 sdd sde serial sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vga_arbiter vhost-net watchdog zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  98 52 bd 17 00 00 00 00  |.........R......|
00000030  04 00 00 00 00 00 00 00  29 d5 7b 01 00 00 00 00  |........).{.....|
00000040  f6 00 00 00 01 00 00 00  62 46 33 22 c6 b9 e2 22  |........bF3"..."|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3d 26 9c 00  |........?...=&..|
00000020  00 00 00 00 80 00 80 00  83 6b 0c 04 00 00 00 00  |.........k......|
00000030  00 00 0c 00 00 00 00 00  b8 c6 40 00 00 00 00 00  |..........@.....|
00000040  f6 00 00 00 01 00 00 00  17 0a b4 b8 39 b4 b8 66  |............9..f|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdc12
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 a6 3b 33 2a  |........?....;3*|
00000020  00 00 00 00 80 00 80 00  25 4b 49 06 00 00 00 00  |........%KI.....|
00000030  04 00 00 00 00 00 00 00  b2 94 64 00 00 00 00 00  |..........d.....|
00000040  f6 00 00 00 01 00 00 00  2a e7 bb 01 98 71 e1 73  |........*....q.s|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1001M  530M  472M  53% /
udev           devtmpfs   990M   12K  990M   1% /dev
tmpfs          tmpfs      201M  1.4M  199M   1% /run
/dev/sr0       iso9660    964M  964M     0 100% /cdrom
/dev/loop0     squashfs   923M  923M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     1001M  2.0M 1000M   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     1001M  272K 1001M   1% /run/shm
none           tmpfs      100M   68K  100M   1% /run/user
/dev/sdb2      fuseblk     33G   26G  7.0G  79% /media/ubuntu/66B8B439B8B40A17
/dev/sdc5      ext4        50G   52M   47G   1% /media/ubuntu/e8703383-5e2d-41fa-8ffc-e393207619ec
/dev/sdc3      ext4        52G   14G   36G  29% /media/ubuntu/5f2a8dfb-6c63-49f7-8480-c2204a4f746f
/dev/sdc2      ext4        28G  3.8G   23G  15% /media/ubuntu/38cf3b09-8e34-410c-ac5e-8c7c2375808e
/dev/sda1      fuseblk    190G  118G   73G  62% /mnt/boot-sav/sda1
/dev/sdc6      ext4        75G  4.8G   66G   7% /mnt/boot-sav/sdc6
/dev/sdc7      ext4        75G  3.4G   68G   5% /mnt/boot-sav/sdc7
/dev/sdc8      ext4        25G   44M   24G   1% /mnt/boot-sav/sdc8
/dev/sdc9      ext4        25G   54M   24G   1% /mnt/boot-sav/sdc9
/dev/sdc10     ext4        39G   20G   18G  53% /mnt/boot-sav/sdc10
/dev/sdc11     ext4       9.4G   36M  8.9G   1% /mnt/boot-sav/sdc11
/dev/sdc12     fuseblk     51G  320M   50G   1% /mnt/boot-sav/sdc12
/dev/sdc13     ext4        29G  172M   28G   1% /mnt/boot-sav/sdc13

=================== fdisk -l:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   398283479   199141708+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c879c87

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    10233404     5116671   82  Linux swap / Solaris
/dev/sdb2   *    10233405    78156224    33961410    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbd3c5204

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    10120949     5060443+  82  Linux swap / Solaris
/dev/sdc2   *    10121216    69468159    29673472   83  Linux
/dev/sdc3        69468160   180248575    55390208   83  Linux
/dev/sdc4       180249361   976768064   398259352    5  Extended
/dev/sdc5       180249363   285716024    52733331   83  Linux
/dev/sdc6       285716088   444293639    79288776   83  Linux
/dev/sdc7       444293703   602871254    79288776   83  Linux
/dev/sdc8       602871318   655435934    26282308+  83  Linux
/dev/sdc9       655435998   708000614    26282308+  83  Linux
/dev/sdc10      813467403   895109669    40821133+  83  Linux
/dev/sdc11      895109733   915335504    10112886   83  Linux
/dev/sdc12      708000678   813467339    52733331    7  HPFS/NTFS/exFAT
/dev/sdc13      915335568   976768064    30716248+  83  Linux

Partition table entries are not in disk order


User choice: Is sdc (500GB) a removable disk? no
Partition outside the disk detected.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sdc (500GB) disk!

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sdc2 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.


```

Thanks for your patience with me.

Danial

---

### Post by oldfred on 2014-08-16
Please use code tags which are the # in the advanced editor. Changed from your quotes above.

You have newer grub version in sda & sdc and a very old one in sdb. I would install a Windows boot loader to sdb as that is where Windows is. Then from BIOS you could always boot Windows even if grub is not working. 

Which drive are you booting from in BIOS? I would use Boot-Repair to reinstall grub to sdc, install a Windows boot loader to sdb and set BIOS to boot sdc drive. You have to use Advanced mode with Boot-Repair as its auto fix just installs grub everywhere.

---

### Post by Danial on 2014-08-16
Fred,
Once again thanks for your time. I had not come out of live cd yet (I can't recall which hd I was using to boot to - I guess it was sdc). Anyway, I will restart and see which drive I am using to boot. Also, as you have suggested earlier to try to boot from a diff. drive, which I will do now (just checking). I will update as soon as possible. And sorry about not using code tags in my previous post. I thought quote tag would work, which it didn't. I will be careful.

Thanks, Danial.

---

### Post by Danial on 2014-08-19
Fred,
Sorry about the delay (got tied up with my son's surgery). Anyway, last night per your advice I tried to boot the pc from other drives. Finally, I was able to boot from sdc. I can boot to both 14.04 and Win7. For next few days, I may not be able to concentrate and work on this issue but once I am free, I'll use teh Boot-Repair to update the Grub on sdc. 
As of now, I will close this thread as completed but will update once I am done. 

Thanks again for your time and guidance to resolve the issue. Always appreciated.
Danial

---

### Post by oldfred on 2014-08-19
It sounds like it is working ok. If grub works you do not have to reinstall it.
But probably worthwhile to have a Windows boot loader in the Windows drive. Grub really only boots working Windows and sometimes you need to directly boot it to try to make repairs.

Hope your son is doing ok.

---

