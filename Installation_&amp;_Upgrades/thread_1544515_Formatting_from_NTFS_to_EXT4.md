---
title: "Formatting from NTFS to EXT4"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by rbalaa on 2010-08-02
I would like to format my current NTFS drive to EXT4. I've searched and found there are two commands to do this, mkfs or mke2fs.

What are the proper steps to do format an NTFS to EXT4 ? 

If you recommend EXT3 over 4, please advise.

---

### Post by lechien73 on 2010-08-02
You could just use GParted to format the drive. Make sure the drive is not mounted, and then go to System > Administration > GParted. You can format the partition to ext4 through there. Make sure you've backed up any data you want to keep, obviously ;)

This thread on the Ubuntu forums gives some of the differences between ext4 and ext3: [http://uri.tl/r](http://uri.tl/r)

---

### Post by Irony on 2010-08-02
System > Admin > Disk Utility

---

### Post by rbalaa on 2010-08-02
Forgot to mention I'm using Ubuntu Server. So I only have command line access.

---

### Post by oldos2er on 2010-08-02
**parted** is the CLI equivalent of gparted.

---

