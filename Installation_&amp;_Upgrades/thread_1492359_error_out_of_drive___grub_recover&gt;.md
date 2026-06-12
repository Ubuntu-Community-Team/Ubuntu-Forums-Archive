---
title: "error: out of drive   grub recover&gt;"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by kartabosh on 2010-05-24
help
i'm sort of stuck 
after installation grub wont work so i try to do it from the live cd and i get 
whats that all about and how to fix it? 

root@ubuntu:/# grub-install --root-directory=/mnt /dev/sda
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Installation finished. No error reported.

as for update-grub

root@ubuntu:/# update-grub
Generating grub.cfg ...
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Found memtest86+ image: /boot/memtest86+.bin
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
Is device-mapper driver missing from kernel?
/proc/devices: fopen failed: No such file or directory
Failed to set up list of device-mapper major numbers
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
/proc/devices: fopen failed: No such file or directory
grep: /proc/mounts: No such file or directory
Cannot find list of partitions!
done

---

### Post by darkod on 2010-05-24
You can't run those commands like that from live mode. Because your hdd ubuntu is not booted.

If you know which is your root partition, for example if it is /dev/sda5, you need to run:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If you are not sure which is the root partition post the output of:

sudo fdisk -l (small L)

and we can tell you.

---

### Post by kartabosh on 2010-05-24
thank you for your fast reply
here's your solution

root@ubuntu:~# mount /dev/sda1 /mnt
root@ubuntu:~# grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.

everything seams to be fine, oh except for 

root@ubuntu:~# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

is that good?

---

### Post by kartabosh on 2010-05-24
p.s. after reboot its still 
error: out of drive

grub recover>

---

### Post by darkod on 2010-05-24
Can you run the boot info script as per these instructions and post the content of your results file?
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by kartabosh on 2010-05-24
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   150,294,527   150,292,480  83 Linux
/dev/sda2         150,296,574   156,301,311     6,004,738   5 Extended
/dev/sda5         150,296,576   156,301,311     6,004,736  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 997 MB, 997195776 bytes
31 heads, 62 sectors/track, 1013 cylinders, total 1947648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     1,946,985     1,946,924   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        bf6f8366-6d10-4508-9673-05b8df30a04e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        18ac829c-1804-46d0-a51a-3408634afe1e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5E93-D6CC                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set bf6f8366-6d10-4508-9673-05b8df30a04e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set bf6f8366-6d10-4508-9673-05b8df30a04e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bf6f8366-6d10-4508-9673-05b8df30a04e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=bf6f8366-6d10-4508-9673-05b8df30a04e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bf6f8366-6d10-4508-9673-05b8df30a04e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=bf6f8366-6d10-4508-9673-05b8df30a04e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bf6f8366-6d10-4508-9673-05b8df30a04e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set bf6f8366-6d10-4508-9673-05b8df30a04e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bf6f8366-6d10-4508-9673-05b8df30a04e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=18ac829c-1804-46d0-a51a-3408634afe1e none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  64.5GB: boot/grub/core.img
  64.5GB: boot/grub/grub.cfg
  64.5GB: boot/initrd.img-2.6.32-21-generic
  64.5GB: boot/vmlinuz-2.6.32-21-generic
  64.5GB: initrd.img
  64.5GB: vmlinuz
```

---

### Post by darkod on 2010-05-24
You are right, it all looks fine. Strange that it doesn't work.

Can you try step 1 from here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

if that works and allows you to boot the hdd ubuntu, continue with step 4 to make the fix permanent. You don't need steps 2 and 3 in your situation.

---

### Post by kartabosh on 2010-05-24
the uuid is correct in the grub.cfg

---

### Post by darkod on 2010-05-24
> **kartabosh said:**
> the uuid is correct in the grub.cfg

OK. Do step 4 from that guide to make it a permanent fix. The error should be gone after that hopefully.

---

### Post by kartabosh on 2010-05-24
what i said was that my uuid was already correct, the grub doesnt even get that far, 
if i press shift it says grub loading and the error pops up i don't get to the menu, and i checked my uuid in the fstab and grub configuration files and they were fine, the error is sadly somewhere else ...

---

### Post by darkod on 2010-05-24
I'm out of ideas. Just make sure you are hitting Shift on time because if it starts loading ubuntu it's already late. Because you don't have dual boot it doesn't stop and show the menu so it's difficult to judge.

---

### Post by kartabosh on 2010-05-25
thanks anyway

help!

---

### Post by kartabosh on 2010-05-25
while trying to install windows xp (don't ask) i noticed that in the select hdd part it said 33 gb hdd instead of 80 gb 
how could this be
i don't get it, the hard disk testing tools see it as a 33gb hdd while the linux disk partitioning software gparted and the default one when installing ubuntu see it as a 80gb hdd

its kind of odd that it wont work since just few days ago i had ubuntu on it working perfectly, only difference in the pc is that i changed the cd devices and the video card which shouldnt effect the hdd

---

