---
title: "Deleting Feisty Fawn and Installing Gutsy Gibbon"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by gamingx2005 on 2008-01-11
Hello everyone,
         It's a long time since I've been here. I haven't been able to access Ubuntu for weeks. I don't know why, but my keyboard doesn't work during startup. I had installed Ubuntu Feisty Fawn along with Windows XP, but then my brother also installed Fedora 7 too. I am completely helpless. Can I remove the Ubuntu Feisty Fawn completely and then install Gutsy without affecting anything in Fedora and Windows XP?

---

### Post by wjp.reg on 2008-01-11
You can take note of which partition feisty is installed on and run gutsy install and choose to have it overwrite that same partition..

---

### Post by gamingx2005 on 2008-01-11
> **wjp.reg said:**
> You can take note of which partition feisty is installed on and run gutsy install and choose to have it overwrite that same partition..

I don't have any clue as to what partition it is installed on. Can I find out from Windows XP? It's the only OS I am able to access now.

---

### Post by daisyfoofpoof on 2008-01-11
look up partlogic, its a free partition software... you have to have an iso burn software though.

---

### Post by wjp.reg on 2008-01-11
You can boot from a live cd and run```
 sudo fdisk -l
``` from a terminal.

Here's the output for my dual-boot system:

> 
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8095    65015055    7  HPFS/NTFS
/dev/sda2           11517       12161     5180962+  12  Compaq diagnostics
/dev/sda3   *        8096        8107       96390   83  Linux
/dev/sda4            8108       11516    27382792+   f  W95 Ext'd (LBA)
/dev/sda5           10128       11516    11157111    b  W95 FAT32
/dev/sda6            8108        8999     7164927   83  Linux
/dev/sda7            9000        9936     7526421   83  Linux
/dev/sda8            9937       10127     1534176   82  Linux swap / Solaris

Partition table entries are not in disk order


You will have at least 2 linux partitions if you have ubuntu and fedora installed.

---

