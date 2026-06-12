---
title: "Windows entry in Grub 1.98 gone after kernel update"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by merajchhaya on 2010-09-02
Hello

Today I updated my kernel on Ubuntu 10.04 (fresh install). Before that I used to dual-boot with Windows 7 with no problems.

Both are in different partitions.

My Windows entry is gone after I updated the kernel.

I've looked through many posts, but can't get it right.

I would like to stay with Grub 1.98, as it worked fine, but would like my Windows entry back.

Kindly help

---

### Post by garvinrick4 on 2010-09-02
sudo update-grub

If does not work see below:

Post results:

```
sudo fdisk -l  
```(small L)

```
sudo blkid 
``` (small L second letter)

---

### Post by merajchhaya on 2010-09-02
I had done sudo update-grub, but it didn't the Windows installation:
```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

```

Now for fdisk -l:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03c46d0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   82  Linux swap / Solaris
/dev/sda2   *         192        7111    55575552    7  HPFS/NTFS
/dev/sda3            7111       13485    51198976   83  Linux
/dev/sda4           13485       38914   204257280    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x921b9beb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312568832    7  HPFS/NTFS

```

And for sudo blkid:
```
/dev/sda1: UUID="481f77cd-2439-4ca8-8f73-87fd195aca71" TYPE="swap" 
/dev/sda2: UUID="0AC04A3FC04A316D" TYPE="ntfs" 
/dev/sda4: LABEL="Multimedia2" UUID="AAECEC38ECEC0085" TYPE="ntfs" 
/dev/sdb1: LABEL="Multimedia1" UUID="AE288B67288B2E01" TYPE="ntfs" 
/dev/sda3: UUID="129d127b-36a6-46b6-aff2-c299062eae3d" TYPE="ext3" 
```

---

### Post by garvinrick4 on 2010-09-02
Grab a Ubuntu install Cd and use Try Ubuntu. When it boots up start gparted in System Administration to gparted. Right click on sda3 and go to Label and give it a label. Lets say
lucid. Then click the green arrow to apply it. Open a terminal. Copy and paste these codes: One at a time. Sorry did not hit code tag before submitting myself.

sudo mkdir /media/lucid
sudo mount /dev/sda3 /media/lucid
sudo grub-install --recheck --root-directory=/media/lucid /dev/sda
sudo umount /media/lucid (not a typo)
Then reboot into disk install of ubuntu and;
sudo update-grub

Then lets take a look at it by downloading this script to DESKTOP:

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
run this code in a terminal: Will give a text file on Desktop.
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```Post it to this thread; copy and paste whole thing and then while highlighted
click code tag the # sign and will be easier to read.

---

### Post by merajchhaya on 2010-09-03
Thanks for the reply.

I ran the commands, rebooted and ran "sudo update-grub", and I got:

```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

And then I downloaded the file you asked, here are the results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1               2,048     3,074,047     3,072,000  82 Linux swap / Solaris
/dev/sda2    *      3,074,048   114,225,151   111,151,104   7 HPFS/NTFS
/dev/sda3         114,225,152   216,623,103   102,397,952  83 Linux
/dev/sda4         216,625,152   625,139,711   408,514,560   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   625,139,711   625,137,664   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        481f77cd-2439-4ca8-8f73-87fd195aca71   swap                                     
/dev/sda2        0AC04A3FC04A316D                       ntfs                                     
/dev/sda3        129d127b-36a6-46b6-aff2-c299062eae3d   ext3       lucid                         
/dev/sda4        AAECEC38ECEC0085                       ntfs       Multimedia2                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AE288B67288B2E01                       ntfs       Multimedia1                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/lucid             ext3       (rw,nosuid,nodev,uhelper=udisks)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=129d127b-36a6-46b6-aff2-c299062eae3d /               ext3    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/core.img
  77.4GB: boot/grub/grub.cfg
  77.4GB: boot/grub/stage2
  77.4GB: boot/initrd.img-2.6.32-21-generic
  77.4GB: boot/initrd.img-2.6.32-22-generic
  77.5GB: boot/initrd.img-2.6.32-23-generic
  77.4GB: boot/initrd.img-2.6.32-24-generic
  77.5GB: boot/vmlinuz-2.6.32-21-generic
  77.4GB: boot/vmlinuz-2.6.32-22-generic
  77.4GB: boot/vmlinuz-2.6.32-23-generic
  77.5GB: boot/vmlinuz-2.6.32-24-generic
  77.4GB: initrd.img
  77.5GB: initrd.img.old
  77.5GB: vmlinuz
  77.4GB: vmlinuz.old
```

