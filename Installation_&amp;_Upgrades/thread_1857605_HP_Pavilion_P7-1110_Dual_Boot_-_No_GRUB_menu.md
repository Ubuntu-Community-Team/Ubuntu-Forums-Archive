---
title: "HP Pavilion P7-1110 Dual Boot - No GRUB menu?"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by csete on 2011-10-10
Hello,

I just picked up a new HP P7-1110 with Windows 7 that I want to set up for dual-boot.  I've partitioned and installed Ubuntu 11.04 on the machine with no problems.  I installed GRUB to the MBR, but it appears that it isn't being loaded.  When I reboot, I go direct to Win7.  Is there something else I need to do to install GRUB properly on this machine?  Do I need to put it in a different partition and, if so, are there things I should be concerned about when doing that?

Thanks so much for any input.
Craig

---

### Post by Quackers on 2011-10-10
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by csete on 2011-10-10
Here you go.  Looking forward to further directions.

Thanks,
Craig

```

                  Boot Inf                  Boot Info Script 0.60    from 17 May 2011


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
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
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
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   105,064,447   104,857,600   7 NTFS / exFAT / HPFS
/dev/sda3       1,929,029,632 1,953,521,663    24,492,032   7 NTFS / exFAT / HPFS
/dev/sda4         105,066,494 1,929,029,631 1,823,963,138   5 Extended
/dev/sda5         105,066,496   205,064,191    99,997,696  83 Linux
/dev/sda6       1,905,029,120 1,929,029,631    24,000,512  82 Linux swap / Solaris
/dev/sda7         205,066,240 1,905,018,879 1,699,952,640  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0CFC8212FC81F66C                       ntfs       SYSTEM
/dev/sda2        EC1092291091FAB2                       ntfs       OS
/dev/sda3        2E1215581215267D                       ntfs       HP_RECOVERY
/dev/sda5        f95b5aac-8cb9-4423-957f-6cec30ccf7b4   ext4       
/dev/sda6        1a4ef0a8-5e84-4abe-8881-85b6d5cf75ff   swap       
/dev/sda7        cbd7b1a7-08af-4932-9d8f-9493bea8b993   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
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
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f95b5aac-8cb9-4423-957f-6cec30ccf7b4 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f95b5aac-8cb9-4423-957f-6cec30ccf7b4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0CFC8212FC81F66C
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 2E1215581215267D
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
UUID=f95b5aac-8cb9-4423-957f-6cec30ccf7b4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=cbd7b1a7-08af-4932-9d8f-9493bea8b993 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=1a4ef0a8-5e84-4abe-8881-85b6d5cf75ff none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  64.633674622 = 69.399879680   boot/grub/grub.cfg                             1
  51.777912140 = 55.596109824   boot/initrd.img-2.6.38-8-generic               2
  94.232425690 = 101.181296640  boot/vmlinuz-2.6.38-8-generic                  1
  51.777912140 = 55.596109824   initrd.img                                     2
  94.232425690 = 101.181296640  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

o Script 0.60    from 17 May 2011


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
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
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
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   105,064,447   104,857,600   7 NTFS / exFAT / HPFS
/dev/sda3       1,929,029,632 1,953,521,663    24,492,032   7 NTFS / exFAT / HPFS
/dev/sda4         105,066,494 1,929,029,631 1,823,963,138   5 Extended
/dev/sda5         105,066,496   205,064,191    99,997,696  83 Linux
/dev/sda6       1,905,029,120 1,929,029,631    24,000,512  82 Linux swap / Solaris
/dev/sda7         205,066,240 1,905,018,879 1,699,952,640  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0CFC8212FC81F66C                       ntfs       SYSTEM
/dev/sda2        EC1092291091FAB2                       ntfs       OS
/dev/sda3        2E1215581215267D                       ntfs       HP_RECOVERY
/dev/sda5        f95b5aac-8cb9-4423-957f-6cec30ccf7b4   ext4       
/dev/sda6        1a4ef0a8-5e84-4abe-8881-85b6d5cf75ff   swap       
/dev/sda7        cbd7b1a7-08af-4932-9d8f-9493bea8b993   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
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
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f95b5aac-8cb9-4423-957f-6cec30ccf7b4 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=f95b5aac-8cb9-4423-957f-6cec30ccf7b4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root f95b5aac-8cb9-4423-957f-6cec30ccf7b4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0CFC8212FC81F66C
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root 2E1215581215267D
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
UUID=f95b5aac-8cb9-4423-957f-6cec30ccf7b4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=cbd7b1a7-08af-4932-9d8f-9493bea8b993 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=1a4ef0a8-5e84-4abe-8881-85b6d5cf75ff none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  64.633674622 = 69.399879680   boot/grub/grub.cfg                             1
  51.777912140 = 55.596109824   boot/initrd.img-2.6.38-8-generic               2
  94.232425690 = 101.181296640  boot/vmlinuz-2.6.38-8-generic                  1
  51.777912140 = 55.596109824   initrd.img                                     2
  94.232425690 = 101.181296640  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 



```

