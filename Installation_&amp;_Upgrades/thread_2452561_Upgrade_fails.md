---
title: "Upgrade fails"
date: 2020-10-24
forum: Installation &amp; Upgrades
---

### Post by yegnal on 2020-10-24
Greetings;

20.04 will not upgrade to the latest 20.10 stating EFI System Partition (ESP) not usable
Your EFI System Partition (ESP) is not mounted at /boot/efi.  Please ensure that it is properly configured and try again.

This is on a dual boot Windows machine that has been working flawlessly.

---

### Post by grahammechanical on 2020-10-24
Open the Disks utility and examine the partitions one by one. What information do you see regarding Partition type: Contents. Under Contents you should see the mount point.

Regards

---

### Post by yegnal on 2020-10-24
```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0   450M  0 part 
&#9500;&#9472;sda2   8:2    0   100M  0 part 
&#9500;&#9472;sda3   8:3    0    16M  0 part 
&#9492;&#9472;sda4   8:4    0 232.3G  0 part 
sdb      8:16   0 119.2G  0 disk 
&#9500;&#9472;sdb1   8:17   0   476M  0 part 
&#9500;&#9472;sdb2   8:18   0 102.5G  0 part /
&#9492;&#9472;sdb3   8:19   0  16.3G  0 part [SWAP]
sdc      8:32   0   3.7T  0 disk 
&#9500;&#9472;sdc1   8:33   0     1M  0 part 
&#9500;&#9472;sdc2   8:34   0    15M  0 part 
&#9492;&#9472;sdc3   8:35   0   3.7T  0 part 
sdd      8:48   0   3.7T  0 disk 
&#9500;&#9472;sdd1   8:49   0     1M  0 part 
&#9500;&#9472;sdd2   8:50   0    15M  0 part 
&#9492;&#9472;sdd3   8:51   0   3.7T  0 part 
sde      8:64   0 465.8G  0 disk 
&#9492;&#9472;sde1   8:65   0 465.8G  0 part /mnt/MISCSHARED
sdf      8:80   0 465.8G  0 disk 
&#9492;&#9472;sdf1   8:81   0 465.8G  0 part /run/timeshift/backup
sr0     11:0    1  1024M  0 rom  
```


sda is Windows, sdb is Ubuntu

---

