---
title: "Ubuntu 14.04 locked HDD ?!"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by jiri5 on 2014-10-26
Hello guys !
I have been happy Ubuntu 14.04 and Windows 7 dualboot user on my notebook Asus K73SV.
Yesterday I wanted to reinstall ubuntu because I wanted to have clean installation -
plugged in my usb stick with live ubuntu, changed BIOS priority....
I was offered to re-install Ubuntu in graphic setup. So I did.... and suddenly blackscreen for an hour.. So I restarted my notebook and there wasn't possible to find any OS !
It wanted some bootable device....
So I booted up my Live Ubuntu from usb stick to check what happened....
There was icon of my HDD with key and it said 749 GB ENCRYPTED.
When I tried to open it, there was a message Enter a passphare to unlock this volume.
So I did and icon of this HDD dissapeared from a list.
I have no idea what to do... Are my data only locked or are thez gone?!
Will be ever possible to boot up my Windows 7 from part of a HDD?
What should I do?
Please help, I need my notebook for studying my College...
PS: I am sorry for my English, it's not my first language.

---

### Post by yancek on 2014-10-26
Which option did you select for Installation Type?  If you did not use the manual method (Something Else) you don't really have much control.  Boot the Ubuntu flash drive and open a terminal then run:  sudo fdisk -l(Lower Case Letter L in the command) and post the output which will show information on drives, partitions and filesystem types.

---

### Post by jiri5 on 2014-10-26
I maybe select that option with encrypting - I am not sure now ...
This is what I got
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 15.5 GB, 15479597056 bytes
32 heads, 63 sectors/track, 14996 cylinders, total 30233588 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0e5b1917

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    30231935    15115936+   c  W95 FAT32 (LBA)

Disk /dev/mapper/luks-56984563-8d61-4604-81c2-b19bf64c353c: 749.4 GB, 749359595520 bytes
255 heads, 63 sectors/track, 91104 cylinders, total 1463592960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/luks-56984563-8d61-4604-81c2-b19bf64c353c doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 745.2 GB, 745155854336 bytes
255 heads, 63 sectors/track, 90593 cylinders, total 1455382528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 4202 MB, 4202692608 bytes
255 heads, 63 sectors/track, 510 cylinders, total 8208384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
ubuntu@ubuntu:~$

Does anybody know what to do? Or options to do?

---

### Post by jiri5 on 2014-10-27
Does anybody know what to do? Or my options I have now?

---

### Post by oldfred on 2014-10-27
Post this.
Because it is encrypted, it also uses LVM which is shown as the /dev/mapper partitions.
And you are showing gpt which fdisk does not support.

Normally LVM is a full drive install, or not a dual boot install.

sudo parted -l

Do you have a good backup of Windows?

---

### Post by jiri5 on 2014-10-27
I have the most important files from windows on my external hard drive... And I don't have windows cd...... I always installed from part of a disk - as it came on my notebook.

---

### Post by oldfred on 2014-10-27
Hard drives also fail, so relying on a partition on same hard drive as Windows is usually not recommended. Better to have full image backup.

The LVM install default install will overwrite all partitions. Only if you select Something Else and manually install do you then have total control over which partitions may be overwritten or not.

The Product ID is now inside the UEFI. And it only works with the Vendor OEM version. Some vendors will ship you the recovery DVDs that you should have made for just a nominal charge. Others do not. Check with your vendor.
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