---

### Post by csete on 2011-10-11
Does anybody have any insights on what I can do to solve this?

Thanks again,
Craig

---

### Post by mikewhatever on 2011-10-11
All looks good, except Grub is not in the MBR:
```
 => Windows is installed in the MBR of /dev/sda.
```

---

### Post by csete on 2011-10-11
Any idea why the installer didn't set up the MBR?  What do I need to invoke outside the installer to get GRUB installed in the MBR?

---

### Post by Quackers on 2011-10-11
Please boot from the live cd/usb and select "try Ubuntu" and when the desktop loads open up a terminal and copy/paste these commands in one at a time pressing enter after each one ```
sudo mount /dev/sda5 /mnt  
sudo grub-install --boot-directory=/mnt /dev/sda
``` This should report "Finished. No errors".
If it does, reboot and you should go straight into Ubuntu. If Ubuntu loads please open a terminal again and run ```
sudo update-grub
``` and watch the screen as grub.cfg is run. The Windows Loader should be recognised. If it is reboot and you should then get a grub menu giving you the choice of which operating system to boot.

---

### Post by csete on 2011-10-11
Unfortunately, that didn't get me there.  I didn't get any errors from grub-install, but when I reboot, I end up at the grub prompt rather than within Ubuntu.  Not sure if I did something wrong, but I did try twice with the same results.  

It does appear I've managed to mess things up though.  I can't seem to even boot to the Ubuntu CD anymore... I end up at the grub prompt even if I go through the BIOS boot loader and select the CD drive.

I noticed when I went through the BIOS menu it mentioned UEFI.  Is there a chance that that is somehow causing issues.

Thanks again for any help,
Craig

---

### Post by Quackers on 2011-10-11
Yes, UEFI is a different thing.
Does your system use UEFI? I see no mention of it anywhere in the boot script.
If your live cd/usb is not booting when it was doing so previously it suggests that it is not first boot device or that there is a bios problem of some kind.

You could try turning off the machine for a few minutes, then try booting the cd/usb again, or setting your bios back to default settings, temporarily.

---

### Post by csete on 2011-10-11
Unfortunately, that didn't work.  There are references to UEFI throughout the BIOS setup screens, so that appears to be the case.  Rebooting and resetting BIOS defaults didn't help... I still end up booting to a GRUB prompt no matter what I choose.

Hopefully I've not "bricked" my computer at this point.  I'm really unaware of UEFI and how that plays into things.  I'm a software engineer, but generally not deep into the hardware aspect of things.

Thanks again,
Craig

---

### Post by Quackers on 2011-10-11
Setting the bios back to default has probably set it to boot from the hard drive. That appears to be what it's doing. Have you tried setting boot priority again to cd drive or usb flash drive, if that's what you are using?
Did UEFI appear to be in use according to your bios?

---

### Post by csete on 2011-10-11
I managed to get booted back into the Ubuntu Live CD.  What do I try now?  It definitely looks like UEFI is enabled in the BIOS.  If I look at boot ordering in the BIOS, it appears that UEFI is ordered before "legacy" devices and that that can't be changed.  I can change the order *within* that group, but I can't set "legacy" before UEFI.

