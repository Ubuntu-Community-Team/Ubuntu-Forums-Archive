---
title: "Failure running wubi-move-2.2 on an Ubuntu 10.04"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by Jonathan Lennox on 2012-07-20
I have an Ubuntu 10.04 Wubi installation which I am trying to migrate onto a native partition.

Unfortunately, the script fails when trying to uninstall the lupin-support package, as follows:

wubi-move-2.2.sh:  Starting chroot to the target install.
wubi-move-2.2.sh:  Removing lupin-support on target...
wubi-move-2.2.sh:  An error occurred within chroot
wubi-move-2.2.sh:  Error is: /dev/loop0 does not have any corresponding BIOS drive.
wubi-move-2.2.sh:  Attempting to exit chroot normally...
wubi-move-2.2.sh:  Exiting from chroot on target install...

wubi-move-2.2.sh:  Migration did not complete successfully.

This is on an x86_64 platform (a Dell Optiplex desktop machine).  The machine was originally Ubuntu 9.10 (I believe), and was upgraded at some point to 10.04 inside the Wubi install.

Does anyone have any idea of what's wrong?  Is there any good way to fix it?  I don't mind restarting the wubi-move from scratch if necessary (and redoing the rsync step), though I'd obviously rather not.

My suspicion would be that the problem has something to do with grub2 vs. grub-legacy, but I could be wrong, and I can't figure out what the correct fix would be.

Thanks for any help!


Here is the full output of the wubi-move script:

$ sudo bash ./wubi-move-2.2.sh /dev/sda5 /dev/sda6
wubi-move-2.2.sh:  Validating migration source...
wubi-move-2.2.sh:  Source for migration validated successfully:
wubi-move-2.2.sh:    Wubi host partition: /dev/sda3
wubi-move-2.2.sh:    Size of install: 66536920 K
wubi-move-2.2.sh:    Size of /boot: 213176 K
wubi-move-2.2.sh:    Size of /usr: 5869712 K
wubi-move-2.2.sh:    Size of /home: 57940764 K
wubi-move-2.2.sh:  Validating migration target(s)...
wubi-move-2.2.sh:  Target(s) for migration validated successfully:
wubi-move-2.2.sh:    Size of / partition: 723076144 K
wubi-move-2.2.sh:    Swap partition validated
wubi-move-2.2.sh:  Target partition size is sufficient
wubi-move-2.2.sh:  Grub (legacy) is installed - this will be replaced
wubi-move-2.2.sh:  with Grub2 (only on the migrated install).

wubi-move-2.2.sh:  Grub2 will be installed to /dev/sda

wubi-move-2.2.sh:  Please close all open files before continuing.
wubi-move-2.2.sh:  About to format the target partition (/dev/sda5).
wubi-move-2.2.sh:  Proceed with format (Y/N)
y
wubi-move-2.2.sh:  Formatting /dev/sda5 with ext3 file system

wubi-move-2.2.sh:  Copying files - please be patient - this takes some time
wubi-move-2.2.sh:  Copying from / (root)
wubi-move-2.2.sh:  Copying from /usr
wubi-move-2.2.sh:  Copying from /boot
wubi-move-2.2.sh:  Copying from /home
wubi-move-2.2.sh:  Copying completed
wubi-move-2.2.sh:  Creating swap...

wubi-move-2.2.sh:  Starting chroot to the target install.
wubi-move-2.2.sh:  Removing lupin-support on target...
wubi-move-2.2.sh:  An error occurred within chroot
wubi-move-2.2.sh:  Error is: /dev/loop0 does not have any corresponding BIOS drive.
wubi-move-2.2.sh:  Attempting to exit chroot normally...
wubi-move-2.2.sh:  Exiting from chroot on target install...

wubi-move-2.2.sh:  Migration did not complete successfully.

---

