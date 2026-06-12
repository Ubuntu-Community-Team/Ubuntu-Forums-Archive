---
title: "Problem with GRUB2/Ubuntu update"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by libertin on 2010-05-14
Hi,
right now I got Ubuntu 10.04, Slackware 13.0 and VLOS 2.0 installed on my notebook. Since the grub-menu got messed up after installing VLOS, I completely reinstalled Ubuntu to set up GRUB anew (repairing didn't work somehow).
When rebooting after install, the menu did show all entries correctly and I could also boot all three of them.

Later, after I updated Ubuntu (including a regular kernel-update), the entries are messed up again: All entries were named like "Ubuntu-[kernelversion] (on [partition])" and if I try to boot those entries, which formerly were Slackware and VLOS, Ubuntu will load.
Ubuntu, VLOS and Slackware do all use the same /boot-Partition (sda1).
Using update-grub, os-prober identifies all installed distributions correctly, but the grub-menu on booting ain't changed.

What am I doing wrong?

---

### Post by kansasnoob on 2010-05-14
It may be helpful to see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by libertin on 2010-05-14
Here are the results

---

### Post by kansasnoob on 2010-05-14
Sorry, I dozed off.

I've dealt with a lot of boot problems but I've never seen this:

> ============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext4       (rw)
/dev/sda7        /extra/2ndhome           ext4       (rw)
/dev/sda12       /extra/3rdhome           ext4       (rw)
/dev/sda13       /extra/3rdroot           ext4       (rw)
/dev/sda6        /home                    ext4       (rw)
/dev/sda10       /extra/Spiele            ext4       (rw)
/dev/sda8        /extra/2ndroot           ext4       (rw)
/dev/sda11       /extra/Kram              ext4       (rw)


For that matter I see things recognized in grub.cfg that are not elsewhere:

```
"Ubuntu, mit Linux 2.6.33-02063303-generic (on /dev/sda13)"
```

```
Ubuntu, mit Linux 2.6.33-02063303-generic (on /dev/sda8)
```

Just beyond me :confused:

---

### Post by kansasnoob on 2010-05-14
Oh, and here's your RESULTS.txt in code tags (some people don't like opening attachments):

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Slackware 13.0.0.0.0
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Platte /dev/sda: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       787,184       787,122  83 Linux
/dev/sda2             787,246   976,768,064   975,980,819   5 Extended
/dev/sda5             787,248    30,089,744    29,302,497  83 Linux
/dev/sda6          30,089,808    69,159,824    39,070,017  83 Linux
/dev/sda7          69,159,888    98,462,384    29,302,497  83 Linux
/dev/sda8          98,462,448   137,532,464    39,070,017  83 Linux
/dev/sda9         137,532,528   147,299,984     9,767,457  82 Linux swap / Solaris
/dev/sda10        147,300,048   244,959,119    97,659,072  83 Linux
/dev/sda11        316,641,213   976,768,064   660,126,852  83 Linux
/dev/sda12        244,959,183   275,675,399    30,716,217  83 Linux
/dev/sda13        275,675,463   316,641,149    40,965,687  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       98ecc5b9-55bd-4455-a623-875bbc46783d   ext4       /extra/Spiele                 
/dev/sda11       b5a78ac9-543e-4337-ab8d-fae64305ad48   ext4       /extra/Kram                   
/dev/sda12       245c09c4-a928-4df3-8530-577097ed10b1   ext4                                     
/dev/sda13       22f6e439-96fc-4de0-b4ea-6a53e48f41e4   ext4                                     
/dev/sda1        f20b6ae6-d97c-4e85-a203-87ef397fe2b3   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1df5dde3-b676-45b1-a4ca-1d077c344fd3   ext4                                     
/dev/sda6        bde8dd2a-162e-471e-9d0e-3b72d197010d   ext4       /extra/ubuhome                
/dev/sda7        54ca12f0-a691-48ab-addd-7ea82efadf9d   ext4       /home                         
/dev/sda8        d1f23e37-af02-4fc5-83c6-5649800a6682   ext4       /                             
/dev/sda9        defe1b13-e1c0-45d3-9e25-388c1602158a   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot                    ext4       (rw)
/dev/sda7        /extra/2ndhome           ext4       (rw)
/dev/sda12       /extra/3rdhome           ext4       (rw)
/dev/sda13       /extra/3rdroot           ext4       (rw)
/dev/sda6        /home                    ext4       (rw)
/dev/sda10       /extra/Spiele            ext4       (rw)
/dev/sda8        /extra/2ndroot           ext4       (rw)
/dev/sda11       /extra/Kram              ext4       (rw)