What next?  How do I deal with UEFI and GRUB?

Thanks,
Craig

---

### Post by Quackers on 2011-10-11
Glad you got the live session booting again.
Sadly I know almost nothing about UEFI systems and how they work, never having owned one.
There are a few threads around which discuss it. In fact I see a couple on this same page. I can only suggest that you use the search function and see what comes up. I'm sorry I can't be of any help because one day we'll all be using UEFI or something like it.
Best of luck! :-)

Actually post #2 here may give you some leads
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

---

### Post by csete on 2011-10-11
Thanks for your help.  I guess I will have to do a bit more spelunking now.  If I manage to figure out a solution, I will try to remember to post it back to this thread.

---

### Post by Quackers on 2011-10-11
Thank you, that would be beneficial to lots of others in the future.

---

### Post by csete on 2011-10-11
Reading about UEFI, I think my head may explode.  Does anyone have an idea how "stable" UEFI support is?  I'm reading a lot about building various binaries, which makes me wonder.

---

### Post by Quackers on 2011-10-11
It may be an idea to ensure that you are in fact using UEFI. I don't know how you should do that, but if you can confirm it in some way at least you are then researching something you know that you need, though it does seem likely that UEFI is in use.
If your system is not using UEFI we should look elsewhere for your booting problem.

---

### Post by csete on 2011-10-12
I can definitely see EFI messages in DMESG output.  So, it is there.  One thing I still want to try to do is see if I can "disable" it... and just use plain BIOS.  The other thing I'm planning to try is 11.10 to see if it "just works".  After that, I will have to actually start to understand how the pieces fit together for UEFI.

---

### Post by csete on 2011-10-12
After trying a number of different things from throughout the web, I'm currently at my wits end.  I have no idea what to do or how to fix my machine at this point.  The closest I got was the ArchLinux instructions, but failed with "cannot find a device for / (is /dev mounted?)" when trying to do the "grub-mkconfig -o /boot/efi/efi/grub/grub.cfg".

I honestly have no idea what I'm doing with all of this and I'm worried I've cratered this machine to the point I won't even be able to return it.  (I'm still hopeful the Firmware "recovery") function could get it back to factory defaults if necessary).  I like the machine, but I'm beginning to believe that UEFI and Ubuntu are not stable enough for a UEFI newbie like me to deal with.

Does anyone else have any thoughts on what I can try?  Any way to get this silly machine to boot into Linux?  Any help appreciated.

Does anyone know what a reasonable grub.cfg file might look like in this case?

Thanks,
Craig

---

### Post by oldfred on 2011-10-13
While your BIOS may have a UEFI mode, all the new UEFI have a BIOS mode. Your system does not show a efi partition so you must be in BIOS & MBR mode. Windows 7 has to have efi partition, Windows boot partition and be in gpt not MBR to use UEFI. 

Ubuntu/grub will boot from BIOS or UEFI. But dual booting with UEFI and grub have some issues that are difficult currently. But those do not seem to be your issues.

Your issues then may be more related to video or parameters in the grub menu that allow booting to continue. The newest i3, i5 & i7 systems need additional settings to work it seems, but I do not know all the details.

What video are you using? What is system specs?

---

### Post by csete on 2011-10-13
oldfred: thanks for jumping in to the conversation.  I can use all of the help I can get :-)

I've looked at the "BIOS" settings screen and I'm not seeing anything that would allow me UEFI versus BIOS mode settings.  How is that controlled?  

This is a new HP machine with a Core I3 processor, so perhaps some of the extra parameters you mentioned might be necessary?  Where would I find out more about that?

I've read that legacy GRUB is easier to deal with in this situation?  Is that supported in 11.04 or 11.10?  If so, how would I deal with it?

For reference, here is my partitions at the moment:

```

Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   fat16           boot
 2      106MB   53.8GB  53.7GB  primary   ntfs
 4      53.8GB  988GB   934GB   extended
 5      53.8GB  105GB   51.2GB  logical   ext4
 7      105GB   975GB   870GB   logical   ext4
 6      975GB   988GB   12.3GB  logical   linux-swap(v1)
 3      988GB   1000GB  12.5GB  primary   ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


```

