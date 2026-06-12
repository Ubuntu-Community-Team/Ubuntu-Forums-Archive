---
title: "Incomplete Upgrade"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by Alienspecimen on 2011-06-25
I finally decided to upgrade to 11.04.

For some reason, the installation process froze during the installation  of one of the fonts (I dont remember which one), or "about 44 minutes"  prior to completion.  I waited for an hour and a half, during which all  the fans of my older Gateway MT 6916 were going at full speed.

I decided to shut it down and upon doing it, the shut down menu (the one  that gives you the choices to shut down, restart, etc.) came up but it  was unreadable.  I knew what to click on and the computer turned off.

This is what happens now when I reboot it:

1.  I am given a choice of which version of the OS to boot, prior to upgrade it was booting up right up.

2.  I choose recovery mode of course (but same thing happens even if I choose normal boot...) and this is what I get


init:udevtrigger main process (387) terminated with status 1
init: udevtrigger post-stop process (391) terminated with status 1
init: udevmonitor main process (386) killed by TERM signal
The disk drive for / is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery

After pressing S it shows some information about the HW present and  about the start of running couple of scripts ( local-bottom and  init-bottom)

It all ends with the following message at the bottom of the screen:

mountall:  Plymouth command failed
mountall: Disconnected from Plymouth

So I then shut down by pressing the power button and repeat the entire  process.  When this time I choose "M for manual recovery",  I get the  same thing on the scree, with the exception of the last four lines:

Root filesystem check failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
root@Alienspecimen:~#

Yes, you guessed it right, Alienspecimen is the name of my computer, dont ask...:smile:

How bad is it? Is it possible to complete the installation?

Can you provide me with detailed instructions how to return my laptop to life?  And I mean annoyingly detailed....:smile:  

I really appreciate your help.

Best

Boris

---

### Post by coffeecat on 2011-06-25
Do you have a live CD or live USB of Ubuntu? Versions 10.04 or 10.10 will do as well as 11.04. If so, boot up with the live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for legibility You can use the message toolbar [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] icon for this.

This will give us an overview of your system and particularly may help to explain why the boot process cannot find your root (/) partition.

---

### Post by j0eb0b on 2011-06-25
I had something similar happen when attempting to upgrade to 11.04.  For me the resolution was a clean install from CD.  I use a Windows 7 Ubuntu dual boot system,  The install wrote to the Linux partition without disturbing Windows.  Clean install is a whole lot faster than the upgrade, Took less than 15 minutes on my system.

Good luck.

---

### Post by Alienspecimen on 2011-06-25
Thank you for your reply.

I followed the instructions and below are the contents of the file

Please, let me know if you need anything else.  Please, note that I came from the "Absolute Beginner" forum...:)

Best

