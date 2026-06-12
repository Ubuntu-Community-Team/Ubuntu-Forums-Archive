---
title: "two home directories after install, home directory in seperate partition unrecognized"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by yeshua-1 on 2015-01-20
Install of 14.10, although I indicated during the install that my old home directory should be /home, the install created a new home dirctory, within the system partition.
I don't want to use the new home directory in the system partition, I want to use the former directory which is in its own seperate partition. 
How do I get Ubuntu to solely use the former home directory in its seperate partition.

Here is my fstab file
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=b34b9a8d-971c-4bb5-86ef-754fb4d3b465 /               ext4    errors=remount-ro 0       1
# /data1 was on /dev/sda7 during installation
UUID=5CD5-2F9A  /data1          vfat    utf8,umask=007,gid=46 0       1
# /home was on /dev/sda6 during installation
UUID=8ceb8b8e-73ee-438c-bab9-7a3dff593e79 /home           ext4    defaults        0       2
# /win7 was on /dev/sda1 during installation
UUID=204F406A2D979568 /win7           ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=372c7945-4df2-4a92-a030-19207d4700c0 none            swap    sw              0       0

---

### Post by grahammechanical on 2015-01-20
Please do not start duplicate threads for the same problem

[http://ubuntuforums.org/showthread.php?t=2261672&p=13211885#post13211885](http://ubuntuforums.org/showthread.php?t=2261672&p=13211885#post13211885)

---

### Post by oldos2er on 2015-01-20
Duplicate closed.

---

### Post by oldfred on 2015-01-21
Is this not the correct partition for /home as shown in your fstab?

```
# /home was on /dev/sda6 during installation
UUID=8ceb8b8e-73ee-438c-bab9-7a3dff593e79 /home           ext4    defaults        0       2
```

---

