---
title: "can't choose between OS (No grub?!)"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by Mina Fouad on 2010-08-27
Hi all,
I installed ubuntu 10.04 inside windows vista but I un-installed  it and I created an extended partition and created inside it 2 partitions one of them are ext4 with size 10 GB and the other with size 3 GB as swap.
the installation was done successfully but when I boot my system I couldn't have the option of choosing OS
it opens ubuntu always .
I tried to fix mbr using vista recovery disc. and I succeeded (windows installed in MBR)
but the same problem with the windows
the system always boot into windows
I used ubuntu life CD
and I got this info about my boot files and dirs
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2          24,578,048   106,498,047    81,920,000   7 HPFS/NTFS
/dev/sda3         106,498,048   207,174,239   100,676,192   7 HPFS/NTFS
/dev/sda4         207,174,301   234,436,544    27,262,244   5 Extended
/dev/sda5         207,174,303   228,139,064    20,964,762  83 Linux
/dev/sda6         228,139,128   234,436,544     6,297,417  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9AD0FBFDD0FBDD87                       ntfs       WinRE                         
/dev/sda2        2E64E23464E1FE89                       ntfs                                     
/dev/sda3        0E5EE59E5EE57EB9                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        36865e8b-618f-4e6a-89c6-15b3472f4c1a   ext4                                     
/dev/sda6        0236cdd4-1d7d-4888-a3f0-c61005024e63   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/0E5EE59E5EE57EB9  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/2E64E23464E1FE89  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /mnt/root                ext4       (rw)
/dev             /mnt/root/dev            none       (rw,bind)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 36865e8b-618f-4e6a-89c6-15b3472f4c1a
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 36865e8b-618f-4e6a-89c6-15b3472f4c1a
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36865e8b-618f-4e6a-89c6-15b3472f4c1a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=36865e8b-618f-4e6a-89c6-15b3472f4c1a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36865e8b-618f-4e6a-89c6-15b3472f4c1a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=36865e8b-618f-4e6a-89c6-15b3472f4c1a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36865e8b-618f-4e6a-89c6-15b3472f4c1a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 36865e8b-618f-4e6a-89c6-15b3472f4c1a
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=36865e8b-618f-4e6a-89c6-15b3472f4c1a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0236cdd4-1d7d-4888-a3f0-c61005024e63 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 115.3GB: boot/grub/core.img
 113.5GB: boot/grub/grub.cfg
 115.3GB: boot/initrd.img-2.6.32-21-generic
 115.3GB: boot/vmlinuz-2.6.32-21-generic
 115.3GB: initrd.img
 115.3GB: vmlinuz

```  

any help will be appreciated..

---

### Post by ptptaylor on 2010-08-27
I'm not an expert, but you may want to run the 'sudo update-grub' command in a terminal.

---

### Post by Grenage on 2010-08-27
Yup, I'm with ptptaylor on this one.

That said, last time I did this, I believe I ran the live CD, then reinstalled Grub2:

```
sudo grub-install /dev/sda
```

Then ran the update command for good measure:

```
sudo update-grub2
```

---

### Post by oldfred on 2010-08-28
I do not even know how you are booting Ubuntu as you still show windows boot loader in the MBR. 

You somehow installed part of grub2 to both windows partitions, your recovery in sda1 and install in sda2.
/boot/grub/core.img

Grenage's instructions will reinstall grub2 to the MBR if you are booted into Ubuntu. Instructions are slightly different if from liveCD.

But you do need to remove the /boot/grub/core.img from both partitions. Windows is not CaseSensitive and will see two boot folders and get confused. In sda1 it looks like you only have /boot but /grub is inside that, so delete /grub under the /boot. Not sure if you then have some grub files in /boot mixed up with the windows files. Compare with your sda2 folder to see grub vs windows files.
In sda2 your have windows /Boot - do not delete it but delete the /boot folder. You may want to first see what is in /boot besides the /boot/grub folder, and files would also be files you want to delete from sda1's /boot folder.

---