Boris

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

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

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 15296 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   300,560,084   300,560,022  83 Linux
/dev/sda2         300,560,085   312,576,704    12,016,620   5 Extended
/dev/sda5         300,560,148   312,576,704    12,016,557  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,826,383     7,826,322   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3e80be17-7252-4c8c-b2aa-cf33b46b45a0   ext4       
/dev/sda5        d6038b73-b253-4927-881b-198f72a8f688   swap       
/dev/sdb1        3806-708D                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e80be17-7252-4c8c-b2aa-cf33b46b45a0
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3e80be17-7252-4c8c-b2aa-cf33b46b45a0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d6038b73-b253-4927-881b-198f72a8f688 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.129798412 = 0.139369984    boot/grub/core.img                             1
   7.321963787 = 7.861898752    boot/grub/grub.cfg                             2
   6.960917950 = 7.474228736    boot/initrd.img-2.6.31-21-generic              1
  13.579333782 = 14.580698624   boot/initrd.img-2.6.32-26-generic              1
  11.822547436 = 12.694363648   boot/initrd.img-2.6.35-23-generic              2
   6.638717175 = 7.128268288    boot/initrd.img-2.6.35-24-generic              2
   5.010051250 = 5.379501568    boot/initrd.img-2.6.35-25-generic              2
  11.187530041 = 12.012518912   boot/initrd.img-2.6.35-27-generic              2
  11.275683880 = 12.107173376   boot/initrd.img-2.6.35-28-generic              1
   1.879310131 = 2.017893888    boot/vmlinuz-2.6.31-21-generic                 1
   9.792289257 = 10.514390528   boot/vmlinuz-2.6.32-26-generic                 1
  13.584414959 = 14.586154496   boot/vmlinuz-2.6.35-23-generic                 1
   1.660586834 = 1.783041536    boot/vmlinuz-2.6.35-24-generic                 1
   1.758906841 = 1.888611840    boot/vmlinuz-2.6.35-25-generic                 1
   8.381885052 = 8.999980544    boot/vmlinuz-2.6.35-27-generic                 1
  13.932170391 = 14.959554048   boot/vmlinuz-2.6.35-28-generic                 1
  36.519561291 = 39.212580352   boot/vmlinuz-2.6.38-8-generic                  2
  11.275683880 = 12.107173376   initrd.img                                     1
  11.187530041 = 12.012518912   initrd.img.old                                 2
  13.932170391 = 14.959554048   vmlinuz                                        1
   8.381885052 = 8.999980544    vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/Extract/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```
> **coffeecat said:**
> Do you have a live CD or live USB of Ubuntu? Versions 10.04 or 10.10 will do as well as 11.04. If so, boot up with the live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for legibility You can use the message toolbar [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] icon for this.

This will give us an overview of your system and particularly may help to explain why the boot process cannot find your root (/) partition.

---

### Post by Alienspecimen on 2011-06-25
> **j0eb0b said:**
> I had something similar happen when attempting to upgrade to 11.04.  For me the resolution was a clean install from CD.  I use a Windows 7 Ubuntu dual boot system,  The install wrote to the Linux partition without disturbing Windows.  Clean install is a whole lot faster than the upgrade, Took less than 15 minutes on my system.

Good luck.

Thanks,

I thought about it, but it will take me at least a week of installing all the programs that I need and adjust all the settings to my needs.

Best

Boris

---

### Post by coffeecat on 2011-06-25
> **Alienspecimen said:**
> I thought about it, but it will take me at least a week of installing all the programs that I need and adjust all the settings to my needs.

[noparse]I can understand this, but j0eb0b makes an important point. Incomplete upgrades can be difficult to repair, and there is no guarantee that we will succeed. It might be quicker to backup your personal files using a live CD and then re-install. Something to think about.

In the meantime, a few observations from your boot script output. The UUID of your Ubuntu root partition is correct in grub.cfg and /etc/fstab, so this is not a reason for the error message you see about the root partition. The 11.04 kernel (2.6.38-8) is present, but grub.cfg has not been updated so you are trying to boot into the older Maverick/10.10 kernel. This won't matter temporarily but does need to be fixed in due course. There are a few things to try but perhaps the first is a filesystem check.

Boot up the live Ubuntu CD and open Gparted (System > Administration). Right-click on the sda1 partition and choose "check". What happens? Do you get any error messages?[/noparse]

---

### Post by Alienspecimen on 2011-06-25
> **coffeecat said:**
> [noparse]I can understand this, but j0eb0b makes an important point. Incomplete upgrades can be difficult to repair, and there is no guarantee that we will succeed. It might be quicker to backup your personal files using a live CD and then re-install. Something to think about.

In the meantime, a few observations from your boot script output. The UUID of your Ubuntu root partition is correct in grub.cfg and /etc/fstab, so this is not a reason for the error message you see about the root partition. The 11.04 kernel (2.6.38-8) is present, but grub.cfg has not been updated so you are trying to boot into the older Maverick/10.10 kernel. This won't matter temporarily but does need to be fixed in due course. There are a few things to try but perhaps the first is a filesystem check.

Boot up the live Ubuntu CD and open Gparted (System > Administration). Right-click on the sda1 partition and choose "check". What happens? Do you get any error messages?[/noparse]
  
I used Gparted, but the "check" isnt highlighted.  Also there is a key next to the partition name, so I assume that I need to figure out the privileges.

I think I just made my life more difficult.  Clicked on "install Ubuntu" and luckily for me was presented with three choices:

1 erase the entire disk and install

2 upgrade 11.04 to 11.04 (all files and programs kept)

3 do something else

I clicked on the second choice and everything was going smoothly, until came to a menu asking me for set a name and a password.  I canceled the entire thing, because had to attend to something else.  When I got back to it, only choices 1 and three were present.  Now it tells me that it cant detect an OS.

If I remove the USB live disk, I still get the menu which allows me to choose a version.

Where do I go from here?

Thanks

Boris

---

### Post by coffeecat on 2011-06-25
> **Alienspecimen said:**
> I used Gparted, but the "check" isnt highlighted.  Also there is a key next to the partition name, so I assume that I need to figure out the privileges.

If there was a key next to the partition, then you must have mounted it. You can't do a filesystem check on a mounted partition. Unmount it first.

---

### Post by coffeecat on 2011-06-26
A further thought:

> **Alienspecimen said:**
> I think I just made my life more difficult.  Clicked on "install Ubuntu" and luckily for me was presented with three choices:

1 erase the entire disk and install

2 upgrade 11.04 to 11.04 (all files and programs kept)

3 do something else

I clicked on the second choice and everything was going smoothly, until came to a menu asking me for set a name and a password.  I canceled the entire thing, because had to attend to something else.  When I got back to it, only choices 1 and three were present.  Now it tells me that it cant detect an OS.

If this was all in the live USB session, the disappearance of the upgrade from 11.04 to 11.04 the second time around could be because Ubiquity (the installer) had become confused when you cancelled the process first time around. Try rebooting the live USB and see if you can get that option again. Give yourself plenty of time and do a filesystem check from Gparted before you start the installer. The filesystem may not be corrupted but it will do no harm to check it first.

If none of that works, you may be able to complete the upgrade by chrooting into the hard drive partition from the live USB. I can post details of how to do that, but it's not as straightforward as attempting the upgrade from the live session installer, so try that again first.

---

### Post by ashpash150 on 2011-06-26
Hey guys sorry if I'm posting in the wrong place but iv got an error similar to this I turned on my computer today and was faced with 

Mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_a_dd_Mach_subsystem_devtype
Init : mountall main process (295) terminates with status 127 

If someone could please please help me plus I don't have a live disk so I was hoping there'd be a way to fix it without one any help would be really appreciated

---

### Post by Alienspecimen on 2011-06-26
> **coffeecat said:**
> A further thought:



If this was all in the live USB session, the disappearance of the upgrade from 11.04 to 11.04 the second time around could be because Ubiquity (the installer) had become confused when you cancelled the process first time around. Try rebooting the live USB and see if you can get that option again. Give yourself plenty of time and do a filesystem check from Gparted before you start the installer. The filesystem may not be corrupted but it will do no harm to check it first.

If none of that works, you may be able to complete the upgrade by chrooting into the hard drive partition from the live USB. I can post details of how to do that, but it's not as straightforward as attempting the upgrade from the live session installer, so try that again first.

I rebooted several times prior to using Gparted, but was not able to see the upgrade operation.  I also unmounted the partition, but have not started the check, because it told me that I will loose some data.

I tried copying the files to my external back-up drive, but am told that I dont have the permission.  It appears that it applies to the entire Documents folder and selected folders within the directory.  More specifically, it tells me that User1000 is the owner.  I am able to open the files and folders within these directories and transfer them to my backup device.

So, my two questions are:

1.  How do I unlock these folders?

2.  Is there a way to back-up my Mozilla bookmarks?

Best

Boris

---

### Post by coffeecat on 2011-06-26
> **Alienspecimen said:**
> I also unmounted the partition, but have not started the check, because it told me that I will loose some data.

Are you sure? The normal prompt when you want to check a filesystem in Gparted is, "Editing partitions has the potential to cause LOSS of DATA. You are advised to backup your data before proceeding." That is a completely routine message which always appears, but which needs to be taken seriously. It is not saying that you **will** lose data.

> **Alienspecimen said:**
> I tried copying the files to my external back-up drive, but am told that I dont have the permission.  It appears that it applies to the entire Documents folder and selected folders within the directory.  More specifically, it tells me that User1000 is the owner.  I am able to open the files and folders within these directories and transfer them to my backup device.

This is normal. The UID of your account in your hard drive installation is 1000. That of the ubuntu live user account is 999 and Linux permissions are preventing access for user 999 to user 1000 files. There is an easy way around this. In the live session, open a root nautilus window with:

```
gksudo nautilus /media
```

This will open in the /media folder of the live session. Double-click on the folder in /media that is the mountpoint for your Ubuntu partition and navigate to your home folder. You will now be able to copy your files.

> **Alienspecimen said:**
> 
2.  Is there a way to back-up my Mozilla bookmarks?


Yes. In your home folder, press ctrl-H to reveal hidden files (while still in the root nautilus). Open the .mozilla folder. Note the leading point. Now the firefox folder, now random.default (where random = a random string), now bookmarkbackups. There will be a number of bookmarks*.json files which can be copied and imported into Firefox in another system.

---

### Post by Alienspecimen on 2011-06-26
I was able to run Gparted, you can see the results below.  Unfortunately, the menu option that allows me to upgrade the current 11.04 version did not show up upon clicking the "Install Ubuntu 11.04.  I am willing to try the "not so straight forward" approach (or any approach), sorry for the inconvenience.  Please, be as specific as possible, I came from the "Absolute Beginner's" forum, remember...:)


Boris

P.S.  I did not try to reboot the computer and see if would boot up the "regular" way.
GParted 0.7.0 --enable-libparted-dmraid
 Libparted 2.3
    **Check and repair file system (ext4) on /dev/sda1**  00:00:19    ( SUCCESS )             calibrate /dev/sda1  00:00:00    ( SUCCESS )             [I]path: /dev/sda1
start: 63
end: 300560084
size: 300560022 (143.32 GiB)[/I]          check file system on /dev/sda1 for errors and (if possible) fix them  00:00:19    ( SUCCESS )             ***e2fsck -f -y -v /dev/sda1***             [I]Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  171200 inodes used (1.82%)
     993 non-contiguous files (0.6%)
     112 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 164534/95
 6753376 blocks used (17.98%)
       0 bad blocks
       1 large file

  134581 regular files
   28785 directories
       0 character device files
       0 block device files
       0 fifos
       1 link
    7783 symbolic links (6519 fast symbolic links)
      42 sockets
--------
  171192 files
[/I]       [I]e2fsck 1.41.14 (22-Dec-2010)
[/I]             grow file system to fill the partition  00:00:00    ( SUCCESS )             ***resize2fs /dev/sda1***             [I]resize2fs 1.41.14 (22-Dec-2010)
The filesystem is already 37570002 blocks long.  Nothing to do![/I]

---

### Post by coffeecat on 2011-06-27
> **Alienspecimen said:**
>  I am willing to try the "not so straight forward" approach (or any approach), sorry for the inconvenience.  Please, be as specific as possible, I came from the "Absolute Beginner's" forum, remember...:)

Sorry for the delay in getting back. I was too tired last evening to post without the risk of making errors.

Boot up with the live USB. Make sure you are connected to the internet - the following will not work without internet connectivity. Don't try to mount your Ubuntu partition from "Places". That will mount it to a mountpoint in /media, and the instructions below mount it to /mnt in order to make the following commands a little more straightforward.

Open a terminal and mount your Ubuntu partition:

```
sudo mount /dev/sda1 /mnt
```

First thing. Have you backed up your personal files yet? If not, it would be a good idea to do so now. We need to modify the command that I gave you in my last post to get a root Nautilus. It will now be:

```
gksudo nautilus /mnt
```

.... and the nautilus window will open in the filesystem of your Ubuntu partition from where you can navigate to your home folder and backup what you need. When you have finished, close the root nautilus window.

You now need to check your sources.list file. I am 99% sure that this has been updated to show natty sources, but we need to check this. Run this command:

```
cat /mnt/etc/apt/sources.list > Desktop/sources.txt
```

A text file called sources.txt will appear on the live desktop. Copy it to a USB drive in case you need to post it or refer to it later. Now open it. You can ignore all the lines that start with a '#'. These are so-called commented lines and are not parsed by the system. Look at all the uncommented lines. Does each have a mention of "natty" (no quotes) in it? Are there any with the word "maverick"? If yes to either, don't go any further and post the sources.txt file.

If the sources file checks out OK, then run these following commands:

```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
```

Finally, chroot into your Ubuntu partition with:

```
sudo chroot /mnt /bin/bash
```

You will see that the prompt changes from a $ to a #. Now:

```
apt-get update
apt-get upgrade
```

Note that you do not need to use sudo while in the chroot environment. If, by chance, the problem with the font installation before was to do with the ms corefonts, this might have been to do with the EULA. If you are presented with a EULA in the terminal, press the tab key to highlight accept/OK, and then press enter. Once the upgrade command has finished, refresh your grub.cfg with:

```
update-grub
```

Now close the terminal with:

```
exit
exit
```

Yes, twice.

Now reboot. As I warned you before, there is no guarantee that this will work. If the situation is simply an incomplete upgrade then it should. If something more serious has gone wrong - the error messages you described in your first post suggest that this might be so - then it probably won't. If this doesn't work, then I have nothing further to suggest and would recommend a re-install.

---

### Post by Alienspecimen on 2011-07-01
I ended up reinstalling the entire OS.  It was not worth the effort of troubleshooting.

Thanks for all the help

Boris

---

