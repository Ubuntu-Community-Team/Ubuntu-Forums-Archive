---
title: "Partition Problem"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by Raan03 on 2008-03-24
Hi all

I have ubuntu installed on a partition (ext3), the swap (ext3) and a windows partition (ntfs). Recently I wanted to reinstall ubuntu (a "major" blowup: I deleted gnome and it wouldn't reinstall). The problem is now that I have a "corrupt" partition table (or so?)

I have runned gpart, (sudo gpart /dev/sda) on the Ubuntu Live CD and it detects my "lost" partitions very well. I gave the command to write the MBR again (sudo gpart -W /dev/sda /dev/sda), but he gives me a problem and a warning. The problem is that he couldn't reread the disk as it might be busy and the warning is that I have to reboot the system...

Now the problem is that he still doesn't show up the lost partitions when I want to "reinstall" Ubuntu through the installer, BUT I can access the NTFS partition through the Places/Computer...

Gpart says...
```

ubuntu@ubuntu:~$ sudo gparted 
======================
libparted : 1.7.1
automounting disabled
======================
Invalid partition table on /dev/sda -- wrong signature 0.

```

and the installer only shows up sda (only the hard disk, without the partitions)...

---

### Post by housam on 2008-03-24
boot from the live CD and type in the terminal 
```
sudo fdisk -l 
```
Where -l is a small L and post the results

---

### Post by Pumalite on 2008-03-24
Use TestDisk to fix your partition table: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Backup everything.

---

