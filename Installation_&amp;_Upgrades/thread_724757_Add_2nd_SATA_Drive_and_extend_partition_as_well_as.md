---
title: "Add 2nd SATA Drive and extend partition as well as RAID"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by routerman on 2008-03-14
I want to add a second 500 gig SATA drive and extend the partition of the existing to make it 1000 gig. What commands do I need to use to accomplish this? I assume I can extend the partition so it looks like 1 big drive. Right now I have 2 500 gig drives in place and am adding 2 more to make 2 1000 gig setups and the second group will be RAID. First I need to get the 1000 gig configuration setup if anyone can help. My current df shows the drive I want to extend into the second as /dev/md0 and it's mounted as /pictures....Thanks

---

### Post by thinkdez on 2008-03-17
Welcome to the world of LVM's and RAID.  I am going to make a couple of assumptions here.  
- You have an existing disk [500GB] with data on it.
- The existing 500GB disk is formatted as ext3 or similar file system.
- Your RAID array only consists of one disk currently. I am assuming you did this because you mention that you want to add a 'Second' 500GB drive.

Steps
1. unmount /dev/md0 ****VERY IMPORTANT**** Otherwise you can lose data.
2. To do this you need to create a partition table on the new 500GB drive which we will refer to /dev/sdc using fdisk
3. Then run the following command to add the partition to the array: ```
mdadm --add /dev/md0 /dev/sdc1
```

4. Then run the following command to grow the array to use the new disk:```
mdadm --grow /dev/md0 --raid-devices=2
```

5. Then resize the filesystem using: ```
resize2fs /dev/md0
```
6. At this point you can remount /dev/md0 and the disk space should consume the new disk.

I personally use LVM's to expand my disk as I need more space.  I like the fact that I am not limited to the same size disk to create the partition.  Its helpful when you have a bunch of disks around with different sizes.  

This takes some time so be patient.

Personally if you have important data on /Pictures [which it looks like you do] I would create a new array with two disks Create the partition and mount it to an alternate directory then copy the files from /Pictures and use the 500GB disk with the 4th disk to create your second array.  This way you don't lose any pictures in the event of a failure while extending the array.

Hope this helps.  And remember to backup your data first.

---

### Post by routerman on 2008-03-17
When I initially set the raid up with 2 500 gig SATA drives for the pictures volume. The OS is on a separate IDE drive. I did a "mdadm --create /dev/md0 --chunk=64 --level=raid1 --raid-devices=2 /dev/sda1 /dev/dsb1 --auto=md".  So what I really need to do is add 2 more 500 gig drives making the volume 1000 gig with the raid being 1000 gig as well.

---

