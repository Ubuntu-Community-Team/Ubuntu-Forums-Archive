---
title: "Boot problems after kernel upgrade"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by Marcin Kraszewski on 2011-02-13
Hello, everyone

I had problems with booting my PC after kernel updates several times. In the past I just reinstalled Ubuntu and after several tries with running Update Manager things were working again.

This time I applied another recommended set of updates, including a kernel upgrade and got the usual "Kernel Panic - not syncing: VFS: Unable to mount root fs on unkown-block(0,0)"
After booting from a LiveCD and running boot_info_script I rebooted again and this time I am getting tons of errors which seem to be generated while running grub. After a few minutes of 'error: syntax error' and 'error: Incorrect command' scrolling through my screen, grub gives my a grub> prompt... Not what I expected!
Here is the output of the boot_info_script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/mapper/isw_cagifdjehe_Volume0 and 
    looks on the same drive in partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cagifdjehe_Volume01: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

isw_cagifdjehe_Volume02: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_cagifdjehe_Volume05: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 1,928,945,663 1,928,943,616  83 Linux
/dev/sda2       1,928,947,710 1,953,519,615    24,571,906   5 Extended
/dev/sda5       1,928,947,712 1,953,519,615    24,571,904  82 Linux swap / Solaris


Drive: isw_cagifdjehe_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_cagifdjehe_Volume0: 1000.2 GB, 1000202178560 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_cagifdjehe_Volume01              2,048 1,928,945,663 1,928,943,616  83 Linux
/dev/mapper/isw_cagifdjehe_Volume02      1,928,947,710 1,953,519,615    24,571,906   5 Extended
/dev/mapper/isw_cagifdjehe_Volume05      1,928,947,712 1,953,519,615    24,571,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_cagifdjehe_Volume01 a6071eb5-6fc6-45b3-babb-c1a2156278d7   ext4                                     
/dev/mapper/isw_cagifdjehe_Volume05 1cb0edc5-e434-425e-9486-a49c9b915a7c   swap                                     
/dev/mapper/isw_cagifdjehe_Volume0: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
error: /dev/mapper/isw_cagifdjehe_Volume02: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda5: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_cagifdjehe_Volume0
isw_cagifdjehe_Volume01
isw_cagifdjehe_Volume05

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_cagifdjehe_Volume01 /media/a6071eb5-6fc6-45b3-babb-c1a2156278d7 ext4       (rw,nosuid,nodev,uhelper=udisks)


================= isw_cagifdjehe_Volume01/boot/grub/grub.cfg: =================

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
search --no-floppy --fs-uuid --set a6071eb5-6fc6-45b3-babb-c1a2156278d7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set a6071eb5-6fc6-45b3-babb-c1a2156278d7
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a6071eb5-6fc6-45b3-babb-c1a2156278d7
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a6071eb5-6fc6-45b3-babb-c1a2156278d7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a6071eb5-6fc6-45b3-babb-c1a2156278d7
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=a6071eb5-6fc6-45b3-babb-c1a2156278d7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a6071eb5-6fc6-45b3-babb-c1a2156278d7
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=a6071eb5-6fc6-45b3-babb-c1a2156278d7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a6071eb5-6fc6-45b3-babb-c1a2156278d7
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=a6071eb5-6fc6-45b3-babb-c1a2156278d7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a6071eb5-6fc6-45b3-babb-c1a2156278d7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a6071eb5-6fc6-45b3-babb-c1a2156278d7
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

====================== isw_cagifdjehe_Volume01/etc/fstab: ======================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_cagifdjehe_Volume01 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_cagifdjehe_Volume05 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

========== isw_cagifdjehe_Volume01: Location of files loaded by Grub: ==========


 704.5GB: boot/grub/core.img
 575.7GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-24-generic-pae
  23.0GB: boot/initrd.img-2.6.35-25-generic-pae
 704.5GB: boot/vmlinuz-2.6.35-24-generic-pae
 704.6GB: boot/vmlinuz-2.6.35-25-generic-pae
  23.0GB: initrd.img
    .8GB: initrd.img.old
 704.6GB: vmlinuz
 704.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on isw_cagifdjehe_Volume02



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/mapper/isw_cagifdjehe_Volume02: No such file or directory
hexdump: /dev/mapper/isw_cagifdjehe_Volume02: No such file or directory

```I have two RAIDed disks (mirrored and showing OK during POST). The disk shows above as a6071eb5-6fc6-45b3-babb-c1a2156278d7. Ubuntu 10.10 installs fine from a LiveCD, but gets broken by kernel updates. I can see the original 1 TB disk when I start with the LiveCD and I can access all the files. Could someone help me with getting a procedure developed for fixing this problem? I would like to USE my Linux machine (now when I got rid of Windows ;) and not spend days troubleshooting and fixing after every kernel upgrade. If I know what breaks I can fix it quickly. I would really appreciate your help. If you need more information, I will gladly post it. Thanks.

---

### Post by Marcin Kraszewski on 2011-02-13
I tried a few things and here is what happened. I tried to reinstall grub2. After running os-prober I got the following:
```
/dev/mapper/isw_cagifdjehe_Volume01:Ubuntu 10.10 (10.10):Ubuntu:linux
```I then mounted that partition and chrooted into it.
```

mount /dev/mapper/isw_cagifdjehe_Volume01 /mnt
mount /dev/mapper/isw_cagifdjehe_Volume01 /mnt/boot
mount --bind /dev /mnt/dev
chroot /mnt

```Then I tried installing grub and here is what I got:
```

root@ubuntu:/# grub-install /dev/sda
/proc/devices: fopen failed: No such file or directory
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/isw_cagifdjehe_Volume01.  Check your device.map.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```I don't have device.map in my chrooted partition. How can I find out what module I should specify for this command to work? Thanks.

---

### Post by Marcin Kraszewski on 2011-02-20
Unfortunately, I can only work on my computer on weekends, but this weekend I made some progress. I managed to re-install grub2 using Ubuntu 10.10 Alternate CD. Selecting 'Rescue a broken system' option let me fix the grub problem (thank you YouTube for the tip). I still have the kernel panic problem, but I think I will open a new thread for it. One step at a time...

---