### Post by bcbc on 2012-07-20
This could be the result of changes to grub. All Wubi installs have /dev/loop0 as the target drive (to prevent updates to the disk MBR that prevent booting, so it's strange it would complain about that). 

I'll have to run some tests to confirm what the problem is. I'll let you know what I find...

---

### Post by bcbc on 2012-07-21
I've duplicated the problem and found the bug in the wubi-move script. It affects wubi installs with grub-legacy only (i.e. original install prior to release 9.10).

I'm patching it and testing it now.

---

### Post by bcbc on 2012-07-21
Okay... fixed, tested... and attached. 

Download and extract wubi-move-2.2.sh and replace the version you have. 

Then rerun it with the --resume option. It will pick up from where it left off so all that remains to be done is replace grub-legacy with grub2 on the migrated install and install the bootloader. I reran mine with --resume and confirmed everything was good.

So for your example you would submit:
```
sudo bash wubi-move-2.2.sh /dev/sda5 /dev/sda6 --resume
```

---

### Post by Jonathan Lennox on 2012-07-21
Thanks!  I won't be able to test it until Monday (server is at my office), but I'll try it out it then.

It does indeed seem possible that the Wubi installation was originally 9.04.

Would an alternate solution be to upgrade my Wubi installation to use  grub2, if that's possible?  I noticed that another consequence of having  grub-legacy installed in Wubi was that the native partition was  formatted as ext3, even though my Wubi is using ext4 natively.   (Obviously changing the partition format would mean that I'd need to re-run the rsync.)

---

### Post by bcbc on 2012-07-21
I've never attempted to manually convert a wubi install from grub legacy to grub2. I'm not sure what the benefit of this would be. It's obviously worked pretty well if you've had it since release 9.04.

It's far better to switch to a normal dual boot as you are doing.

Regarding the ext3/4, the migration script will migrate to an ext3 partition by default if the source is Wubi with grub-legacy. I believed that this would be the preferred choice. There's no reason it couldn't migrate to an ext4 partition if that's your preference. But there is no 'automatic' option built into the script for this. You could just edit it yourself (line 550):
```
        # grub legacy wubi is always ext3
        if [ "$wubi_install" = "true" ]; then
          **fs=ext3**
        fi

```
Change to:
```
        # grub legacy wubi is always ext3
        if [ "$wubi_install" = "true" ]; then
          **fs=ext4**
        fi

```

Yes, you are correct... if you choose to do this you'll have to start the migration from scratch (don't use the --resume option). This means you'll have to manually clear the target partition (the script requires an empty partition for safety). The safest way to achieve this is to format it using GParted.

---

### Post by Jonathan Lennox on 2012-07-23
Thanks -- that worked great!  I now have Ubuntu 10.04 installed on a native partition.

The system seems **much** snappier now.  I hadn't realized how much  performance overhead there was in going through Wubi's NTFS layer.

---

### Post by bcbc on 2012-07-23
Glad to hear. You're welcome.

---

### Post by darrel12 on 2012-09-18
Hi, I got the same issue as Johnathan Lennox above.
However upon resuming, I got this:
```
wubi-move-2.2.sh:  Validating migration source...
wubi-move-2.2.sh:  Source for migration validated successfully:
wubi-move-2.2.sh:    Wubi host partition: /dev/sda2
wubi-move-2.2.sh:    Size of install: 11909601 K
wubi-move-2.2.sh:    Size of /boot: 97440 K
wubi-move-2.2.sh:    Size of /usr: 2573997 K
wubi-move-2.2.sh:    Size of /home: 7593671 K
wubi-move-2.2.sh:  Validating migration target(s)...
wubi-move-2.2.sh:  Target(s) for migration validated successfully:
wubi-move-2.2.sh:    Size of / partition: 114759248 K
wubi-move-2.2.sh:    Swap partition validated
wubi-move-2.2.sh:  Validating --resume option
wubi-move-2.2.sh:  The UUID on swap partition /dev/sda4 has changed
wubi-move-2.2.sh:  The target partitions cannot be changed
wubi-move-2.2.sh:  when using the --resume option

wubi-move-2.2.sh:  Migration did not complete successfully.

```

---

### Post by bcbc on 2012-09-18
Darrel,

The --resume option is pretty fussy and here's the reason why:
1. It bypasses the normal checks to ensure the partition is empty
2. It will modify existing files to what you are migrating (removing anything else)

While technically I could have ignored the swap partition since there's no data risk, I didn't. So in your case it's found that the UUID of the swap partition has been modified since you first ran the migration and won't continue. Did you modify this?


So... being hard-nosed about the check seemed like a good idea at the time. But it leaves you with having to reformat your target partition and start all over again which is a bit of a pain. If you are sure you know what you are doing you can edit the file: ~/.wubi-move 
Change the second string to the UUID of the swap partition.

