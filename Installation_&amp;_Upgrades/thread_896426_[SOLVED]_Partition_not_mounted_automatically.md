---
title: "[SOLVED] Partition not mounted automatically"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by yBfj3nbmn7 on 2008-08-21
Hi!

I recently migrated from Windows to Ubuntu, but I made some mistakes in the installation that I'm paying for. My main problem is this:

When Ubuntu partitioned my hard drive, I thought that it would be a wise decision to partition it into four drives:
1. Linux-swap (8Gb)
2. Windows NTFS (28Gb)
3. Ubuntu (28Gb)
4. A FAT32 drive which could be accessed from both OS. (402Gb)

But after I had installed everything, I could not read the FAT32 drive from either Windows nor Ubuntu. I was finally able to solve this by installing GParted, and I could change the FAT32 into a ext3 system. The problem is that after I did this, the drive does not mount automatically. So every time I start Ubuntu, I have to start GParted and mount the drive manually.

How can I solve this? I've got four partitions right now. In GParted, they are listed as:
/dev/sda1  linux-swap  8.01G
/dev/sda2  ntfs  /windows  27.95G
/dev/sda3  ext3  /  27.94G
/dev/sda4  ext3  /media/commonfiles  401.87G

---

### Post by Too Late on 2008-08-21
You have to edit your /etc/fstab file. Post its contents here if you are unsure what to do.

Also, post the output of this command:
```
sudo blkid
```

---

### Post by yBfj3nbmn7 on 2008-08-21
My /etc/fstab file is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=11ca1e6d-6c38-41ee-88f3-9344542c34dc /               ext3    relatime,errors=remount-ro 0       1
/dev/sda4       /media/commonfiles vfat    utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=3EBC58C0BC5873FD /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=f7eb7e32-e78b-4460-a3d0-fded3ff8e5a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


sudo blkid returns the following information:

/dev/sda1: TYPE="swap" UUID="f7eb7e32-e78b-4460-a3d0-fded3ff8e5a9" 
/dev/sda2: UUID="3EBC58C0BC5873FD" LABEL="HDD" TYPE="ntfs" 
/dev/sda3: UUID="11ca1e6d-6c38-41ee-88f3-9344542c34dc" TYPE="ext3" 
/dev/sda4: UUID="23d944be-155e-4498-9ef6-17c7096176f7" TYPE="ext3" 
/dev/sdb1: LABEL="My Book" UUID="3717-D230" TYPE="vfat"

---

### Post by Too Late on 2008-08-21
Ok, let's look at this line:
```
/dev/sda4 /media/commonfiles vfat utf8,umask=007,gid=46 0 1
```

Because the partition is not FAT32 anymore, it should be like this:
```
/dev/sda4 /media/commonfiles ext3 relatime 0 2
```
Alternatively (and maybe preferably), you can use the UUID number to identify your partition:
```
UUID=23d944be-155e-4498-9ef6-17c7096176f7 /media/commonfiles ext3 relatime 0 2
```
Lines starting with # are comments, they do nothing.

---

### Post by yBfj3nbmn7 on 2008-08-21
Okay, I tried to change the file as you suggested, but I got the following error message:

"Could not save the file /etc/fstab. You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

---

### Post by Too Late on 2008-08-21
Yes, you have the root permissions to edit that file. Go to terminal and type:
```
gksudo gedit /etc/fstab
```

It's always a good idea to make backups before editing important system files, just in case:
```
sudo cp /etc/fstab /etc/fstab.backup
```

---

### Post by yBfj3nbmn7 on 2008-08-21
Wow! I made the change that you suggested, and now it mounts automatically! Thank you, Too Late!

---

