---
title: "Help with Installing to Partition"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by seandgibbonsy on 2010-01-21
I need to install Ubuntu to a pre-designated partition.  Here's what I have so far:
Partition #1 - 195 GB  (Windows 7)
Partition #2 - 85 GB  (Special)
Partition #3 - 19 GB (Blank ext4 partition)

How would I install ubuntu 9.10 to the ext4 partition.  I would prefer to not use a swap partition (use a swap file instead).  I also do not need to install the bootloader, as I will be using another of my own.

Could someone please give me step-by-step directions.  Sorry, I'm a little new to all this.

I got to the point of the installer where I can set my partitions (manual install), i click the ext4 partition, then "Forward".  I keep getting an error that the "root filesystem is not defined".  I tried setting the ext4 partition to mount to /home, but that was no help.

---

### Post by dstew on 2010-01-22
You need to set the mount point of the ext4 partition to '/' (without the single quotes). That is the "name" of the root partition. When you get to the last step (I think it is step 7) click the Advanced tab and tell the installer not to install a boot loader. However, whatever boot loader you plan to use must be able to load the Linux kernel directly. If you plan to "chainload" your Linux system, you need to install a boot loader in the Linux *partition* to give the chainloader something to execute.

---

