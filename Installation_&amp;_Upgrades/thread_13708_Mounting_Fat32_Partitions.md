---
title: "Mounting Fat32 Partitions"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by Kokosnuss on 2005-02-02
Hi, I tried to mount some FAT32 partitions using the instructions on [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows). These partitions already contain data and are also used by Windows XP.

First I thought it would work, but when I took a closer look, I found out that only files were displayed. Any filetype wasn't recognized and folders were displayed as files.

Of course, on Windows XP, these partitions are displayed correctly.

Could anyone help me with this problem, please?

---

### Post by rudi on 2005-02-02
if you add this line to your /etc/fstab it ought to be working:
 ```
 /dev/hda1	 /media/windows	vfat	umask=000	 0	 0
``` 
   (it does on my computer ;))
 
 ow, make sure the folder /media/windows exists after you reload/ reboot

---

### Post by Kokosnuss on 2005-02-02
Thank you! It works!

---

### Post by Cybergrinder on 2008-02-14
Hi there,

I have 3 FAT 32 partitions which I'm trying to mount; I've also followed the tutorial. My windows partition (hda1) mounts fine, but all the other partitions I get an error message stating no file system found. 

Windows is using these partitions fine.

---

### Post by housam on 2008-02-14
> **Cybergrinder said:**
> Hi there,

I have 3 FAT 32 partitions which I'm trying to mount; I've also followed the tutorial. My windows partition (hda1) mounts fine, but all the other partitions I get an error message stating no file system found. 

Windows is using these partitions fine.

Try to use this guide
[[COLOR="Red"]https://help.ubuntu.com/community/MountingWindowsPartitions[/COLOR]]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

