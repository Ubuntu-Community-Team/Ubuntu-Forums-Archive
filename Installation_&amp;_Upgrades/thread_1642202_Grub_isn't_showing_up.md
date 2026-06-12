---
title: "Grub isn't showing up"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by billburn2 on 2010-12-10
I've been searching through threads related to my problem, and I've tried following the instructions in them, but there are too many things different between my setup and theirs for it to work.

I started out with Windows XP on C: and Ubuntu on D:   I liked Ubuntu enough, I wanted to make it my primary OS, so it boots Ubuntu by default through Grub, unless I tell it to go to Windows. 
So I load up the live CD, install Ubuntu on C: alongside WinXP, gave it 50 GB of space, let it do its thing, and restarted.
No Grub, just goes right to the WinXP loading screen.
So I've loaded up the live CD, and typed in "grub" it said grub wasn't installed, so I installed it (sudo apt-get install grub") 
And now:
```

grub
find /boot/grub/stage1
Error 15: file not found

```In the thread I read that was a lot like my problem, the helper said to post the results of ```
sudo fdisk -l
``` so I'm going to go ahead and guess it might be a good idea for me to do so as well:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08860886

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32795   263425413    7  HPFS/NTFS
/dev/sda2           32796       38914    49144833    5  Extended
/dev/sda5           32796       38914    49144832   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    7  HPFS/NTFS


```The other thread said to remove the boot flag from sda or sdb, I don't remember... but I tried that, and when I started my computer, it said something about an error, and to insert the system disk. SOOOO I went back into gparted and put the boot flag back on, and now my computer starts up windows no problem, so nothing got broken, but... I'm right back where I started.
I also tried supergrub, I wasn't 100% sure what I was doing, but I tried all the stuff that said Linux next to it, and none of them worked, but windows started just fine. 

I tried my best to figure it out without making a post about it, but it's obvious I didn't get far. I like to think I'm at least moderately tech-savvy, good at figuring things out on my own, but... yeah. I need help. Any help you guys can give would be superb.  If it worst comes to worst, I'll just reinstall Ubuntu on D: and make do.

---

### Post by sikander3786 on 2010-12-10
Welcome to the forums :-)

I admit I haven't read whole of your post.

What we need to see is output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would help us better understand your setup ;-)

---

### Post by billburn2 on 2010-12-10
I only glanced at the first few lines of that .txt file, and I already know that everything I knew was wrong :\
So, do you want the entire .txt file? It's ... really long. Just wanna make sure you don't only need the short summary and not the entire thing.
If you need the summary: 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

If you need it all... I'll wait till you say so, because the full file is 255 lines.

---

### Post by sikander3786 on 2010-12-10
Yes we want the complete Results.txt.

Paste it between code tags # as you did in your first post and it won't be long for this page ;-)

---

### Post by billburn2 on 2010-12-10
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   526,850,888   526,850,826   7 HPFS/NTFS
/dev/sda2         526,852,094   625,141,759    98,289,666   5 Extended
/dev/sda5         526,852,096   625,141,759    98,289,664  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        402C72282C72195C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a980f5f4-2ccd-4d91-a37f-969fbf65f330   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0458F8A658F8981E                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a980f5f4-2ccd-4d91-a37f-969fbf65f330 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a980f5f4-2ccd-4d91-a37f-969fbf65f330 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 402c72282c72195c
    drivemap -s (hd0) ${root}
    chainloader +1
}
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=a980f5f4-2ccd-4d91-a37f-969fbf65f330 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=dd97949b-35d9-4566-8ffb-0c0ae1340371 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 310.9GB: boot/grub/core.img
 312.9GB: boot/grub/grub.cfg
 313.4GB: boot/initrd.img-2.6.35-22-generic
 270.1GB: boot/vmlinuz-2.6.35-22-generic
 313.4GB: initrd.img
 270.1GB: vmlinuz
```

---

### Post by sikander3786 on 2010-12-10
The problem seems to lie here.

> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.


It should be installed to MBR of dev/sda and should look in sda5 for boot files.

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the second one it is just sda without an integer and not sda5.

Make sda your first boot device in Bios and boot. If it doesn't pick up Windows, from installed Ubuntu's terminal,

```
sudo update-grub
```

If you prefer to keep Windows bootloader on sda and want to install Grub to sdb instead,

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

But I would recommend to install Grub to sda instead. You may later need to remove Grub from MBR of sdb that way.

---

### Post by billburn2 on 2010-12-10
Okay, it said ```
Probing devices to guess BIOS drives. This may take a long time.

```, and it said that it was installing to hd0
And now it just says ```
grub>
``` so I'm taking that as meaning it was successful. In which case, thanks a billion! :D

Just to make sure, is this the part where I restart? I don't want to reboot if there are steps remaining :P

---

### Post by sikander3786 on 2010-12-10
It shoudn't say grub> :-k or it might. Not sure....

Reboot and try booting from the HDD, you installed Grub to. Lets see...

---

### Post by billburn2 on 2010-12-10
Grub loaded, it said ```
grub>
``` I tried "boot ubuntu" and it said ```
Error 8: Kernel must be loaded before booting.*
```

---

### Post by sikander3786 on 2010-12-10
Are you sure you are booting from the proper HDD. If you installed Grub to sda following the post above, you still contain Grub in MBR of sdb and that might give you a Grub rescue prompt like grub>. You need to boot from your first HDD.

So, re-check boot order in Bios. If boot order is ok and you are still unable to boot Ubuntu, once again boot an Ubuntu Live CD, run and post the new output of bootinfoscript.

---

### Post by billburn2 on 2010-12-10
I'm positive I booted from sda... 
Here's the results file
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,436,544   234,436,482   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   526,850,888   526,850,826   7 HPFS/NTFS
/dev/sdb2         526,852,094   625,141,759    98,289,666   5 Extended
/dev/sdb5         526,852,096   625,141,759    98,289,664  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0458F8A658F8981E                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        402C72282C72195C                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        a980f5f4-2ccd-4d91-a37f-969fbf65f330   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a980f5f4-2ccd-4d91-a37f-969fbf65f330 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a980f5f4-2ccd-4d91-a37f-969fbf65f330 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set a980f5f4-2ccd-4d91-a37f-969fbf65f330
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 402c72282c72195c
    drivemap -s (hd0) ${root}
    chainloader +1
}
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=a980f5f4-2ccd-4d91-a37f-969fbf65f330 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=dd97949b-35d9-4566-8ffb-0c0ae1340371 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 310.9GB: boot/grub/core.img
 312.9GB: boot/grub/grub.cfg
 310.9GB: boot/grub/stage2
 313.4GB: boot/initrd.img-2.6.35-22-generic
 270.1GB: boot/vmlinuz-2.6.35-22-generic
 313.4GB: initrd.img
 270.1GB: vmlinuz
