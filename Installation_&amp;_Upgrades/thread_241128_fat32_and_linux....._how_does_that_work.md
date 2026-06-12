---
title: "fat32 and linux..... how does that work?"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by Mazehero55 on 2006-08-21
I just have a few questions, basicly what I want to do is be able to move files from a windows partition to a Linux partition. I hate just wasting cd's just to move files and the like, is there some way to do this by just sending them to the other partition? 
I heard that you can install Linux on a fat32(aparently ntfs isn't that good to linux) and be able to drag and drop to it from windows. I'd just hate to waste 5 cd's just to move my music. But the problem is that when I try to install Ubuntu on it, it says wrong filesystem. Basicly all I want to know is how to install ubuntu on a fat32 partition ????:confused:???? does anyone know how I can do this. 
Or if there is any other way to exchange files from partition to partition then I'm all ears.

Thank you so much.

---

### Post by catlett on 2006-08-21
Install Ubuntu to an ext3 filesystem. That is the fs of choice for ubuntu. It is similar to ntfs in that it handles large files and has journaling.
Then go here [http://www.fs-driver.org/](http://www.fs-driver.org/) and download the ext3 driver for windows (it is technically the ext2 driver but iot works because ext3 is ext2 with journaling). Once you install it, ubuntu's partition will show up on your My Computer page as another disk next to C. Then you just drag and drop to it like you would any other folder.

---

### Post by encompass on 2006-08-21
Try this....
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by randell6564 on 2006-08-21
> **Mazehero55 said:**
> I just have a few questions, basicly what I want to do is be able to move files from a windows partition to a Linux partition. I hate just wasting cd's just to move files and the like, is there some way to do this by just sending them to the other partition? 
I heard that you can install Linux on a fat32(aparently ntfs isn't that good to linux) and be able to drag and drop to it from windows. I'd just hate to waste 5 cd's just to move my music. But the problem is that when I try to install Ubuntu on it, it says wrong filesystem. Basicly all I want to know is how to install ubuntu on a fat32 partition ????:confused:???? does anyone know how I can do this. 
Or if there is any other way to exchange files from partition to partition then I'm all ears.

Thank you so much.


Hi!  I was dual booting Windows and ubuntu for a while.  I also have a 20GB HD formatted as fat32 that I used just to store my music and video files.  This way I could access those files from either OS.

If you have only one HD and some unallocated space on it somwhere then just format that space to fat32 from windows, and then make sure that you add that partition to your /etc/fstab in ubuntu.

---

### Post by VK2XCI on 2006-08-21
> **Mazehero55 said:**
> I just have a few questions, basicly what I want to do is be able to move files from a windows partition to a Linux partition. I hate just wasting cd's just to move files and the like, is there some way to do this by just sending them to the other partition? 
I heard that you can install Linux on a fat32(aparently ntfs isn't that good to linux) and be able to drag and drop to it from windows. I'd just hate to waste 5 cd's just to move my music. But the problem is that when I try to install Ubuntu on it, it says wrong filesystem. Basicly all I want to know is how to install ubuntu on a fat32 partition ????:confused:???? does anyone know how I can do this. 
Or if there is any other way to exchange files from partition to partition then I'm all ears.

Thank you so much.

Ubuntu will READ an NTFS partition, but NOT WRITE. Writing is experimental at this time. Linux WILL write to a FAT32 partition! And yes, you can drag and drop from NTFS to Linux but not the other way. You can drag and drop both ways between linux and FAT32!

I have a dual boot Win2K/Ubuntu 6.06 box. I created a separate FAT32 partition of 2GB between the Win2K NTFS partition and the Linux Ext2 partition. I use this partition to share document, music etc between the two OSs. I have a folder called "My Shared Documents" which I sync with the Win2K "My Documents" Folder Also a folder to sync Thunderbird Mail stuff and Firefox Bookmarks so I get the same info no matter what OS I boot.


You CAN"T install Linux on a Fat32 partition to my knowledge! So leave Windows on the NTFS partition and manually partition in the Ubuntu installation process.

I have
Win2KSP4 NTSF  8GB
Shared   FAT32 2GB
Linux    EXT3  8GB
Linux    Swap  1GB

Works for me!

---

### Post by komputes on 2006-09-18
Hmmm, I like the solution for providing Windows NT4.0/2000/XP with full access to Linux Ext2 volumes, but I would like to ask a question tu you linux gurus: is for the reverse possible?

I want to be able to have full access to my Windows fat32 C: drive from within Ubuntu, but I have no idea how to do this. Before moving to Ubuntu, I was using SuSe Linux v10. In SuSe, all I had to do to have access to my files was go to Filesystem>windows> and I had access to my C: drive  - that was frekin' easy! Why should it be any different with Ubuntu? Why does SuSe have this feature and Ubuntu does not?

Anyone? Anyone? Buller? Buller?

:cool:

---

### Post by hearnden on 2006-09-18
Yes, you can mount a fat32 partition so it can be used from within ubuntu.  You just need to know the device name for the partition (if your fat32 partition is partition #3 on disk 1, then it's /dev/hda3; partition #1 on disk 2 is /dev/hdb1, etc), then try:

```

$ sudo mkdir /windows
$ sudo mount -t vfat /dev/hda3 /windows

```

(using whatever device name for your fat32 partition instead of /dev/hda3)
You can read more about having this done automatically and controlling the permissions of /windows (all users, some users, only root user, ...) by reading the man page for mount:

```

$ man mount

```

---

### Post by randell6564 on 2006-09-18
> **komputes said:**
> Hmmm, I like the solution for providing Windows NT4.0/2000/XP with full access to Linux Ext2 volumes, but I would like to ask a question tu you linux gurus: is for the reverse possible?

I want to be able to have full access to my Windows fat32 C: drive from within Ubuntu, but I have no idea how to do this. Before moving to Ubuntu, I was using SuSe Linux v10. In SuSe, all I had to do to have access to my files was go to Filesystem>windows> and I had access to my C: drive  - that was frekin' easy! Why should it be any different with Ubuntu? Why does SuSe have this feature and Ubuntu does not?

Anyone? Anyone? Buller? Buller?

:cool:

HI! Just follow this [tutorial]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite") and you will have full access to your Fat32.

---

