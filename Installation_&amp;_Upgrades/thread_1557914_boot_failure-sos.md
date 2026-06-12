---
title: "boot failure-sos"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by hocico0777 on 2010-08-21
Hi,ihave  a 500 gb internal disk which i made 2 equal partitions.i installed in both windows 7.
in one of the 2 partitions i installed also ubuntu 10.04 lts 3 weeks ago through cd.
everything was fine untill yesterday,something was not working right so i decided to make a restart but it didnt boot.
it stucks on a black screen - in some part of it it writes:

mount:mounting/syson/root/sys failed: No such file or directory
mount:mounting /proc on/root/ proc failed:No such file or directory
target file system doesnt have /sbin/init.
No init found. Try passing init=bootarg


someone said to type sudo fsck /dev/sda1 through a live cd
when typing sudo fsck /dev/sda4  in the terminal throygh the presentation mode of the cd i get the following message:

ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda4
Could this be a zero-length partition?

Any suggestions?

---

### Post by Rubi1200 on 2010-08-21
Since you have the live cd, boot the computer with it choosing the option to try not install.

Click on the link at the bottom of my post and follow the instructions there.

Post the results back here and wrap the text with the # tag.

The bootscript should tell us what we need to know in order to offer solutions.

Thanks.

---

### Post by hocico0777 on 2010-08-21
the results are:

#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   488,386,559   488,179,712   7 HPFS/NTFS
/dev/sda3         488,386,560   632,940,210   144,553,651   7 HPFS/NTFS
/dev/sda4         632,940,542   976,773,119   343,832,578   5 Extended
/dev/sda5         747,554,816   967,368,703   219,813,888  83 Linux
/dev/sda6         967,370,752   976,773,119     9,402,368  82 Linux swap / Solaris
/dev/sda7         632,940,544   742,782,975   109,842,432  83 Linux
/dev/sda8         742,785,024   747,552,767     4,767,744  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2A169757169722BD                       ntfs       &#916;&#949;&#963;&#956;&#949;&#965;&#956;&#941;&#957;&#959; &#945;&#960;&#972; &#964;&#959; &#963;&#973;&#963;&#964;&#951;&#956;&#945;
/dev/sda2        3036AD0036ACC864                       ntfs                                     
/dev/sda3        601CCE331CCE03CE                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        c1d4af33-466a-4fa6-8bac-b40c1e90d32a   ext4                                     
/dev/sda6        a71f90cb-e7e2-4107-8a1b-6f8d60ddbced   swap                                     
/dev/sda7        e3716ba3-753e-4609-a66f-e3c06f4b4a5c   ext4                                     
/dev/sda8        e642a626-3dc6-4246-b6d5-da5fb3390d22   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E09CF1169CF0E7C4                       ntfs       FreeAgent Drive               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
UUID=c1d4af33-466a-4fa6-8bac-b40c1e90d32a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a71f90cb-e7e2-4107-8a1b-6f8d60ddbced none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set e3716ba3-753e-4609-a66f-e3c06f4b4a5c
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set e3716ba3-753e-4609-a66f-e3c06f4b4a5c
set locale_dir=($root)/boot/grub/locale
set lang=el
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
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set e3716ba3-753e-4609-a66f-e3c06f4b4a5c
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e3716ba3-753e-4609-a66f-e3c06f4b4a5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-24-generic (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set e3716ba3-753e-4609-a66f-e3c06f4b4a5c
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e3716ba3-753e-4609-a66f-e3c06f4b4a5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set e3716ba3-753e-4609-a66f-e3c06f4b4a5c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e3716ba3-753e-4609-a66f-e3c06f4b4a5c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, &#956;&#949; Linux 2.6.32-21-generic (&#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962;)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set e3716ba3-753e-4609-a66f-e3c06f4b4a5c
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e3716ba3-753e-4609-a66f-e3c06f4b4a5c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set e3716ba3-753e-4609-a66f-e3c06f4b4a5c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set e3716ba3-753e-4609-a66f-e3c06f4b4a5c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2a169757169722bd
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=e3716ba3-753e-4609-a66f-e3c06f4b4a5c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e642a626-3dc6-4246-b6d5-da5fb3390d22 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 326.3GB: boot/grub/core.img
 326.5GB: boot/grub/grub.cfg
 326.4GB: boot/initrd.img-2.6.32-21-generic
 350.1GB: boot/initrd.img-2.6.32-24-generic
 324.2GB: boot/vmlinuz-2.6.32-21-generic
 326.6GB: boot/vmlinuz-2.6.32-24-generic
 350.1GB: initrd.img
 326.4GB: initrd.img.old
 326.6GB: vmlinuz
 324.2GB: vmlinuz.old #

---

### Post by Rubi1200 on 2010-08-21
Thanks for posting the results.

A couple of things:

I don't see a boot flag on the drive (normally indicated by an asterisk * next to one of the sda's)