### Post by yegnal on 2020-10-24
```
Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Windows is installed in the MBR of /dev/sde.
 => No boot loader is installed in the MBR of /dev/sdf.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi


sda3: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-f0o2hEPf/sda3: unknown filesystem type ''.


sda4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab


sdb3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdc1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-f0o2hEPf/sda3: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdc1: unknown filesystem type ''.


sdc2: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-f0o2hEPf/sda3: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdc1: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdc2: unknown filesystem type ''.


sdc3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdc3 has 
                       3519033343 sectors, but according to the info from 
                       fdisk, it has 4592778894 sectors.
    Operating System:  
    Boot files:        


sdd1: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-f0o2hEPf/sda3: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdc1: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdc2: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdd1: unknown filesystem type ''.


sdd2: __________________________________________________________________________


    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /tmp/BootInfo-f0o2hEPf/sda3: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdc1: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdc2: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdd1: unknown filesystem type ''.
mount: /tmp/BootInfo-f0o2hEPf/sdd2: unknown filesystem type ''.


sdd3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdd3 has 
                       3519033343 sectors, but according to the info from 
                       fdisk, it has 4592778894 sectors.
    Operating System:  
    Boot files:        


sde1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdf1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 232.91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


/dev/sda1 ends after the last sector of /dev/sda


GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       923,646       921,599 Data partition (Windows/Linux)
/dev/sda2         923,648     1,128,447       204,800 EFI System partition
/dev/sda3       1,128,448     1,161,215        32,768 Microsoft Reserved Partition (Windows)
/dev/sda4       1,161,216   488,394,883   487,233,668 Data partition (Windows/Linux)


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 119.25 GiB, 128034594304 bytes, 250067567 sectors
Disk model: SanDisk SDSSDHP1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                   1   250,067,566   250,067,566  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       976,895       974,848 EFI System partition
/dev/sdb2         976,896   215,820,287   214,843,392 Data partition (Linux)
/dev/sdb3     215,820,288   250,066,943    34,246,656 Swap partition (Linux)


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD4005FZBX-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdc1                   1 4,294,967,295 4,294,967,295  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1              34         2,081         2,048 Logical Disk Manager metadata partition (Windows)
/dev/sdc2           2,082        32,767        30,686 Microsoft Reserved Partition (Windows)
/dev/sdc3          32,768 4,592,811,662 4,592,778,895 Logical Disk Manager data partition (Windows)


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 3.65 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD4005FZBX-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdd1                   1 4,294,967,295 4,294,967,295  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1              34         2,081         2,048 Logical Disk Manager metadata partition (Windows)
/dev/sdd2           2,082        32,767        30,686 Microsoft Reserved Partition (Windows)
/dev/sdd3          32,768 4,592,811,662 4,592,778,895 Logical Disk Manager data partition (Windows)


Drive: sde _____________________________________________________________________
Disk /dev/sde: 465.78 GiB, 500106780160 bytes, 976771055 sectors
Disk model: WDC WD5000AAKS-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sde1               2,048   976,769,023   976,766,976   7 NTFS / exFAT / HPFS




Drive: sdf _____________________________________________________________________
Disk /dev/sdf: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: WDC WD5000AAKS-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdf1                   1   976,773,167   976,773,167  ee GPT




GUID Partition Table detected.


Partition    Start Sector    End Sector  # of Sectors System
/dev/sdf1           2,048   976,771,071   976,769,024 Data partition (Linux)


"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop15                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/sda1        00F40F9EF40F94D6                       ntfs       Recovery
/dev/sda2        3811-A49D                              vfat       
/dev/sda3                                                          
/dev/sda4        44B0CA44B0CA3BE4                       ntfs       
/dev/sdb1        33AB-5AAC                              vfat       
/dev/sdb2        5cd3dbcb-22a7-4264-a89b-f4e4a2028840   ext4       
/dev/sdb3        0f60281f-7114-4ed8-98f5-73f8ae8bda59   swap       
/dev/sdc1                                                          
/dev/sdc2                                                          
/dev/sdc3        DE90B09B90B07B99                       ntfs       Storage
/dev/sdd1                                                          
/dev/sdd2                                                          
/dev/sdd3        DE90B09B90B07B99                       ntfs       Storage
/dev/sde1        779A70C23D0FD88C                       ntfs       MISCSHARED
/dev/sdf1        f164fafc-afc2-4b9d-86eb-77fecd89f2c6   ext4       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/fuse        /run/user/1000/doc       fuse       (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdb2        /                        ext4       (rw,relatime,errors=remount-ro)
/dev/sde1        /mnt/MISCSHARED          fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,x-gvfs-show)
/dev/sdf1        /home                    ext4       (rw,relatime)
/dev/sdf1        /run/timeshift/backup    ext4       (rw,relatime)




=========================== sdb2/boot/grub/grub.cfg: ===========================


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
if [ "${initrdfail}" = 2 ]; then
   set initrdfail=
elif [ "${initrdfail}" = 1 ]; then
   set next_entry="${prev_entry}"
   set prev_entry=
   save_env prev_entry
   if [ "${next_entry}" ]; then
      set initrdfail=2
   fi
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="${saved_entry}"
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
function initrdfail {
    if [ -n "${have_grubenv}" ]; then if [ -n "${partuuid}" ]; then
      if [ -z "${initrdfail}" ]; then
        set initrdfail=1
        if [ -n "${boot_once}" ]; then
          set prev_entry="${default}"
          save_env prev_entry
        fi
      fi
      save_env initrdfail
    fi; fi
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
set root='hd1,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  5cd3dbcb-22a7-4264-a89b-f4e4a2028840
else
  search --no-floppy --fs-uuid --set=root 5cd3dbcb-22a7-4264-a89b-f4e4a2028840
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=1440x900x16
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='hd1,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  5cd3dbcb-22a7-4264-a89b-f4e4a2028840
else
  search --no-floppy --fs-uuid --set=root 5cd3dbcb-22a7-4264-a89b-f4e4a2028840
fi
insmod gfxmenu
loadfont ($root)/boot/grub/themes/Einstein/NanumMyeongjo-Regular16.pf2
loadfont ($root)/boot/grub/themes/Einstein/NanumMyeongjo-Regular18.pf2
loadfont ($root)/boot/grub/themes/Einstein/SourceCodePro-Regular16.pf2
insmod png
set theme=($root)/boot/grub/themes/Einstein/theme.txt
export theme
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5cd3dbcb-22a7-4264-a89b-f4e4a2028840' {
	recordfail
	savedefault
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	set root='hd1,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  5cd3dbcb-22a7-4264-a89b-f4e4a2028840
	else
	  search --no-floppy --fs-uuid --set=root 5cd3dbcb-22a7-4264-a89b-f4e4a2028840
	fi
	linux	/boot/vmlinuz-5.4.0-52-generic root=UUID=5cd3dbcb-22a7-4264-a89b-f4e4a2028840 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-5.4.0-52-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-5cd3dbcb-22a7-4264-a89b-f4e4a2028840' {
	menuentry 'Ubuntu, with Linux 5.4.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-52-generic-advanced-5cd3dbcb-22a7-4264-a89b-f4e4a2028840' {
		recordfail
	savedefault
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  5cd3dbcb-22a7-4264-a89b-f4e4a2028840
		else
		  search --no-floppy --fs-uuid --set=root 5cd3dbcb-22a7-4264-a89b-f4e4a2028840
		fi
		echo	'Loading Linux 5.4.0-52-generic ...'
		linux	/boot/vmlinuz-5.4.0-52-generic root=UUID=5cd3dbcb-22a7-4264-a89b-f4e4a2028840 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.4.0-52-generic
	}
	menuentry 'Ubuntu, with Linux 5.4.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-52-generic-recovery-5cd3dbcb-22a7-4264-a89b-f4e4a2028840' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  5cd3dbcb-22a7-4264-a89b-f4e4a2028840
		else
		  search --no-floppy --fs-uuid --set=root 5cd3dbcb-22a7-4264-a89b-f4e4a2028840
		fi
		echo	'Loading Linux 5.4.0-52-generic ...'
		linux	/boot/vmlinuz-5.4.0-52-generic root=UUID=5cd3dbcb-22a7-4264-a89b-f4e4a2028840 ro recovery nomodeset dis_ucode_ldr 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.4.0-52-generic
	}
	menuentry 'Ubuntu, with Linux 5.4.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-48-generic-advanced-5cd3dbcb-22a7-4264-a89b-f4e4a2028840' {
		recordfail
	savedefault
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  5cd3dbcb-22a7-4264-a89b-f4e4a2028840
		else
		  search --no-floppy --fs-uuid --set=root 5cd3dbcb-22a7-4264-a89b-f4e4a2028840
		fi
		echo	'Loading Linux 5.4.0-48-generic ...'
		linux	/boot/vmlinuz-5.4.0-48-generic root=UUID=5cd3dbcb-22a7-4264-a89b-f4e4a2028840 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.4.0-48-generic
	}
	menuentry 'Ubuntu, with Linux 5.4.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-48-generic-recovery-5cd3dbcb-22a7-4264-a89b-f4e4a2028840' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd1,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt2 --hint-efi=hd1,gpt2 --hint-baremetal=ahci1,gpt2  5cd3dbcb-22a7-4264-a89b-f4e4a2028840
		else
		  search --no-floppy --fs-uuid --set=root 5cd3dbcb-22a7-4264-a89b-f4e4a2028840
		fi
		echo	'Loading Linux 5.4.0-48-generic ...'
		linux	/boot/vmlinuz-5.4.0-48-generic root=UUID=5cd3dbcb-22a7-4264-a89b-f4e4a2028840 ro recovery nomodeset dis_ucode_ldr 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.4.0-48-generic
	}
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/10_linux_zfs ###
### END /etc/grub.d/10_linux_zfs ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober_proxy ###




set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
menuentry "Windows 10" --class windows --class os $menuentry_id_option 'osprober-efi-3811-A49D' {
	savedefault
	insmod part_gpt
	insmod fat
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  3811-A49D
	else
	  search --no-floppy --fs-uuid --set=root 3811-A49D
	fi
	chainloader /efi/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/30_os-prober_proxy ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'UEFI Firmware Settings' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
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


=============================== sdb2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
#<file system> <mount point>   <type>  <options>       <dump>  <pass>


#Boot EFI partition
#/boot/efi was on /dev/sda2 during installation
UUID=3811-A49D /boot/efi vfat umask=0077,noauto 0 1


# / was on /dev/sdb2 during installation
UUID=5cd3dbcb-22a7-4264-a89b-f4e4a2028840 /               ext4    errors=remount-ro 0       1


# /home was on /dev/sdf1 during installation
UUID=f164fafc-afc2-4b9d-86eb-77fecd89f2c6 /home           ext4    defaults        0       2


# swap was on /dev/sdb3 during installation
UUID=0f60281f-7114-4ed8-98f5-73f8ae8bda59 none            swap    sw              0       0


# ?
#/dev/disk/by-uuid/AB65-0DC0 /mnt/AB65-0DC0  nosuid,nodev,nofail,x-gvfs-show 0 0
#/dev/disk/by-uuid/AB65-0DC0 /mnt/AB65-0DC0 auto nosuid,nodev,nofail,umask=0000 0 0
#/dev/disk/by-uuid/00F40F9EF40F94D6 /mnt/00F40F9EF40F94D6 auto nosuid,nodev,nofail,noauto 0 0
#/dev/disk/by-uuid/44B0CA44B0CA3BE4 /mnt/44B0CA44B0CA3BE4 auto nosuid,nodev,nofail,noauto 0 0




#Shared drive for Windows and Linux dual boot
/dev/disk/by-uuid/DE90B09B90B07B99 /mnt/DE90B09B90B07B99 auto nosuid,nodev,nofail,noauto,ro 0 0
/dev/disk/by-uuid/779A70C23D0FD88C /mnt/MISCSHARED auto nosuid,nodev,nofail,umask=0000,x-gvfs-show 0 0
--------------------------------------------------------------------------------


=================== sdb2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)




======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda2


00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 18 0e 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 9d a4 11 38 4e  4f 20 4e 41 4d 45 20 20  |..)...8NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


Unknown BootLoader on sdd2


00000000  00 0a 01 0a 02 0a 03 0a  04 0a 05 0a 06 0a 07 0a  |................|
00000010  08 0a 09 0a 0a 0a 0b 0a  0c 0a 0d 0a 0e 0a 0f 0a  |................|
00000020  10 0a 11 0a 12 0a 13 0a  14 0a 15 0a 16 0a 17 0a  |................|
00000030  18 0a 19 0a 1a 0a 1b 0a  1c 0a 1d 0a 1e 0a 1f 0a  |................|
00000040  20 0a 21 0a 22 0a 23 0a  24 0a 25 0a 26 0a 27 0a  | .!.".#.$.%.&.'.|
00000050  28 0a 29 0a 2a 0a 2b 0a  2c 0a 2d 0a 2e 0a 2f 0a  |(.).*.+.,.-.../.|
00000060  30 0a 31 0a 32 0a 33 0a  34 0a 35 0a 36 0a 37 0a  |0.1.2.3.4.5.6.7.|
00000070  38 0a 39 0a 3a 0a 3b 0a  3c 0a 3d 0a 3e 0a 3f 0a  |8.9.:.;.<.=.>.?.|
00000080  40 0a 41 0a 42 0a 43 0a  44 0a 45 0a 46 0a 47 0a  |@.A.B.C.D.E.F.G.|
00000090  48 0a 49 0a 4a 0a 4b 0a  4c 0a 4d 0a 4e 0a 4f 0a  |H.I.J.K.L.M.N.O.|
000000a0  50 0a 51 0a 52 0a 53 0a  54 0a 55 0a 56 0a 57 0a  |P.Q.R.S.T.U.V.W.|
000000b0  58 0a 59 0a 5a 0a 5b 0a  5c 0a 5d 0a 5e 0a 5f 0a  |X.Y.Z.[.\.].^._.|
000000c0  60 0a 61 0a 62 0a 63 0a  64 0a 65 0a 66 0a 67 0a  |`.a.b.c.d.e.f.g.|
000000d0  68 0a 69 0a 6a 0a 6b 0a  6c 0a 6d 0a 6e 0a 6f 0a  |h.i.j.k.l.m.n.o.|
000000e0  70 0a 71 0a 72 0a 73 0a  74 0a 75 0a 76 0a 77 0a  |p.q.r.s.t.u.v.w.|
000000f0  78 0a 79 0a 7a 0a 7b 0a  7c 0a 7d 0a 7e 0a 7f 0a  |x.y.z.{.|.}.~...|
00000100  80 0a 81 0a 82 0a 83 0a  84 0a 85 0a 86 0a 87 0a  |................|
00000110  88 0a 89 0a 8a 0a 8b 0a  8c 0a 8d 0a 8e 0a 8f 0a  |................|
00000120  90 0a 91 0a 92 0a 93 0a  94 0a 95 0a 96 0a 97 0a  |................|
00000130  98 0a 99 0a 9a 0a 9b 0a  9c 0a 9d 0a 9e 0a 9f 0a  |................|
00000140  a0 0a a1 0a a2 0a a3 0a  a4 0a a5 0a a6 0a a7 0a  |................|
00000150  a8 0a a9 0a aa 0a ab 0a  ac 0a ad 0a ae 0a af 0a  |................|
00000160  b0 0a b1 0a b2 0a b3 0a  b4 0a b5 0a b6 0a b7 0a  |................|
00000170  b8 0a b9 0a ba 0a bb 0a  bc 0a bd 0a be 0a bf 0a  |................|
00000180  c0 0a c1 0a c2 0a c3 0a  c4 0a c5 0a c6 0a c7 0a  |................|
00000190  c8 0a c9 0a ca 0a cb 0a  cc 0a cd 0a ce 0a cf 0a  |................|
000001a0  d0 0a d1 0a d2 0a d3 0a  d4 0a d5 0a d6 0a d7 0a  |................|
000001b0  d8 0a d9 0a da 0a db 0a  dc 0a dd 0a de 0a df 0a  |................|
000001c0  e0 0a e1 0a e2 0a e3 0a  e4 0a e5 0a e6 0a e7 0a  |................|
000001d0  e8 0a e9 0a ea 0a eb 0a  ec 0a ed 0a ee 0a ef 0a  |................|
000001e0  f0 0a f1 0a f2 0a f3 0a  f4 0a f5 0a f6 0a f7 0a  |................|
000001f0  f8 0a f9 0a fa 0a fb 0a  fc 0a fd 0a fe 0a ff 0a  |................|
00000200


