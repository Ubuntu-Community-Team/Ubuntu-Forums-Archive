---
title: "Windows 7 loader line in Grub menu is selected but the menu screen turns back."
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by kd_dubai on 2011-10-30
The problem is that when the "Windows 7" loader line in Grub menu is selected the screen(menu) turns black and again shows the Grub menu.
below is the sequence of steps produced this issue.

1.> in new netbook i could see only 2 drives, one for OS another D: where drivers was copied so i shrink C: drive but in disk management console it was already showing 4 drive so i was not able to use unallocated space achieved after shrink. restarted system, **Win7 was working fine.**

2.> Downloaded Ubuntu, extracted iso in USB. restarted system from **USB flash**, started installation.
selected customs kind of installation, where i formated unallocated partition(which was achieved after shrink C:). created / and swap partition. after installation and restarting machine, system directly went into Win7 (could not recognize Ubuntu). note-> **was able to login to Win7**. 
 
3.> Again i restarted the system, booted from USB, deleted the created partition , created again but **selected Win7 Loader partition to install Ubuntu** [as i was thinking may be on same place both OS can fix  boot menu to come :( ]

4.> After installation finished,restarted the system, **THIS time i got boot screen to choose** (attached). happily login to Ubuntu and started using but then i thought lets see how is Win7. i restated machine and selected Win7 from the boot BUT **what i see the menu comes again and again. **
Finally i realize i lost Win7 :(. 
just for your information, i dont have Windows 7 starter OS installation disk(which came with my netbook). 

I went through forums since couple of hours and got some similar kind of thread but my scenario was bit different so finally i started this thread. i have executed bootinfo script (output attached).

Thanks,
KD

---

### Post by Mark Phelps on 2011-10-31
Pasted your results in line using Code tags -- since text file is really hard to read:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 539407656 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943919 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       411,647       409,600   7 NTFS / exFAT / HPFS
/dev/sda2             411,648   288,026,623   287,614,976   7 NTFS / exFAT / HPFS
/dev/sda3         288,028,670   594,198,527   306,169,858   f W95 Extended (LBA)
/dev/sda5         288,028,672   530,739,199   242,710,528   b W95 FAT32
/dev/sda6         585,428,992   594,198,527     8,769,536  82 Linux swap / Solaris
/dev/sda7         530,741,248   585,422,847    54,681,600  83 Linux
/dev/sda4         594,198,528   625,142,447    30,943,920  12 Compaq diagnostics


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        B8F6C1E3F6C1A1CC                       ntfs       
/dev/sda2        FE42C07642C03565                       ntfs       OS
/dev/sda4        C2B230F2B230ED13                       ntfs       LENOVO_PART
/dev/sda5        4CF7-9364                              vfat       MYDATA
/dev/sda6        7fc49b40-4c9d-4e62-b5c0-5f6ac39477b3   swap       
/dev/sda7        6ddc3d74-59bc-41f8-9a47-6a475ba28bb5   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 6ddc3d74-59bc-41f8-9a47-6a475ba28bb5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root 6ddc3d74-59bc-41f8-9a47-6a475ba28bb5
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 6ddc3d74-59bc-41f8-9a47-6a475ba28bb5
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=6ddc3d74-59bc-41f8-9a47-6a475ba28bb5 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 6ddc3d74-59bc-41f8-9a47-6a475ba28bb5
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=6ddc3d74-59bc-41f8-9a47-6a475ba28bb5 ro recovery nomodeset 
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
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 6ddc3d74-59bc-41f8-9a47-6a475ba28bb5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set=root 6ddc3d74-59bc-41f8-9a47-6a475ba28bb5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root B8F6C1E3F6C1A1CC
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root C2B230F2B230ED13
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=6ddc3d74-59bc-41f8-9a47-6a475ba28bb5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7fc49b40-4c9d-4e62-b5c0-5f6ac39477b3 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     1
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

### Post by Mark Phelps on 2011-10-31
Before you panic (more on this later) you need to confirm that Win7 is actually GONE.

If you're using 11.04 or 11.10 (if NOT, you should have told us WHAT you're using), then click on the Home icon in the Launcher.  That will open a window showing a list of partitions.  Click on each and see what is in there.  You originally had two partitions containing Win7 stuff: the first was the boot loader, the second was the OS with the other files.

IF the first is empty, that can be fixed -- but it will involve a lot of work on your part.  If the second is empty, Win7 is GONE -- and NOW, you can panic.  To restore in the second situation, you would have to check the documentation that came with your netbook to see what key sequence you need to press to do a Factory Restore.  Even then, since you messed around with your partitions, that might not work. You would then have to REMOVE the Ubuntu partitions and see if Factory Restore then works.  If it still does not work, you will have to contact the netbook supplier and see if you can purchase Full Restore Media from them.

---

### Post by Quackers on 2011-10-31
Good advice from Mark Phelps above.
It's not clear to me what has happened. There appear to be some anomalies.
According to the output of the boot script Grub is not installed to the mbr of the hard drive, yet you are getting a grub menu. 
Grub appears to have been installed to the sda1 partition, which now has a Boot Sector type of Grub. See below. This is almost certainly what is stopping Windows from booting. Windows doesn't like it's boot sector messed with.
It may be an option to repair the Windows boot sector with a Windows 7 repair disc. If you don't have one then you should do! It may be possible to download one. You can then boot from that disc and repair the mbr of the drive.
This will hopefully get Windows booting again.

```

============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    [COLOR="Red"]Boot sector type:  Grub2 (v1.99)[/COLOR]
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 539407656 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

```

---

### Post by fantab on 2011-10-31
> **kd_dubai said:**
> The problem is that when the "Windows 7" loader line in Grub menu is selected the screen(menu) turns black and again shows the Grub menu.
below is the sequence of steps produced this issue.

1.> in new netbook i could see only 2 drives, one for OS another D: where drivers was copied so i shrink C: drive but in disk management console it was already showing 4 drive so i was not able to use unallocated space achieved after shrink. restarted system, **Win7 was working fine.**

2.> Downloaded Ubuntu, extracted iso in USB. restarted system from **USB flash**, started installation.
selected customs kind of installation, where i formated unallocated partition(which was achieved after shrink C:). created / and swap partition. after installation and restarting machine, system directly went into Win7 (could not recognize Ubuntu). note-> **was able to login to Win7**. 
 
[COLOR=Red]3.> Again i restarted the system, booted from USB, deleted the created partition , created again but **selected Win7 Loader partition to install Ubuntu** [as i was thinking may be on same place both OS can fix  boot menu to come :( ]
[/COLOR] 
4.> After installation finished,restarted the system, **THIS time i got boot screen to choose** (attached). happily login to Ubuntu and started using but then i thought lets see how is Win7. i restated machine and selected Win7 from the boot BUT **what i see the menu comes again and again. **
Finally i realize i lost Win7 :(. 
just for your information, i dont have Windows 7 starter OS installation disk(which came with my netbook). 

I went through forums since couple of hours and got some similar kind of thread but my scenario was bit different so finally i started this thread. i have executed bootinfo script (output attached).

Thanks,
KD

GRUB Boot Loader, in your case, MUST be installed on /dev/sda. 

You may have to re-install Ubuntu and Fix Windows MBR.

Follow these steps:

[LIST=1]
[*]If you can go to **Windows Recovery** directly, without Grub, then follow the steps below. (If you can't then From Grub choose **Windows Recovery** Environment. If this doesn't work either then get a Windows Recovery Disk or contact your Netbook service.)
[*]Once with Windows Recovery select your language etc.
[*]Select **Repair your Computer**
[*]In the System Recovery Options choose **Command Prompt** and run following command:   ***Bootrec.exe /fixmbr.***
[*]Restart your computer it should boot to Windows directly.
[*]this should fix your windows Mbr, if it doesn't then try this: ***Bootrec.exe /fixboot  ***and restart****
[*]Reinstall Ubuntu and Install GRUB on /dev/sda.
[/LIST]
hope this will help....

---

