---
title: "Read Errors when Cloning Hard Drive"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by dbqp on 2008-06-04
Well, I had a T30 IBM Notebook with a 40GB drive containing 3 partitions (one is swap). I purchased a 250GB drive (clean, unformatted, no partitions) and have tried cloning the three partitions (after setting a disk label on the new drive) to the new 250GB drive.

I have tried GParted and Clonezilla. Both give me read errors after getting about 2.5GB copied (stops at a sector). The 40GB drive was in god condition without any issues. The old drive has been put into an external case so I am copying from /dev/sda to /dev/hda and their respective partitions.

Would anyone know what is causing this I/O error?

---

### Post by hal8000 on 2008-06-04
If youre cloning using DD or cpio then every sector will be cloned, whether it contains data or not. You have a sector thats damaged and unreadable.

You may get lucky and that sector or area of the disk may not contain data,
so boot with the live hardy cd.

Use fdisk to create 3 new partitions on the 250G HD.  Then use cp -aR to copy data from each partition, this way you are only copying data not empty sectors.

Suppose you create a new / called sda1 and a new home called sda2
on your 250G drive.

Type these commands
mkdir tmp1 tmp2 tmp3 tmp4
mount /dev/sda1 tmp1
Mount your old drive on tmp2
mount /dev/sdb1 tmp2 (change partitions to your drives requirements)
cd tmp1
whilst your in tmp1
cp -aR tmp2 .
dont forgot to include the period .
Do the same with your home partition.
For swap dont copy just create a new /swap
e.g.  mkswap /dev/sda3
swapon /dev/hda3

Once completed it is advisable to check /etc/fstab just to make sure
the mount points reflect the new partitions.

---

### Post by dbqp on 2008-06-04
> Suppose you create a new / called sda1 and a new home called sda2
on your 250G drive.

Type these commands
mkdir tmp1 tmp2 tmp3 tmp4
mount /dev/sda1 tmp1
Mount your old drive on tmp2
mount /dev/sdb1 tmp2 (change partitions to your drives requirements)
cd tmp1
whilst your in tmp1
cp -aR tmp2 .
dont forgot to include the period .
Do the same with your home partition.
For swap dont copy just create a new /swap
e.g. mkswap /dev/sda3
swapon /dev/hda3

Once completed it is advisable to check /etc/fstab just to make sure
the mount points reflect the new partitions.

Thank you, I'll try this at home tonight and reply with the results. Since the new drive is installed in my notebook it is considered /dev/hda1, 2, and 3 - thank you though!

---

### Post by dbqp on 2008-06-06
I tried everything I could think of, but it appears this hard drive was ready to fail at anytime and I am now grateful I replaced the drive before anything could happen.

I was unable to clone, but I reloaded the notebook and am painstakingly going through the old drive and transferring mail files, vm ware files, etc...

Thanks.

---

