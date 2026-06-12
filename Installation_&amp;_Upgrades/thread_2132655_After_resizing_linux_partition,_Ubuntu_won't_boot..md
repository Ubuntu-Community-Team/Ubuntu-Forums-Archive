---
title: "After resizing linux partition, Ubuntu won't boot."
date: 2013-04-05
forum: Installation &amp; Upgrades
---

### Post by paulxx on 2013-04-05
Acer Aspire 5733
i3-370M
60GB ram
640GB HDD
Windows 7

About a year ago I downloaded Ubuntu live cd 12.04LTS and have been running a dual-boot.
At the time I created a partition 100GB for Linux Ubuntu.

I'm almost exclusively Ubuntu now and yesterday my computer started telling me that I only have <1gb space left for Ubuntu.
After checking on this forum on how to increase the size of my Linux partition, someone, somewhere advised doing it from W7 as "linux tools don't work too well altering Windows partitions".
So from Windows I downloaded a free tool called "Mini tools Partition Wizard". It was very easy to use and I added 100GB of unallocated space to my Linux partition.

Now Ubuntu won't load. 
I'd be very grateful for any help.
Thanks in advance.

---

### Post by darkod on 2013-04-05
If that 100GB partition was a linux partition, it's the other way around. They are right that you should resize ntfs partitions with windows tools but linux partitions are NOT ntfs. On the other hand, you can only install on ntfs wubi inside windows, which is not a proper ubuntu.

If it was ext4 partition it might have been corrupted during the resize. On the other hand, it might only need grub2 reinstall since resizing can move the grub2 core.img. Since you wanted to resize the linux partition, didn't it sound strange to you that "linux tools don't work well on windows partition"? If you are resizing linux partition and not windows, that is not relevant.

First boot into ubuntu live mode with the ubuntu cd, open terminal and post the output of:
sudo parted -l (small L)

Then we will know more about your partitions.

---

### Post by bcbc on 2013-04-05
If it's Wubi and you resized the NTFS partition... this might have changed the UUID. Which will stop Wubi booting. Easy enough to fix. From grub prompt:
```
search -s -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $root
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

After booting drop to terminal (Ctrl+Alt+T) and run:
```
sudo update-grub
```

Then do a Wubi resize or migrate:
[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)
[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by conradin on 2013-04-08
> **paulxx said:**
>  "linux tools don't work too well altering Windows partitions".

You got some bad information from somewhere. 

show us:
```

sudo fdisk -l


```

Does Win7 still boot? if you go into msconfig, do you have lines for bootions for linux?
is this a wubi install?

---

### Post by paulxx on 2013-04-10
Thanks everyone for all your help, it's ok now. 

I'm going to be a lot more careful in future until I know what I'm doing. 

paul.

---

### Post by Slim Odds on 2013-04-10
> **paulxx said:**
> Thanks everyone for all your help, it's ok now. 

I'm going to be a lot more careful in future until I know what I'm doing. 

paul.
It's OK now as in you fixed it?

Tell the class so that others may learn....

---

