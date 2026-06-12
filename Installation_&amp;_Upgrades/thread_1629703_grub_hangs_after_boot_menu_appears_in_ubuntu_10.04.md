---
title: "grub hangs after boot menu appears in ubuntu 10.04"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by xihad76 on 2010-11-24
i have ubuntu 10.04 and xp installed in two different hard disc partitions. everything was fine until i came from vacation and found that after turning on my pc it gets hang as soon as the grub menu with duel boot option appears. i cant do anything at that stage, just nothing.keyboard doesn't work also. here one thing to be mentioned that for last few days my pc used to hang frequently in ubuntu 10.04 and then i had no option left but to restart my pc. 

any suggestion guys? is this a grub loader issue or hard disc problem?? any help would be highly appreciated . thnx in advance!

---

### Post by sikander3786 on 2010-11-24
Regardless of Grub menu, are you able to use your Keyboard for accessing and making changes to Bios.

I doubt if the keyboard cables/ports or the keyboard itself is gone bad.

Test your keyboard with Bios or try with some other keyboard.

And if it is a problem with the keyboard, was Grub set to auto-boot the default OS after an X interval of time? If yes, it should be booting.

If the keyboard is ok and it is just a problem with Grub, please boot from a Live CD and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us exactly nearly everything related to Grub and your partitions. Please wrap the output with proper code tags # from post menu.

---

### Post by xihad76 on 2010-11-24
today morning i removed both xp and ubuntu installation and did a fresh install of ubuntu 10.04. at firt attempt pc hanged after 93% progress and in second attempt it somehow managed to finish the installation. Booting for the first time in new installation my pc again hanged after few minutes and i had to restart again. so i think its a hard disc issue. 

before removing both ubuntu and xp i ran the bootinfo script and found results.txt like this: 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40019582464 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78163247 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    14,329,979    14,329,917   7 HPFS/NTFS
/dev/sda2          14,330,104    78,140,159    63,810,056   f W95 Ext d (LBA)
/dev/sda5          14,330,106    25,655,804    11,325,699  83 Linux
/dev/sda6          25,655,868    28,659,959     3,004,092  82 Linux swap / Solaris
/dev/sda7          28,660,023    45,046,259    16,386,237   b W95 FAT32
/dev/sda8          45,046,323    61,432,559    16,386,237   b W95 FAT32
/dev/sda9          61,432,623    78,140,159    16,707,537   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D66009D66009BDED                       ntfs       WinXp                         
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5016cf3e-2b33-41ff-8fd9-65b822a867bd   ext4                                     
/dev/sda6        33b95c58-e3a8-49e5-a639-8efe19ec2782   swap                                     
/dev/sda7        C071-901E                              vfat       AUDIO                         
/dev/sda8        A878-B034                              vfat       SOFT                          
/dev/sda9        BC7E-AD57                              vfat       VIDEO                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5C6D-279F                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda9        /media/sda9              vfat       (rw,nosuid,nodev,uid=1000,umask=000)
/dev/sda8        /media/sda8              vfat       (rw,nosuid,nodev,uid=1000,umask=000)
/dev/sda7        /media/sda7              vfat       (rw,nosuid,nodev,uid=1000,umask=000)
/dev/sda1        /media/sda1              fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
search --no-floppy --fs-uuid --set 5016cf3e-2b33-41ff-8fd9-65b822a867bd
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
search --no-floppy --fs-uuid --set 5016cf3e-2b33-41ff-8fd9-65b822a867bd
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 5016cf3e-2b33-41ff-8fd9-65b822a867bd
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=5016cf3e-2b33-41ff-8fd9-65b822a867bd ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 5016cf3e-2b33-41ff-8fd9-65b822a867bd
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=5016cf3e-2b33-41ff-8fd9-65b822a867bd ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 5016cf3e-2b33-41ff-8fd9-65b822a867bd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 5016cf3e-2b33-41ff-8fd9-65b822a867bd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d66009d66009bded
	drivemap -s (hd0) ${root}
	chainloader +1
}
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
proc                                       /proc        proc  nodev,noexec,nosuid                         0  0  
/dev/sda5                                  /            ext4  errors=remount-ro                           0  1  

# swap was on /dev/sda6 during installation
UUID=33b95c58-e3a8-49e5-a639-8efe19ec2782  none         swap  sw                                          0  0  
/dev/sda9                                  /media/sda9  vfat  uid=xihad,owner,umask=000                   0  0  
/dev/sda8                                  /media/sda8  vfat  uid=xihad,owner,umask=000                   0  0  
/dev/sda7                                  /media/sda7  vfat  uid=xihad,owner,umask=000                   0  0  
/dev/sda1                                  /media/sda1  ntfs  nls=iso8859-1,ro,umask=000,owner,uid=xihad  0  0  

=================== sda5: Location of files loaded by Grub: ===================


   7.7GB: boot/grub/core.img
   9.1GB: boot/grub/grub.cfg
   9.2GB: boot/initrd.img-2.6.32-25-generic
   9.0GB: boot/vmlinuz-2.6.32-25-generic
   9.2GB: initrd.img
   9.0GB: vmlinuz
```


any idea what might cause the problem? i also experienced hang issue while running from ubuntu usb install.

---

### Post by lmarmisa on 2010-11-24
[B]NOTE: sorry. I do not read your last comment. You deleted XP and Ubuntu. So, forget this post.

[/B]
Start your system from a Live CD, open a terminal and type these commands:

```

sudo bash
mount /dev/sda5 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda
exit
exit
exit

```Reboot the system without Live CD and check if the problem is solved.

If everything works fine, type this command:

```

sudo update-grub

```

---

### Post by sikander3786 on 2010-11-25
I don't see any problems with the older output for bootinfoscript.

So at the moment you are running a fresh install of 10.04 and it is acting the same.

Me too suspect that it is a hard drive or may be a RAM issue.

You can download diagnostic tools from manufacturer's website and use them to scan your HDD for any bad sectors. And if you've got SMART Monitoring Tool option in Bios, turn it on and it might tell you about drive state.

And for RAM, you can run memtest from Grub menu and see if any of the RAM modules has gone bad.

Both of those tests would run overnight I believe, so, prepare accordingly.

Good Luck!

---

### Post by xihad76 on 2010-11-28
> **sikander3786 said:**
> I don't see any problems with the older output for bootinfoscript.

So at the moment you are running a fresh install of 10.04 and it is acting the same.

Me too suspect that it is a hard drive or may be a RAM issue.

You can download diagnostic tools from manufacturer's website and use them to scan your HDD for any bad sectors. And if you've got SMART Monitoring Tool option in Bios, turn it on and it might tell you about drive state.

And for RAM, you can run memtest from Grub menu and see if any of the RAM modules has gone bad.

Both of those tests would run overnight I believe, so, prepare accordingly.

Good Luck!

This was a motherboard issue actually. i had to change it and everything is working fine now :-) but right now facing another problem installing ubuntu. i m opening a new thread for this as it is different than this one. the new thread link is [here]("http://ubuntuforums.org/showthread.php?p=10173560#post10173560")

i do really appreciate your help. thnk you so much. take care.

---

