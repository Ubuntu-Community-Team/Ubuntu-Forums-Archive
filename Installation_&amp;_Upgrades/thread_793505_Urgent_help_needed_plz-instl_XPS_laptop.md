---
title: "Urgent help needed plz-instl XPS laptop"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by R0Y_G_B1V on 2008-05-13
I'm trying to install Ubuntu on 10GB of what the Ubuntu partitioner supposedly calls "free space", I select that partition, hit "new partition", make it mount point "/", and make it the size so I have 256MB left over. So it's about 10,480MB, then, the 256MB comes up after that as unusable space, what gives? Here's the list of all my partitions....this is on a Dell XPS 1330 with a 64GB SSD and the recovery disk has been formatted which is what the 10GB free space is. 

Device         Type   Mount Point    Size       Used
/dev/sda
   /dev/sda1   fat16  /media/sda1      90MB       33MB
   free space                        10,738MB
   /dev/sda2   ntfs   /media/sda2    50,508MB   14,700MB
   /dev/sda5   fat32  /media/sda5     2683MB      749MB

---

### Post by Partyboi2 on 2008-05-14
You can only have 4 primary partitions, so what happens if you make the 10,738MB as a extended partition then create the partitions you want?

---

### Post by housam on 2008-05-14
> **R0Y_G_B1V said:**
> I'm trying to install Ubuntu on 10GB of what the Ubuntu partitioner supposedly calls "free space", I select that partition, hit "new partition", make it mount point "/", and make it the size so I have 256MB left over. So it's about 10,480MB, then, the 256MB comes up after that as unusable space, what gives? Here's the list of all my partitions....this is on a Dell XPS 1330 with a 64GB SSD and the recovery disk has been formatted which is what the 10GB free space is. 

Device         Type   Mount Point    Size       Used
/dev/sda
   /dev/sda1   fat16  /media/sda1      90MB       33MB
   free space                        10,738MB
   /dev/sda2   ntfs   /media/sda2    50,508MB   14,700MB
   /dev/sda5   fat32  /media/sda5     2683MB      749MB

Boot from the live CD and type in a terminal :
```
sudo fdisk -l
```
where -l is a small L and post the results to give us a clear vision about your partitions.

---

