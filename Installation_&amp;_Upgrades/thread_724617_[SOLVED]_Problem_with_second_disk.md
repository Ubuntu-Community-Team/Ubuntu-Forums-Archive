---
title: "[SOLVED] Problem with second disk"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by Gargorb on 2008-03-14
I am new to Ubuntu. I have trawled the web to sort out most of my installation issues but I am now stuck.

So far I have installed Ubuntu desktop - running Samba on it and all is fine.

However, there is a second disk in the box.  The PC was formerly Windows XP and the disk was a slave used for data storage.  I want to use the second disk for data storage under Ubuntu.  

After the install I could see the disk and read and write to it but I was having issues with Samba which made me decide to reformat it with a Linux file system. I used QT Parted to format it as ext3. Now I can see the disk using Fdisk in terminal (see below) and also in QT Parted but not in 'Places'.

There is also a message about different physical/logical endings????

Can anyone tell me how I make this disk visible and usable?

Here's the fdisk info:
Disk /dev/sda: 4324 MB, 4324368384 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ba42ba3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         496     3984088+  83  Linux
/dev/sda2             497         525      232942+   5  Extended
/dev/sda5             497         525      232911   82  Linux swap / Solaris

Disk /dev/sdb: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15a504ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         788     6329578+  83  Linux
Partition 1 has different physical/logical endings:
     phys=(786, 254, 63) logical=(787, 254, 63)

---

### Post by Rocket2DMn on 2008-03-14
Can you please post your fstab file
```
cat /etc/fstab
```
Since you formatted the drive with a different filesystem, if the drive is in fstab, it needs to be updated.

---

### Post by Gargorb on 2008-03-14
gargoyle@gargoyle:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=54defdc8-e04a-4e96-856a-3f9e134fcd33 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b3a0a64c-3338-4c18-8549-6675843677f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Rocket2DMn on 2008-03-14
Ok, so pick a mount point, like /media/data or something (we'll use that, but you can change it if you want)
Make the mountpoint and edit fstab:
```
sudo mkdir /media/data
gksudo gedit /etc/fstab
```
add the line:
```
/dev/sdb1 /media/data ext3 defaults 0 0
```
Save and close.  Then mount the partition and chown it to your username.
```
sudo mount -a
sudo chown -R /media/data
```
You should now be good to go.

---

