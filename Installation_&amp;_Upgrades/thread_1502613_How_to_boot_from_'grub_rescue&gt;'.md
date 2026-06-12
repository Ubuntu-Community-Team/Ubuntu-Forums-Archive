---
title: "How to boot from 'grub rescue&gt;'?"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by alem189 on 2010-06-05
Hi - 
I've got Ubuntu 10.04 installed on one partition, and Windows Vista on another. I was messing around with my partitions, and now I can't boot to either one. I just get an error when I boot up on GRUB which says "error: no such partition", and then a prompt saying 'grub rescue>'. I've read up on other people's posts, and they said that I should reinstall GRUB from a livecd, but that doesn't look like it does anything. It seems that GRUB is trying to boot from hd0,8, and that doesn't exist anymore. I can change the 'root' and 'prefix' variables to the right partitions, but the 'boot' or 'chainloader' command doesn't work. You should be able to boot from 'grub rescue>', because that's what it's for, right?

I just want to be able to boot into Ubuntu, not Windows.

PS: Sorry if I'm specifying way too much information(or not enough), I'm fairly new to forums.

---

### Post by darkod on 2010-06-05
Boot again with the cd in live mode, and in terminal execute:

sudo fdisk -l (small L)

That will list your partitions. Post the results here so we can give you the exact commands to reinstall grub2 to the MBR. Maybe you did it wrong.

It should work unless you completely deleted/wiped your ubuntu partition.

---

### Post by alem189 on 2010-06-05
OK, here's my output:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00638cbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6         995     7943362    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        6654       38913   259128450    7  HPFS/NTFS
/dev/sda4             996        6653    45447120    5  Extended
/dev/sda5             996        1631     5108638+  82  Linux swap / Solaris
/dev/sda6            1632        5073    27647833+  83  Linux
/dev/sda7            5074        6652    12683286   83  Linux

Partition table entries are not in disk order
```

---

### Post by darkod on 2010-06-05
Uhhh... you have two Linux partitions. Did you install with manual partitioning? If you did, you should know which is your root partition, /dev/sda6 or /dev/sda7, just use that in the first command, the second is the same:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

or

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart and you should see the grub2 menu. Check if booting into ubuntu and windows works. If it still doesn't, there are other diagnostic tools to run. This is the simplest solution to start with. :)

---

### Post by alem189 on 2010-06-05
> **darkod said:**
> Uhhh... you have two Linux partitions. 

Yes, one is my main partition, and one is /home.

> Did you install with manual partitioning? If you did, you should know which is your root partition, /dev/sda6 or /dev/sda7, just use that in the first command, the second is the same:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

or

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Restart and you should see the grub2 menu. Check if booting into ubuntu and windows works. If it still doesn't, there are other diagnostic tools to run. This is the simplest solution to start with. :)That worked. I see what I did wrong: I got a similar instruction from another post, which said to replace /dev/sda with the respective sda, but they were referring to something else. I replaced sudo grub-install '--root-directory=/mnt/ /dev/sda' with 'sudo grub-install --root-directory=/mnt/ /dev/sda6', and got a bunch of warnings (EMBEDDING NOT SUPPORTED, THIS IS A BAD IDEA!, etc.) I had to use a --force option, do you know if this did any unapparent damage to my filesystem?

---

### Post by darkod on 2010-06-05
If you used the --force option it installed grub2 to the partition /dev/sda6 too. But luckily grub2 can boot ubuntu OK even with another grub2 installed onto the ubuntu partition, so you won't even notice it.

Next time you are doing a clean install and formatting /dev/sda6 I think it will get wiped.

So everything is OK now?

---

### Post by alem189 on 2010-06-05
Yes, the problem is fixed and Ubuntu is workng fine! :)

---

