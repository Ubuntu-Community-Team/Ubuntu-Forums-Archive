---
title: "Upgrading from Ubuntu 13.10 to Ubuntu 14.04 ( low memory error )"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by Vlad_Ulmeanu on 2015-01-26
Hello ,
I have recently installed Ubuntu 13.04 alongside Windows 7 via WUBI, allocating Ubuntu 9.31 GB of memory .
Because I couldn't download anything from the software center, I upgraded to Ubuntu 13.10 and then to Ubuntu 14.04 LTS .
Before I could end the second installation, Ubuntu said that I have less then 400 MB remaining ( low memory ) , while Windows says that the partition has 1.62 GB free .

At the moment, I can't run Ubuntu, because this message shows up ( " some serious errors have been found " ) when I try to open Ubuntu .

What can I do now ?
Thanks ,
Vlad

---

### Post by Vlad_Ulmeanu on 2015-01-26
( Ubuntu shows less than 400 MB free and Windows shows 1.62 GB free ) - might it be because for Ubuntu 1 MB = 1024 KB and for Windows 1 MB = 1000 KB ?

It's just a hypothesis, I don't know .

---

### Post by Impavidus on 2015-01-26
Wubi, Ubuntu 13.04 and Ubuntu 13.10 have all been unsupported for quite some time. Ubuntu needs the free space in the Ubuntu partition (which, in case of Wubi, is a virtual partition on the Windows partition). Windows reports free space on the Windows partition, but cannot look into the Ubuntu partition. And to prevent you and us from getting confused the next time, memory is RAM, the fast volatile memory of a computer. For permanent storage space we use the term disk space.

The best thing to do would be a clean install of Ubuntu 14.04 as a proper dual boot. You can make a backup of your Wubi system by making a backup of the file root.disk, which you can find on Windows. You can also access the root.disk file from an Ubuntu live disk and make backups of the files present.

---

### Post by Bucky Ball on 2015-01-26
> **Impavidus said:**
> Wubi, Ubuntu 13.04 and Ubuntu 13.10 have all been unsupported for quite some time. Ubuntu needs the free space in the Ubuntu partition (which, in case of Wubi, is a virtual partition on the Windows partition). Windows reports free space on the Windows partition, but cannot look into the Ubuntu partition. And to prevent you and us from getting confused the next time, memory is RAM, the fast volatile memory of a computer. For permanent storage space we use the term disk space.

The best thing to do would be a clean install of Ubuntu 14.04 as a proper dual boot. You can make a backup of your Wubi system by making a backup of the file root.disk, which you can find on Windows. You can also access the root.disk file from an Ubuntu live disk and make backups of the files present.

^^^
This. And [this]("http://ubuntuforums.org/showthread.php?t=2229730"). ;)

---

### Post by hakuna_matata on 2015-01-26
> **Vlad_Ulmeanu said:**
> 
Ubuntu said that I have less then 400 MB remaining ( low memory ) , while Windows says that the partition has 1.62 GB free .

If you install Ubuntu with Wubi, Ubuntu doesn't use the space of a whole real partition for system files. 
```
df -h
```
shows you the difference:

The line with "/" the available space for system files:
```
/dev/loop0       18G     18G  18G   100% /
```
The line with "/host" the available space on your Windows partition:
```
/dev/sda1       100G     20G  80G   20% /host
```

A solution could be: [URL="https://help.ubuntu.com/community/ResizeWubiDisk"]How_do_I_resize_the_virtual_disks
[/URL]
In your case (1.62 GB is not enough space to duplicate a virtual disk) a real resize  is a better solution: [Resize WubiDisk]("https://help.ubuntu.com/community/ResizeWubiDisk")

But my recommended solution is to migrate virtual disks to real partitions: [Migrate Wubi]("https://help.ubuntu.com/community/MigrateWubi") OR this:
 > **Impavidus said:**
> 
The best thing to do would be a clean install of Ubuntu 14.04 as a proper dual boot.

In all cases, please backup important data: [How_can_I_make_a_backup_of_my_Wubi_install]("https://wiki.ubuntu.com/WubiGuide#How_can_I_make_a_backup_of_my_Wubi_install.3F")

---

### Post by Vlad_Ulmeanu on 2015-01-28
Thank you for your answers .

I uninstalled wubi and installed Ubuntu 14.04 from an USB .

However , I got another problem, which will be covered in another thread, because now it has noting to do with wubi .

---

### Post by Bucky Ball on 2015-01-29
Perhaps mark this thread as solved to help future travelers and post a link to the new thread if you'd like. Good luck. ;)

---

