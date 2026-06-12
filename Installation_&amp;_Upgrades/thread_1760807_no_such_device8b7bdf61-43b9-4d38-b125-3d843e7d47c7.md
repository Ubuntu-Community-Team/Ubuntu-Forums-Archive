---
title: "no such device:8b7bdf61-43b9-4d38-b125-3d843e7d47c7"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by ubuntienewb on 2011-05-17
after a graphics card driver "issue" had to reinstall OS and got this
 
no such device:8b7bdf61-43b9-4d38-b125-3d843e7d47c7
grub rescue
 
tried reinstall several times, including using bootcd to run OS and removing all drive partitions etc still nothing.
 
any ideas?

---

### Post by drs305 on 2011-05-17
Grub2 is not finding it's configuration files. Please provide a copy of RESULTS.txt. It shows us the status of your boot files and other system information which allow us to give you specific recommendations.

Click [_this link_]("http://bootinfoscript.sourceforge.net"). It will take you to the Boot Info Script web page. Download and run the script. There are additional instructions by *louieb* in a link on the left side of that page.

To post the contents of RESULTS.txt for us to review, open a new post. Next click on the **#** icon in the post's menu bar. This will generate [noparse]```
 
```[/noparse] tags. Copy the contents of RESULTS.txt and paste between the code tags. Pasting between 'code' tags helps with formatting and viewing.

RESULTS.txt shows us the status of your boot files and other system information which allow us to give you specific recommendations.

---

### Post by ubuntienewb on 2011-05-17
k one sec

---

### Post by ubuntienewb on 2011-05-17
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 8b7bdf61-43b9-4d38-b125-3d843e7d47c7 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   295,804,927   295,802,880  83 Linux
/dev/sda2         295,806,974   312,580,095    16,773,122   5 Extended
/dev/sda5         295,806,976   312,580,095    16,773,120  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   398,283,479   398,283,417   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9ff82fe9-d554-4cf9-8e82-e562c2861bfb   ext4       
/dev/sda5        e59f855e-cae8-42cb-a556-15b059533293   swap       
/dev/sdb1        1752F59B3A4922B5                       ntfs       IDE Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9ff82fe9-d554-4cf9-8e82-e562c2861bfb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 9ff82fe9-d554-4cf9-8e82-e562c2861bfb
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9ff82fe9-d554-4cf9-8e82-e562c2861bfb
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9ff82fe9-d554-4cf9-8e82-e562c2861bfb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9ff82fe9-d554-4cf9-8e82-e562c2861bfb
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9ff82fe9-d554-4cf9-8e82-e562c2861bfb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9ff82fe9-d554-4cf9-8e82-e562c2861bfb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9ff82fe9-d554-4cf9-8e82-e562c2861bfb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
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
UUID=9ff82fe9-d554-4cf9-8e82-e562c2861bfb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e59f855e-cae8-42cb-a556-15b059533293 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  94.135513306 = 101.077237760  boot/grub/core.img                             1
  94.135520935 = 101.077245952  boot/grub/grub.cfg                             1
   1.428127289 = 1.533440000    boot/initrd.img-2.6.38-8-generic               2
  94.133792877 = 101.075390464  boot/vmlinuz-2.6.38-8-generic                  1
   1.428127289 = 1.533440000    initrd.img                                     2
  94.133792877 = 101.075390464  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by drs305 on 2011-05-17
ubuntienewb,

Sorry for the delay. 've been playing with this for the past 55 minutes.

The problem is shown in the first part of the results. It's the only place in RESULTS.txt that the UUID appears:
>     ---------------------------------------------------------------------------
    **search.fs_uuid 8b7bdf61-43b9-4d38-b125-3d843e7d47c7 root **
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

The problematic UUID is displayed in the search line. What I have been trying to do is find the way to get rid of it. 

DISCLAIMER: There is probably a very simple grub command that will fix this issue, I just don't know what it is. Someone else may know, so check other responses before taking the time to wade through the rest of this post.

Uninstalling/reinstalling grub-pc didn't do it, nor did uninstalling grub-common, nor running *dpkg-reconfigure grub-pc*. It also wasn't in device.map. The only way I initially found to remove it was to write TESTDISK to the MBRs of both drives. If I removed G2 from only one drive it did not disappear.

Anyway, what I finally discovered is that when G2 is installed to multiple drives, a file called "load.cfg" is generated in /boot/grub. I imagine this file contains the erroneous UUID.

Possible solutions, from easiest:
[LIST]
[*]Make sure BIOS is booting from the Ubuntu drive (sda).
[*]Change the UUID in /boot/grub/load.cfg to the proper UUID (the UUID of Ubuntu partition). This should work.
[*]Delete /boot/grub/load.cfg and boot from sda (Ubuntu drive). I don't know if G2 would ignore the bad UUID but it might.
[*]Remove G2 from sdb only and delete /boot/grub/load.cfg - Maybe.
[*]Remove G2 from both drives. Delete /boot/grub/load.cfg from the Ubuntu partition. Reinstall G2 to one drive.  
[*]Remove G2 from both drive MBRs, write TESTDISK to the MBRs. Remove /boot/grub/load.cfg if it still exists. Reinstall Grub2 to one or both devices. If you install to one, no load.cfg file is created. If you install to both, check /boot/grub/load.cfg for the proper UUID.
[LIST]
[*]The tricky part here is that uninstalling grub-pc/grub-common won't do it. You must write to the MBRs. I used TestDisk to clear both MBRs. Figuring this out is what took me the most time.
[/LIST]
[/LIST]

To accomplish either of the first two options, boot the Natty LiveCD, mount sda1, and accomplish the actions.
```

sudo mount /dev/sda1 /mnt
gksu gedit /mnt/boot/grub/load.cfg
or
gksu nautilus /boot/grub

```

If neither of these works, let me know and I can provide more details on how to accomplish the other methods.

---

