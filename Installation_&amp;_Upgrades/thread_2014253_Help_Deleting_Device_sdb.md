---
title: "Help Deleting Device sdb"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by Gotit on 2012-07-01
Hi, I need some help deleting a device off a hard drive.  I have 1 physical hard drive and it is divided into 2 devices, sda and sdb.  Both devices are 250 GB.  I am trying to reformat the entire drive and end up with all usable space (500 GB) in 1 device, sda.  However, I can not find how to delete sdb and use that space in sda.  

I was able to delete all the information in both devices, but I don't find how to dump device sdb. fdisk seems to want me to pick either sda or sdb to format.  Do I need to do something with device labels?

Thanks.

---

### Post by sudodus on 2012-07-01
Normally each hard drive is a device

/dev/sda (hdd0)
/dev/sdb (hdd1)
... 

and it is divided into partitions

/dev/sda1
/dev/sda2
/dev/sda3
...

What kind of hard drive are you using, and what is its history?

---

### Post by darkod on 2012-07-01
It sounds to me like you were using a raid0 array made up of two disks of 250GB. That would have a total of 500GB.

sda and sdb are separate physical disks, you can't "delete sdb and have 500GB in sda" because it looks like you have two disks of 250GB each.

You can't make one disk of 500GB from that.

When you ran fdisk, did it say that both sda and sdb are 250GB disks? You can check all disks with:
```
sudo fdisk -l
```

---

### Post by Gotit on 2012-07-02
Thanks for the quick response!

OK, duh, I have 2 drives not 1 :oops:

I was reading the Device Information in GParted and the two drives are the same exact model, which is why I was thinking it was the same drive.

Guess I should have looked before firing off this thread.  Sorry.

---

