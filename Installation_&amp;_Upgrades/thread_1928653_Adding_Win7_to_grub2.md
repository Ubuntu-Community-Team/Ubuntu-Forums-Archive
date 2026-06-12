---
title: "Adding Win7 to grub2"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by WheelDawg on 2012-02-20
Need help getting an entry for Win7 in the grub loader.

Just reformatted yesterday to fix some Windows issues (we've all been there, right? heh heh)

I figured that while I was in the nerd zone, I might as well install Ubuntu again, haven't tried it out since Edgy.

Got Win7 installed, all is well, and Ubuntu 11.10 is installed on the same physical drive on a 2nd partition.

Grub has taken over and left me with no entry to boot Win7 from, and using the Windows installation disk to Repair Startup didn't help. For a while I couldn't get a grub menu either, it would boot straight into Ubuntu, but I've got that back.

So what I would like to end up with is a simple grub list, with Win7 as the default choice, then Ubuntu underneath that, and no memtest entries.

I used the boot info script since I knew it would help in diagnosing exactly what kind of entry I will need. 

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *         16,065   976,768,064   976,752,000   f W95 Extended (LBA)
/dev/sda5              16,128   976,768,064   976,751,937   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *    491,364,352   625,141,759   133,777,408  83 Linux
/dev/sdb2               2,048   491,364,351   491,362,304   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda5        137D51441DEB1C79                       ntfs       Installs and Docs
/dev/sdb1        28c33afe-78aa-49eb-9aed-f1fe74df8ffb   ext4       
/dev/sdb2        5E5676E55676BD79                       ntfs       Win7
/dev/sdc1        7C203D78203D3A8A                       ntfs       FreeAgent Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 28c33afe-78aa-49eb-9aed-f1fe74df8ffb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root 28c33afe-78aa-49eb-9aed-f1fe74df8ffb
  set locale_dir=($root)/boot/grub/locale
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 28c33afe-78aa-49eb-9aed-f1fe74df8ffb
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=28c33afe-78aa-49eb-9aed-f1fe74df8ffb ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 28c33afe-78aa-49eb-9aed-f1fe74df8ffb
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=28c33afe-78aa-49eb-9aed-f1fe74df8ffb ro recovery nomodeset 
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 28c33afe-78aa-49eb-9aed-f1fe74df8ffb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 28c33afe-78aa-49eb-9aed-f1fe74df8ffb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
fi
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=28c33afe-78aa-49eb-9aed-f1fe74df8ffb /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 278.451416016 = 298.984931328  boot/grub/core.img                             1
 266.427803040 = 286.074675200  boot/grub/grub.cfg                             1
 235.944774628 = 253.343772672  boot/initrd.img-3.0.0-12-generic               2
 236.433784485 = 253.868843008  boot/vmlinuz-3.0.0-12-generic                  1
 235.944774628 = 253.343772672  initrd.img                                     2
 236.433784485 = 253.868843008  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

I've looked at a few examples of what I would need to add, but I've seen everything from
```
menuentry 'Windows 7' {
set root='(hd1,msdos2)
chainloader +1
}
``` to
```
#! /bin/sh -e
echo Adding Windows >&2
cat << EOF
menuentry "Windows 7&#8243; {
    set root='(hd1,mdsos1)'
    chainloader +1
}
``` and I don't know why those look different.

Also, when trying to run sudo update-grub2, it "finds" a linux and an initrd image, and then just hangs there and will not finish updating the /boot/grub/grub/cfg

---

### Post by dubsides on 2012-02-20
Think you should be using sudo update-grub, not "grub2" (even though it is grub2).

here's a good place to read up:  

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by darkod on 2012-02-20
You have no win7 boot files. With win7 they usually come on small partition that says System Reserved. You probably deleted it.

Since there are no boot files to detect, grub doesn't create win7 entry. I also notice you installed ubuntu without a swap partition but it can function without it.

What I would do:
1. Disconnect the other two 500GB disks temporarily.
2. Boot your ubuntu or boot the cd in live mode, open Gparted and set the boot flag on the partition #2 of your 320GB disk. That is the win7 partition and needs to have the boot flag on it.
3. Boot with the win7 dvd and run the repair 3-4 times (windows sometimes fixes one thing at a time so you need to run it more than once). That should repair the boot files and write windows bootloader on the MBR.
4. Once win7 boots fine, reinstall grub2 to the MBR. Boot ubuntu and run sudo update-grub again. It should detect win7 now.
5. Connect the disks you disconnected.

---

### Post by WheelDawg on 2012-02-20
> **darkod said:**
> You have no win7 boot files. With win7 they usually come on small partition that says System Reserved. You probably deleted it.

Since there are no boot files to detect, grub doesn't create win7 entry. I also notice you installed ubuntu without a swap partition but it can function without it. 

It didn't "come" with any partitions as it wasn't a prebuilt system. I built this rig and installed Win7 myself.

As for the swap partition, I figured it was unnecessary as I don't plan on Ubuntu being a main OS, I just wanted it around to be somewhat familiar with it for kicks.

Trying your suggestions now.

---

### Post by WheelDawg on 2012-02-20
Have run System Repair 5 times in a row, the log it produced said it was fixing the same thing each time, saying there was no valid system partition there.

The initial screen where you pick which drive you want to attempt  repair options or to do a system restore on was also blank. It let me leave it blank and go on to pick startup repair, but it not being listed doesn't seem right to me.

So unless there's some console magic to work, my next guess is having to reinstall Win7 again to get its boot files back.

---

### Post by darkod on 2012-02-20
> **WheelDawg said:**
> It didn't "come" with any partitions as it wasn't a prebuilt system. I built this rig and installed Win7 myself.

As for the swap partition, I figured it was unnecessary as I don't plan on Ubuntu being a main OS, I just wanted it around to be somewhat familiar with it for kicks.

Trying your suggestions now.

Another "feature" MS added to win7 install: When you create the win7 partition during the install process (unless it exists in advance) it chops off a 100MB or 200MB and it creates the system partition with boot files. This partition is not displayed in Computer, you will never see it there. But if you open Disk Management it will be there.

Win7 is sometimes a pain to restore the boot files because it expects the system partition to be there again. But it's not impossible from what I have seen.

Hold on a sec, let me try to find a link with manual commands. If not, the last option is new install.

---

### Post by darkod on 2012-02-20
Look here in post #1 in the section titled How to restore Windows Vista or 7 bootloader.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It has the command line option and how to run the commands. If that doesn't work, you know what to do. :)

---

### Post by ottosykora on 2012-02-20
> **darkod said:**
> Another "feature" MS added to win7 install: When you create the win7 partition during the install process (unless it exists in advance) it chops off a 100MB or 200MB and it creates the system partition with boot files. .

just as info

yes, as you say, if the target partition is created in advance manually and installation of w7 is simply directed to settle there, it will do so and not create any further boot partition. I have it so on one of my 'big' installs.

But beware!
when w7 does not find itself with 2 partitions, that means a separate boot or they call it system partition, it will never be possible to install any service packs to it! Ordinary updates will work, but no service packs at all.
Unfortunate, but authors of w7 decided to have it so...

---

### Post by darkod on 2012-02-20
> **ottosykora said:**
> just as info

yes, as you say, if the target partition is created in advance manually and installation of w7 is simply directed to settle there, it will do so and not create any further boot partition. I have it so on one of my 'big' installs.

But beware!
when w7 does not find itself with 2 partitions, that means a separate boot or they call it system partition, it will never be possible to install any service packs to it! Ordinary updates will work, but no service packs at all.
Unfortunate, but authors of w7 decided to have it so...

Not to drag the thread away... I have never heard of this. Plus, I am pretyy sure I have my work laptop installed with single partition and I have installed SP1 on it.

---