============================= sda1/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 1df5dde3-b676-45b1-a4ca-1d077c344fd3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600
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
search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
set locale_dir=($root)/grub/locale
set lang=de
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, mit Linux 2.6.33-02063303-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux	/vmlinuz-2.6.33-02063303-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro   quiet splash
	initrd	/initrd.img-2.6.33-02063303-generic
}
menuentry 'Ubuntu, mit Linux 2.6.33-02063303-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	echo	'Linux 2.6.33-02063303-generic wird geladen …'
	linux	/vmlinuz-2.6.33-02063303-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro single 
	echo	'Initiale Ramdisk wird geladen …'
	initrd	/initrd.img-2.6.33-02063303-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux	/vmlinuz-2.6.32-22-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro   quiet splash
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-22-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	echo	'Linux 2.6.32-22-generic wird geladen …'
	linux	/vmlinuz-2.6.32-22-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro single 
	echo	'Initiale Ramdisk wird geladen …'
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux	/vmlinuz-2.6.32-21-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, mit Linux 2.6.32-21-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	echo	'Linux 2.6.32-21-generic wird geladen …'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro single 
	echo	'Initiale Ramdisk wird geladen …'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, mit Linux 2.6.33-02063303-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.33-02063303-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro quiet splash
	initrd /initrd.img-2.6.33-02063303-generic
}
menuentry "Ubuntu, mit Linux 2.6.33-02063303-generic (Wiederherstellungsmodus) (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.33-02063303-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro single
	initrd /initrd.img-2.6.33-02063303-generic
}
menuentry "Ubuntu, mit Linux 2.6.32-22-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.32-22-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro quiet splash
	initrd /initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, mit Linux 2.6.32-22-generic (Wiederherstellungsmodus) (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.32-22-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro single
	initrd /initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, mit Linux 2.6.32-21-generic (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.32-21-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro quiet splash
	initrd /initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, mit Linux 2.6.32-21-generic (Wiederherstellungsmodus) (on /dev/sda13)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.32-21-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro single
	initrd /initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, mit Linux 2.6.33-02063303-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.33-02063303-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro quiet splash
	initrd /initrd.img-2.6.33-02063303-generic
}
menuentry "Ubuntu, mit Linux 2.6.33-02063303-generic (Wiederherstellungsmodus) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.33-02063303-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro single
	initrd /initrd.img-2.6.33-02063303-generic
}
menuentry "Ubuntu, mit Linux 2.6.32-22-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.32-22-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro quiet splash
	initrd /initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, mit Linux 2.6.32-22-generic (Wiederherstellungsmodus) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.32-22-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro single
	initrd /initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, mit Linux 2.6.32-21-generic (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.32-21-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro quiet splash
	initrd /initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, mit Linux 2.6.32-21-generic (Wiederherstellungsmodus) (on /dev/sda8)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f20b6ae6-d97c-4e85-a203-87ef397fe2b3
	linux /vmlinuz-2.6.32-21-generic root=UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 ro single
	initrd /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: initrd.img-2.6.32-22-generic
    .0GB: initrd.img-2.6.33-02063303-generic
    .0GB: vmlinuz-2.6.32-21-generic
    .0GB: vmlinuz-2.6.32-22-generic
    .0GB: vmlinuz-2.6.33-02063303-generic

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
UUID=1df5dde3-b676-45b1-a4ca-1d077c344fd3 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=f20b6ae6-d97c-4e85-a203-87ef397fe2b3 /boot           ext4    defaults        0       2
# /extra/2ndhome was on /dev/sda7 during installation
UUID=54ca12f0-a691-48ab-addd-7ea82efadf9d /extra/2ndhome  ext4    defaults        0       2
# /extra/2ndroot was on /dev/sda8 during installation
UUID=d1f23e37-af02-4fc5-83c6-5649800a6682 /extra/2ndroot  ext4    defaults        0       2
# /extra/3rdhome was on /dev/sda12 during installation
UUID=245c09c4-a928-4df3-8530-577097ed10b1 /extra/3rdhome  ext4    defaults        0       2
# /extra/3rdroot was on /dev/sda13 during installation
UUID=22f6e439-96fc-4de0-b4ea-6a53e48f41e4 /extra/3rdroot  ext4    defaults        0       2
# /extra/Kram was on /dev/sda11 during installation
UUID=b5a78ac9-543e-4337-ab8d-fae64305ad48 /extra/Kram     ext4    defaults        0       2
# /extra/Spiele was on /dev/sda10 during installation
UUID=98ecc5b9-55bd-4455-a623-875bbc46783d /extra/Spiele   ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=bde8dd2a-162e-471e-9d0e-3b72d197010d /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=defe1b13-e1c0-45d3-9e25-388c1602158a none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


    .4GB: initrd.img
    .4GB: initrd.img.old
    .4GB: vmlinuz
    .4GB: vmlinuz.old

=============================== sda8/etc/fstab: ===============================

/dev/sda8               /                       ext4    user_xattr,noatime 1 1
/dev/sda13              /extra/3rdroot          ext4    user_xattr,noatime 1 2
/dev/sda10              /extra/Spiele           ext4    user_xattr,noatime 1 2
/dev/sda11              /extra/Kram             ext4    user_xattr,noatime 1 2
/dev/sda5               /extra/1stroot          ext4    user_xattr,noatime 1 2
/dev/sda6               /extra/1sthome          ext4    user_xattr,noatime 1 2
/dev/sda7               /home                   ext4    user_xattr,noatime 1 2
/dev/sda12              /extra/3rdhome          ext4    user_xattr,noatime 1 2
/dev/sda1               /boot                   ext4    user_xattr,noatime 1 2
/dev/shm                /dev/shm                tmpfs   defaults        0 0
/dev/sda9               swap                    swap    defaults        0 0

=============================== sda13/etc/fstab: ===============================

/dev/sda9        swap             swap        defaults         0   0
/dev/sda13       /                ext4        defaults         1   1
/dev/sda12       /home            ext4        defaults         1   2
/dev/sda1        /boot            ext4        defaults         1   2
/dev/sda10       /extra/Spiele    ext4        defaults         1   2
/dev/sda11       /extra/Kram      ext4        defaults         1   2
/dev/sda5        /extra/1sthome   ext4        defaults         1   2
/dev/sda6        /extra/1stroot   ext4        defaults         1   2
/dev/sda7        /extra/2ndhome   ext4        defaults         1   2
/dev/sda8        /2ndroot         ext4        defaults         1   2
#/dev/cdrom      /mnt/cdrom       auto        noauto,owner,ro  0   0
/dev/fd0         /mnt/floppy      auto        noauto,owner     0   0
devpts           /dev/pts         devpts      gid=5,mode=620   0   0
proc             /proc            proc        defaults         0   0
tmpfs            /dev/shm         tmpfs       defaults         0   0
```

---

### Post by libertin on 2010-05-14
I don't know, what exactly you mean, but let me explain this:

sda5 is my Ubuntu, which I use right now,
sda8 is slackware and
sda13 is VLOS.

Before updating Ubuntu to kernel 2.6.33, those entries were like 
Ubuntu 2.6.xx (depending on the kernel slackware and VLOS use)


I created all in all a /boot-Partition, three /homes and /roots, of which the other two I mount on /extra, plus a Partition for games and one for all the other stuff.
Makes alltogether a whole bunch of partitions, but I like it that way :)

---

### Post by kansasnoob on 2010-05-14
Well, I know this was written for legacy grub but it still explains the problem of having a separate /boot partition fairly well:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

Skip down to **Don't do that.**

> The main disadvantage of having to use a separate /boot partition is that is you want to dual boot more than one Linux installation, it is a bit tricky to get two or more linuxes to share the same separate /boot partition.
If you try, any files with the same name in the new system you might be installing will overwrite files belonging to your existing system and you will lose the boot of your existing Linux.

I multi-boot too and that's why I never use a separate /boot:

> /dev/sda1: UUID="F4C8C431C8C3F042" TYPE="ntfs" 
/dev/sda2: LABEL="Lucid Root" UUID="fb0e61a6-d355-4687-9a98-da164a56cc60" TYPE="ext3" 
/dev/sda3: LABEL="Karmic Root" UUID="b976dd82-1719-42e0-8a78-9e86e8ceba88" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="Lucid Home" UUID="9397c183-6db2-4b47-b8d2-98234ce442d9" TYPE="ext3" 
/dev/sda6: LABEL="Karmic Home" UUID="e7319a14-febc-4b42-ac32-9c0c2bbb53dc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="Backups" UUID="594c3d40-2791-4c0a-8644-d9812545da2d" TYPE="ext3" 
/dev/sda8: LABEL="Pictures" UUID="8a3f6c83-cb52-4caf-96b8-5faf2c830453" TYPE="ext3" 
/dev/sda9: LABEL="Downloads" UUID="05289ee4-d681-4806-b6fd-aefd784f9323" TYPE="ext3" 
/dev/sda10: LABEL="Documents" UUID="571cfad8-68c7-4703-883e-c0baa2a381d4" TYPE="ext3" 
/dev/sda11: UUID="bf502251-6ccd-4b66-8f9a-458603a6d2f2" TYPE="swap" 
/dev/sda12: LABEL="Squeeze Root" UUID="2d74adb5-1d41-46b0-b1ae-c0a2bf65cdcd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: LABEL="Squeeze Home" UUID="732e374a-bfff-4b75-95ba-d35b4217df54" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda14: LABEL="Lenny Root" UUID="7810ffb6-28e9-42ce-af70-195f38155bbc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda15: LABEL="Lenny Home" UUID="0ff06334-bf05-4f7d-8666-714f5d14187e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda16: LABEL="Isadora Root" UUID="d935211b-cc91-429b-bb0f-4a61e25d39fb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda17: LABEL="Isadora Home" UUID="a738f4d8-f42c-4e97-bbb5-3b7a06271a39" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda18: LABEL="Maverick Root" UUID="00848f9d-37ce-4987-814b-8eb8bfe982ba" TYPE="ext4" 
/dev/sda19: LABEL="Maverick Home" UUID="df09c41a-0ac8-47ae-a1c7-8d92598138f4" TYPE="ext4" 
/dev/sdb1: UUID="bc27d3ed-7028-4a49-ada4-ca39878db300" TYPE="ext4" 
/dev/sdb5: UUID="62332d1e-b642-4a4a-9754-9d16cd495142" TYPE="swap" 
/dev/sdb6: UUID="980cbd8b-1038-433d-8a91-7da5c73d9582" TYPE="ext4" 
/dev/sdb7: UUID="d81dd0ac-d6ea-45e5-9417-1a6f183f94ac" TYPE="swap" 


---

### Post by libertin on 2010-05-14
Well, lol, I think this explains my problems. :)

Thanks!

---

### Post by darkod on 2010-05-14
> **libertin said:**
> 
Before updating Ubuntu to kernel 2.6.33, those entries were like 
Ubuntu 2.6.xx (depending on the kernel slackware and VLOS use)


Ubuntu kernel 2.6.33??? Isn't the 2.6.32 latest? Did you update to some non-oficial kernel?

I also think suing same /boot mixed it up for you. And when installing more linux versions, just tell the second, third, etc installation not to install a bootloader. That way you keep your grub that you are already using from the start, provided that is the one you want to keep.
For further linux installs no need for a bootloader to be installed.

---

### Post by dino99 on 2010-05-14
when i have issues like yours ( all my distro use grub2, i've erase grub1 and menu.lst because os-prober fail with it):

- as i've several hdd and several distro and plug/unplug them time to time for my needs, each distro is installed with its grub2.

- if i add a kernel on a distro, i run: sudo grub-mkconfig && update-grub. The problem is that grub menu is not always updated with that new kernel, i need to rebuilt it on the other distro too.

What it is strange because all the kernels are well identified on all partitions and hdds, only the menu is not updated: with several grub, only one seem to act as master.

---

### Post by libertin on 2010-05-14
> **darkod said:**
> Ubuntu kernel 2.6.33??? Isn't the 2.6.32 latest? Did you update to some non-oficial kernel?

2.6.32 is the one officially used by lucid, but, for support of the Arrandale CPU IGP I installed the 2.6.33 from Ubuntu ppa.

> **darkod said:**
> I also think suing same /boot mixed it up for you. And when installing more linux versions, just tell the second, third, etc installation not to install a bootloader. That way you keep your grub that you are already using from the start, provided that is the one you want to keep.
For further linux installs no need for a bootloader to be installed.

Yeah, did that...I'll see what happens, if I use different /boot, as soon as I have the time to.

---

