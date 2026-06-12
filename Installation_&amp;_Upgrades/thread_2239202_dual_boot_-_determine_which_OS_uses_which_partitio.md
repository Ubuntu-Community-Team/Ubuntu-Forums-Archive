---
title: "dual boot - determine which OS uses which partitions"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by JimLS on 2014-08-12
Have a dual boot system.  11.10 and 12.04 with 5 partitions.  Had trouble with the 12.04 install and never did much with it but it runs ok now.  I have forgotten the partition layout and want to replace 12.04 with 14.04.  How do I determine the layout for the two existing OS so I can reuse the 12.04 partitions?  Need to keep 11.10 until I have the new system up and transfer over some things.

---

### Post by lucianloonstra on 2014-08-12
Hello JimLS,

Can't you get that information with gparted?

---

### Post by ajgreeny on 2014-08-12
Start with commands ```
sudo fdisk -l
df -h
``` which will tell us all your partitions for both OSs then the partitions for the OS you are running.

If you boot to the other OS and run the **df -h** command again you will see the different partitions for that OS listed.

---

### Post by oldfred on 2014-08-12
If you want lots of detail run the report from this:

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by JimLS on 2014-08-12
Here is the output, first from 11.10:
 sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030cf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1041654599   520826276   83  Linux
/dev/sda2      1994545150  2930276351   467865601    5  Extended
/dev/sda3      1041654600  1994543476   476444438+  83  Linux
/dev/sda5      2926086144  2930276351     2095104   82  Linux swap / Solaris
/dev/sda6      1994545152  2926086143   465770496   83  Linux

Partition table entries are not in disk order

myth@jimmyth:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             489G  461G  3.6G 100% /
udev                 1000M  4.0K 1000M   1% /dev
tmpfs                 403M  848K  402M   1% /run
none                  5.0M  8.0K  5.0M   1% /run/lock
none                 1007M  120K 1007M   1% /run/shm
myth@jimmyth:~$

 and this from Ubuntu 12.04:

myth@jimmyth:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       438G  4.3G  411G   2% /
udev           1001M  4.0K 1001M   1% /dev
tmpfs           202M  888K  201M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1009M   76K 1009M   1% /run/shm

---

### Post by oldfred on 2014-08-12
Your sda1 is 11.10, but it also shows 100% used of 489GB.

Your sda6 is 12.04 and shows 2% used of 438GB.

Often better with large drive to have a smaller / (root) of 20 or 25GB and use rest of space you want for /home or data partition(s).

What is in the Linux partition sda3?

---

### Post by JimLS on 2014-08-13
sda1 is full because it is mythtv and deletes recordings as needed.  Need to figure out how to use another partition as data for new install.

just ran gparted.  It reports sda3 as ubuntu 12.4.  Will post a screen shot soon...

---

### Post by Mark Phelps on 2014-08-13
Also be aware that if you select the "Replace" option in the Ubuntu installer, it is likely to erase the ENTIRE DRIVE!  This would remove all the existing partitions on the drive.

To prevent this, you need to boot using the install media and reformat the partition you want to replace and then use the "Something Else" option to install to that partition.

---

### Post by JimLS on 2014-08-13
Here is the screen shot of gparted.

[IMG]http://i1183.photobucket.com/albums/x472/JimS27/MythPartitions/DSCN0351a.jpg[/IMG]

---

### Post by oldfred on 2014-08-13
Ubuntu has a screenshot tool to create those. And then you attach those with the paperclip icon in the advanced editor.

You sda3 just has a label of 12_4, which you must have created. Do you also have it as a boot option in grub menu? Or is it just a non-working version?

---

### Post by JimLS on 2014-08-13
I was running System Rescue CD with gparted, not Ubuntu.  From what I could find getting screen shots on that system is difficult.

I  booted 11.10 and mounted sda3.  Only one empty folder named lost+found.  I don't remember if I named it or it was automatically named.  I think I was planning to have a large partition for tv recording storage.

---

### Post by oldfred on 2014-08-13
Lost & found is a default.

Best to only use 12.04 or 14.04 as those are LTS, so they will not expire for a long time.

If wanting to multi-boot, better to have a smaller / (root) partition of 25GB, and add a large data partition that can be shared with other installs. There can be issues of sharing if not Debian based, but those can also be worked out with some planning during install. The issue is UID and GID. First user in Debian is 1000, but not always that with other distributions.

---

