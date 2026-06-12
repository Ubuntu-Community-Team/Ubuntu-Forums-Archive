---
title: "wrong version of ubuntu in grub"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by kjv161147201 on 2012-12-07
Last night I rebooted my computer and it received a grub rescue>
 
My system is dualboot with win7. I managed to get the grub back but I only had version 9.10 CD but was running 12.04...
 
Is there anyway to get the grub back to where I can get back into version 12.04 at boot?

---

### Post by darkod on 2012-12-07
So, does ubuntu boot now or not?

If it boots, you don't really need to change grub since 9.10 also had grub2 included (the first version that came with grub2). If you do wish to reinstall grub2, you need to boot ubuntu (not from live mode), remove/purge the existing grub and reinstall it.

If you have more complex setup, like multiple disks, you need to make sure you know where you boot from right now.

Under the assumption you are using grub2 on the MBR of /dev/sda, to purge and reinstall would be like:
```
sudo apt-get remove --purge grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda
```

That should do it.

---

### Post by kjv161147201 on 2012-12-07
Hello..

Yes, I can get to ubuntu but it isn't version 12.04 once I log in, it is 9.10

Thanks for the response!

---

### Post by darkod on 2012-12-07
You restored only grub or you installed 9.10 from the cd you had?

The ubuntu version can't change if you only restored grub. On the other hand, if you installed 9.10 over your 12.04, there is little chance to get it back now.

You can use boot-repair to create the bootinfo summary and post the link it gives you. That will show many details about your system including all the OSs installed. The boot-repair instructions are here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you did overwrite the 12.04 partitions and you wish to get them back, you have to try to get them back with testdisk. In that case you shouldn't use the new 9.10 too much because using it lowers the possibility to get 12.04 back.

---

### Post by kjv161147201 on 2012-12-07
Hello and thanks for the reply..

I just fixed the grub...I have tried to install boot repair but it won't install...PPA problems I believe..

---

### Post by darkod on 2012-12-07
It should install. I don't know what to say.

Alternatively you can try running the bootinfoscript directly, the link is in my signature.

One thing is for sure: If you only repaired grub, there is no way to turn your 12.04 into 9.10. Can you post the output of this command:
ls /boot

---

### Post by kjv161147201 on 2012-12-08
I have only been studying linux for a short time, but is it possible that I pointed the grub to the wrong partition when trying to fix? My explanation may not be equal to the required terms to help explain...

~$ ls /boot
abi-2.6.31-11-generic            memtest86+.bin
config-2.6.31-11-generic       System.map-2.6.31-11-generic
grub                                        vmcoreinfo-2.6.31-11-generic
initrd.img-2.6.31-11-generic  vmlinuz-2.6.31-11-generic

---

### Post by oldfred on 2012-12-08
Please run bootinfo script as Darko suggested. It still should run in your old version.

But you should have liveCDDVD/flash drive of 12.04 and then should be able to add Boot-Repair to that.

---

### Post by kjv161147201 on 2012-12-08
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd8862b51

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    30,410,751    30,408,704  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     30,410,752    30,615,551       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          30,615,552   369,137,808   338,522,257   7 NTFS / exFAT / HPFS
/dev/sda4         369,139,710   625,137,344   255,997,635   5 Extended
/dev/sda5         619,916,283   624,783,914     4,867,632  83 Linux
/dev/sda6         624,783,978   625,137,344       353,367  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7272CD4972CD12B1                       ntfs       PQSERVICE
/dev/sda2        DC4A17E84A17BDE8                       ntfs       SYSTEM RESERVED
/dev/sda3        A0061930061908C4                       ntfs       eMachines
/dev/sda5        fa991ce9-82ee-451d-a1a0-36d96dd23968   ext4       
/dev/sda6        23274699-4350-4677-b524-c6d318cf91b8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set fa991ce9-82ee-451d-a1a0-36d96dd23968
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set fa991ce9-82ee-451d-a1a0-36d96dd23968
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=fa991ce9-82ee-451d-a1a0-36d96dd23968 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set fa991ce9-82ee-451d-a1a0-36d96dd23968
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=fa991ce9-82ee-451d-a1a0-36d96dd23968 ro single 
    initrd    /boot/initrd.img-2.6.31-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7272cd4972cd12b1
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set dc4a17e84a17bde8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=fa991ce9-82ee-451d-a1a0-36d96dd23968 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=23274699-4350-4677-b524-c6d318cf91b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.31-11-generic              1
               =                boot/vmlinuz-2.6.31-11-generic                 1
               =                initrd.img                                     1
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by oldfred on 2012-12-08
You only have one install of Ubuntu in sda5 and it is 9.10 Karmic.

If you have any data you want to save, I would back it up and install 12.04 or 12.10 if your systems supports it. Since you have Windows 7 it would seem like it does.

If you did have 12.10, then you must have totally installed 9.10 over it?

---

### Post by kjv161147201 on 2012-12-08
Ok, thanks for the help..Oh, well, I'll start over. Great learning experience..

Thanks for your time

---

