---
title: "dual boot proplems"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by atliia on 2010-03-09
Hello, I am trying to set up my new Dell 1545, which is running win 7, for an ubuntu dual boot. I am indtending to run 9.10 as my primary os however I am having a few problems.

My Harddrive has an os partition a recovery partition both NTFS and a Dell Utilities partition in FAT16. I am looking to put ubutnu in an ext4 partition and then I would like to add a shared NTFS partition. However, I am only permitted to have 4 primary partitions. I was wondering if there is any way to move the dell utility partition or perhaps the recovery partition into an extended partition with the primary os. If not, is there some other meathod that would permit me to set up a dual boot using a shared file system? Thanks.

---

### Post by presence1960 on 2010-03-09
Turn off System restore and page file, then defrag windows at least once possibly twice. Use windows disk management utility to shrink the windows partition to create space for Ubuntu & intended shared NTFS partition. When the resize is complete reboot into windows to make sure windows still boots properly.

If it boots properly boot the Ubuntu Live CD and choose "try ubuntu without any changes." When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
gksu gparted
```Create an extended partition from all the unallocated space. Click the green checkmark at top. Now think how much space you want for the NTFS shared partition. Create a logical NTFS partition within the extended partition. Click the green check mark at top. When completed close gparted.

On the desktop double click the install ubuntu icon and begin the install. At the prepare disk space window choose "use the largest continuous free space" option. This will install Ubuntu to the unallocated space for you.

---

### Post by atliia on 2010-03-09
Thank you very much. This was exactly what I wanted to do.

---

### Post by presence1960 on 2010-03-10
> **atliia said:**
> Thank you very much. This was exactly what I wanted to do.

Glad to help. Let us know how it turns out!

---

