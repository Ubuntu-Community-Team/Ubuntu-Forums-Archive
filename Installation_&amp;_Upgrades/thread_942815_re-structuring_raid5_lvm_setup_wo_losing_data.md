---
title: "re-structuring raid5 lvm setup w/o losing data"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by markley268 on 2008-10-09
i've currently got a 3x1TB raid 5 array setup and then lvm2 on top of that.  I'd like to carve off some space on the 3 drives for the 'system' partitions that are currently on a stand-alone 400G drive.  Basically i've seen this type of suggested setup....


sd[abcd]1     /boot
sd[abcd]2     /
sd[abcd]3     swap
sd[abcd]5-13  LVM2 (/usr,/home,/var,/tmp,/opt)


where the the /boot, /, and swap partitions are setup as on a raid1 across let's say two of the 3 drives w/ the third being a spare for the raid1, and then the others being on the raid5 volume.

So, the question is, how do i safely reduce the lvm volumes and mdadm array to allow for the creation of the raid1 on the drives that are currently fully taken up by the raid5 w/o losing any data and w/o having to offload all the current data that's on the raid5 to someplace else (ie: not having to start over from scratch w/ the 3x1TB drives)

I've looked around and unfortunately not been able to find anything that addresses this particular situation, so please forgive if this has been addresses somewhere already.

I'm assuming that this will involve the basic following steps:

1. reducing the lvm volumes to ensure there's enough 'room' to reduce the mdadm array
2. reducing the mdadm array to free up enough space for the raid1
3. creating the raid1
4. creating new lvm volumes for /boot from the raid1, and the other mount points from the (now reduced) raid5
5. moving data to the new lvm volumes from the current drive
6. adjusting /etc/fstab to mount the new volumes
7. ???

---

