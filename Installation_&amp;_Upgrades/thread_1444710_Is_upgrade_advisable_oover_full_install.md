---
title: "Is upgrade advisable? oover full install?"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by bigsmitty64 on 2010-04-01
My bud has 9.10 installed and when lucid is released plans on going to that. Question is, (He has NOTHING on this 9.10 install worth saving)
is it advisable to upgrade ? or just do a full install of lucid. Please give the reasoning for your answer as I'm not sure how to explain it. I personally would just do a full install (he has no info to lose remember)

---

### Post by Boondoklife on 2010-04-01
> **bigsmitty64 said:**
> My bud has 9.10 installed and when lucid is released plans on going to that. Question is, (He has NOTHING on this 9.10 install worth saving)
is it advisable to upgrade ? or just do a full install of lucid. Please give the reasoning for your answer as I'm not sure how to explain it. I personally would just do a full install (he has no info to lose remember)

Well "IF" he has not made any changes to the OS configurations or hacked up anything then an upgrade is just fine. I have had great luck with upgrades and in general there are very few problems unless you have customized the install greatly or done different hacks.

---

### Post by bigsmitty64 on 2010-04-01
He actually hasn't touched the 9.10 install yet. It's just a few days old. He originally was going to test 10.04 but couldn't get passed the login screen. It was weird, it would go black, then we could here the "welcome" music but not see anything, so we gave up. Probably a graphics issue?  Anyways he decided to wait til the official release.

The strange thing is, he has the nvidia 9500 gt and I have the 9400 gt and I'm happily testing 10.04 beta 1
Go figure. Thanks for your response.

---

### Post by bigsmitty64 on 2010-04-02
Well he did the upgrade and it went bad, and I believe he had all other drives unplugged .

 at reboot it goes to:



```
error: no such device: c33cca4d-5f9c-439b-833f-0df01c523f03
grub rescue>_
```

---

### Post by Boondoklife on 2010-04-02
Hey sorry your having an issue. Try booting from the cd and running this boot info script and post back the results.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by bigsmitty64 on 2010-04-02
I think I see the problem already, looks like grub is installed on both drives?

```
     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 8192.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e4b9e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   149,838,254   149,838,192  83 Linux
/dev/sdb2         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,192     7,744,511     7,736,320   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        04F87221F8721162                       ntfs       Storage                       
/dev/sdb1        c33cca4d-5f9c-439b-833f-0df01c523f03   ext4                                     
/dev/sdb5        6feb460c-80db-4fbd-b64f-8f101aefb412   swap                                     
/dev/sdc1        BE7A-BFA8                              vfat       4GigSD                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc1        /media/4GigSD            vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c33cca4d-5f9c-439b-833f-0df01c523f03
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set c33cca4d-5f9c-439b-833f-0df01c523f03
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
menuentry "Ubuntu, with Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c33cca4d-5f9c-439b-833f-0df01c523f03
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=c33cca4d-5f9c-439b-833f-0df01c523f03 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.32-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c33cca4d-5f9c-439b-833f-0df01c523f03
    echo    Loading Linux 2.6.32-19-generic ...
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=c33cca4d-5f9c-439b-833f-0df01c523f03 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c33cca4d-5f9c-439b-833f-0df01c523f03
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=c33cca4d-5f9c-439b-833f-0df01c523f03 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c33cca4d-5f9c-439b-833f-0df01c523f03
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=c33cca4d-5f9c-439b-833f-0df01c523f03 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c33cca4d-5f9c-439b-833f-0df01c523f03
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set c33cca4d-5f9c-439b-833f-0df01c523f03
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c33cca4d-5f9c-439b-833f-0df01c523f03 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6feb460c-80db-4fbd-b64f-8f101aefb412 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
   3.0GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-20-generic
    .8GB: boot/initrd.img-2.6.32-19-generic
    .2GB: boot/vmlinuz-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.32-19-generic
    .8GB: initrd.img
    .6GB: initrd.img.old
    .6GB: vmlinuz
    .2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf 
```

---

### Post by bigsmitty64 on 2010-04-02
official 2 hr bump.....too soon?   :)

---

### Post by bigsmitty64 on 2010-04-03
Ttt

---

