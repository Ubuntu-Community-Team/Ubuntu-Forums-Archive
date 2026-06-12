---
title: "grub2 upgrade"
date: 2010-02-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by darco on 2010-02-04
This isnt necessarily a Lucid issue but I figured most here know grub2 better than the rest. I am running Linux Mint 8 which is using the grub2 1.97 beta 4 version. I was itching to update to the current version (dont ask) so I went ahead and updated the source list to the lucid repos. I chose the option to upgrade grub2. During the install, it asked me a host of options on how to upgrade, I chose the "maintainers version". It also asked which of my partition to install it to. I chose sda4 where my /root partition is. My windows mbr is on sda1. After reboot, got the grub rescue prompt. I loaded the livecd thinking grub just needed to be reinstalled. Well it did reinstall but it gave me back 1.97. 
What did I do wrong? 
thxs

---

### Post by lindsay7 on 2010-02-05
look in this file, it should tell you what you grub cfg file looks like

/etc/grub.d

Have you run sudo update-grub


Take a look at this site

[https://wiki.edubuntu.org/Grub2](https://wiki.edubuntu.org/Grub2)

---

### Post by darco on 2010-02-05
I ran this command:

```
 grub-install -v
grub-install (GNU GRUB 1.98~20100128-1ubuntu2)
  
```

on reboot, the grub menu still shows 1.97 beta 4.

---

### Post by Sef on 2010-02-05
I think that there is a problem updating it.  On upgrades, it says to click the boxes for grub to see, but it always crashes and does not update.

---

### Post by darco on 2010-02-05
well at this point should I assume I AM running 1.98? If so, Ill take care of the boot screen later.

---

### Post by dino99 on 2010-02-05
see grub2 doc.

grub2 works with : os-prober, grub-mkconfig and update-grub2

---

### Post by kansasnoob on 2010-02-05
> **darco said:**
> This isnt necessarily a Lucid issue but I figured most here know grub2 better than the rest. I am running Linux Mint 8 which is using the grub2 1.97 beta 4 version. I was itching to update to the current version (dont ask) so I went ahead and updated the source list to the lucid repos. I chose the option to upgrade grub2. During the install, it asked me a host of options on how to upgrade, I chose the "maintainers version". It also asked which of my partition to install it to. I chose sda4 where my /root partition is. My windows mbr is on sda1. After reboot, got the grub rescue prompt. I loaded the livecd thinking grub just needed to be reinstalled. Well it did reinstall but it gave me back 1.97. 
What did I do wrong? 
thxs

I don't think you're quite understanding "mbr":

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

To prevent a bunch of guesswork just post the output of the Boot Info script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by xebian on 2010-02-05
> **darco said:**
> This isnt necessarily a Lucid issue but I figured most here know grub2 better than the rest. I am running Linux Mint 8 which is using the grub2 1.97 beta 4 version. I was itching to update to the current version (dont ask) so I went ahead and updated the source list to the lucid repos. I chose the option to upgrade grub2. During the install, it asked me a host of options on how to upgrade, I chose the "maintainers version". It also asked which of my partition to install it to. I chose sda4 where my /root partition is. My windows mbr is on sda1. After reboot, got the grub rescue prompt. I loaded the livecd thinking grub just needed to be reinstalled. Well it did reinstall but it gave me back 1.97. 
What did I do wrong? 
thxs

You need to ask yourself which livecd you used?  If what you used has the 1.97 b4 version then it's what's going to be installed.

---

### Post by darco on 2010-02-05
Yup, thats it. I used the LM Livecd....WHat can I do at this point?

```
 ============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - x64 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe868f6fc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   553,953,329   553,953,267   7 HPFS/NTFS
/dev/sda2         577,022,670   976,768,064   399,745,395  83 Linux
/dev/sda3         553,953,330   554,483,474       530,145  82 Linux swap / Solaris
/dev/sda4         554,483,475   577,022,669    22,539,195  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00017ea3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   345,092,264   345,092,202   7 HPFS/NTFS
/dev/sdb2    *    345,092,265   531,880,019   186,787,755  83 Linux
/dev/sdb3         533,835,775   554,803,199    20,967,425   f W95 Ext d (LBA)
/dev/sdb5         533,835,776   554,803,199    20,967,424   7 HPFS/NTFS
/dev/sdb4         554,804,775   976,768,064   421,963,290   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="C684A28884A27B17" LABEL="darco" TYPE="ntfs" 
/dev/sda2: UUID="741f6752-f896-44df-8c8b-992d00314b83" TYPE="ext4" 
/dev/sda3: UUID="cca43b7f-4d59-4de3-b938-0f5d2975bc61" TYPE="swap" 
/dev/sda4: UUID="89998ee1-abb7-482a-a30c-d7f8ebd67425" TYPE="ext4" 
/dev/sdb1: UUID="4D0F7A76155EFB8F" LABEL="Folders" TYPE="ntfs" 
/dev/sdb2: UUID="e1e70dd5-7b91-455e-b60a-22d0a17ba535" TYPE="ext4" 
/dev/sdb4: UUID="159D9B604228267B" LABEL="Storage" TYPE="ntfs" 
/dev/sdb5: UUID="724218F94218C42F" LABEL="Page" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda4 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/darco/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=darco)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root=(hd0,4)
search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd0,4)
search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc6-generic (/dev/sda4)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc6-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single 
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc5-generic (/dev/sda4)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc5-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single 
	initrd	/boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.32-9-generic (/dev/sda4)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.32-9-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-9-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.32-9-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.32-9-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single 
	initrd	/boot/initrd.img-2.6.32-9-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c684a28884a27b17
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro quiet splash pci=routeirq
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc5-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro quiet splash pci=routeirq
	initrd /boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc5-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single
	initrd /boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro quiet splash pci=routeirq
	initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single
	initrd /boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=741f6752-f896-44df-8c8b-992d00314b83 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=cca43b7f-4d59-4de3-b938-0f5d2975bc61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 283.8GB: boot/grub/grub.cfg
 283.8GB: boot/initrd.img-2.6.32-9-generic
 283.8GB: boot/initrd.img-2.6.33-020633rc5-generic
 283.8GB: boot/initrd.img-2.6.33-020633rc6-generic
 283.8GB: boot/vmlinuz-2.6.32-9-generic
 283.8GB: boot/vmlinuz-2.6.33-020633rc5-generic
 283.8GB: boot/vmlinuz-2.6.33-020633rc6-generic
 283.8GB: initrd.img
 283.8GB: initrd.img.old
 283.8GB: vmlinuz
 283.8GB: vmlinuz.old

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic" {
        recordfail
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro   quiet splash pci=routeirq
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	echo	Loading Linux 2.6.33-020633rc6-generic ...
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc5-generic" {
        recordfail
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux	/boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro   quiet splash pci=routeirq
	initrd	/boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc5-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	echo	Loading Linux 2.6.33-020633rc5-generic ...
	linux	/boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro   quiet splash pci=routeirq
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	echo	Loading Linux 2.6.32-10-generic ...
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c684a28884a27b17
	chainloader +1
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc5-generic (/dev/sda4) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro quiet splash
	initrd /boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc5-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single
	initrd /boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.32-9-generic (/dev/sda4) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.32-9-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro quiet splash
	initrd /boot/initrd.img-2.6.32-9-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.32-9-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.32-9-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single
	initrd /boot/initrd.img-2.6.32-9-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 176.6GB: boot/grub/grub.cfg
 176.6GB: boot/initrd.img-2.6.32-10-generic
 176.6GB: boot/initrd.img-2.6.33-020633rc5-generic
 176.6GB: boot/initrd.img-2.6.33-020633rc6-generic
 176.6GB: boot/vmlinuz-2.6.32-10-generic
 176.6GB: boot/vmlinuz-2.6.33-020633rc5-generic
 176.6GB: boot/vmlinuz-2.6.33-020633rc6-generic
 176.6GB: initrd.img
 176.6GB: initrd.img.old
 176.6GB: vmlinuz
 176.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |.c....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 04 00  |.....V.U.F...F..|
00000040  00 80 00 08 01 00 00 00  00 00 00 00 ff ff fa eb  |................|
00000050  07 f6 c2 80 75 02 b2 80  ea 5d 00 80 01 00 00 00  |....u....]......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  fc f6 68 e8 00 00 80 01  |...<.u....h.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 f3 a7 04 21 00 fe  |......?......!..|
000001d0  ff ff 83 fe ff ff ce aa  64 22 73 a1 d3 17 00 fe  |........d"s.....|
000001e0  ff ff 82 fe ff ff 32 a8  04 21 e1 16 08 00 00 fe  |......2..!......|
000001f0  ff ff 83 fe ff ff 13 bf  0c 21 bb eb 57 01 55 aa  |.........!..W.U.|
00000200

Unknown MBR on /dev/sdb

00000000  eb 63 90 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |.c..............|
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 01 8b  |.........|...t..|
00000040  4c 02 cd 13 ea 00 7c 00  00 eb fe 00 00 00 00 00  |L.....|.........|
00000050  00 00 00 00 00 00 00 00  00 00 00 80 01 00 00 00  |................|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  a3 7e 01 00 00 00 00 01  |...<.u...~......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 6a b0 91 14 80 fe  |......?...j.....|
000001d0  ff ff 83 fe ff ff a9 b0  91 14 ab 27 22 0b 00 fe  |...........'"...|
000001e0  ff ff 0f fe ff ff ff af  d1 1f 01 f0 3f 01 00 fe  |............?...|
000001f0  ff ff 07 fe ff ff 27 a6  11 21 1a a6 26 19 55 aa  |......'..!..&.U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by VMC on 2010-02-05
I would use Mint, since its on the first hard drive (sda4).

Chroot to mint using a LiveCD then grub-install from there.

---

### Post by xebian on 2010-02-05
What you can do?

Get rid of whatever that mint is and stick to [COLOR="DarkOrange"]genuine and original Ubuntu [/COLOR] :P

Since you want to have a newer grub2, boot into your lucid install and make it the boot loader.  
At the terminal (in Ubuntu of course),

  sudo grub-install /dev/sda  
  sudo update-grub

---

### Post by darco on 2010-02-05
> **VMC said:**
> I would use Mint, since its on the first hard drive (sda4).

Chroot to mint using a LiveCD then grub-install from there.

Thats what I did already and that is where the problem is, it installed 1.97.
thxs

---

### Post by darco on 2010-02-05
> **xebian said:**
> What you can do?

Get rid of whatever that mint is and stick to [COLOR="DarkOrange"]genuine and original Ubuntu [/COLOR] :P

Since you want to have a newer grub2, boot into your lucid install and make it the boot loader.  
At the terminal (in Ubuntu of course),

  sudo grub-install /dev/sda  
  sudo update-grub

Thats how it was a while back. I disconnected sda and installed Lucid to sdb, later after plugging back sda, Lucid Grub took over and was the primary menu but I didnt want that since Lucid was in Alpha stage.

---

### Post by VMC on 2010-02-05
> **darco said:**
> Thats what I did already and that is where the problem is, it installed 1.97.
thxs

According to you boot-info-script it didn't install grub to your mbr. 

What message are you using. Be specific.

---

### Post by darco on 2010-02-05
My system boots up fine. It just shows Grub 1.97 beta 4 instead of the 1.98 version I installed. I dont know why the bootscript says no mbr installed

---

### Post by dino99 on 2010-02-05
add this repo to synaptic:   ppa:fzielcke/grub-ppa

---

### Post by VMC on 2010-02-05
> **darco said:**
> My system boots up fine. It just shows Grub 1.97 beta 4 instead of the 1.98 version I installed. I dont know why the bootscript says no mbr installed

You are using an older version of boot-info-script. The newest is v50.

Look at the section labeled "Unknown MBRs/Boot Sectors/etc"

---

### Post by darco on 2010-02-05
new bootscript

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 554989355 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #4 for /boot/grub.
    Operating System:  Linux Mint 8 Helena - x64 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 345420361 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #2 for /boot/grub.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe868f6fc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   553,953,329   553,953,267   7 HPFS/NTFS
/dev/sda2         577,022,670   976,768,064   399,745,395  83 Linux
/dev/sda3         553,953,330   554,483,474       530,145  82 Linux swap / Solaris
/dev/sda4         554,483,475   577,022,669    22,539,195  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00017ea3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   345,092,264   345,092,202   7 HPFS/NTFS
/dev/sdb2    *    345,092,265   531,880,019   186,787,755  83 Linux
/dev/sdb3         533,835,775   554,803,199    20,967,425   f W95 Ext d (LBA)
/dev/sdb5         533,835,776   554,803,199    20,967,424   7 HPFS/NTFS
/dev/sdb4         554,804,775   976,768,064   421,963,290   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A4B0765CB0763540                       ntfs                                     
/dev/sda2        741f6752-f896-44df-8c8b-992d00314b83   ext4                                     
/dev/sda3        cca43b7f-4d59-4de3-b938-0f5d2975bc61   swap                                     
/dev/sda4        89998ee1-abb7-482a-a30c-d7f8ebd67425   ext4                                     
/dev/sdb1        4D0F7A76155EFB8F                       ntfs       Folders                       
/dev/sdb2        e1e70dd5-7b91-455e-b60a-22d0a17ba535   ext4                                     
/dev/sdb4        159D9B604228267B                       ntfs       Storage                       
/dev/sdb5        724218F94218C42F                       ntfs       Page                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext4       (rw)


=========================== sda4/boot/grub/grub.cfg: ===========================

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

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "LinuxMint, with Linux 2.6.33-020633rc6-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "LinuxMint, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	echo	Loading Linux 2.6.33-020633rc6-generic ...
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "LinuxMint, with Linux 2.6.33-020633rc5-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "LinuxMint, with Linux 2.6.33-020633rc5-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	echo	Loading Linux 2.6.33-020633rc5-generic ...
	linux	/boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "LinuxMint, with Linux 2.6.32-9-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.32-9-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-9-generic
}
menuentry "LinuxMint, with Linux 2.6.32-9-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	echo	Loading Linux 2.6.32-9-generic ...
	linux	/boot/vmlinuz-2.6.32-9-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-9-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a4b0765cb0763540
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro quiet splash pci=routeirq
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro quiet splash pci=routeirq
	initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single
	initrd /boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=741f6752-f896-44df-8c8b-992d00314b83 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=cca43b7f-4d59-4de3-b938-0f5d2975bc61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
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
set root=(hd1,2)
search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
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
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
insmod tga
if background_image /boot/grub/TulipStair_QueensHouse_Greenwich.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro   quiet splash pci=routeirq
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	echo	Loading Linux 2.6.33-020633rc6-generic ...
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro   quiet splash pci=routeirq
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	echo	Loading Linux 2.6.32-10-generic ...
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a4b0765cb0763540
	chainloader +1
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc6-generic (/dev/sda4) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=/dev/sda4 ro quiet splash
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc6-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=/dev/sda4 ro single
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc5-generic (/dev/sda4) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc5-generic root=/dev/sda4 ro quiet splash
	initrd /boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc5-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc5-generic root=/dev/sda4 ro single
	initrd /boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.32-9-generic (/dev/sda4) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.32-9-generic root=/dev/sda4 ro quiet splash
	initrd /boot/initrd.img-2.6.32-9-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.32-9-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.32-9-generic root=/dev/sda4 ro single
	initrd /boot/initrd.img-2.6.32-9-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 176.6GB: boot/grub/core.img
 176.6GB: boot/grub/grub.cfg
 176.6GB: boot/initrd.img-2.6.32-10-generic
 176.6GB: boot/initrd.img-2.6.33-020633rc6-generic
 176.6GB: boot/vmlinuz-2.6.32-10-generic
 176.6GB: boot/vmlinuz-2.6.33-020633rc6-generic
 176.6GB: initrd.img
 176.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf   
```

---

### Post by kansasnoob on 2010-02-05
**[COLOR="Red"]I posted this while you were posting your new Boot Script output so I need to look![/COLOR]**

Lets keep it simple:)

