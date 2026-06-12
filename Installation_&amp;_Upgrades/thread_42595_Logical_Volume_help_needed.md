---
title: "Logical Volume help needed"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by Enki on 2005-06-18
I'm installing Hoary (server) on a system with two 20GB IDE disks. It's just a play-box, but I want to set it up like a proper production server for the experience.

Since I have no idea how the size of different parts of the filesystem will develop, I would like to combine both disks into one logical volume. I don't want to use RAID 0 because it will double my fault chance.

Question 1: does LVM use striping (like RAID 0) or are files kept more in one piece like with JBOD?

Question 2: Ubuntu uses Ext3 by default. I would like to use ReiserFS instead. Any reason I shouldn't?

---

### Post by alastair on 2005-06-18
LVM is separate to RAID. It can sit on a RAID device if desired. From low-level to high-level :

partitions -> RAID md -> LVM

On install - partition your 2 disks the same.

You can use RAID 1 i.e. mirror.

Example :

create partitions on EACH disk :

    part1 for /boot  (e.g. 200 MB)
    part2 for /   (e.g. 300 MB)
    part3 for swap   (e.g. 1 GB)
    part4 for REST of data  (rest of free space)

Make 1,2 and 4 RAID type - RAID 1 :

    sda part 1 + sdb part 1  == md0 say
    sda part 2 + sdb part 2  == md1 say
    sda part 4 + sdb part 4  == md2 say

Then, make md2 a logical volume type (LVM) - and create partitions inside e.g. /var,/usr,/home etc.).

Use whatever filesystem you want.

---

### Post by Enki on 2005-06-18
Thanks,

I'd rather skip the whole RAID bit though. There's nothing important enough on this box to justify mirroring.

What I have in mind is this:

HDA
- primary 100MB   /boot
- primary 400MB   swap
- primary <rest>   LVM part1

HDD
- primary 400MB     swap
- primary <rest>   LVM part2

both LVM parts in one LVM group, one LVM volume. This volume then should hold 4 logical partitions for /, /home, /var, and /usr

All partitions ext3 (changed my mind).

Problem is, creating ext3 partitions on the logical volume fails. It seems to work if I only put one partition on the logical volume. Should I create a volume for each partition?

---

### Post by Enki on 2005-06-18
To answer my own question: one LV will hold one partition. Install went fine after I realised that.

Still wonder if LVM uses striping though?

---

### Post by crouton on 2005-08-10
Tell us how you did it, please?

---

