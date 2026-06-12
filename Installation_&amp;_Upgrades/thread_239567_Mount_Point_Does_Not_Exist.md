---
title: "Mount Point Does Not Exist"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by TriJump on 2006-08-19
I have a partition on my hard drive setup as a FAT32 file system, that way I can read and write between xp and ubuntu.  While XP recognizes the FAT32 partition, ubuntu does not.  If I try to mount it via the terminal using sudo mount /dev/hda5 it says that mount point /media/hda5 does not exist.  I've looked in my my fstab file and there was no entry for the fat32 partition so I added one to that file and still nothing.  I really have no idea where to go from here, any help would be greatly appreciated.

---

### Post by christhemonkey on 2006-08-19
You need to create the folder for it to be mounted to:
```
sudo mkdir /media/hda5 
```

---

### Post by zxee on 2006-08-19
If you want to mount in linux you have to create a place to mount to.
> sudo mkdir /media/hda5
I mostly use /mnt to mount things in but media should work.
then try the mount command you posted again.

---

### Post by TriJump on 2006-08-19
Okay, I used the mkdir and created a place and then used the mount command and got it mounted, so I am extremely thankful to you all for your help.  But now I have another question, as best I can tell I can not write to this partition.  I was under the impression that I could read and write to vfat/fat32 partitions from windows and linux?

---

### Post by christhemonkey on 2006-08-19
Yes you can, you need to make sure your line in fstab looks (something) like this:
```
/dev/hda5 /media/hda5 vfat user,umask=0000 0 0

```

---

### Post by TriJump on 2006-08-19
Awesome, it worked and I can read and write to it from both XP and Ubuntu.  You guys were a great help. Thanks again.

---

### Post by christhemonkey on 2006-08-19
No problem.
If you have any more probems/issues come back and let us know :)

---

