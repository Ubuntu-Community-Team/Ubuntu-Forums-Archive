---
title: "Grub2 Kills windows boot sector"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Thomas_Osborn on 2011-04-30
Hello All
 
Been away from linux for a few years thaught id come back and give it a try again. I have Win7 on sda and installed 11.4 Ubuntu on sdb. Grub2 Over wrote the boot sector for windows so windows wouldnt show in the boot menu. I repaired that after some research and then tried it again with 10.4 LTS version of Ubuntu. Same thing. Now ive fixed windows boot sector a second time and im ready for round 3. Any hints on how to get grub2 to boot both OS's? Ubuntu 10.4 is still on sdb I think i should just need to re-install grub2 But how to do it without Killing the windows boot sector? Any Ideas would be appreciated. Thanks

---

### Post by manzdagratiano on 2011-04-30
Normally when you install grub, it automatically detects all the OSes on the system - and Windows is no exception. You can leave the Windows drive untouched, and install grub2 to the MBR of sdb - you can select that during the installation process, but since you have Ubuntu already, just boot off a LiveCD/LiveUSB and then follow this guide:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Just go with the `SIMPLEST' method, and you should be in business!

I know that sometimes setting up GNU/Linux can be hard, but once it is ready, you will not be disappointed!

---

### Post by oldfred on 2011-04-30
Are you discussing boot sector (partiiton) or MBR drive.

With default install, grub usually defaults to install to sda which most users use to boot and want to then boot with grub2.

But if you  have two drives, you probably want to leave the windows boot loader in the MBR of sda, and install grub2's boot loader in sdb and change BIOS to boot sdb as grub lets you choose which to boot. 

Only if you use manual install or whatever they call it now do you get the choice on where to install grub2's boot loader.

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

If you have an install already you just need to install grub2's boot loader to sdb.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sdb's MBR:
#Find linux partition, change sdb5 if not correct:
sudo fdisk -l
#confirm that linux is sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb

Change BIOS to boot sdb.
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by MAFoElffen on 2011-04-30
+1 & +1 on the above 2 posts... AND-- I multi-boot across multiple drves and muliple partions of both semi=permanent and removable drives.  My advice on installing to drives that already have windows on them?  

**I start up on a GParted LiveCD and move the Windows Partion back a sector before I do an Ubuntu Install!**

Don't ask me why, but I have had much too many nightmare adventures before I started doing this AND have not had a single problem since.  I read this back in the original grub days that it needed the first sector for room for itself - so to start the first partition after the first sector/not on the first sector...  I then install grub to /dev/sda/ and... no problems.

My personal preference is Grub2 boot and menu, but I am familiar with them and they are easy for me to manipulate.  I could have left them all as "separate" drives as discribed above > Bios booted them... but updates down the road of "U" are going to update the grub during the update process anyway... And doing that every time you boot is a pain.

---

### Post by Thomas_Osborn on 2011-04-30
I had time to try the easy option before i left for work and it returned an error about /dev not being mounted when i ran update grub. Im going to read through the whole tutorial for a full understanding of it and try it again tonight when i get home. I appreciate the help folks.

---

### Post by Thomas_Osborn on 2011-05-01
Well folks I have tried the advise in this thread and appreciate youre help. On the negative side grub still wont recognize win7 but on the plus side i can change the boot order in the bios and boot either os. The advanced install tutorial did show where i made several mistake though, mostly by not reading everything through but there graphics work against simplicity. Ill come back to this tonight and try again.

---

### Post by oldfred on 2011-05-01
If the windows is working on selecting from BIOS, this should find your windows and give you a choice in the grub menu.

```

sudo update-grub
```

Grub's os-prober normally only finds working windows. And grub will only boot a working copy of windows.

---

### Post by Thomas_Osborn on 2011-05-01
> **oldfred said:**
> If the windows is working on selecting from BIOS, this should find your windows and give you a choice in the grub menu.

```

