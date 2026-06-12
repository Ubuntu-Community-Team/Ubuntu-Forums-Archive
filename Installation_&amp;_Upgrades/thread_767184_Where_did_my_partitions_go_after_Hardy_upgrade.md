---
title: "Where did my partitions go after Hardy upgrade?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by skubisnack on 2008-04-25
I first tried a fresh install of Hardy (Xubuntu), keeping my home partition from 7.10.  After that installation, my Home partition was recognized, but all of my other partitions were missing.

I reinstalled 7.10, then upgraded using the same separate home partition.  /home is still working, and I was excited to see my partitions in /media.  I just opened one of the folders and it shows nothing there.  A right click gives no option to mount or unmount, and properties lists 0 items and 0 size. 

I've searched several times for similar issues, but have been unable to find any.  I'm hoping this is something simple.  All of my media files and work documents are on other partitions.  I'm not sure where to start with this. I'll have to go back to 7.10 if I can't get this figured out.  

Thanks in advance for your help!

---

### Post by Pumalite on 2008-04-25
Post:
sudo fdisk -l

---

### Post by skubisnack on 2008-04-25
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007ecf9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1        9729    78148161    f  W95 Ext'd (LBA)
/dev/sda5            8487        8959     3799372+   7  HPFS/NTFS
/dev/sda6            8960        9729     6184993+   7  HPFS/NTFS
/dev/sda7             925        3566    21221833+  83  Linux
/dev/sda8            5818        8486    21438711   83  Linux
/dev/sda9   *           1         793     6369678   83  Linux
/dev/sda10            794         924     1052226   82  Linux swap / Solaris
/dev/sda11           3567        4349     6289416   83  Linux
/dev/sda12           4350        5817    11791678+  83  Linux

Partition table entries are not in disk order
```

---

### Post by Pumalite on 2008-04-25
What about sda1?

---

### Post by skubisnack on 2008-04-25
SDA1 used to be my windows partition.  It is now unformatted space.

---

### Post by Pumalite on 2008-04-25
You can mount your partitions with this formula:
sudo mkdir /media/sda7
sudo mount -t ext3 /dev/sda7 /media/sda7

---