I don't know which of your drives is set to boot first in BIOS but it doesn't matter, look:

> No known boot loader is installed in the MBR of /dev/sda
No known boot loader is installed in the MBR of /dev/sdb


That's because you've been installing the bootloader to a partition rather than the mbr of the drive. That seldom works.

Now we know Vista is on sda1, Helena is on sda4, and Lucid is on sdb2. So if you haven't changed any settings in the BIOS I'd let Helena boot:

```
sudo mount /dev/sda4 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

If that shows any errors then run:

```
grub-install --recheck /dev/sda
```

Then exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then give sdb a readable mbr:

```
sudo mount /dev/sdb2 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sdb
```

Any errors:

```
grub-install --recheck /dev/sdb
```

And exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Whichever OS boots go to terminal and run:

```
sudo os-prober
```

```
sudo update-grub
```

Wait until it says done!

Reboot and enjoy (hopefully)!

---

### Post by kansasnoob on 2010-02-05
> **darco said:**
> new bootscript

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda4 and 
                       looks at sector 554989355 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #4 for /boot/grub.
    Operating System:  Linux Mint 8 Helena - x64 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb2 and 
                       looks at sector 345420361 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #2 for /boot/grub.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe868f6fc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   553,953,329   553,953,267   7 HPFS/NTFS
/dev/sda2         577,022,670   976,768,064   399,745,395  83 Linux
/dev/sda3         553,953,330   554,483,474       530,145  82 Linux swap / Solaris
/dev/sda4         554,483,475   577,022,669    22,539,195  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00017ea3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   345,092,264   345,092,202   7 HPFS/NTFS
/dev/sdb2    *    345,092,265   531,880,019   186,787,755  83 Linux
/dev/sdb3         533,835,775   554,803,199    20,967,425   f W95 Ext d (LBA)
/dev/sdb5         533,835,776   554,803,199    20,967,424   7 HPFS/NTFS
/dev/sdb4         554,804,775   976,768,064   421,963,290   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A4B0765CB0763540                       ntfs                                     
/dev/sda2        741f6752-f896-44df-8c8b-992d00314b83   ext4                                     
/dev/sda3        cca43b7f-4d59-4de3-b938-0f5d2975bc61   swap                                     
/dev/sda4        89998ee1-abb7-482a-a30c-d7f8ebd67425   ext4                                     
/dev/sdb1        4D0F7A76155EFB8F                       ntfs       Folders                       
/dev/sdb2        e1e70dd5-7b91-455e-b60a-22d0a17ba535   ext4                                     
/dev/sdb4        159D9B604228267B                       ntfs       Storage                       
/dev/sdb5        724218F94218C42F                       ntfs       Page                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /home                    ext4       (rw)


=========================== sda4/boot/grub/grub.cfg: ===========================

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

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "LinuxMint, with Linux 2.6.33-020633rc6-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "LinuxMint, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	echo	Loading Linux 2.6.33-020633rc6-generic ...
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "LinuxMint, with Linux 2.6.33-020633rc5-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "LinuxMint, with Linux 2.6.33-020633rc5-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	echo	Loading Linux 2.6.33-020633rc5-generic ...
	linux	/boot/vmlinuz-2.6.33-020633rc5-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "LinuxMint, with Linux 2.6.32-9-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux	/boot/vmlinuz-2.6.32-9-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-9-generic
}
menuentry "LinuxMint, with Linux 2.6.32-9-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	echo	Loading Linux 2.6.32-9-generic ...
	linux	/boot/vmlinuz-2.6.32-9-generic root=UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-9-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a4b0765cb0763540
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro quiet splash pci=routeirq
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro quiet splash pci=routeirq
	initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode) (on /dev/sdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single
	initrd /boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=89998ee1-abb7-482a-a30c-d7f8ebd67425 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=741f6752-f896-44df-8c8b-992d00314b83 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=cca43b7f-4d59-4de3-b938-0f5d2975bc61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
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
set root=(hd1,2)
search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
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
insmod ext2
set root=(hd1,2)
search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
insmod tga
if background_image /boot/grub/TulipStair_QueensHouse_Greenwich.tga ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro   quiet splash pci=routeirq
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.33-020633rc6-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	echo	Loading Linux 2.6.33-020633rc6-generic ...
	linux	/boot/vmlinuz-2.6.33-020633rc6-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro   quiet splash pci=routeirq
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
	set gfxpayload=keep
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	echo	Loading Linux 2.6.32-10-generic ...
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set e1e70dd5-7b91-455e-b60a-22d0a17ba535
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a4b0765cb0763540
	chainloader +1
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc6-generic (/dev/sda4) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=/dev/sda4 ro quiet splash
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc6-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc6-generic root=/dev/sda4 ro single
	initrd /boot/initrd.img-2.6.33-020633rc6-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc5-generic (/dev/sda4) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc5-generic root=/dev/sda4 ro quiet splash
	initrd /boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.33-020633rc5-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.33-020633rc5-generic root=/dev/sda4 ro single
	initrd /boot/initrd.img-2.6.33-020633rc5-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.32-9-generic (/dev/sda4) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.32-9-generic root=/dev/sda4 ro quiet splash
	initrd /boot/initrd.img-2.6.32-9-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.32-9-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 89998ee1-abb7-482a-a30c-d7f8ebd67425
	linux /boot/vmlinuz-2.6.32-9-generic root=/dev/sda4 ro single
	initrd /boot/initrd.img-2.6.32-9-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=e1e70dd5-7b91-455e-b60a-22d0a17ba535 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


 176.6GB: boot/grub/core.img
 176.6GB: boot/grub/grub.cfg
 176.6GB: boot/initrd.img-2.6.32-10-generic
 176.6GB: boot/initrd.img-2.6.33-020633rc6-generic
 176.6GB: boot/vmlinuz-2.6.32-10-generic
 176.6GB: boot/vmlinuz-2.6.33-020633rc6-generic
 176.6GB: initrd.img
 176.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf   
```

