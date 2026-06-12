---
title: "no such partition"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by gaben on 2011-11-14
Hy

Unfortunately I had to replace my Winchester in my computer and reinstalled Windows XP and then installed kubuntu 11.10.

After restarting, it received:
error: No such partition.
Grub rescue>

So much has changed that, so far Samsung 320GB SATA2 7200RPM 16MB HD321KJ was in the machine, and now Samsung 320GB 3.5 "SATAII HD322GJ

I tried reinstalling grub2, but it was not good.
After installation, Fedora 15 was the same.

For now, I ran the fixboot and fixmbr commands, so I use XP.

Thank you for your help.

Boot Info Script result:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   106,061,129   106,061,067   7 NTFS / exFAT / HPFS
/dev/sda2         106,061,130   537,936,524   431,875,395   7 NTFS / exFAT / HPFS
/dev/sda3         537,936,586   625,137,344    87,200,759   5 Extended
/dev/sda5         537,936,588   542,129,489     4,192,902  82 Linux swap / Solaris
/dev/sda6         542,129,553   625,137,344    83,007,792  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
249 heads, 55 sectors/track, 142645 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,519,678 1,953,519,616   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3A20336E2033306D                       ntfs       
/dev/sda2        43B58A212319D86C                       ntfs       Misc
/dev/sda5        382b01b6-f293-4ac9-b4ac-fa618f461661   swap       
/dev/sda6        7f784446-f92c-4890-ad4d-e7df9238d7c8   ext4       
/dev/sdb1        E4FC64B9FC64881E                       ntfs       DATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Misc              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional - magyar Avid 2.7GB" /3GB /userva=2700 /noexecute=AlwaysOff /fastdetect
--------------------------------------------------------------------------------

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
  set locale_dir=($root)/boot/grub/locale
  set lang=hu_HU
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
if background_color 0,71,115; then
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
menuentry 'Ubuntu, Linux 3.0.0-12-generic verzi&#258;&#322;val' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=7f784446-f92c-4890-ad4d-e7df9238d7c8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, Linux 3.0.0-12-generic verzi&#258;&#322;val (helyre&#258;&#711;ll&#258;*t&#258;&#711;si m&#258;&#322;d)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
	echo	'Linux 3.0.0-12-generic bet&#258;¶lt&#258;©seâ€¦'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=7f784446-f92c-4890-ad4d-e7df9238d7c8 ro recovery nomodeset 
	echo	'Kiindul&#258;&#322; ramdisk bet&#258;¶lt&#258;©seâ€¦'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 3A20336E2033306D
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=7f784446-f92c-4890-ad4d-e7df9238d7c8 /               ext4    errors=remount-ro 0       1
# /media/misc was on /dev/sda2 during installation
UUID=43B58A212319D86C /media/misc     ntfs    defaults,umask=007,gid=46 0       0
# /media/winxp was on /dev/sda1 during installation
UUID=3A20336E2033306D /media/winxp    ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=382b01b6-f293-4ac9-b4ac-fa618f461661 none            swap    sw              0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 266.643284321 = 286.306046464  boot/grub/core.img                             1
 262.655132771 = 282.023801344  boot/grub/grub.cfg                             1
 260.012192249 = 279.185965568  boot/initrd.img-3.0.0-12-generic               2
 266.639980793 = 286.302499328  boot/vmlinuz-3.0.0-12-generic                  1
 260.012192249 = 279.185965568  initrd.img                                     2
 266.639980793 = 286.302499328  vmlinuz                                        1