I've split my root and home directories across the EXT4 partitions.  The smaller is the root partition.  The FAT16 partition is the EFI partition which I pointed the installer to use when trying to install.  Partition 2 is Windows 7 and partition 3 is the recovery partition.

Here is the output from efibootmgr:

```

** Warning ** : Boot000a is not EFI 1.10 compliant (lowercase hex in name)
** Warning ** : please recreate these using efibootmgr to remove this warning.
BootCurrent: 000A
Timeout: 0 seconds
BootOrder: 0000,0009,0003,000A,0001,0002,0004,0005,0006,0007
Boot0000* ubuntu	HD(1,800,32000,03e10800)File(\EFI\ubuntu\grubx64.efi)
Boot0001* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0002* USB Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot0003* ATAPI CD-ROM Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot0004* Unknown Device	BIOS(3,0,00)AMGOAMNOm.......+.h.p. . . . . . .D.V.D. .A. . .D.H.1.6.A.B.S.H.........................rN.D+..,.\.........AMBO
Boot0005* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot0006* Hard Drive	BIOS(2,0,00)AMGOAMNO].......+.S.A.M.S.U.N.G. .H.D.1.0.3.S.J.........................rN.D+..,.\.........AMBO
Boot0007* Realtek PXE B06 D00	BIOS(6,0,00)AMBO
Boot0009* GRUB2	HD(1,800,32000,4b6e0800)File(\EFI\grub\grub.efi)
Boot000a* UEFI: hp      DVD A  DH16ABSH	ACPI(a0341d0,0)PCI(1f,2)03120a000400ffff0000CD-ROM(1,56e3a,400)AMBO


```

Any insights that you could provide would be most appreciated.

Thanks,
Craig

---

### Post by oldfred on 2011-10-13
Your partition table is still MBR(msdos). Windows will only boot with UEFI and gpt partitions. So when installing Ubuntu did you use an UEFI mode and it put grub's files in the 100MB NTFS Windows hidden boot/recovery partition that is sda1 normally. It is now FAT16.

Your original boot script showed the standard MBR Windows install with the NTFS boot partition as sda1. That was MBR mode.

Not sure how system knows if BIOS or UEFI or if it just depends on if files are in a efi partition it uses them (UEFI), if not it boots from MBR (BIOS mode)??

I think you need to eliminate the FAT partition and restore the Windows boot/recovery 100MB boot/recovery. Do you have a backup of that? I understand in efi mode grub often just overwrites a windows efi loader and it is best for UEFI to install Ubuntu first then Windows (just the opposite of BIOS/MBR). Or you have to fully back up the Windows efi partition and copy the files back into the efi partition after grub. But you were not using efi in Windows, just the standard BIOS/MBR.

---

### Post by csete on 2011-10-13
I don't have a specific backup of that partition.  I do have the recovery option, which I assume (hope) would reset all of this?  I can run that since I don't have anything on this machine that I can't afford to lose at this point.  Does that seem like my best next step?  Assuming I can get back to a stable Windows 7 (only) boot, does it seem like I should be able to get this machine installed to use GRUB/Linux eventually?  My other option is to recover the machine and then just return it... but I do like the machine otherwise.

Thanks again,
Craig

---

### Post by oldfred on 2011-10-13
If it is the vendor recovery then it should restore system to as purchased. Some require you to erase the Linux partitions as it cannot see them and gets confused. Some use just DVDs you created and I believe some use DVD to get started and then use vendor partition.

There is also a Microsoft Windows repairCD. You can recreate the NTFS 100MB partition copy back the bootmgr and a BCD and repair the BCD to be yours. See your first boot script. Depending on what was overwritten testdisk may recover some or all of it also.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by csete on 2011-10-13
I think I want to get back to a completely "clean" install.  Here's what I'm thinking I will do:

