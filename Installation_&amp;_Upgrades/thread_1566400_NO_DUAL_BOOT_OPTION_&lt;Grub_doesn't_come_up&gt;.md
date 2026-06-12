---
title: "NO DUAL BOOT OPTION &lt;Grub doesn't come up&gt;"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by aryanwicked on 2010-09-02
Hi dudes
 
I've just installed Lucid Lynx on my laptop alongside m$ win 7 . It is installed correctly but when I restart Ubuntu and trying to get into M$ win I noticed that there is **no Dual Boot Option available** . and it *boots* **straight away** to Ubuntu and **Grub menu doesn't come up** at all.

This is what I've done to install Ubuntu

I had just one partition on my windows disk ( C: ) 
so I resized the partition and created a free space (unallocated) on my hard disk (30 GB), and I proceeded Ubuntu installation and I selected "**the largest continuous free space**" in Ubuntu setup.

I think I've done everything correctly, does anybody know how to deal with this issue?

I Also tried this terminal command without lcuk
```

sudo os-prober

sudo update-grub

```

thx

---

### Post by Sef on 2010-09-02
First let's check how you partitioned your hard disk.

Applications > Accessories > Terminal

then copy and paste this command:

```
sudo fdisk -l
```

Copy and paste the results here.

Thank you.

---

### Post by aryanwicked on 2010-09-02
thnx for your kind reply :D

here it is

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe90405a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       26460   212436526    7  HPFS/NTFS
/dev/sda3           26461       30402    31657985    5  Extended
/dev/sda5           26461       30234    30308352   83  Linux
/dev/sda6           30234       30402     1348608   82  Linux swap / Solaris


```

---

### Post by oldfred on 2010-09-02
You actually have two windows partitions. sda1 is a 100mb boot/recovery partition that windows does not normally show you. Your main install then should be in sda2.

If sudo update-grub does not see windows then there may be some issue.

To see the entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by lege101 on 2010-09-05
hi i have kinda the same option i think. i just have ubuntu running and i want windows too but i cant. here is the same stuff you told the other person to get. i have the windows 7 re-installation cd if that helps me at all.

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29652   238179658+  83  Linux
/dev/sda2           29653       30401     6016342+   5  Extended
/dev/sda5           29653       30401     6016311   82  Linux swap / Solaris

---

### Post by oldfred on 2010-09-05
lege101
You have a large / (root) linux partition. You should be able to shrink it and create a sda3 primary NTFS for windows. If you directly install windows into a NTFS with the boot flag set on then it will install into one partition.

You may want to also create another partition eithe sda4 or using space next to the sda2 the extended expand the extended and create another logical inside the extended as NTFS for data. Then you can easily share data between windows & Ubuntu. Ubuntu root can be 20GB if you are planning on putting most data elsewhere. I use 20-25GB for root and actually only use about 6GB but put data into either shared for use with windows or another ext3 data partition to for use with my other linux installs.

---

