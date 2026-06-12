---
title: "Dual boot with XP (ubuntu first)"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by lover_of_sc on 2008-10-11
Hi all,

I am still very new to ubuntu and would really appreciate some detailed help here. I would like to take out some of my second hard drive, change it from EXT3 to NTFS and add a dual boot Windows XP. I have tried to read a few tutorials but I am still uncertain how to do it as easy as possible. I have backed up all my files to an external HD, but I really don't want to mess it up so I have to reinstall my ubuntu as it have taken me a looooong time to get it working like I want. 

Below are some information about my current system, may be of any help?

---------------------------------------------------------
anders@anders-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5966b27

Device Boot Start End Blocks Id System
/dev/sda1 * 1 18701 150215751 83 Linux
/dev/sda2 18702 19457 6072570 5 Extended
/dev/sda5 18702 19457 6072538+ 82 Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1de2c90e

Device Boot Start End Blocks Id System
/dev/sdb1 1 19457 156288321 83 Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fcdf9c4

Device Boot Start End Blocks Id System
/dev/sdd1 1 60801 488384001 83 Linux
---------------------------------------------------------
anders@anders-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a8ece2c8-1bfb-4f2d-8261-e418284af78d /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1   /media/disc   ext3   defaults   0   1
# /dev/sda5
UUID=f3692d2a-63a0-4f91-befe-1a8406428a35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
---------------------------------------------------------
anders@anders-laptop:~$ sudo blkid
[sudo] password for anders: 
/dev/sda1: UUID="a8ece2c8-1bfb-4f2d-8261-e418284af78d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="f3692d2a-63a0-4f91-befe-1a8406428a35" 
/dev/sdb1: UUID="89c48ec6-2861-4bc7-a8e8-8086fd53d7ea" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="f79d1e32-5cf6-4b48-b204-40d9d9733e82" TYPE="ext3" 
anders@anders-laptop:~$ 
---------------------------------------------------------
anders@anders-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G  107G   27G  80% /
varrun               1013M  132K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   68K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1             147G  124G   16G  89% /media/disc
/dev/scd0             7.9G  7.9G     0 100% /media/cdrom0
/dev/sdc1             463G  212G  228G  49% /media/disk

---------------------------------------------------------

---

### Post by Pumalite on 2008-10-11
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
If you want to use Ubuntu in one and Windows in another hard drive:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by lover_of_sc on 2008-10-11
Thank you, still a little confused. if I backup and change the grub boot menu first, then reformat my second harddrive to NTFS. Then reboot the computer with the XP installation CD. Will the XP installation CD overwrite any on my ubuntu drive? Will XP overwrite the boot menu created within ubuntu? 

many thanks.

---

### Post by Pumalite on 2008-10-11
You have Ubuntu first with his boot loader Grub. You install XP, which will erase Grub. Then you reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
And make an entry for XP in menu.lst if XP doesn't show up at first. Most of the time all is swell. Read the link carefully.

---

### Post by caljohnsmith on 2008-10-11
It should be as simple as just adding another primary partition to your sda drive for Windows XP, installing Windows, then restoring Grub using the link that Pumalite gave. To make the new primary partition, you'll need to do it from a Live CD by running:
```
gksudo gparted
```
Let us know how it goes or if you have more questions. :)

---

### Post by status001 on 2008-10-11
*A simple way to that is using wubi(Windows based UBuntu Installer) and do some work. Install Ubuntu inside windows no need to partition your HDD. Then in XP right click on My Computer> Properties> Advanced> Startup and Recovery(click on Settings)> Then choose your default operating system. That's all.*

---