Use gparted to remove all of the extra partitions that I created for Linux
Use gparted to resize the ntfs Win 7 partition back to the original full size
Use recovery to try to get back to an initial state

Assuming that works, I will backup all of the partitions that matter so I have a way back next time

Assuming I get back to a stable state for Win 7 booting, can I get some help to get things set up with Linux after that?

Thanks,
Craig

---

### Post by csete on 2011-10-13
The good news is that set of steps has the machine back to a point where it will boot Win 7 the way it did initially.  What information do I need to collect and post here that would help get me set up correctly to dual-boot this machine with 11.10?

Thanks,
Craig

---

### Post by oldfred on 2011-10-13
If you are not using and special Windows software that has DRM or a virus checker that thinks grub is a virus in the MBR, I would use grub2 as the boot loader. It offers to boot Window also.

I like to partition in advance as then I have control over sizes. Best to shrink Windows with Windows MMC, but only create partitions with gparted from the Ubuntu liveCD. I like smaller system partitions - both Windows & Ubuntu and larger partition(s) for data. If sharing with Windows a NTFS partition is a good shared data partition.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If all you data is in a shared NTFS you may not need a separate /home, but if not make the / (root) partition somewhat larger as some data may stay in Ubuntu.

I have not seen any examples with the new version yet. But the install process is the same with minor screen differences.
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by csete on 2011-10-13
Thanks.  I guess my primary concern is that I originally tried an 11.04 installation where I didn't do anything EFI specific and it ended up not booting.  That is what led me to thinking I needed to do EFI-specific things.  I can certainly take another run at it with a "standard" Ubuntu installation if that makes the most sense, but I'm just wondering if it will work?  Is there anything non-standard I would need to specify when going through the installer?

Thanks,
Craig

---

### Post by oldfred on 2011-10-13
In BIOS/MBR mode it is just like any dual boot boot with grub2. 

Someday you may want to try UEFI. But grub is not real good yet with UEFI on some systems. 

I just like having separate drives for each system as then it is cleaner.

---

### Post by csete on 2011-10-13
Any thoughts on what I might have done wrong the first time through?  I'd love to avoid making the same mistakes the second time around.

---

### Post by oldfred on 2011-10-13
From original boot script install looked fine. And the instructions you had to reinstall grub2's boot loader to the MBR seemed as the best solution. 

Do you have any thing locking MBR in BIOS? A few computers have that. Sometimes it just takes a reinstall or a full chroot.

Sometimes if system if installed correctly Supergrub bypasses MBR and boots a system so you can reinstall from inside the system.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)


You manual install Something else to reuse your existing partitions.

---

### Post by csete on 2011-10-14
Latest update...

I used MSFT MMC to shrink my Win 7 partition.  I then used gparted to create the partitions (root, home and swap).  I set the installer to install bootloader to /dev/sda.  When I rebooted the machine, I ended up booting to Win 7.  I tried to select each possible boot option from the "BIOS" screen (both UEFI options as well as "legacy") options and they all ended up booting into Windows 7.  I never get a GRUB prompt or anything else.

Any thoughts on what I can try next?  What information can I capture that would help make better sense of this?

Thanks again,
Craig

---

### Post by csete on 2011-10-14
Another question for the group.  Is there a way until I figure out the issues with booting on this system to boot the installed system via CD?  Is that what Super Grub 2 is all about?

---

### Post by csete on 2011-10-14
Supergrub 2 worked to boot into the system.  Still hopeful people can help me get it to boot correctly without Supergrub, but at least now I can start to set the machine up the way I want it.

Thanks yet again for all of the help thus far and into the future!
Craig

---

### Post by oldfred on 2011-10-14
If you are in system does either of these correctly install grub2's boot loader to the MBR?

sudo grub-install /dev/sda

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

A run of boot script will tell you if it installed without having to reboot.

---

### Post by csete on 2011-10-14
sudo grub-install /dev/sda

Says installation completed successfully, however I still boot to Win 7 automatically.

The other commands fail because grub-pc is not installed.  It appears that grub-efi is installed.  Is this a case that the installer is confused and picked EFI instead of BIOS and I should swap to grub-pc?

