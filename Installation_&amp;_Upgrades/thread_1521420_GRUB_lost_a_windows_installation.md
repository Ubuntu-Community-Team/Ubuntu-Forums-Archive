---
title: "GRUB lost a windows installation"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by josec on 2010-06-30
I have windows 7 installed on a pair of sata drives in raid0.  I have the following drives installed:
3 SATA (250gb each) with 2 in raid0
1 IDE (120gb)

The drives in raid0 contain the windows 7 installation.  The 3rd SATA drive has the new ubuntu installation (at least I think it does).  The IDE has windows XP (which I'm able to select from grub).

I've searched and read similar posts but was unable to follow what was going on.

Here is a copy/paste of fdisk -l...
Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6eca6eca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14595   117234306    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c10bf36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4555ee38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       15021   120654087   83  Linux
/dev/sdd2           15021       30401   123541185+   5  Extended
/dev/sdd5           29839       30401     4522266   82  Linux swap / Solaris
/dev/sdd6           15021       29231   114139136   83  Linux
/dev/sdd7           29231       29838     4878336   82  Linux swap / Solaris


I saw other posts mention a /boot/grub/menu.list file but I see nothing close to that in /boot/grub/

Any ideas?

---

### Post by Chame_Wizard on 2010-06-30
How the hell can you lose a Winblows partition?

What does Gparted said?

---

### Post by darkod on 2010-06-30
I'm not sure it can detect fakeraid raid0 systems. And you have win7 on a system like that.
On top of that it says:

Disk /dev/sdc doesn't contain a valid partition table

That's one of your raid disks. Not sure whether this is because it can't recognize the raid0 or it really detects some problem/issue on it.

You have to note that linux sometimes detects problems on disks even when windows doesn't report them.

In theory, the dmraid package that handles fakeraid is included by default since 9.10 and it should recognize the array.

---

### Post by josec on 2010-06-30
> **darkod said:**
> I'm not sure it can detect fakeraid raid0 systems. And you have win7 on a system like that.
On top of that it says:

Disk /dev/sdc doesn't contain a valid partition table

That's one of your raid disks. Not sure whether this is because it can't recognize the raid0 or it really detects some problem/issue on it.

You have to note that linux sometimes detects problems on disks even when windows doesn't report them.

In theory, the dmraid package that handles fakeraid is included by default since 9.10 and it should recognize the array.

I'm not sure what fakeraid is.  I see messages after the bios screen that lists the drives and it still has two of them as raid members.

When I boot with the ubuntu installation cd I can mount the raid0 drives and browse files (so I believe everything is still there) but I cannot see them from the actual ubuntu installation.  I'm not sure what to make of this behavior but perhaps it will give someone some ideas.

I was looking at boot devices in the bios and noticed that I can only boot from the IDE drive or the raid0.  When I boot from the IDE drive grub gives me different options.  From the IDE I can boot to an older version of ubuntu (installed ages ago) or windows XP.  From the raid0 grub lets me choose from old ubuntu, new ubuntu and windows XP.  I should note that at one point the IDE drive and the non-raid0 sata drive were in another box with ubuntu and windows xp installed.

---

### Post by darkod on 2010-06-30
The term fakeraid is used for motherboard BIOS raid. It is not true hardware raid, so it got called fakeraid. Most probably you are using raid settings in BIOS and not separate raid hardware controller.

Maybe you should have installed ubuntu with the alternate cd. You need to use that when installing ubuntu onto the raid array. Not sure in a case like this when it's on separate disk. But using the alternate cd might have helped to recognize the raid array properly and set up grub2.
And why did you put grub2 on the raid MBR, why not use the MBR of the ubuntu disk?

---

### Post by josec on 2010-06-30
> **darkod said:**
> The term fakeraid is used for motherboard BIOS raid. It is not true hardware raid, so it got called fakeraid. Most probably you are using raid settings in BIOS and not separate raid hardware controller.

Maybe you should have installed ubuntu with the alternate cd. You need to use that when installing ubuntu onto the raid array. Not sure in a case like this when it's on separate disk. But using the alternate cd might have helped to recognize the raid array properly and set up grub2.
And why did you put grub2 on the raid MBR, why not use the MBR of the ubuntu disk?

I don't think any changes were made to the raid0 disks/partitions.  What I thought I was doing was partitioning the 3rd sata disk and installing it on there.  To be honest I'm not sure where grub ended up since I went with the automatic option.

What are some things I could do to troubleshoot and at least figure out what went where?

---

### Post by josec on 2010-06-30
> **Chame_Wizard said:**
> How the hell can you lose a Winblows partition?

What does Gparted said?

Here are screenshots from gparted:

[http://i.imgur.com/kZcay.png](http://i.imgur.com/kZcay.png)  /dev/sda
[http://i.imgur.com/z1Kcx.png](http://i.imgur.com/z1Kcx.png) /dev/sdb
[http://i.imgur.com/BaWDa.png](http://i.imgur.com/BaWDa.png) /dev/sdc
[http://i.imgur.com/Szuqz.png](http://i.imgur.com/Szuqz.png) /dev/sdd

It looks like sda and sdb are/were the raid0 drives, but it's saying unallocated.  Am I screwed?

Also, when I ran gparted from the terminal it had these messages:
Can't have a partition outside the disk!
/dev/sdb: unrecognised disk label

---

### Post by wilee-nilee on 2010-06-30
Post the bootscript in my signature in code tags as described.

---

### Post by josec on 2010-06-30
> **wilee-nilee said:**
> Post the bootscript in my signature in code tags as described.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/sdd and looks for 
    (UUID=c7938c11-59ff-49c2-b44a-ea8b2b84352d)/boot/grub.

sda1: _________________________________________________________________________

    File system:       isw_raid_member
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'isw_raid_member'

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 HPFS/NTFS

/dev/sda1 ends after the last sector of /dev/sda

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   241,308,236   241,308,174  83 Linux
/dev/sdc2         241,309,694   488,392,064   247,082,371   5 Extended
/dev/sdc5         479,347,533   488,392,064     9,044,532  82 Linux swap / Solaris
/dev/sdc6         241,309,696   469,587,967   228,278,272  83 Linux
/dev/sdc7         469,590,016   479,346,687     9,756,672  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   234,468,674   234,468,612   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1                                               isw_raid_member                               
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc1        c7938c11-59ff-49c2-b44a-ea8b2b84352d   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        12311281-de75-4bb5-8046-5a5fa16c5f3c   swap                                     
/dev/sdc6        24418dac-d572-44bb-915e-b4ef5901e2c2   ext4                                     
/dev/sdc7        2d499afd-58ec-4db2-a844-cc41447ac951   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        A4484E0A484DDBA4                       ntfs                                     
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc6        /                        ext4       (rw,errors=remount-ro)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set c7938c11-59ff-49c2-b44a-ea8b2b84352d
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c7938c11-59ff-49c2-b44a-ea8b2b84352d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c7938c11-59ff-49c2-b44a-ea8b2b84352d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set c7938c11-59ff-49c2-b44a-ea8b2b84352d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c7938c11-59ff-49c2-b44a-ea8b2b84352d ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set a4484e0a484ddba4
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=c7938c11-59ff-49c2-b44a-ea8b2b84352d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=12311281-de75-4bb5-8046-5a5fa16c5f3c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  13.7GB: boot/grub/core.img
  13.7GB: boot/grub/grub.cfg
    .4GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .4GB: initrd.img
    .5GB: vmlinuz

=========================== sdc6/boot/grub/grub.cfg: ===========================

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
set root='(hd2,6)'
search --no-floppy --fs-uuid --set 24418dac-d572-44bb-915e-b4ef5901e2c2
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
set root='(hd2,6)'
search --no-floppy --fs-uuid --set 24418dac-d572-44bb-915e-b4ef5901e2c2
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
    set root='(hd2,6)'
    search --no-floppy --fs-uuid --set 24418dac-d572-44bb-915e-b4ef5901e2c2
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=24418dac-d572-44bb-915e-b4ef5901e2c2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,6)'
    search --no-floppy --fs-uuid --set 24418dac-d572-44bb-915e-b4ef5901e2c2
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=24418dac-d572-44bb-915e-b4ef5901e2c2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,6)'
    search --no-floppy --fs-uuid --set 24418dac-d572-44bb-915e-b4ef5901e2c2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,6)'
    search --no-floppy --fs-uuid --set 24418dac-d572-44bb-915e-b4ef5901e2c2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c7938c11-59ff-49c2-b44a-ea8b2b84352d
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c7938c11-59ff-49c2-b44a-ea8b2b84352d ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdc1)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set c7938c11-59ff-49c2-b44a-ea8b2b84352d
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c7938c11-59ff-49c2-b44a-ea8b2b84352d ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Microsoft Windows XP Professional (on /dev/sdd1)" {
    insmod ntfs
    set root='(hd3,1)'
    search --no-floppy --fs-uuid --set a4484e0a484ddba4
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=24418dac-d572-44bb-915e-b4ef5901e2c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=2d499afd-58ec-4db2-a844-cc41447ac951 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc6: Location of files loaded by Grub: ===================


 136.5GB: boot/grub/core.img
 216.1GB: boot/grub/grub.cfg
 136.5GB: boot/initrd.img-2.6.32-21-generic
 136.5GB: boot/vmlinuz-2.6.32-21-generic
 136.5GB: initrd.img
 136.5GB: vmlinuz

================================ sdd1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
```

---

### Post by wilee-nilee on 2010-06-30
Anything raid is beyond my knowledge and generally is not read correctly by the script, I believe, but having it available might show something that darkod or others who are more familiar can help with.

---

### Post by josec on 2010-06-30
> **wilee-nilee said:**
> Anything raid is beyond my knowledge and generally is not read correctly by the script, I believe, but having it available might show something that darkod or others who are more familiar can help with.

Thanks for trying!

I still think it's odd that I can browse that drive from the installation CD but can't from the actual ubuntu installation.  Apparently all the files are still there, I just don't know what it would take to boot from it.

---

### Post by ronparent on 2010-06-30
This may be too simple but its worth a try. You have a grub MBR on sdd that points to 9.10 installed in sdc1. Have you tried setting sdd as boot in bios? It should default boot to 9.10 on sdc1. Since it is also using a grub2, you could run > sudo update grub This should find all the systems installed on your system. Once you can boot to everything, you can investigate the grub2 on sda??? To boot from a raid to a raid partition the grub2 should be installed to /dev/mappar/<YourRaidArray>. Of course boot info script may not be reporting that correctly.

I don't think there is anything wrong with the new install or windows 7 since you installed 10.04 to sdc6. 

Incidently, you don't need 3 swap parittions - one will serve both ubuntu installs. Post what you discover.

---

### Post by ronparent on 2010-06-30
One more concern. Win 7 doesn't appear to have a valid boot loader. While loaded into either 9.10 or 10.04 you might want to investigate what the raid contains. The lack of a valid OS could explain why it doesn't show up in the grub menu.

---

### Post by josec on 2010-06-30
> **ronparent said:**
> One more concern. Win 7 doesn't appear to have a valid boot loader. While loaded into either 9.10 or 10.04 you might want to investigate what the raid contains. The lack of a valid OS could explain why it doesn't show up in the grub menu.

update-grub reports 
```
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sdc1
Found Microsoft Windows XP Professional on /dev/sdd1

```This was from the 10.04 install. 

How should I investigate what the raid contains?  From 10.04 system->administration->disk utility shows the following: [http://i.imgur.com/vdUUO.png](http://i.imgur.com/vdUUO.png) and [http://i.imgur.com/Nyw4f.png](http://i.imgur.com/Nyw4f.png)

Not sure what to make of that...

---

### Post by josec on 2010-07-01
Ok, PROBLEM SOLVED!!!

Since you guys seemed to find the raid aspect to be the most odd I decided to look into it.  Found out there's a utility called dmraid.  I still don't understand what it does but when I ran it (shown below) it made it possible to mount the drive in the installed ubunutu (previously I could only do this from the CD).  Once the drive was mounted I ran update-grub (and update-grub2 just to be safe :)) and it found the windows 7 loader (with memory leaks?). 

After that I rebooted and found the windows 7 loader in the menu and tried it out.  Everything works as expected now!

```
josec@josec-desktop:~$ sudo dmraid -ay -v
RAID set "isw_bdeghcbajg_Volume0" was activated
INFO: Activating GROUP raid set "isw_bdeghcbajg"
RAID set "isw_bdeghcbajg_Volume01" was activated
INFO: Activating partition raid set "isw_bdeghcbajg_Volume01"
josec@josec-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sdc1
Found Microsoft Windows XP Professional on /dev/sdd1
Found Windows 7 (loader) on /dev/mapper/isw_bdeghcbajg_Volume01
You have a memory leak (not released memory pool): [0x20d58a0]
You have a memory leak (not released memory pool): [0x1c5f8a0]
You have a memory leak (not released memory pool): [0x1d6dc80]
done
josec@josec-desktop:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sdc1
Found Microsoft Windows XP Professional on /dev/sdd1
Found Windows 7 (loader) on /dev/mapper/isw_bdeghcbajg_Volume01
You have a memory leak (not released memory pool): [0x16648a0]
You have a memory leak (not released memory pool): [0x19f78a0]
You have a memory leak (not released memory pool): [0x1e39c80]
done
```

Thanks for everything!  I was definitely lost going into this but managed to find my way :)

---

