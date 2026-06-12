---
title: "Not enough free space for installation?"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by Scooter7 on 2007-05-29
I'm having a similar problem... I'm trying to install Edgy to a 500 GB external HDD, which has 460 GB of free space on it.

I tried to make a partition of 166 GB, but Ubuntu tells me there's not enough space on the drive (when I try the install with Dapper LTS), and when I try with Edgy's installer, it just sits and does nothing at the partitioning screen after choosing partition size and clicking continue.

---

### Post by aysiu on 2007-05-29
Even though your freezing issue may be related, I think it's best for you to have a dedicated thread to your problem, so I've moved your post out of the other thread.

Unfortunately, I don't know how to help you with this problem. I'm hoping someone else will jump in.

Have you installed to an external drive before? Could that be the cause of the problem somehow?

---

### Post by Scooter7 on 2007-05-29
No, I have never installed to an external - only to an old IBM PC and a Dell.

The hard drive file system is FAT32, if that's of any help, and I know it works, as I copied some data to it in Windows, and I can access it while running Ubuntu's Live CD.

---

### Post by ikonia on 2007-05-29
please show us the output of 

```


sudo fdisk -l /dev/$drive_device_name


```


replacing $drive_device_name with the device file name of your hard disk eg: /dev/sda

thanks

---

### Post by Scooter7 on 2007-05-29
Here's the output:

> Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)

---

### Post by ikonia on 2007-05-30
you've used up all the disk with a 500GB partition as I read that. 

You've then put a fat 32 file system on it, so there is no way to resize that disk as there is no empty or usable space.

---

### Post by Wim Sturkenboom on 2007-05-30
Adding to ikonia:
[LIST]
[*]make a backup of the data (if necessary)
[*]delete the existing partition
[*]create new partitions for swap (2x memorysize with a max of 1GB), root (/; with so much space I suggest something like 20GB)) and home (/home; whatever you feel like). I suggest that you also create a fat32 partition for data exchange in case of a dual boot scenario (quite likely when you have an external HD for Ubuntu and as you mentioned windows)
[/LIST]

---

### Post by Scooter7 on 2007-06-03
Well, that worked!

Thanks for your help.   I apologize for not replying earlier - my internet connection has been down for most of the week.

   ~Teh DS (aka Scooter7) ;)

---

