---
title: "Copied partition, now sda1 sees himself as sda2"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by mrwebmaster on 2012-09-18
Hi, my HDD has 4 partitions:
sda1 (80GB)
sda2 (15GB)
sda3 - linux swap
sda4 

Using Gparted, I removed the contents of sda1 and copied sda2 to sda1, because I was running linux on sda2 and needed more free space. 

After that, I updated grub and booted to sda1. But It seems that I cannot mount sda2 from sda1. If I run "df -h", I get:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        59G   13G   43G  24% /
udev            994M  4.0K  994M   1% /dev
tmpfs           401M  892K  400M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1002M  276K 1002M   1% /run/shm
/dev/sda4       386G   88G  278G  25% /media/311502bd-0a3d-4037-a0ca-2728dae85b2
```
I think I'm on sda1 because now I have 43GB free space, but it looks like sda1 seems himself as sda2?

How can I mount sda2 from sda1?

Thanks

---

### Post by darkod on 2012-09-18
Are you sure sda1 exists now at all? If you copied over it, it might have replaced it with sda2.

I never use Gparted for operations like that. Besides, you did it wrong by trying to copy a partition. That doesn't mean to copy the content, it means to copy the partition, as it says. You copy content the same way as you copy files and folders.

You should have shrinked sda1 and then expand sda2. Not to use any copy option.

See which partitions you have now:
```
sudo fdisk -l
sudo parted -l
```

---

### Post by oldfred on 2012-09-18
In addition post this. Often a full partition copy copies UUIDs. Post in code tags to maintain formatting:

sudo blkid -c /dev/null -o list

---