```

---

### Post by oldfred on 2011-11-14
I do not see anything really wrong. But Ubuntu 11.10 would be using grub 1.99 and you have grub 1.98 in the MBR. I know they made a lot of changes with 1.99 and you have to use a liveCD of the same version to get the correct grub2 installed. Did you reinstall with an older liveCD? I would try again with the latest liveCD to get grub 1.99 in the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda6 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
[COLOR=DarkRed]sudo mount /dev/sda6 /mnt[/COLOR]
sudo grub-install --root-directory=/mnt/ /dev/sda
[COLOR=DarkRed]#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR]

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by gaben on 2011-11-14
I have not tried older Live CD but I try. Thank you.

---

### Post by oldfred on 2011-11-14
No you need the current 11.10 version to match what you have installed. Or your installs of grub 1.99 to the MBR never worked and you just have an old grub 1.98 still there.

---

### Post by gaben on 2011-11-14
Now re-installed the grub2 kubuntu 11.10 Live CD
Results: grub 1.99
Sudo update-grub command after the error:
/ usr / sbin / grub-probe: error: can not find the device for / (is / dev mounted?)

You might try the boot repair disc.

Boot Info Script result:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot file info:      Grub2 (v1.97-1.98) in the file 
                       /super_grub_disk_hybrid-1.98s1.iso looks at sector 1 
                       of the same hard drive for core.img. core.img is at 
                       this location and looks in partition 256 for 
                       /boot/grub/i386-pc.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   106,061,129   106,061,067   7 NTFS / exFAT / HPFS
/dev/sda2         106,061,130   537,936,524   431,875,395   7 NTFS / exFAT / HPFS
/dev/sda3         537,936,586   625,137,344    87,200,759   5 Extended
/dev/sda5         537,936,588   542,129,489     4,192,902  82 Linux swap / Solaris
/dev/sda6         542,129,553   625,137,344    83,007,792  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
249 heads, 55 sectors/track, 142645 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,519,678 1,953,519,616   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3A20336E2033306D                       ntfs       
/dev/sda2        43B58A212319D86C                       ntfs       Misc
/dev/sda5        382b01b6-f293-4ac9-b4ac-fa618f461661   swap       
/dev/sda6        7f784446-f92c-4890-ad4d-e7df9238d7c8   ext4       
/dev/sdb1        E4FC64B9FC64881E                       ntfs       DATA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/Misc              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional - magyar Avid 2.7GB" /3GB /userva=2700 /noexecute=AlwaysOff /fastdetect
--------------------------------------------------------------------------------

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

insmod ntfs
set root='(hd0,6)'
search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod ntfs
  set root='(hd0,6)'
  search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
  set locale_dir=($root)/boot/grub/locale
  set lang=hu_HU
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
if background_color 0,71,115; then
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
menuentry 'Ubuntu, Linux 3.0.0-12-generic verzióval' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod ntfs
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=7f784446-f92c-4890-ad4d-e7df9238d7c8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, Linux 3.0.0-12-generic verzióval (helyreállítási mód)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ntfs
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
	echo	'Linux 3.0.0-12-generic betöltése…'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=7f784446-f92c-4890-ad4d-e7df9238d7c8 ro recovery nomodeset 
	echo	'Kiinduló ramdisk betöltése…'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ntfs
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ntfs
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set=root 7f784446-f92c-4890-ad4d-e7df9238d7c8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set=root 3A20336E2033306D
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=7f784446-f92c-4890-ad4d-e7df9238d7c8 /               ext4    errors=remount-ro 0       1
# /media/misc was on /dev/sda2 during installation
UUID=43B58A212319D86C /media/misc     ntfs    defaults,umask=007,gid=46 0       0
# /media/winxp was on /dev/sda1 during installation
UUID=3A20336E2033306D /media/winxp    ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=382b01b6-f293-4ac9-b4ac-fa618f461661 none            swap    sw              0       0
/dev/scd1       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in



```

---

### Post by darkod on 2011-11-14
You said XP is booting now directly, right? In that case you have sdb as first option to boot from because you have windows bootloader only there.
Try setting sda, the other disk as first choice to boot from. Do you get grub menu? Does it boot kubuntu correctly?

---

