---
title: "grub: Error 15 File not found... when file present"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by DasLemm on 2009-12-04
Ok, I've been googling this for the better part of 2 days now, and I can't seem to find an answer.
I've recently adjusted my partitions so i could install and test out Crunchbang without hurting my old Ubuntu data.
After setting aside 10gb on my main hdd crunchbang installed without a hitch, but now I cannot boot to it.
I've been messing around with grub/menu.lst trying to get it working, but the closest I've come is grub seeing the partition, but not finding whatever file it needs.
Any help would be greatly appreciated.

Included is my menu.lst file.
It should be noted that uuid's are correct, i've verified that multiple times. the location of vmlinuz and initrd.img is correct aswell.

---

### Post by presence1960 on 2009-12-04
I need way more info. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by DasLemm on 2009-12-04
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks at sector 111088893 
    on boot drive #2 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #4 for /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #3 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34 1,953,525,134 1,953,525,101 Microsoft Windows

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000cd08b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1           4,192,965   107,908,604   103,715,640  83 Linux
/dev/sdb2    *    128,873,430   149,838,254    20,964,825   7 HPFS/NTFS
/dev/sdb3         149,838,255   156,296,384     6,458,130   5 Extended
/dev/sdb5         149,838,318   156,296,384     6,458,067  82 Linux swap / Solaris
/dev/sdb4         107,908,605   128,873,429    20,964,825  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ffc810

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   625,121,279   625,121,217   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="1BBFBB0167404A9D" TYPE="ntfs" 
/dev/sdb1: LABEL="Ubuntu" UUID="3eac6dc9-8e42-44d1-a8a3-27e60a1af614" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="2CF8C2AFF8C2769C" LABEL="Billy" TYPE="ntfs" 
/dev/sdb4: LABEL="Crunchy" UUID="471491b4-0303-41e7-afb6-68f4f62dba90" TYPE="ext4" 
/dev/sdb5: UUID="e1aff95d-285c-4afe-a7d9-f54c246c9802" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: LABEL="FRANK" UUID="D0C5-4C6E" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/FRANK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3eac6dc9-8e42-44d1-a8a3-27e60a1af614

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		3eac6dc9-8e42-44d1-a8a3-27e60a1af614
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		3eac6dc9-8e42-44d1-a8a3-27e60a1af614
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

#title		Ubuntu 9.10, kernel 2.6.31-14-generic
#uuid		3eac6dc9-8e42-44d1-a8a3-27e60a1af614
#kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 ro quiet splash 
#initrd		/boot/initrd.img-2.6.31-14-generic
#quiet

#title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
#uuid		3eac6dc9-8e42-44d1-a8a3-27e60a1af614
#kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 ro  single
#initrd		/boot/initrd.img-2.6.31-14-generic

#title		Ubuntu 9.10, kernel 2.6.28-16-generic
#uuid		3eac6dc9-8e42-44d1-a8a3-27e60a1af614
#kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-16-generic
#quiet

#title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
#uuid		3eac6dc9-8e42-44d1-a8a3-27e60a1af614
#kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 ro  single
#initrd		/boot/initrd.img-2.6.28-16-generic

#title		Ubuntu 9.10, kernel 2.6.27-15-generic
#uuid		3eac6dc9-8e42-44d1-a8a3-27e60a1af614
#kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-15-generic
#quiet

#title		Ubuntu 9.10, kernel 2.6.27-15-generic (recovery mode)
#uuid		3eac6dc9-8e42-44d1-a8a3-27e60a1af614
#kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 ro  single
#initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 9.10, memtest86+
uuid		3eac6dc9-8e42-44d1-a8a3-27e60a1af614
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows XP x64
root		(hd0,1)
makeactive
chainloader +1

title		!#Crunchbang
uuid		471491b4-0303-41e7-afb6-68f4f62dba90
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=471491b4-0303-41e7-afb6-68f4f62dba90 ro
initrd		/boot/initrd.img-2.6.28-13-generic