---

### Post by merajchhaya on 2010-09-06
bump :)

---

### Post by kansasnoob on 2010-09-06
A few dumb questions/comments:

1) Were you booted into your installed Lucid when you ran "sudo update-grub" and got this error:

> /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

2) Are you still using BURG:

> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in partition #3 for /boot/**[COLOR="Red"]burg[/COLOR]**.

3) I haven't tried BURG since Karmic development because it really hosed things for me :(

4) I'm thinking if you can still boot into your installed Ubuntu I'd purge and then reinstall grub 2 completely as follows:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub-pc grub-common
```

```
sudo apt-get install grub-pc
```

```
sudo apt-get install --reinstall os-prober
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

```
sudo grub-install /dev/sdb
```

NOTE: Should either of the "grub-install" commands fail also run:

```
sudo grub-install --recheck /dev/sd**[COLOR="Red"]X[/COLOR]**
```

You must of course replace the **[COLOR="Red"]X[/COLOR]** with the proper drive designation, ie: a or b.

Also it shouldn't normally be necessary to install grub to /dev/sdb but since burg is there I want to be rid of it!

The only other thing I see that's slightly confusing is this:

> sda2: Location of files loaded by Grub:
??GB: boot/grub/stage2

But to me Win 7's boot files look OK:

> sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe


Anyway, if "update-grub" fails to pick up Windows after completely reinstalling grub 2 then I guess we'll have to try adding a custom entry.

---

### Post by merajchhaya on 2010-09-07
1 - I was in the live CD installation, just like the instructions said, but I tested that command in my Lucid install, and it didn't pick up Windows.

2 - BURG got overridden when I updated the kernel a couple of weeks ago

4 - I just did that, and will try reboot now. Here are the messages I got:
```
user@user-laptop:~$ sudo mv /boot/grub /boot/grub_backup
[sudo] password for user: 
user@user-laptop:~$ sudo mkdir /boot/grub
user@user-laptop:~$ sudo apt-get --purge remove grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4
  libkscreensaver5 libsolidcontrolifaces4 plasma-widgets-workspace
  libplasma-geolocation-interface4 libksgrd4 kdebase-workspace-bin
  libkworkspace4 libplasmagenericshell4 libkfontinst4 libkephal4
  kdebase-workspace-data ksysguardd libplasmaclock4 libweather-ion4
  kdebase-workspace-kgreet-plugins libsolidcontrol4 akonadi-server
  libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 4 not upgraded.
After this operation, 6,603kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 235599 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info ...
user@user-laptop:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4
  libkscreensaver5 libsolidcontrolifaces4 plasma-widgets-workspace
  libplasma-geolocation-interface4 libksgrd4 kdebase-workspace-bin
  libkworkspace4 libplasmagenericshell4 libkfontinst4 libkephal4
  kdebase-workspace-data ksysguardd libplasmaclock4 libweather-ion4
  kdebase-workspace-kgreet-plugins libsolidcontrol4 akonadi-server
  libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-common
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 2,112kB of archives.
After this operation, 6,603kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://za.archive.ubuntu.com/ubuntu/ lucid-updates/main grub-common 1.98-1ubuntu7 [1,504kB]
Get:2 http://za.archive.ubuntu.com/ubuntu/ lucid-updates/main grub-pc 1.98-1ubuntu7 [608kB]
Fetched 2,112kB in 5s (368kB/s)
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 235324 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98-1ubuntu7_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98-1ubuntu7_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98-1ubuntu7) ...

Setting up grub-pc (1.98-1ubuntu7) ...

Creating config file /etc/default/grub with new version

user@user-laptop:~$ sudo apt-get install --reinstall os-prober
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4
  libkscreensaver5 libsolidcontrolifaces4 plasma-widgets-workspace
  libplasma-geolocation-interface4 libksgrd4 kdebase-workspace-bin
  libkworkspace4 libplasmagenericshell4 libkfontinst4 libkephal4
  kdebase-workspace-data ksysguardd libplasmaclock4 libweather-ion4
  kdebase-workspace-kgreet-plugins libsolidcontrol4 akonadi-server
  libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 4 not upgraded.
Need to get 22.9kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://za.archive.ubuntu.com/ubuntu/ lucid/main os-prober 1.38 [22.9kB]
Fetched 22.9kB in 0s (117kB/s)   
(Reading database ... 235600 files and directories currently installed.)
Preparing to replace os-prober 1.38 (using .../os-prober_1.38_i386.deb) ...
Unpacking replacement os-prober ...
Setting up os-prober (1.38) ...
user@user-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/Boot
boot: No such file or directory
done
user@user-laptop:~$ sudo grub-install /dev/sda
Installation finished. No error reported.
user@user-laptop:~$ sudo grub-install /dev/sdb

Installation finished. No error reported.

```

