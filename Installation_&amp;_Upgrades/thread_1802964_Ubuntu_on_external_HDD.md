---
title: "Ubuntu on external HDD"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by Vaderetro on 2011-07-12
Hi, all. I have an external HDD connected through USB. I tried install Ubuntu 10.10 (few times) from a live cd. Each time, happened the same thing: after finishing install from live cd, it required to restart the pc. When it shall boot from HDD, i get the error:
[I]error: no such partition
grub rescue>
C[/I]an anyone help me with this? Is it becouse i use an external disk? When i installed i checked the option to erase the disk and it automatically created the necessary partition(s).
I don't have any other OS installed on it. Thanks

---

### Post by oldfred on 2011-07-12
Welcome to the forums.

Post this with external plugged in. Grub default install is to sda and normally the external is sdb, this may tell us what is where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Vaderetro on 2011-07-12
I tried the boot info script (downloaded to desktop, then extracted to desktop) i had the .sh file on the desktop, as in the tutorial, but didn' t work. Here is the screenshot.
[ATTACH]197350[/ATTACH]


with fdisk -l, i can see the partitions. This hdd is the only attached to pc. Here is another screenshot:
[ATTACH]197351[/ATTACH]

I also checked the install explanations u suggested, anything i did different is that i selected the 'Erase and use entire disk' option, instead of 'Specify partitions manually'. I currently use live cd.
Thanks alot for your reply.
Also thanks for the welcome message.

---

### Post by oldfred on 2011-07-12
When you have a huge drive like that, you create one very large system partition & swap. You actually only need 20-25GB for an Ubuntu partition and can have the rest as /home or other data partitions. If dual booting with windows you may want another NTFS to be a shared data partition so you can save data and read from both systems.

It is saying the file is not there. It now usually downloads into Downloads and you end up extracting it there.

cd Desktop 
or 
cd Downloads
sudo bash boo {then hit tab}
when you hit tab it will add as many unique characters as it can find, to save typing.

Mine is in my home and I have two versions so tab only partially completes and then I have to type .sh to finish
```
fred@fred-MavericDT:~$ ls boo*
boot_info_script_2011-05-21_23:54:33.sh  boot_info_script.sh
fred@fred-MavericDT:~$ sudo bash boot_info_script

```

---

### Post by Vaderetro on 2011-07-12
```
[COLOR=Black]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

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

/dev/sda1    *          2,048 1,928,949,759 1,928,947,712  83 Linux
/dev/sda2       1,928,951,806 1,953,523,711    24,571,906   5 Extended
/dev/sda5       1,928,951,808 1,953,523,711    24,571,904  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        280c2511-2dc8-4682-90ff-e20e282de0da   ext4       
/dev/sda5        58d5696c-c337-4ff8-bb72-d9c367fbd57e   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/280c2511-2dc8-4682-90ff-e20e282de0da ext4       (rw,nosuid,nodev,uhelper=udisks)
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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 280c2511-2dc8-4682-90ff-e20e282de0da
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 280c2511-2dc8-4682-90ff-e20e282de0da
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 280c2511-2dc8-4682-90ff-e20e282de0da
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=280c2511-2dc8-4682-90ff-e20e282de0da ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 280c2511-2dc8-4682-90ff-e20e282de0da
    echo    'Loading Linux 2.6.35-30-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-30-generic-pae root=UUID=280c2511-2dc8-4682-90ff-e20e282de0da ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 280c2511-2dc8-4682-90ff-e20e282de0da
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 280c2511-2dc8-4682-90ff-e20e282de0da
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
UUID=280c2511-2dc8-4682-90ff-e20e282de0da /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=58d5696c-c337-4ff8-bb72-d9c367fbd57e none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 248.136978149 = 266.435051520  boot/grub/core.img                             1
 364.247463226 = 391.107735552  boot/grub/grub.cfg                             1
 346.765403748 = 372.336517120  boot/initrd.img-2.6.35-30-generic-pae          2
 248.132987976 = 266.430767104  boot/vmlinuz-2.6.35-30-generic-pae             1
 346.765403748 = 372.336517120  initrd.img                                     2
 248.132987976 = 266.430767104  vmlinuz                                        1


[/COLOR]
```

---

### Post by oldfred on 2011-07-12
Boot script looks normal.

I am seeing more of this, but still think it is a BIOS setting on newer drives/BIOS. Look at drive settings in BIOS and try Large or LBA.

You can also try making the / (root) partition smaller and make the rest of the drive /home or /data.

Sometimes booting with Supergrub and then reinstalling grub2's boot loader to the MBR works. Not sure if it will have same issue of seeing partition.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

