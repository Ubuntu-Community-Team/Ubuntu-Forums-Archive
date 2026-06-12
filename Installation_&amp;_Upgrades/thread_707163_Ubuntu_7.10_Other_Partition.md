---
title: "Ubuntu 7.10 Other Partition"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by Adeel on 2008-02-25
i installed Ubuntu 7.10 64-bit on Hard drive (200 GB) its working well but didn't show other free space of (180 GB) just showing (20 GB) in which Ubuntu installed and also showing the Hard drive(250 GB) in which Win XP PRO installed.
How can i use 180 GB of free space of Hard Drive in which Ubuntu installed.

---

### Post by housam on 2008-02-25
Type in a terminal 
```
sudo fdisk -l 
```
where -l is a small L . and post the result

---

### Post by Adeel on 2008-02-25
The result is below

"Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  82  Linux swap / Solaris
/dev/sda2   *         123        2554    19535040   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40b040af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdb2            3825       30400   213471720    f  W95 Ext'd (LBA)
/dev/sdb5            3825        7648    30716248+   7  HPFS/NTFS
/dev/sdb6            7649       11472    30716248+   7  HPFS/NTFS
/dev/sdb7           11473       15296    30716248+   7  HPFS/NTFS
/dev/sdb8           15297       19120    30716248+   7  HPFS/NTFS
/dev/sdb9           19121       22944    30716248+   7  HPFS/NTFS
/dev/sdb10          22945       26768    30716248+   7  HPFS/NTFS
/dev/sdb11          26769       30400    29174008+   7  HPFS/NTFS

---

### Post by housam on 2008-02-25
I t seems that you have an unallocated space on your HDD .can you boot from the live cd and open Gparted tool to see the situation of your partitions and posted using the snap shot tool.

---

### Post by Adeel on 2008-02-25
Try to execute the Gparted tool but reply is this "Root privileges are required for running GParted (Since GParted can be a weapon of mass destruction only root may run it.)"

---

### Post by housam on 2008-02-25
You can download and burn the newer version of Gparted cd from [[COLOR="Red"]_here_[/COLOR]]("http://gparted-livecd.tuxfamily.org/"). then boot from it and use it .

---

### Post by Adeel on 2008-02-25
Opened the Partition Editor and attaching the Screen Shot What Next/home/ubuntu/Desktop/Screenshot.png

---

### Post by housam on 2008-02-25
resend the attachement using the clips beside the smilly face in the message tools.

---

### Post by Adeel on 2008-02-25
Here it is

---

### Post by Adeel on 2008-02-25
Made Partitions see the attachment is it done?

---

### Post by housam on 2008-02-25
Congratulations . I see that you solve the problem. ( name the new partitions and have fun.

---

### Post by Adeel on 2008-02-25
Thanks for your Support

---

