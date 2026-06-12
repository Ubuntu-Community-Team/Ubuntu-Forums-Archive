---
title: "Hello, Is it safe to change the filesystem of ubnutu to NTFS?"
date: 2024-08-17
forum: Installation &amp; Upgrades
---

### Post by jameswasincanada on 2024-08-17
I want to install windows but i cant because its not NTFS, can you answer that?

---

### Post by jameswasincanada on 2024-08-17
by meaning ubnutu i mean the drive that ubnutu was installed in.

---

### Post by deadflowr on 2024-08-17
You'll need to shrink the Ubuntu partition and then you can use the freed space to install Windows on.
Ubuntu won't work on NTFS.

---

### Post by jameswasincanada on 2024-08-17
Well, If I just format the drive by the normal way and change the filesystem to NTFS and boot with my Thumbdrive (contains windows11 iso) Will it still be able to install windows?

---

### Post by deadflowr on 2024-08-17
Do you want to keep Ubuntu?

---

### Post by TheFu on 2024-08-17
> **jameswasincanada said:**
> I want to install windows but i cant because its not NTFS, can you answer that?

NTFS is what MS-Windows uses.
Linux needs native Linux file systems for everything that isn't purely data.  HOME directories on Linux must also be native Linux file systems, That's /home/ by default, but HOME directories can be in other locations if you like.

You can make external storage devices NTFS, if you like.
You can make partitions that aren't used for any Linux OS NTFS as well.

Just like MS-Windows cannot use EXT4 for the OS, Linux cannot use NTFS for the OS or key storage areas.

Hope this is clear.

To get more specific help, post the command and output of these commands:
```
sudo parted -l
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

Use _forum code tags_ when posting or the columns will be lost and it is just too hard to read.

---

### Post by yancek on 2024-08-17
The answer to  your question in post 4 is yes, that is if you want to completely delete/overwrite Ubuntu.  You haven't indicated that.  If you want to keep Ubuntu, you need to shrink your current partitions to create free/unallocated space on which to install windows.  You could create a partition for it from Ubuntu and format it ntfs but it is usually better to do that from windows.  You won't be able to shrink the partitions on which you have Ubuntu installed while booting from Ubuntu.

Since you want to install windows, is there some reason you didn't post your question at a windows forum?i

---

### Post by oldfred on 2024-08-17
Windows in UEFI boot mode on gpt partitioned drives since 2012 wants many partitions, ESP, system reserved, main partition, and often several recovery partitions.
Do not create one NTFS partition in advance.
Leave unallocated space on drive for the total size you want for Windows.

---

### Post by jameswasincanada on 2024-08-18
no, theres aren't enough programs for me to use so im gonna switch to windows. (replying to deadflowr's comment)

---

### Post by jeremy31 on 2024-08-18
You can't delete the existing partitions with the Windows installer?

---