[COLOR="Red"]Update:[/COLOR] The grub menu has disappeared, now my computer boots straight into Ubuntu.

Thanks

---

### Post by kansasnoob on 2010-09-07
Well the menu is hidden because it's not finding Windows due to this error:

> ls: cannot access /var/lib/os-prober/mount/Boot
boot: No such file or directory


So I've been googling and found two instances of this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

But that's not the case with your machine, to me the Windows boot files look fine:

> Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe


In a third instance I found this:

[http://www.techenclave.com/open-source-and-linux/not-getting-windows-7-after-installing-174344.html](http://www.techenclave.com/open-source-and-linux/not-getting-windows-7-after-installing-174344.html)

And it appears that something changed in an update:

> Update your Ubuntu install by running update manager to get the latest bits then rerun "sudo update-grub", does that make a difference?


Next reply was:

> Ya I'm using final version. I'm currently updating it. Thanks let me check it out.

--- Updated Post - Automerged ---

Yupieee..!! It worked. Thanks. Thanks a lot buddy. 

I do see you have some "held" updates:

> 0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and **[COLOR="Red"]4 not upgraded[/COLOR]**

You also have some old packages:

> The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4
  libkscreensaver5 libsolidcontrolifaces4 plasma-widgets-workspace
  libplasma-geolocation-interface4 libksgrd4 kdebase-workspace-bin
  libkworkspace4 libplasmagenericshell4 libkfontinst4 libkephal4
  kdebase-workspace-data ksysguardd libplasmaclock4 libweather-ion4
  kdebase-workspace-kgreet-plugins libsolidcontrol4 akonadi-server
  libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.


So you could check grub package versions with:

```
aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```

My Lucid shows:

> lance@lance-desktop:~$ aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
Package: grub-pc
State: installed
Automatically installed: no
**Version: 1.98-1ubuntu7**
Package: grub-common
State: installed
Automatically installed: yes
**Version: 1.98-1ubuntu7**
Package: os-prober
State: installed
Automatically installed: yes
**Version: 1.38**


Once we're sure the packages are correct we'll consider what else to do. We could try adding a custom entry to "/etc/grub.d/40_custom" if all else fails.

---

### Post by kansasnoob on 2010-09-07
If you want to try manually adding Win 7 the general instructions are here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

> Custom User Entries (/etc/grub.d/40_custom).

    * Entries to grub.cfg can be manually inserted by creating a file in the /etc/grub.d folder.
          o The name of the file determines the order in the menu. 30_os-prober entries will be placed before 40_custom entries, which will be placed before 50_my-sample entries.
          o Any created file must be made executable. This can be done as root by running "sudo chmod +x /etc/grub.d/filename".
          o The files in the /etc/grub.d folder will be read and the contents included in grub.cfg when the "update-grub" command is executed as root.
    * A sample entry. This file creates a menu item for running the SystemRescueCD (previously installed) from a partition created on sda10. Folders and files must have been copied to the correct location in accordance with the SystemRescueCD if you wish to actually use this entry. Note this entry will not work for a SystemRescue ISO. See Section 14 for instructions on how to add an entry to boot ISO images.
          o
            Quote:
            #!/bin/sh
            exec tail -n +3 $0
            # This file provides an easy way to add custom menu entries. Simply type the
            # menu entries you want to add after this comment. Be careful not to change
            # the 'exec tail' line above.

            menuentry "System Rescue CD" {
            set root=(hd0,10)
            linux /sysrcd/rescuecd subdir=sysrcd setkmap=us
            initrd /sysrcd/initram.igz
            } 

So you'd use gedit (or substitute your choice of text editor) like:

```
sudo gedit /etc/grub.d/40_custom
```

Then below this:

> #!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

Add:

```
menuentry "Windows 7 (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0AC04A3FC04A316D
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

I think I have that right. Sometimes it seems to work better without the "drivemap" line altogether if you have only one hard drive.

Be sure to click on save before closing gedit, and then run "sudo update-grub" so it'll be added to grub/cfg.

I'd really prefer if we could get os-prober working properly though.

---

### Post by merajchhaya on 2010-09-07
Thank you once again

I missed your post, and went on and added a custom entry to GRUB. After doing that, I checked my packages, and got:

```
 aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
Package: grub-pc
State: installed
Automatically installed: no
Version: 1.98-1ubuntu7
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.98-1ubuntu7
Package: os-prober
State: installed
Automatically installed: yes
Version: 1.38

```

When updating grub, I get:
```
sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

```

Doesn't look like it found Windows, but I'll restart now and update this post.
[COLOR="Red"]Update: [/COLOR] Restarted it, and the GRUB menu didn't even appear, computer boots straight into Ubuntu.

---

### Post by kansasnoob on 2010-09-07
By default the grub menu should show if it finds anything in "/etc/grub.d/30_os-prober" or "/etc/grub.d/40_custom" AFAIK. To unhide the menu on reboot you need to press the Shift key immediately after the system/BIOS screen passes.

There is a hackish way to make the menu show when it doesn't want to but it shouldn't be necessary if everything is working correctly.

I wonder if "update-grub" pulled in /etc/grub.d/40_custom? In order to see I'll need to see the output of these two commands:

```
cat /etc/grub.d/40_custom
```

```
cat /boot/grub/grub.cfg
```

We really need to figure out why you're getting this error:

> ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory


Would you mind running the Boot Info Script again and posting the new results?

Something we could try just as a matter of troubleshooting is restoring a Windows readable mbr to the drive just to see if Win 7 will boot under it's own power. But that will leave Ubuntu unbootable so you'd then have to use an Ubuntu Live CD to restore grub to the mbr!

In fact both can be done with an Ubuntu Live CD. To give the drive a Windows readable mbr:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Then we'd at least know if Windows will boot under it's own power. Whether it does or not to restore grub to the mbr:

```
sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

Should that ever show a failure also run:

```
grub-install --recheck /dev/sda
```

Then:

```
update-grub
```

Then just exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

Is that fairly clear? I'll be out for a couple of hours.

Maybe we'll get lucky and someone else will see something I'm overlooking :)