sudo update-grub
```

Grub's os-prober normally only finds working windows. And grub will only boot a working copy of windows.

This option tells me there is a broken copy of Linux on sda where there is a working copy of win 7. Also one of the commands from the above tutorials told me something about a raid bit being set. I have no raid arrays and can't seem to reproduce the error message a second time or I would post it.

Thanks for all who are trying to help.

---

### Post by wilee-nilee on 2011-05-01
This will help in that it will give us pertinent info to understand exactly what's going on.

So from a booted live Ubuntu cd or thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by orion2001 on 2011-05-01
Thomas, I'm a complete linux noob, but I think that it might be useful to boot using a liveCD and then type 

sudo fdisk -l

in a terminal window. Check if it spits out any errors for the drive on which Windows is installed on. I had an issue with Ubuntu not detecting my Windows 7 install because it somehow had GPT data in the bootsector, preventing Ubuntu/Gparted from recognizing the install and the contents of that drive.

I ended up using Rob's FixParts tool to fix the issue. Just a thought in case that is what might be causing Ubuntu to not see your Win 7 install.

---

### Post by Thomas_Osborn on 2011-05-02
Ok Here it is the results from the script.


```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   156,299,263   156,092,416   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   151,466,891   151,464,844  83 Linux
/dev/sdb2         151,468,030   156,301,311     4,833,282   5 Extended
/dev/sdb5         151,468,032   156,301,311     4,833,280  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   320,144,511   320,142,464   7 HPFS/NTFS
/dev/sdc2         320,145,406   488,396,799   168,251,394   5 Extended
/dev/sdc5         320,145,408   481,456,127   161,310,720  83 Linux
/dev/sdc6         481,458,176   488,396,799     6,938,624  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C8AC6B2CAC6B13EA                       ntfs       System Reserved               
/dev/sda2        648876EA8876BA5E                       ntfs                                     
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        b113fc49-ad15-42a4-8081-3028c90f0ef6   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        e7eb0b07-b419-4253-a82f-b482cd9d1162   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7E0C44B90C446E69                       ntfs       My Music                      
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        0a4c7630-8844-4cdc-810f-f3f7b2b5b40a   ext4                                     
/dev/sdc6        80e3ff38-aa67-4983-a2e4-eba91c6a3f60   swap                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/648876EA8876BA5E  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

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
search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
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
search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b113fc49-ad15-42a4-8081-3028c90f0ef6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b113fc49-ad15-42a4-8081-3028c90f0ef6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=b113fc49-ad15-42a4-8081-3028c90f0ef6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=b113fc49-ad15-42a4-8081-3028c90f0ef6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sdc5)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 0a4c7630-8844-4cdc-810f-f3f7b2b5b40a
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=0a4c7630-8844-4cdc-810f-f3f7b2b5b40a ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sdc5)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 0a4c7630-8844-4cdc-810f-f3f7b2b5b40a
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=0a4c7630-8844-4cdc-810f-f3f7b2b5b40a ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=b113fc49-ad15-42a4-8081-3028c90f0ef6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e7eb0b07-b419-4253-a82f-b482cd9d1162 none            swap    sw              0       0
# swap was on /dev/sdc6 during installation
UUID=80e3ff38-aa67-4983-a2e4-eba91c6a3f60 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  58.1GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
  13.4GB: boot/initrd.img-2.6.32-28-generic
   1.0GB: boot/initrd.img-2.6.38-8-generic
  58.1GB: boot/vmlinuz-2.6.32-28-generic
  58.1GB: boot/vmlinuz-2.6.38-8-generic
  13.4GB: initrd.img
  58.1GB: vmlinuz

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 0a4c7630-8844-4cdc-810f-f3f7b2b5b40a
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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 0a4c7630-8844-4cdc-810f-f3f7b2b5b40a
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 0a4c7630-8844-4cdc-810f-f3f7b2b5b40a
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=0a4c7630-8844-4cdc-810f-f3f7b2b5b40a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 0a4c7630-8844-4cdc-810f-f3f7b2b5b40a
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=0a4c7630-8844-4cdc-810f-f3f7b2b5b40a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 0a4c7630-8844-4cdc-810f-f3f7b2b5b40a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 0a4c7630-8844-4cdc-810f-f3f7b2b5b40a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=b113fc49-ad15-42a4-8081-3028c90f0ef6 ro splash quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b113fc49-ad15-42a4-8081-3028c90f0ef6
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=b113fc49-ad15-42a4-8081-3028c90f0ef6 ro single splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=0a4c7630-8844-4cdc-810f-f3f7b2b5b40a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=80e3ff38-aa67-4983-a2e4-eba91c6a3f60 none            swap    sw              0       0

=================== sdc5: Location of files loaded by Grub: ===================


 187.6GB: boot/grub/core.img
 230.6GB: boot/grub/grub.cfg
 164.4GB: boot/initrd.img-2.6.32-28-generic
 187.6GB: boot/vmlinuz-2.6.32-28-generic
 164.4GB: initrd.img
 187.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  59 aa 95 9e 7c eb 29 67  e6 ab 2e 82 86 ce 83 8b  |Y...|.)g........|
