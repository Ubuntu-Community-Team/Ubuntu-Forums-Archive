---
title: "Grub can't see Vista"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by Slovak on 2011-06-08
I upgraded a while back from 10.04 to 11.04, but have since gone back to 10.04 for various reasons. Anyway, since going back Ubuntu fails to see my Vista install on a separate drive, and it did way back in the day when I first installed 10.04 to begin with, then upgraded to 10.10, then to 11.04. Only since going back in Ubuntu is my Vista not seen on installing Ubuntu, and I have installed many times over too.. 
When using the alternate install disk, it sees my other drive, but fails to install grub anywhere but in Ubuntu, so I can't boot my Vista since it is not listed in Grub2.
Any ideas?

---

### Post by jerrrys on 2011-06-08
in terminal try 

sudo update grub

---

### Post by Slovak on 2011-06-09
I have done that already, no luck.

---

### Post by Quackers on 2011-06-09
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Slovak on 2011-06-12
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   321,667,071   321,665,024   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   308,533,247   308,531,200  83 Linux
/dev/sdb2         308,535,294   321,671,167    13,135,874   5 Extended
/dev/sdb5         308,535,296   321,671,167    13,135,872  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 4d60d199-3974-4655-8678-2364f0d3a359   swap       
/dev/sda1        8640391940391203                       ntfs       
/dev/sdb1        7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[operating systems]

[boot loader]

timeout=15

--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
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
search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
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
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=7e3f2b41-4eeb-4c1d-9d61-c7d3b656e3c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
#UUID=338f95a8-ce81-4acd-89d0-b6a5b1da9ceb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 124.133598328 = 133.287436288  boot/grub/core.img                             1
 124.196491241 = 133.354967040  boot/grub/grub.cfg                             2
   0.450984955 = 0.484241408    boot/initrd.img-2.6.32-28-generic              1
   0.766227722 = 0.822730752    boot/initrd.img-2.6.32-31-generic              2
 124.515522003 = 133.697523712  boot/initrd.img-2.6.32-32-generic              2
 124.129741669 = 133.283295232  boot/vmlinuz-2.6.32-28-generic                 1
 124.139511108 = 133.293785088  boot/vmlinuz-2.6.32-31-generic                 1
 124.510826111 = 133.692481536  boot/vmlinuz-2.6.32-32-generic                 1
 124.515522003 = 133.697523712  initrd.img                                     2
   0.766227722 = 0.822730752    initrd.img.old                                 2
 124.510826111 = 133.692481536  vmlinuz                                        1
 124.139511108 = 133.293785088  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

ERROR: isw: wrong number of devices in RAID set "isw_dgfiffibad_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dgfiffibad_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dgfiffibad_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dgfiffibad_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dgfiffibad_Volume0" [1/2] on /dev/sda

```

I have no idea what the raid errors are, as I do not have, nor have I ever had raid set up on this computer, or what dev/sdb5 is with the unknown file system is, how do I not only get Vista back, but fix the rest of this mess

---

### Post by Quackers on 2011-06-12
Which hard drive is set to boot first in your bios?
In your bios settings is there anything referring to a raid array or members disks?
The boot script is picking up Intel software raid data on /dev/sda only, it seems.
Has that hard drive been used in another system which used raid?

Your sdb5 partition is your swap partition, but it is not mounting.

Grub is installed to the mbr of /dev/sda but Ubuntu is installed in /dev/sdb.
Is Ubuntu booting normally?

---

### Post by Slovak on 2011-06-12
Yes, it used to be in a raid system, but has since been low level formatted and made like new. Rebooting now to check bios.
Yes Ubuntu boots fine. 

Rebooted, bios is correct, the windows drive is first to boot.

---

### Post by Quackers on 2011-06-12
ok, that answers that then :-)
In Ubuntu please open a terminal and run the following, one line at a time, pressing enter after each line. (It shouldn't be necessary for sdb, but it won't do any harm.
```
sudo dmraid -rE /dev/sda
sudo dmraid -rE /dev/sdb
``` then please report any output.

---

### Post by Slovak on 2011-06-12
john@ubuntu:~$ sudo dmraid -rE /dev/sda
[sudo] password for john: 
Do you really want to erase "isw" ondisk metadata on /dev/sda ? [y/n] :y
john@ubuntu:~$ sudo dmraid -rE /dev/sdb
no raid disks and with names: "/dev/sdb"
john@ubuntu:~$ 

Done, now what?

---

### Post by Quackers on 2011-06-12
Please reboot and then in Ubuntu open a terminal and run ```
sudo update-grub
``` and see if Windows is now recognised. It may not be, but if that's the case we can re-install grub which may cure that.

One other point is that there is a /boot.ini file in with your Vista boot files. This is a Windows XP boot file and unless you have XP installed shouldn't really be there. I'm wondering if that's causing a problem, though it shouldn't.

---

### Post by Slovak on 2011-06-12
Ok, then reboot again and see if I can't boot Vista?

---

### Post by Quackers on 2011-06-12
Only if the Vista Loader is picked up as grub.cfg is run in the terminal.

---

### Post by Slovak on 2011-06-12
Thanks! It works again!

---

### Post by Quackers on 2011-06-12
Aha! :-)  Very good, glad you're up and running again!

Please mark the thread as solved using Thread Tools near the top of the page. Thanks.

---

