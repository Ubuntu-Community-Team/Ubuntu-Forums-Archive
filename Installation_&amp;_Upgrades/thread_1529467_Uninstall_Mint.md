---
title: "Uninstall Mint"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by sqrooup on 2010-07-12
I have a dual boot system of Mint/Xubuntu; The GRUB is on Mint.
I wish to use the Xubuntu (it has my settings; I have a very low spec PC, the settings for Mint only give me low resolution), so I can free the 200GB that Mint is using.
I still have the ISO DVD for the Mint.

---

### Post by kansasnoob on 2010-07-12
> **sqrooup said:**
> I have a dual boot system of Mint/Xubuntu; The GRUB is on Mint.
I wish to use the Xubuntu (it has my settings; I have a very low spec PC, the settings for Mint only give me low resolution), so I can free the 200GB that Mint is using.
I still have the ISO DVD for the Mint.

If you can boot Xubuntu from Mint's grub then you should be able to put Xubuntu's grub in charge quite easily but it would be best to see the output of the Boot Info Script first:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That way I won't be guessing ;)

---

### Post by sqrooup on 2010-07-12
OK here is the RESULTS.txt for my hard drive

Edit; ignore the sdb, it is just a USB stick plugged at the time of the test, though I do not know why it says it is XP :confused:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

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

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - Main 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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

/dev/sda1    *          2,048   314,327,789   314,325,742  83 Linux
/dev/sda2         314,327,914   625,141,759   310,813,846   5 Extended
/dev/sda5         619,190,272   625,141,759     5,951,488  82 Linux swap / Solaris
/dev/sda6         314,327,916   613,233,179   298,905,264  83 Linux
/dev/sda7         613,233,243   619,177,229     5,943,987  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16039018496 bytes
75 heads, 40 sectors/track, 10442 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             40    31,326,207    31,326,168   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        55b63198-5e47-41bd-b360-a9fa4bece4a4   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f83b03cd-c79e-4a28-a6f3-dd4582c01474   swap                                     
/dev/sda6        1edfe074-af09-4ed2-856f-25990b6e484b   ext4                                     
/dev/sda7        cbaba1d5-697d-4420-8aed-21a29c414ada   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        590F-B4D5                              vfat       Lexar                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/Lexar             vfat       (rw,nosuid,nodev,uhelper=hal,uid=1000,umask=0077,shortname=winnt,utf8)


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
search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
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
search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda6) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1edfe074-af09-4ed2-856f-25990b6e484b
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1edfe074-af09-4ed2-856f-25990b6e484b ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set 1edfe074-af09-4ed2-856f-25990b6e484b
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=1edfe074-af09-4ed2-856f-25990b6e484b ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f83b03cd-c79e-4a28-a6f3-dd4582c01474 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 116.1GB: boot/grub/core.img
  62.4GB: boot/grub/grub.cfg
 116.1GB: boot/initrd.img-2.6.32-21-generic
 116.3GB: boot/initrd.img-2.6.32-22-generic
 116.2GB: boot/initrd.img-2.6.32-23-generic
 116.1GB: boot/vmlinuz-2.6.32-21-generic
 116.2GB: boot/vmlinuz-2.6.32-22-generic
 116.2GB: boot/vmlinuz-2.6.32-23-generic
 116.2GB: initrd.img
 116.3GB: initrd.img.old
 116.2GB: vmlinuz
 116.2GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 1edfe074-af09-4ed2-856f-25990b6e484b
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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 1edfe074-af09-4ed2-856f-25990b6e484b
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
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (/dev/sda6)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 1edfe074-af09-4ed2-856f-25990b6e484b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1edfe074-af09-4ed2-856f-25990b6e484b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Linux Mint 8 Helena, linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 1edfe074-af09-4ed2-856f-25990b6e484b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1edfe074-af09-4ed2-856f-25990b6e484b ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
menuentry "'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	linux /boot/vmlinuz-2.6.32-22-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro single
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 55b63198-5e47-41bd-b360-a9fa4bece4a4
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=55b63198-5e47-41bd-b360-a9fa4bece4a4 ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=1edfe074-af09-4ed2-856f-25990b6e484b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=cbaba1d5-697d-4420-8aed-21a29c414ada none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 166.3GB: boot/grub/core.img
 166.3GB: boot/grub/grub.cfg
 161.3GB: boot/initrd.img-2.6.31-14-generic
 161.2GB: boot/vmlinuz-2.6.31-14-generic
 161.3GB: initrd.img
 161.2GB: vmlinuz