---

### Post by merajchhaya on 2010-09-07
For the 40_custom file I get:

```
meraj@meraj-laptop:~$ cat /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows 7 (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0AC04A3FC04A316D
	drivemap -s (hd0) ${root}
	chainloader +1
}

```

And for grub.cfg:

```
meraj@meraj-laptop:~$ cat /boot/grub/grub.cfg
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
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

menuentry "Windows 7 (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0AC04A3FC04A316D
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/40_custom ###

```

And I ran the boot info script on my Lucid install this time. Here's the text from the Results file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1               2,048     3,074,047     3,072,000  82 Linux swap / Solaris
/dev/sda2    *      3,074,048   114,225,151   111,151,104   7 HPFS/NTFS
/dev/sda3         114,225,152   216,623,103   102,397,952  83 Linux
/dev/sda4         216,625,152   625,139,711   408,514,560   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   625,139,711   625,137,664   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        481f77cd-2439-4ca8-8f73-87fd195aca71   swap                                     
/dev/sda2        0AC04A3FC04A316D                       ntfs                                     
/dev/sda3        129d127b-36a6-46b6-aff2-c299062eae3d   ext3       lucid                         
/dev/sda4        AAECEC38ECEC0085                       ntfs       Multimedia2                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        AE288B67288B2E01                       ntfs       Multimedia1                   
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro)


=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=129d127b-36a6-46b6-aff2-c299062eae3d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 129d127b-36a6-46b6-aff2-c299062eae3d
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

menuentry "Windows 7 (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 0AC04A3FC04A316D
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=129d127b-36a6-46b6-aff2-c299062eae3d /               ext3    errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/core.img
  77.4GB: boot/grub/grub.cfg
  77.4GB: boot/initrd.img-2.6.32-21-generic
  77.4GB: boot/initrd.img-2.6.32-22-generic
  77.5GB: boot/initrd.img-2.6.32-23-generic
  77.4GB: boot/initrd.img-2.6.32-24-generic
  77.5GB: boot/vmlinuz-2.6.32-21-generic
  77.4GB: boot/vmlinuz-2.6.32-22-generic
  77.4GB: boot/vmlinuz-2.6.32-23-generic
  77.5GB: boot/vmlinuz-2.6.32-24-generic
  77.4GB: initrd.img
  77.5GB: initrd.img.old
  77.5GB: vmlinuz
  77.4GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd 

