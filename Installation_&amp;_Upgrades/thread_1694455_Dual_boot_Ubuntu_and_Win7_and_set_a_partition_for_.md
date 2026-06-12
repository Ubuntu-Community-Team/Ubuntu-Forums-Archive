---
title: "Dual boot Ubuntu and Win7 and set a partition for sharing data files"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2011-02-24
I'd like to dual boot Ubuntu and Win7 and set a partition for sharing data files. What kind of file system should I use?

I find if I use FAT32, the x bit of files can't be set. I checked context menu (>Properties>Permissions) and verified that I do have "Allow executing file as program" checked.

Could I use NTFS?

Thanks!

---

### Post by sikander3786 on 2011-02-24
I would recommend doing a manual partitioning in your case. See here for some basic info.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

And for data sharing, I would recommend using NTFS partition instead of FAT32. You can use ntfs-config tool from Software Center to auto-mount your NTFS drives.

However it is not recommended to mount your Windows partition in Ubuntu as Windows doesn't like many changes to its partition without it being notified.

[https://help.ubuntu.com/community/MountingWindowsPartitions#Automatic%20Configuration](https://help.ubuntu.com/community/MountingWindowsPartitions#Automatic%20Configuration)

---

### Post by Rubi1200 on 2011-02-24
I think FAT32 is probably okay as long as you are not dealing with files that exceed the 4GB limit for FAT file-systems.

In any event, it is better to use a shared data partition as you are less likely to encounter permissions problems.

---