title		!#Crunchbang (recovery mode)
uuid		471491b4-0303-41e7-afb6-68f4f62dba90
kernel		/vmlinuz root=UUID=471491b4-0303-41e7-afb6-68f4f62dba90 ro single
initrd		/initrd.img

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=3eac6dc9-8e42-44d1-a8a3-27e60a1af614 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=e1aff95d-285c-4afe-a7d9-f54c246c9802 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/Frank vfat uid=nik,owner,gid=users 0 0
/dev/sdc1 /media/Frank vfat uid=nik,gid=users 0 0
/dev/sda5 /media/sda5 swap defaults 0 0
/dev/sdb2 /media/WinXP ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/Frank /media/Frank vfat defaults 0 0
/dev/sda1 /media/Ezekiel ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb1: Location of files loaded by Grub: ===================


  46.7GB: boot/grub/menu.lst
  46.7GB: boot/grub/stage2
  48.4GB: boot/initrd.img-2.6.27-15-generic
  47.5GB: boot/initrd.img-2.6.28-16-generic
  50.6GB: boot/initrd.img-2.6.31-14-generic
  36.0GB: boot/initrd.img-2.6.31-15-generic
  46.8GB: boot/vmlinuz-2.6.27-15-generic
  48.3GB: boot/vmlinuz-2.6.28-16-generic
  50.1GB: boot/vmlinuz-2.6.31-14-generic
  47.4GB: boot/vmlinuz-2.6.31-15-generic
  36.0GB: initrd.img
  50.6GB: initrd.img.old
  47.4GB: vmlinuz
  50.1GB: vmlinuz.old

================================ sdb2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

```

What a nice little script.

---

### Post by DasLemm on 2009-12-04
is the problem that i formatted the crunchbang partition in ext4? it seems that in RESULTS.txt it's not seeing an OS on that partition. Would it be easier to simply reformat the partition as ext3 and start over?

---

### Post by presence1960 on 2009-12-04
Go into BIOS and set sdb (80 GB) as first hard disk to boot in the hard disk boot order. Save changes to CMOS. Continue booting into Ubuntu.

Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L in .lst

scroll down to this:

```
title		!#Crunchbang
uuid		471491b4-0303-41e7-afb6-68f4f62dba90
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=471491b4-0303-41e7-afb6-68f4f62dba90 ro
initrd		/boot/initrd.img-2.6.28-13-generic

title		!#Crunchbang (recovery mode)
uuid		471491b4-0303-41e7-afb6-68f4f62dba90
kernel		/vmlinuz root=UUID=471491b4-0303-41e7-afb6-68f4f62dba90 ro single
initrd		/initrd.img
```

& change it to:

```
title         Crunchbang
rootnoverify  (hd0,3)
chainloader   +1
```

Click Save at top toolbar, close file and reboot.

Please be aware that there appears to be something amiss with your Crunchbang installation on sdb4. See here:
```

sdb1: _________________________________________________________________________

   [COLOR="Red"] File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab[/COLOR]

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    [COLOR="Red"]File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'[/COLOR]
```

Note the difference between sdb1 Ubuntu and sdb4 Crunchbang. Also there is no menu.lst listed in the script as the sdb1 menu.lst is listed for Ubuntu. I am afraid you will have to reinstall Crunchbang. If you do the above when you reinstall Crunchbang to sdb4 install GRUB to /dev/sdb4 not the MBR. I haven't used Crunchbang in a minute but if the installer is like Ubuntu when you get to the window below clicked Advanced to choose where to install GRUB.

---

### Post by presence1960 on 2009-12-04
> **DasLemm said:**
> is the problem that i formatted the crunchbang partition in ext4? it seems that in RESULTS.txt it's not seeing an OS on that partition. Would it be easier to simply reformat the partition as ext3 and start over?

Could be, I am not sure if Crunchbang supports ext4.

---

### Post by DasLemm on 2009-12-04
So sdb is set in first boot priority.
I edited menu.lst to reflect the 'rootnoverify' setup you had, to no avail.
I'm going to try reformatting that partition as ext3 and reinstall crunchbang.
Thanks for your help up to this point. I'll get back to you when this is all done.

---

### Post by DasLemm on 2009-12-04
ok so, turns out the version of grub i was using does not support ext4. so when trying to boot to that partition, it was not able to read the files.
I reinstalled crunchbang on an ext3 partition and edited menu.lst accordingly and now it all works fine.
Thanks for your help.

---