### Post by oldfred on 2011-11-14
Did you try to run the update-grub before rebooting? It does not work from liveCD, but from your working install, just to update menu.

You also used supergrub and somehow installed something into the PBR partition boot sector of sda2. NTFS partitions have to have a NTFS signature in the PBR or they do not work.

---

### Post by gaben on 2011-11-15
> **darkod said:**
> You said XP is booting now directly, right? In that case you have sdb as first option to boot from because you have windows bootloader only there.
Try setting sda, the other disk as first choice to boot from. Do you get grub menu? Does it boot kubuntu correctly?
Already tried is not connected data hard drive and install Kubuntu.
Unfortunately, the problem can be logged.
So not the boot order the problem.

---

### Post by gaben on 2011-11-15
> **oldfred said:**
> 
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

It escaped my attention. Unfortunately, not even got a "working system".
The grub installation ran without problems, but received the same image. There was no grub menu.

And I'm sorry if bad English. Unfortunately, I need the google translate because my English is poor. :-)

------------------------

And thank you both for your help.

---

### Post by oldfred on 2011-11-15
What come up on the screen. Grub should show menu as you have two systems, but if only one system found it directly boots Ubuntu. Then you have to hold shift key from BIOS until menu appears. Try that.

If you do get a menu then it is a video issue. Normally with grub errors you get to grub> or grub rescue.

Some have been able to boot into an otherwise working Ubuntu with this:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by gaben on 2011-11-18
Hy,

This week does not really mean it. Yesterday was to try the super grub disc.

I tried the partition listing, and for some reason only detected in the primary partition. The extended partition is not.
I think we should not start the grub.

The old hard disk partitions have been extended and there was no problem.

I'm going to try to re-partition your hard drive.
Other ideas?

[[img]http://noob.hu/2011/11/18/tn/P1050273.JPG[/img]](http://noob.hu/2011/11/18/P1050273.JPG)

---

### Post by oldfred on 2011-11-18
Was that list from Windows or DOS. Windows does not see Linux partitions.

Does it show partitions from LiveCD?
```

sudo fdisk -lu
```

---

### Post by gaben on 2011-11-18
> **oldfred said:**
> Was that list from Windows or DOS. Windows does not see Linux partitions.

The list provided by the super grub disc. "List devices/partitions" (see picture)
[http://www.supergrubdisk.org/w/images/7/78/SG2D_1.98s1_main_menu.png]("http://www.supergrubdisk.org/w/images/7/78/SG2D_1.98s1_main_menu.png")

---

### Post by oldfred on 2011-11-18
I can understand why it would be confused on sda2 as that has the supergrub in the boot sector of a NTFS partiiton which makes an invalid NTFS partition. You need to use testdisk to repair sda2. Not sure about why it cannot see the other partition nor why it does not show the other partitions.

It may default to sda1 as that has the boot flag & looks otherwise ok, but you want to fix sda2:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by gaben on 2011-11-19
Hy,

I tried TestDisk. There is still a problem.
I deleted the extended partition and made &#8203;&#8203;a primary. Re-installed Kubuntu.
There result is now: Error unknown file system
Super Disc grub2 menu> detect any OS > nothing
then > Enable PATA support > again detect any OS > and found the operating system.

Maybe something went wrong in the first partitioning?
It may help clear a full partition table?
Or maybe the BIOS is set to something?

Thanks,

---

### Post by oldfred on 2011-11-19
I suggested testdisk to recovery the backup boot sector on the NTFS partition. Did you also have other partition issues?

So what works or is it solved?

---

### Post by darkod on 2011-11-19
Also, why do you still insist on super grub2 disc even after reinstalled kubuntu? Even reinstalled grub2 doesn't boot correctly windows and kubuntu?

---

### Post by gaben on 2011-11-20
I decided to delete the entire partition table and then re-partition the kubuntu partition editor.
Now it looks like the problem is fixed. :-)
Thanks both of you for help. :-)

---