Unknown BootLoader on sde1


00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 47 38 3a 00 00 00 00  |.........G8:....|
00000030  04 00 00 00 00 00 00 00  7f 84 a3 03 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  8c d8 0f 3d c2 70 9a 77  |...........=.p.w|
00000050  00 00 00 00 0e 1f be 71  7c ac 22 c0 74 0b 56 b4  |.......q|.".t.V.|
00000060  0e bb 07 00 cd 10 5e eb  f0 32 e4 cd 16 cd 19 eb  |......^..2......|
00000070  fe 54 68 69 73 20 69 73  20 6e 6f 74 20 61 20 62  |.This is not a b|
00000080  6f 6f 74 61 62 6c 65 20  64 69 73 6b 2e 20 50 6c  |ootable disk. Pl|
00000090  65 61 73 65 20 69 6e 73  65 72 74 20 61 20 62 6f  |ease insert a bo|
000000a0  6f 74 61 62 6c 65 20 66  6c 6f 70 70 79 20 61 6e  |otable floppy an|
000000b0  64 0d 0a 70 72 65 73 73  20 61 6e 79 20 6b 65 79  |d..press any key|
000000c0  20 74 6f 20 74 72 79 20  61 67 61 69 6e 20 2e 2e  | to try again ..|
000000d0  2e 20 0d 0a 00 00 00 00  00 00 00 00 00 00 00 00  |. ..............|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