---

### Post by oldfred on 2011-10-14
Repost boot script. 

It may be just that, uninstall grub-efi and install grub-pc. But why did grub think efi was correct?

---

### Post by csete on 2011-10-14
I'm starting to feel a bit better... Don't think this is just me doing something stupid :-)  I did nothing different during the install that I would not have done for many installs over the past couple of years.  Something in the installer is assuming EFI.  The laptop I'm posting this on is a dual-boot Win 7 laptop and had no troubles at all and this install would have been nearly identical.

Here's the boot script output:

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

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

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

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   105,064,447   104,857,600   7 NTFS / exFAT / HPFS
/dev/sda3       1,929,029,632 1,953,521,663    24,492,032   7 NTFS / exFAT / HPFS
/dev/sda4         105,066,494 1,929,029,631 1,823,963,138   5 Extended
/dev/sda5         105,066,496   188,952,575    83,886,080  83 Linux
/dev/sda6         188,954,624 1,908,058,111 1,719,103,488  83 Linux
/dev/sda7       1,908,060,160 1,929,029,631    20,969,472  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        60885E87885E5C1A                       ntfs       SYSTEM
/dev/sda2        820C5F0D0C5EFB9B                       ntfs       OS
/dev/sda3        2E1215581215267D                       ntfs       HP_RECOVERY
/dev/sda5        cf4f55ab-b2a3-4616-8a06-f6a93f9a594d   ext4       
/dev/sda6        ff215029-0bd0-4a07-b8fb-ce43beb3db9b   ext4       
/dev/sda7        6a4a977f-2bdd-4f1d-953a-d37c18763bec   swap       swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root cf4f55ab-b2a3-4616-8a06-f6a93f9a594d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root cf4f55ab-b2a3-4616-8a06-f6a93f9a594d
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root cf4f55ab-b2a3-4616-8a06-f6a93f9a594d
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=cf4f55ab-b2a3-4616-8a06-f6a93f9a594d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root cf4f55ab-b2a3-4616-8a06-f6a93f9a594d
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=cf4f55ab-b2a3-4616-8a06-f6a93f9a594d ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root cf4f55ab-b2a3-4616-8a06-f6a93f9a594d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root cf4f55ab-b2a3-4616-8a06-f6a93f9a594d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 60885E87885E5C1A
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 820C5F0D0C5EFB9B
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 2E1215581215267D
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=cf4f55ab-b2a3-4616-8a06-f6a93f9a594d /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ff215029-0bd0-4a07-b8fb-ce43beb3db9b /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=6a4a977f-2bdd-4f1d-953a-d37c18763bec none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  52.284381866 = 56.139927552   boot/grub/grub.cfg                             1
  51.740234375 = 55.555653632   boot/initrd.img-3.0.0-12-generic               2
  66.356891632 = 71.250169856   boot/vmlinuz-3.0.0-12-generic                  1
  51.740234375 = 55.555653632   initrd.img                                     2
  66.356891632 = 71.250169856   vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 



```

---

### Post by oldfred on 2011-10-14
You have nothing in your system that looks like efi. No gpt partitioning, no efi boot partition at the beginning of the drive, just a standard Windows 7 100MB boot/recovery partition.

If somehow you have grub.efi you need to uninstall it and reinstall grub-pc and grub-common. Either use synaptic or run these commands. 

sudo -i
apt-get update
apt-get upgrade
apt-get purge grub-efi grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda

sudo dpkg-reconfigure grub-pc

---

### Post by csete on 2011-10-14
Success!

This last set of steps seems to have gotten me to the point of booting (via grub menu) into Ubuntu automatically. 

Now that it is working, the question is why does the installer think this is EFI?  Is there a launchpad issue I should provide more information on?  I'd like to avoid someone else having to deal with this later.

---

### Post by oldfred on 2011-10-14
I found these UEFI related bugs, but none of these are your issue. You should check to see if there is something else reported and if not report the issue.

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

---

### Post by csete on 2011-10-18
I (finally) opened a bug to track this... [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/877813](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/877813)

---