---

### Post by darrel12 on 2012-09-19
> **bcbc said:**
> Darrel,

The --resume option is pretty fussy and here's the reason why:
1. It bypasses the normal checks to ensure the partition is empty
2. It will modify existing files to what you are migrating (removing anything else)

While technically I could have ignored the swap partition since there's no data risk, I didn't. So in your case it's found that the UUID of the swap partition has been modified since you first ran the migration and won't continue. Did you modify this?


So... being hard-nosed about the check seemed like a good idea at the time. But it leaves you with having to reformat your target partition and start all over again which is a bit of a pain. If you are sure you know what you are doing you can edit the file: ~/.wubi-move 
Change the second string to the UUID of the swap partition.

Awesome! it worked great. Now that it is on it's own partition do i need to make that drive my booting drive with fdisk? Or do i just boot into my windows installation and uninstall my wubi, and then load up? or? 

sorry for the lack of experience.

---

### Post by bcbc on 2012-09-19
> **darrel12 said:**
> Awesome! it worked great. Now that it is on it's own partition do i need to make that drive my booting drive with fdisk? Or do i just boot into my windows installation and uninstall my wubi, and then load up? or? 

sorry for the lack of experience.

It depends. If you let the script install the Grub2 bootloader (default), then you're good to uninstall the Wubi. There's no need to change the boot partition flag (it has no affect on Grub and it will cause you problems if you try to reinstall the windows bootloader later).

But if you ran the script with the --no-bootloader option then you can only boot the migrated install via the Wubi grub, so don't uninstall Wubi until you've installed grub.

If you aren't sure, run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the result.

---

### Post by darrel12 on 2012-09-19
I can't access my Windows installation now that I've restarted. The grub only shows linux, previous versions of linux (because i have different kernels from an earlier issue with my wireless card, and grub customizer didn't delete them i suppose), and my recovery partition for windows.

I also notced in GParted that the key icon is no longer on my ntfs partition, but rather my ext3 and swap.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    52,430,847    52,428,800  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     52,430,848 1,219,387,119 1,166,956,272   7 NTFS / exFAT / HPFS
/dev/sda3       1,219,387,392 1,452,566,527   233,179,136  83 Linux
/dev/sda4       1,452,566,528 1,465,147,391    12,580,864  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4C8B-2392                              vfat       RECOVERY
/dev/sda2        BC008F1B008EDBB0                       ntfs       OS
/dev/sda3        c43c8d74-b78b-4385-a5e1-a02b2aa29b51   ext3       
/dev/sda4        4991dbb0-fb08-42a5-94a6-af0052e4154d   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root BC008F1B008EDBB0
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root BC008F1B008EDBB0
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin_proxy ###
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
menuentry "Ubuntu, with Linux 3.2.0-30-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root BC008F1B008EDBB0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.2.0-30-generic root=UUID=BC008F1B008EDBB0 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.2.0-30-generic
}
menuentry "Ubuntu, with Linux 3.2.0-30-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root BC008F1B008EDBB0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.2.0-30-generic ...'
    linux    /boot/vmlinuz-3.2.0-30-generic root=UUID=BC008F1B008EDBB0 loop=/ubuntu/disks/root.disk ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-30-generic
}
### END /etc/grub.d/10_lupin_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
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

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
--------------------------------------------------------------------------------

==================== sda2/Wubi/boot/extlinux/extlinux.conf: ====================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-02063808-generic       75
               =                boot/initrd.img-2.6.38-020638-generic         55
               =                boot/initrd.img-3.2.0-29-generic              59
               =                boot/initrd.img-3.2.0-30-generic              68
               =                boot/vmlinuz                                  26
               =                boot/vmlinuz-2.6.38-02063808-generic          22
               =                boot/vmlinuz-2.6.38-020638-generic            22
               =                boot/vmlinuz-3.2.0-29-generic                 20
               =                boot/vmlinuz-3.2.0-30-generic                 21
               =                initrd.img                                     5
               =                initrd.img.old                                 6
               =                vmlinuz                                       22
               =                vmlinuz.old                                   21