```

I've followed the commands to install and set up lilo:

```
meraj@meraj-laptop:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4
  libkscreensaver5 libsolidcontrolifaces4 plasma-widgets-workspace
  libplasma-geolocation-interface4 libksgrd4 kdebase-workspace-bin
  libkworkspace4 libplasmagenericshell4 libkfontinst4 libkephal4
  kdebase-workspace-data ksysguardd libplasmaclock4 libweather-ion4
  kdebase-workspace-kgreet-plugins libsolidcontrol4 akonadi-server
  libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://za.archive.ubuntu.com/ubuntu/ lucid/main mbr 1.1.10-2 [23.0kB]
Get:2 http://za.archive.ubuntu.com/ubuntu/ lucid/main lilo 1:22.8-8ubuntu1 [390kB]
Fetched 413kB in 1s (380kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 235599 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian


Processing triggers for menu ...
meraj@meraj-laptop:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.

```

I will not reboot and check if Windows can boot on its own, and then follow your other instructions.
[COLOR="Red"]Update-1: [/COLOR] I've managed to boot into Windows, thanks! Will now restore Grub.

[COLOR="Red"]Update-2: [/COLOR] I'm in the Live CD, and ran your commands. Grub doesn't seem to find the Windows entry once again. Here are the results:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt

```

I will restart and confirm.
[COLOR="Red"]Update-3: [/COLOR] I can now see the Windows entry by pressing shift just after the BIOS menu at boot. I can boot into either Windows and Ubuntu, but is there a way that I can have my old menu back, and not have to press shift every time I boot up?


Thanks!

---

### Post by kansasnoob on 2010-09-07
Well, I'm glad we're at least gaining. While I've crafted quite a few custom menu entries it sometimes takes me 2 or 3 tries, it's good to get one right the first time :)

Ultimately we need to find out what's causing this error:

> ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory


But, yes, we should be able to "unhide" the menu until we find a permanent solution. I'm guessing that some old BURG files are causing problems.

Give me a little bit and I'm going to ask a few friends to take a look for me. In the meanwhile please post the output of:

```
cat /etc/default/grub
```

Sorry this has been such a dilemma :p

---

### Post by garvinrick4 on 2010-09-07
This was on thread below and same problem with os-prober
[http://ubuntuforums.org/showthread.php?t=1568955&page=3](http://ubuntuforums.org/showthread.php?t=1568955&page=3)

laptop:~$ sudo update-grub
[sudo] password for mark: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

                                     FIX

Grub2 was installed with  Windows system partition chosen as the   root-directory. This causes the folder /boot/grub to be created on the   Windows system partition. Since ntfs partitions are  case insensitive    this leads  to confusions  between  "/boot" and the already existing   folder "/Boot
[LIST]
[*]Solution
[*]Boot into your Linux OS and deleted or rename the folder /boot  on  the Windows system partition. Make sure that your don't delete the   /Boot folder. The /Boot folder contains the file "bcd" which is   necessary to boot Windows Vista/7.
[/LIST]

         This seems to be a big problem in the forums lately with  everyone upgrading and or installing 10.10. Kansasnoob and oldfred I  hope a lot of users see the solution you all have came up with. It is  handy at this time of release schedule.

---

### Post by kansasnoob on 2010-09-07
> **garvinrick4 said:**
> This was on thread below and same problem with os-prober
[http://ubuntuforums.org/showthread.php?t=1568955&page=3](http://ubuntuforums.org/showthread.php?t=1568955&page=3)

laptop:~$ sudo update-grub
[sudo] password for mark: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

                                     FIX

Grub2 was installed with  Windows system partition chosen as the   root-directory. This causes the folder /boot/grub to be created on the   Windows system partition. Since ntfs partitions are  case insensitive    this leads  to confusions  between  "/boot" and the already existing   folder "/Boot
[LIST]
[*]Solution
[*]Boot into your Linux OS and deleted or rename the folder /boot  on  the Windows system partition. Make sure that your don't delete the   /Boot folder. The /Boot folder contains the file "bcd" which is   necessary to boot Windows Vista/7.
[/LIST]

         This seems to be a big problem in the forums lately with  everyone upgrading and or installing 10.10. Kansasnoob and oldfred I  hope a lot of users see the solution you all have came up with. It is  handy at this time of release schedule.

But I've looked at that:

> Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe


There is no /boot and /Boot. 

I swear it has something to do with BURG!

---

### Post by oldfred on 2010-09-07
I missed it too but gavinrick is right. The script only looks for certain boot files in /boot and shows them in the first part, but the standard boot files are not there. But a remnant of grub still is in sda2 the windows partition which it shows later in the script and /Boot & /boot in windows is a problem.

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/stage2

---

### Post by kansasnoob on 2010-09-07
Well, we know now that Windows will boot either under it's own power with a Win readable mbr or with my custom entry, right?

So this is more of a flaw in grub2, eh?

I'm just not sure, but it seems like since we can get Windows to boot but can't get os-prober to work that something slightly different is messed up ;)

---

### Post by oldfred on 2010-09-08
Since windows sees /Boot as the same as /boot will it always find /Boot and the BCD or will sometimes it find /boot and no BCD and not work? I do not know.

---

### Post by merajchhaya on 2010-09-08
> **kansasnoob said:**
> Well, I'm glad we're at least gaining. While I've crafted quite a few custom menu entries it sometimes takes me 2 or 3 tries, it's good to get one right the first time :)