```

---

### Post by kansasnoob on 2010-07-13
Sorry to take so long replying. But we can see now that Ubuntu is on sda1 and Mint is on sda6. You should also know that Ubuntu is using the SWAP on sda5, and Mint is using the SWAP on sda7, more about that later.

To hand grub back to Ubuntu (actually Xubuntu I guess) just boot into it and in Terminal run:

```
sudo grub-install /dev/sda
```

Should that produce any errors also run:

```
sudo grub-install --recheck /dev/sda
```

Then also:

```
sudo update-grub
```

Then of course reboot and you should find that Xubuntu is now in charge of boot. If so you can then use Gparted from your Xubuntu Live CD to delete and resize partitions.

Just remember that Xubuntu is on /dev/sda1 and it's SWAP is /dev/sda5. If it's necessary to move the SWAP on sda5 you may find that it's UUID has changed but we can easily fix that. To check it once you're all done just run the following commands:

```
sudo blkid -c /dev/null
```

```
cat /etc/fstab
```

```
cat  /etc/initramfs-tools/conf.d/resume
```

Then compare the SWAP UUID's as shown in this example (I've highlighted the SWAP UUID in red):

```
lance@lance-desktop:~$ sudo blkid -c /dev/null
[sudo] password for lance: 
/dev/sdb1: UUID="7cfd5b52-6ff7-41ac-a823-4a6c19e0ecb4" TYPE="ext4" 
/dev/sdb3: LABEL="This test case" UUID="5f555613-01f8-4c98-acc3-ca123cd81b06" TYPE="ext4" 
/dev/sdb5: UUID="8d9402a0-29a4-44c1-ab74-94e268865e8f" TYPE="swap" 
/dev/sdb6: LABEL="Maverick" UUID="4ac10d96-7aea-44f4-a69e-5dfa2a992b44" TYPE="ext4" 
/dev/sda1: LABEL="Maverick" UUID="b7a0df33-53e4-4f0d-856b-0da92ff0d743" TYPE="ext3" 
/dev/sda2: LABEL="Karmic" UUID="1332b9d0-cf18-4299-9094-12acbdac91ad" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="Lucid" UUID="d252929b-949d-432e-a18c-18f9ae770d28" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="Backups" UUID="594c3d40-2791-4c0a-8644-d9812545da2d" TYPE="ext3" 
/dev/sda6: LABEL="Pictures" UUID="8a3f6c83-cb52-4caf-96b8-5faf2c830453" TYPE="ext3" 
/dev/sda7: LABEL="Downloads" UUID="05289ee4-d681-4806-b6fd-aefd784f9323" TYPE="ext3" 
/dev/sda8: LABEL="Documents" UUID="571cfad8-68c7-4703-883e-c0baa2a381d4" TYPE="ext3" 
/dev/sda9: UUID="**[COLOR="Red"]80627269-1ccd-4774-b4ea-a5ef8824ffaa[/COLOR]**" TYPE="swap" 
/dev/sda10: LABEL="Isadora" UUID="f223fe5d-3acb-4d96-950c-62661ad8714b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Squeeze" UUID="0eec2831-7805-437e-a06e-e18ab3268e6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: UUID="f6062e12-09f1-4f19-b6c2-ad58812d6794" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: UUID="44728c55-0c3c-4640-87e7-677420aba8a5" TYPE="ext4" 
lance@lance-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# swap is on /dev/sda9
UUID=**[COLOR="Red"]80627269-1ccd-4774-b4ea-a5ef8824ffaa[/COLOR]** none            swap    sw                0       0
#/dev/sda5    /mnt/sda5 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda5       ext3    defaults          0       2
#/dev/sda6    /mnt/sda6 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda6       ext3    defaults          0       2     
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda8       ext3    defaults          0       2
lance@lance-desktop:~$ cat  /etc/initramfs-tools/conf.d/resume
RESUME=UUID=**[COLOR="Red"]80627269-1ccd-4774-b4ea-a5ef8824ffaa[/COLOR]**

```

If you find those don't match don't try to fix it, just post the results and I'll show you what to do next :)

Also, to drop Mint from the boot menu once you're done repartitioning just run this command once again:

```
sudo update-grub
```

Good luck.

---

