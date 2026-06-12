---
title: "Move Ubuntu from One Hard Disk to Another"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by Monarch2007 on 2007-05-24
Hi all,
I am new to Ubuntu. I have it installed on my first 80GB hard disk. Recently, I bought another 250GB HDD. I created a 80GB Windows partition on it and using the same for backing up my Windows related data.
Now, I wanted to move Ubuntu from the first HDD to the second, so, I created Linux partitions in the second HDD and copied all files (following instructions in this forum and a couple of others - a BIG Thanks !!) to the second HDD. Here is what gparted tells me:
/dev/hdb1     fat32           76.29GiB      boot,lba
/dev/hdb3    ext3              39.06GiB     
/dev/hdb4    extended     117.53GiB
   /dev/hdb5  linux-swap   603.98MiB
   /dev/hdb6  ext3               116.94GiB
/dev/hdb2     unknown       2.49MiB      lba

I find that the files are actually copied correctly.

Now my question is, since I have already partitioned part of HDD2 for Windows, how can I tell GRUB to boot from HDD2? Should I install GRUB on HDD2 or is it enough to modify menu.lst file in HDD1(and HDD2)  to point to HDD2, boot Ubuntu and expect that GRUB would have saved the information in MBR of HDD1? I am a little confused.. Can someone give me the steps please?

Thanks very much.

---