=============== sda2/Wubi: Location of files loaded by Syslinux: ===============

           GiB - GB             File                                 Fragment(s)

               =                boot/extlinux/chain.c32                        3
               =                boot/extlinux/extlinux.conf                    1

============ sda2/Wubi: Version of COM32(R) files used by Syslinux: ============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
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
menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    linux    /boot/vmlinuz-3.2.0-30-generic root=UUID=c43c8d74-b78b-4385-a5e1-a02b2aa29b51 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-30-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    echo    'Loading Linux 3.2.0-30-generic ...'
    linux    /boot/vmlinuz-3.2.0-30-generic root=UUID=c43c8d74-b78b-4385-a5e1-a02b2aa29b51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-30-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=c43c8d74-b78b-4385-a5e1-a02b2aa29b51 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=c43c8d74-b78b-4385-a5e1-a02b2aa29b51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-02063808-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    linux    /boot/vmlinuz-2.6.38-02063808-generic root=UUID=c43c8d74-b78b-4385-a5e1-a02b2aa29b51 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-2.6.38-02063808-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-02063808-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    echo    'Loading Linux 2.6.38-02063808-generic ...'
    linux    /boot/vmlinuz-2.6.38-02063808-generic root=UUID=c43c8d74-b78b-4385-a5e1-a02b2aa29b51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-02063808-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-020638-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    linux    /boot/vmlinuz-2.6.38-020638-generic root=UUID=c43c8d74-b78b-4385-a5e1-a02b2aa29b51 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-2.6.38-020638-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-020638-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    echo    'Loading Linux 2.6.38-020638-generic ...'
    linux    /boot/vmlinuz-2.6.38-020638-generic root=UUID=c43c8d74-b78b-4385-a5e1-a02b2aa29b51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-020638-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin_proxy ###
### END /etc/grub.d/10_lupin_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root c43c8d74-b78b-4385-a5e1-a02b2aa29b51
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 4C8B-2392
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
# root was on /dev/sda3 when migrated
UUID=c43c8d74-b78b-4385-a5e1-a02b2aa29b51    /    ext3    errors=remount-ro    0    1
# swap was on /dev/sda4 when migrated
UUID=4991dbb0-fb08-42a5-94a6-af0052e4154d    none    swap    sw    0    0
--------------------------------------------------------------------------------

====================== sda3/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-02063808-generic        5
               =                boot/initrd.img-2.6.38-020638-generic          5
               =                boot/initrd.img-3.2.0-29-generic               5
               =                boot/initrd.img-3.2.0-30-generic               6
               =                boot/vmlinuz                                   3
               =                boot/vmlinuz-2.6.38-02063808-generic           3
               =                boot/vmlinuz-2.6.38-020638-generic             3
               =                boot/vmlinuz-3.2.0-29-generic                  3
               =                boot/vmlinuz-3.2.0-30-generic                  3
               =                initrd.img                                     5
               =                initrd.img.old                                 6
               =                vmlinuz                                        3
               =                vmlinuz.old                                    3

================= sda3: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

               =                boot/extlinux/chain.c32                        1
               =                boot/extlinux/extlinux.conf                    1

============== sda3: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
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

### Post by bcbc on 2012-09-19
> **darrel12 said:**
> I can't access my Windows installation now that I've restarted. The grub only shows linux, previous versions of linux (because i have different kernels from an earlier issue with my wireless card, and grub customizer didn't delete them i suppose), and my recovery partition for windows.

I also notced in GParted that the key icon is no longer on my ntfs partition, but rather my ext3 and swap.



The key icon just shows which partition is in use. I'm not sure why grub can't find your Windows on /dev/sda2. It should. Try running:
```
sudo update-grub
```

PS in answer to your original questions, yes (once you get Windows into Grub and booting), you can uninstall the Wubi install.

---

### Post by darrel12 on 2012-09-22
> **bcbc said:**
> The key icon just shows which partition is in use. I'm not sure why grub can't find your Windows on /dev/sda2. It should. Try running:
```
sudo update-grub
```PS in answer to your original questions, yes (once you get Windows into Grub and booting), you can uninstall the Wubi install.

Thank you very much.
Everything is working flawlessly now.

---

### Post by bcbc on 2012-09-22
> **darrel12 said:**
> Thank you very much.
Everything is working flawlessly now.

Great! Thanks for the feedback.

---