Ultimately we need to find out what's causing this error:



But, yes, we should be able to "unhide" the menu until we find a permanent solution. I'm guessing that some old BURG files are causing problems.

Give me a little bit and I'm going to ask a few friends to take a look for me. In the meanwhile please post the output of:

```
cat /etc/default/grub
```

Sorry this has been such a dilemma :p

You shouldn't apologise, I'm the one who is thankful for your time :)

Here are the results of that command:

```
meraj@meraj-laptop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I got a bit lost in the last posts. Do I have to do anything with the said /Boot or /boot folder?

---

### Post by drs305 on 2010-09-08
merajchhaya,

Since os-prober still isn't finding your Windows install, to at least get the menu to display on boot, run these commands and try changing the line in */etc/default/grub*:

```
gksu gedit /etc/default/grub
```
Add the # symbol (comment) at the start of this line:
> **[COLOR="DarkRed"]#[/COLOR]**GRUB_HIDDEN_TIMEOUT=0

Update grub:
```
sudo update-grub
```

---

### Post by oldfred on 2010-09-08
The script says it found a /boot in addition to /Boot. Check your root from Ubuntu (windows may not see it correctly). If you have a /boot then check what is in it and if only grub stuff delete it. If worried you can rename it and make sure everything works then delete it. Do not delete /Boot.
I think the osprober will then start working.

---

### Post by kansasnoob on 2010-09-08
I'm curious where we're at with this?

I'm a bit torn over it to be honest. I hate to have someone go mucking around in Windows files unless I'm sure they know what they're doing, especially if their Windows works before the "mucking" :D

That said I honestly do think oldfred is correct in the long run. If you're comfortable going into your Win7 System files and looking for "boot/grub/stage2" I'd say it should be safe to rename it something like "old_boot/grub/stage2", but I'm not absolutely sure!

In my experience having both a /Boot and a /boot in Wins System files will keep Win from booting on it's own also. Before messing around I'd be sure I had the Win7 recovery discs or I'd at least get these:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

NOTE: they will not restore the OS but they will allow you to recover the needed boot files!

---

### Post by kansasnoob on 2010-09-08
Oh, apologies to anyone and everyone if I seemed rude at any point.

I've been fighting what should have been a two month remodel for nearly five months and I'm about cooked :p

---

### Post by merajchhaya on 2010-09-11
Everything was working 100% fine, and suddenly today when I try to boot into Windows I get the following:

```
Windows failed to start. A recent hardware of software modification could be the cause. 

To fix it insert your Windows disc and choose "repair your computer".

File: \Boot\BCD
Status: 0xc000000f
Info: An error occurred when attempting to read data.

```

I went to my "Boot" folder in the Windows partition, and the file BCD is still there. I also have a "boot" folder, but I doubt Windows decided to get confused only today.

Any thoughts?

---

### Post by oldfred on 2010-09-11
Windows does not know the difference. I would expect for whatever reason it to normally read the same one, but it could just be random. Windows will not let you create two partitions with the same name and /boot and /Boot are the same in windows.

---

### Post by kansasnoob on 2010-09-11
I'd try just renaming the /boot folder something like OLD_/boot and see what happens.

Do not change or delete /Boot because BCD is needed to boot.

Grub will also probably start updating properly afterward when you run "sudo update-grub".

---

