---
title: "Swop Disk Misery"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by ngms27 on 2005-10-03
I think I've established that my machines hard disk thrashes for minutes upon minutes when the swop is required.

This is my output from fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12289693+   c  W95 FAT32 (LBA)
/dev/hda2            1531       19457   143998627+   f  W95 Ext'd (LBA)
/dev/hda5            1531        5876    34909213+   b  W95 FAT32
/dev/hda6            5877       18144    98542678+   b  W95 FAT32
/dev/hda7           18145       19457    10546641   83  Linux

And this is /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext2    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda5       /media/windowsd vfat iocharset=utf8,umask=000 0 0
/dev/hda6       /media/windowse vfat iocharset=utf8,umask=000 0 0

And this from df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda7             10381004   7432612   2421060  76% /
proc                         0         0         0   -  /proc
sysfs                        0         0         0   -  /sys
devpts                       0         0         0   -  /dev/pts
tmpfs                   193344         0    193344   0% /dev/shm
/dev/hda5             34892144  30073712   4818432  87% /media/windowsd
/dev/hda6             98494544  89713728   8780816  92% /media/windowse
/dev                  10381004   7432612   2421060  76% /.dev
none                      5120      2808      2312  55% /dev
usbfs                        0         0         0   -  /proc/bus/usb

Is the fact that my swop is on the same partition causing my lockups? 

JonnyT

---

### Post by heimo on 2005-10-03
You're speaking about swap, right? I can't see your swap partition anywhere, which one is it? Or are you using swap file? Can you post output of command *free*. Thanks! :)

---

### Post by ngms27 on 2005-10-03
ngms27@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        386688     378136       8552          0       2948     146136
-/+ buffers/cache:     229052     157636
Swap:            0          0          0


JonnyT

---

### Post by ngms27 on 2005-10-03
How would I create one given it looks like the install didn't make one for me?

---

### Post by heimo on 2005-10-03
If you don't have free partition to use as a swap, it's easiest to create swapfile. This thread gives instructions: 
[http://ubuntuforums.org/showthread.php?t=54307](http://ubuntuforums.org/showthread.php?t=54307)

If you have any questions, don't hesitate to ask. :)

---

