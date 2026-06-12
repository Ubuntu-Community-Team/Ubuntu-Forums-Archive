---
title: "delete mdadm volume info from disk"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by GrimRe on 2008-07-21
Hi,

I am desperately trying to delete mdadm volume information from my disks. They were in a RAID1 but I am trying to swap them out to be a RAID0. I thought I deleted the array properly but whenever I go to install ubuntu server the 2 sata disks are still always used as md0 and I can't delete it!

I have tried everything I can think of, I just need a tool that will remove all traces of the disks ever being used as a mdadm volume device.

Thanks!

---

### Post by GrimRe on 2008-07-22
anyone :confused:

---

### Post by CooLGeeK on 2008-07-22
By default, mdadm automatically scans disk partitions if they contain md superblocks and then continues to assemble raid arrays based on the info gathered.
Configuration file:  /etc/mdadm/mdadm.conf

Try using the --zero-superblock option of mdadm for each linux raid partition you are using OR raid partitions which are members of the raid array you are trying to delete.
For example if you have a linux raid partition /dev/sdc1, use:
```
sudo mdadm --zero-superblock /dev/sdc1
```

You can check all your disk partitions of the type Linux raid by using the following command:
> sudo fdisk -l | grep raid

Those listed in the first column are your Linux raid partitions.

---