```

---

### Post by sikander3786 on 2010-12-10
I apologize. You needed to perform those commands from 9.10, 10.04 or 10.10 Live CD but I think you used an old one. I should have mentioned that.

Now, you've installed both Grub2 and Grub-Legacy. You need to purge and re-install Grub as mentioned here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Secondly, I have noticed that your HDDs have switched now. What was sda previously is sdb now and vice versa. If you didn't change the jumper settings, I think you were playing around with Master/Slave settings in the Bios rather than changing Boot device.

Don't change those settings, purge grub as mentioned in the link above and re-install. Make sure your HDDs don't switch master/slave any more.

---

### Post by billburn2 on 2010-12-10
The first time I tried purging and reinstalling, it didn't work. It wouldn't mount the volume, or something to that effect. So I shut down, removed the secondary hard drive so all we had left was sda (all it was doing was distracting us and getting in the way), fired up the live CD, and purged and reinstalled grub.  After I rebooted, grub loaded up just fine, and I was able to choose what OS to launch.

Thank you for all your help!

---

### Post by sikander3786 on 2010-12-10
Glad to know that it is all sorted finally.

Did you re-connect your 2nd HDD? I hope there are no more problems :P

---

### Post by billburn2 on 2010-12-10
I re-connected my second HDD, and everything is still working just fine. All is well! Thank you for your help

---

### Post by sikander3786 on 2010-12-11
> **billburn2 said:**
> I re-connected my second HDD, and everything is still working just fine. All is well! Thank you for your help

You are Welcome. Glad to know that 'all is well' :-)

You can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

