---
title: "(Computer illiterate) Installing ubuntu on an existing partition"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by Sava2004 on 2010-03-23
I'm trying to install Ubuntu on my currently windowsXP machine and I need help. I have an existing partition ( called D: on my windows, with a bit more that 43GB of free space), But when I run the Ubuntu installer it only finds 7MB of free space, and it can't see the existing partition. Am i doing something wrong?

Pictures are greatly appreciated.

Edit : I want to keep the windows partition intact

---

### Post by pastalavista on 2010-03-23
In the installer, when the partitioner starts, check "manually select partitions" and click forward

---

### Post by anoop999 on 2010-03-23
The 7MB is the free unformatted space in your hard drive - outside any of the partitions.

In order to create space you need to shrink your Windows partition.

This is how I did it:

In Windows:
1. Back up your files (in case something goes wrong!) Delete any unnecessary files and programs to maximise space.
2. Defragment your hard drive.
3. Find out how you want to split your drive between Windows and Linux. You should not allow the partition to be more than 75% full.  For example, if you have a 60GB Windows partition, and you have used 20MB, you can maybe shrink it to 30GB and create 30GB of space for Ubuntu.
4. Shut down

Now boot into the Live CD
1. Run GParted (the partition editor)
You will be able to see all your partitions on your hard drive(s) (Windows partitions, recovery partitions etc.)
2. Shrink your chosen partition to create empty space.
3. Create a Linux extended partition in the empty space
4. Create a swap partition (recommended size = your RAM), a ext4 home partition and a ext4 root partition (recommended 10GB) inside the extended partition.
5. Install Ubuntu into your root partition and designate your new home partition as the mount point /home

Let me know if you have any queries.

---

### Post by theozzlives on 2010-03-23
> **Sava2004 said:**
> I'm trying to install Ubuntu on my currently windowsXP machine and I need help. I have an existing partition ( called D: on my windows, with a bit more that 43GB of free space), But when I run the Ubuntu installer it only finds 7MB of free space, and it can't see the existing partition. Am i doing something wrong?

Pictures are greatly appreciated.

Windows almost always, if not always, leaves unpartitioned space. I bet that's the 7 MB of unused space. If it's empty, you'll wanna manually edit your partitions and delete that 43 GB one (it'll be called sda2). Then create your / and swap partitions.

---

### Post by anoop999 on 2010-03-23
GParted shows you the contents of your hard disc very clearly. I found it easier to manually partition the disk using GParted beforehand rather than during the Ubuntu installation.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Sava2004 on 2010-03-23
> **pastalavista said:**
> In the installer, when the partitioner starts, check "manually select partitions" and click forward

Did what Pastalavista said and found my partition, but am getting an error, " No root file system is defined"

Edit : I still want to keep the windows partition intact.

---

