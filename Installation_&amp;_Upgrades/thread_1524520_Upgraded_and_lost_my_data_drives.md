---
title: "Upgraded and lost my data drives"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by tim_m on 2010-07-05
-I upgraded my Ubuntu install and the system boots except it ignores my two data drives. I get a prompt to continue waiting, skip or manually recover. If I skip I boot into Ubuntu. The fstab entries for the data drives are:
/dev/hdb1       /itunes         ext3 noatime 0 2
/dev/md0        /musicorig      ext3 defaults 1 2

I booted with a knoppix cd and both drives are found and contain data. What steps can I take to remount these drives and recover the data?

Thanks.

---

### Post by oldfred on 2010-07-05
they changed to UUIDs to avoid some of these type issues as UUIDs do not change (unless you are deleting or greatly changing partitions).

Has drive order changed? Also all drives now are sda, sdb, not hd.

to see your drives:

sudo fdisk -l
sudo blkid


Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

This is my entry for my data partition:
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2

---

### Post by darkod on 2010-07-05
/dev/hdb1

That is strange, from what version to what did you upgrade? I thought ubuntu started to use sdX instead of hdX even for IDE disks long ago. So, it should be resolved by using /dev/sdb1 probably. You might also think about using UUID, Lucid started using UUID in fstab but again, you never said to which version you upgraded.

/dev/md0

That's a software raid device. I guess you have to rebuild the array, you should know more about that than me, since you are using raid. My knowledge of raid is limited. Online search about rebuilding software raid array might also help. And you might need to add some packages like mdadm to the current install before being able to recreate the array.

---

### Post by tim_m on 2010-07-05
I changed fstab to use sdb1, sdc1 and sdd1 and I am able to access and see the contents! Not sure how to convert these to UUIDs and that will take more research. Also not sure how to recreate my raid array but I suspect it needs to be recreated. At least I have my data back even if things are not quite right.

---

### Post by darkod on 2010-07-05
If you had a software raid1 (mirror), the good side of software raid is that actually you can look at the data separately without even making a new array. At least if you need to save it of course.

At the moment it will not work as raid1 because there is no array.

sudo blkid

will give you the UUIDs of all partitions. If you want to use that approach, you simply replace in fstab /dev/sdb1 with UUID=xxx and that should be it. All the other parameters remain the same.

---