========= Devices which don't seem to have a corresponding hard drive: =========


sdg sdh sdi sdj 


=============================== StdErr Messages: ===============================


cat: /tmp/BootInfo-f0o2hEPf/Tmp_Log: No such file or directory
```

---

### Post by QIII on 2020-10-24
Please use code tags to surround all commands and their results:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

Also, in the instructions for the use of that script, one should put that content on [https://paste.ubuntu.com/](https://paste.ubuntu.com/) and then paste the link here.  For future reference.

Thanks.

---

### Post by yegnal on 2020-10-25
Sorry about that, I actually know better...

---

### Post by yegnal on 2020-10-25
**I have a laptop setup as dual boot which upgraded without a problem.**

On the machine I'm having trouble updating, I moved grub to sdb2 using grub customizer, but Ubuntu giving the same error when trying to update.

I'm wondering if the following may be the problem on this machine:

1. My /home directory is on a separate physical drive.  I did this because I ran out of space on the 120gb drive Ubuntu was installed on, so I moved all /home contents to a separate 500gb and edited the fstab accordingly.  Works flawlessly.

On the problem machine, /boot/efi is empty and I can navigate there without root.
On the laptop, where the update worked, /boot/efi contains what appears to be boot files and I can only get there as su.

---

### Post by rsteinmetz70112 on 2020-10-26
Going strictly by the error message it seem your /boot/efi partition is not mounted and it looks like that partition is /dev/sda3.
But I'm kind s guessing. Mount /dev/sda3 and see what's in it. If it's the /boot/efi you might try editing fstab so it mounts on boot.

---