00000010  ae a9 b4 53 5b 37 69 3d  63 54 7e 0f 13 4e b5 91  |...S[7i=cT~..N..|
00000020  2a 9a b6 13 f5 e4 ed d6  e5 00 00 0b be 95 40 25  |*.............@%|
00000030  70 34 6e b4 9e a4 4a fd  09 88 70 14 35 8c 99 b2  |p4n...J...p.5...|
00000040  b2 26 0e 0b 0b 06 e6 a9  93 2b 4c 6c 82 8e d5 29  |.&.......+Ll...)|
00000050  86 a3 e1 73 1a 81 0d 72  c7 d8 4e 23 de 06 cb ba  |...s...r..N#....|
00000060  cd 33 60 14 0b 10 3e 11  06 5a 43 2b c0 b8 c1 d6  |.3`...>..ZC+....|
00000070  94 5d 9b 13 bd 5d 4d f0  7c 21 17 d1 2a 8b 22 b3  |.]...]M.|!..*.".|
00000080  35 c2 a7 1d d6 23 f2 43  5a f2 96 dc c2 4b ff fb  |5....#.CZ....K..|
00000090  b2 04 32 86 e4 37 5e 59  9b 0c 43 d2 96 6d 1b 43  |..2..7^Y..C..m.C|
000000a0  3c 66 f6 13 f9 a3 69 47  99 3d 02 14 b2 6c cc f4  |<f....iG.=...l..|
000000b0  8e a9 3d b7 d5 b5 d3 f9  6d 4a 36 12 cf d4 e2 2d  |..=.....mJ6....-|
000000c0  f4 fa 5a 43 2e 8f b8 b8  b9 91 94 c3 12 74 bb ee  |..ZC.........t..|
000000d0  bb b4 f5 ce 00 00 92 b6  43 80 d9 6e 67 2f cb ce  |........C..ng/..|
000000e0  00 9c 39 50 f4 29 b6 73  11 26 2c e5 b9 e1 d0 87  |..9P.).s.&,.....|
000000f0  ab 8e 52 43 61 70 61 34  15 09 b8 cf 30 98 37 df  |..RCapa4....0.7.|
00000100  ae 99 69 1d 6e b0 a5 80  95 54 d2 1d df ac 47 a4  |..i.n....T....G.|
00000110  29 a3 35 39 b8 66 49 1e  63 3d 4c ca e3 fd d9 e6  |).59.fI.c=L.....|
00000120  ef 7e 6b 95 db 77 91 9a  39 8d 02 29 19 55 45 8a  |.~k..w..9..).UE.|
00000130  b2 52 23 96 3d dd 08 50  4f 6f 6c b3 3e e5 a3 93  |.R#.=..POol.>...|
00000140  29 30 e4 24 d2 19 c7 65  34 62 74 b0 b6 24 20 38  |)0.$...e4bt..$ 8|
00000150  83 42 88 0b 38 77 59 8e  96 0f 08 39 12 45 1a 96  |.B..8wY....9.E..|
00000160  16 1f 62 ce 8d 85 94 c8  ab fb cc 00 07 7c 61 86  |..b..........|a.|
00000170  d4 a0 61 7e d2 7d a8 9f  30 80 26 54 43 35 d4 67  |..a~.}..0.&TC5.g|
00000180  6b 6a c1 fe 98 4a dc c4  4f aa aa d5 a6 44 25 0f  |kj...J..O....D%.|
00000190  2f 86 2a 95 0c 48 1f 49  33 f1 18 37 da 53 48 7a  |/.*..H.I3..7.SHz|
000001a0  37 0d 50 5b e1 ed 91 ea  c5 65 69 8e f2 45 63 d8  |7.P[.....ei..Ec.|
000001b0  2e 70 27 4d 90 4f 74 22  d3 a3 25 3c 6d 8e 00 fe  |.p'M.Ot"..%<m...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c0 49 00 00 00  |............I...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```And Also fdisk -l

```
 Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf586f586

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        9730    78046208    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe83e5d8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9429    75732422   83  Linux
/dev/sdb2            9429        9730     2416641    5  Extended
/dev/sdb5            9429        9730     2416640   82  Linux swap / Solaris

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ceb8ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19929   160071232    7  HPFS/NTFS
/dev/sdc2           19929       30402    84125697    5  Extended
/dev/sdc5           19929       29970    80655360   83  Linux
/dev/sdc6           29970       30402     3469312   82  Linux swap / Solaris

``` 

Thanks again folks

---

### Post by wilee-nilee on 2011-05-02
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe **/boot/grub/core.img**

I think this is your problem, So to fix this we need the boot flag moved from sda1 to sda2 do this with gparted right click sda2 manage flags then boot, also you don't need a boot flag for linux generally remove it from the sdb1 partition.

Then boot the W7 disc go to the command line and run.
bootrec.exe /fixboot

Then boot back to Ubuntu, move the flag back to sda1, then run 
sudo update-grub 
and see if windows shows.

Now you can run the script again for yourself if this does not work, look at the stanza I posted and see if the highlighted /boot/grub/core.img is still there we want that gone.

You can also run the repair in the W7 booted disc as well, it takes longer and can be needed to be run three times to fix stuff, hopefully the fixboot alone, will clean it up and you will be on the road again.

The broken ubuntu you mention must be this grub stuff in sda2, there is no Ubuntu install there on that HD.

---

### Post by Thomas_Osborn on 2011-05-05
Sorry about not getting back sooner. I crashed the whole computer and had to rebuild all the partitions. My DVD drive fail in the process so my computer has been down. But now i am back at the beginning and starting all over again.

---

