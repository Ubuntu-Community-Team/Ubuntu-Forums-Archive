---
title: "mounting root filesystem really slow on boot"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by widjajayd on 2006-06-17
I just installed dapper drake release 1 june,

I have windows XP (fat32) in C: drive.

when I install ubuntu dapper drake I choose manual partition,
and it shows error on my fat32 partition
below is the error message:
"Unable to read the contents of this file system because of this some operations may be unavailable

did you install the correct plugin for this file system?"

I just continue my installation and when I reboot the PC after installation it really slow on mounting root file system (Almost 3-4 minutes)

_I do not want to Access my FAT32 partition from Linux,_
How can I disable mount my Fat32 partition to make faster on booting.

Thank you All

---

### Post by catlett on 2006-06-17
First make a backup just in case you want to restore your fstab ```
sudo cp /etc/fstab /etc/fstab_backup
```Enter this command ```
sudo gedit /etc/fstab
``` That will bring up your fstab which is the file that tells your computer which partitions and drives to mount on startup. Just delete the entry for your windows fat32 partition. If you get confused post your /etc/fstab here and I'l tell you which one to remove.

---

### Post by widjajayd on 2006-06-17
I did this, but the problem still exist 
I think it's ubuntu drake bug for some hardware/harddrive

thanks for reply

---