Well at a quick glance that looks good. What boots?

---

### Post by darco on 2010-02-05
Everything boots fine....its just that I installed 1.98 but on reboot the menu still shows 1.97 beta

---

### Post by VMC on 2010-02-05
> **darco said:**
> Everything boots fine....its just that I installed 1.98 but on reboot the menu still shows 1.97 beta

Since you have grub installed on the mbr of both hard drives, which one did you install 1.98 on?

---

### Post by darco on 2010-02-05
on my Mint partition...sda4....sdb2 already has 1.98 (lucid)

---

### Post by kansasnoob on 2010-02-05
If you're using Mint's grub it's still going to be the older version of grub2 :p

If you want Ubuntu's grub you're going to have to do one of two things.

#1. Change the BIOS to boot the Ubuntu drive first.

#2. Install the Ubuntu grub to the mbr of the boot drive, which is simple. Just boot into Ubuntu and run:

```
sudo grub-install /dev/sda
```

And:

```
sudo update-grub
```

---

### Post by darco on 2010-02-05
> **xebian said:**
> You need to ask yourself which livecd you used?  If what you used has the 1.97 b4 version then it's what's going to be installed.

Thanks xebian....I d/l the LL A2 livecd and from there I reinstalled grub and now I have grub2 1.98 on my Mint pc. It was only for the thrill.... ;)

> **kansasnoob said:**
> If you're using Mint's grub it's still going to be the older version of grub2 :p 

 Whys that if I updated it? .....

---