Also, you have 2 installs of Ubuntu; I assume 10.04.1 was the most recent?

In any event, I would advise waiting for one of the more experienced forum members to come along and advise you.

The normal method would be to reinstall GRUB to the MBR, but I think it would be better to wait for another opinion.

Thanks.

---

### Post by hocico0777 on 2010-08-21
> **Rubi1200 said:**
> Thanks for posting the results.

A couple of things:

I don't see a boot flag on the drive (normally indicated by an asterisk * next to one of the sda's)

Also, you have 2 installs of Ubuntu; I assume 10.04.1 was the most recent?

In any event, I would advise waiting for one of the more experienced forum members to come along and advise you.

The normal method would be to reinstall GRUB to the MBR, but I think it would be better to wait for another opinion.

Thanks.

i have 10.04.1 installed?did not know that. i did not do it through a cd
maybe synaptic manager did it through an update.
and where did it put it?it did not made an update over 10.04?:confused:
waiting...

---

### Post by Rubi1200 on 2010-08-21
> **hocico0777 said:**
> i have 10.04.1 installed?did not know that. i did not do it through a cd
maybe synaptic manager did it through an update.
and where did it put it?it did not made an update over 10.04?:confused:
waiting...

sda5: Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda7: Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

If you did not install it, how did it get there?

I assume you can still boot into Windows normally?

---

### Post by hocico0777 on 2010-08-21
> **Rubi1200 said:**
> sda5: Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda7: Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

If you did not install it, how did it get there?

I assume you can still boot into Windows normally?

i told you,synaptic through update
windows yes.

---

### Post by Rubi1200 on 2010-08-21
> **hocico0777 said:**
> i told you,synaptic through update
windows yes.
Synaptic cannot put an upgrade (or anything else) onto a separate partition!

In any event, you now have 2 partitions with Ubuntu and 2 swap partitions and you need to decide what you want to do with them.

---

### Post by hocico0777 on 2010-08-21
> **Rubi1200 said:**
> Synaptic cannot put an upgrade (or anything else) onto a separate partition!

In any event, you now have 2 partitions with Ubuntu and 2 swap partitions and you need to decide what you want to do with them.

i just want to work with 10.04
i dont care about 10.04.1 ,can i erase this partition?
anyway the problem is that i cannot boot in 10.04

---

### Post by Rubi1200 on 2010-08-21
> **hocico0777 said:**
> i just want to work with 10.04
i dont care about 10.04.1 ,can i erase this partition?
anyway the problem is that i cannot boot in 10.04
The boot files are on the partition which has 10.04.1; so either you have to reinstall the bootloader there or back to the partition which has 10.04

Since 10.04.1 is the most recent version I would suggest that you keep that and reinstall GRUB there.

This is what you need to do:

1. boot the computer with the LiveCD choosing to try not install

2. run the following commands in the terminal (Applications > Accessories > Terminal)

```
sudo mount /dev/sda7 /mnt
```

3. 
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

4. Reboot the computer, taking the CD out when you do

5. From within Ubuntu (which hopefully boots now) run this command
```
sudo update-grub
```

Things should then be back to normal and you can decide later what to do with the other partition.

---

### Post by hocico0777 on 2010-08-22
[SIZE=3]Greetings to everyone
i reinstalled ubuntu eventhough ithink i was close to find asolution.
thanks to everyone that showed interest in my case.

Now i would like to do something else.Because of many installations of various os there are many partitions in my disk.
i would like to keep the last with the latest installation of ubuntu that i made and erase the others so when i turn on the pc only one choice of ubuntu appears.
How can i do that?
Also is it possible to 'unite' 2 or 3 different partitions into 1?

If i have to make a new thread about this please let me know.

For one more time,thanks to everyone.[/SIZE]

---

