---
title: "How to add an ext3 formatted hard drive"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by sfwasabi on 2005-07-25
Hello, I have a successful installation of Ubuntu Hoary 5.04. I am new to Linux, but technically saavy on Windows and Macs.

I have a second hard drive connected to the motherboard formatted as ext3. I wanted to mount it and use it for filesharing, but I do not know where to find it in File Browser.

It is showing up as "hdb" under:
cat /proc/partitions.

I tried:
sudo mount -t ext3 /dev/hdb /mnt 
and it told me that the drive was already mounted.

I suspected that I needed a folder name to mount it, and since I plan on it being a webserver file share/network file sharing driver, I tried to name it "wwwroot" by doing:
sudo echo "/dev/hdb /wwwroot ext3 defaults 0 0" >> /etc/fstab

and it told me that I was not allowed to do this.

What I would like to do is to be able to access the drive in File Browser and it would be easiest for me if the drive were called 'wwwroot'.

Thanks!

---

### Post by grim42 on 2005-07-25
What is the output of the following commands:
```

sudo mount

sudo cat /etc/fstab
```

---

### Post by wrtrdood on 2005-07-25
I think your problem is trying to use only hdb.  It should probably be /dev/hdb1.

The mount point is what it would be called so creating a directory at the root level with the name wwwroot and mounting it with: **sudo mount /dev/hdb1 /wwwroot** should work.

---

