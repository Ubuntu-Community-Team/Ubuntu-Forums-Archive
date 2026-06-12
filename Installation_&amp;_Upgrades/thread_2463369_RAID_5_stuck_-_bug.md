---
title: "RAID 5 stuck - bug ?"
date: 2021-06-09
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-06-09
Just created RAID 5 - it has no files. 
After an hour I did check the status 

sudo cat /proc/mdstat

**it will finish in 2452.5min **

md0 : active raid5 sda8[3] sda7[1] sda6[0] 
      51324928 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_] 
      [===>.................]  recovery = 17.7% (4552160/25662464) finish=2452.5min speed=143K/sec

---

### Post by MAFoElffen on 2021-06-09
You are missing information needed from your post. Specifically, the size of the disks in your Array. 

Based on your post:

It depends on the size of the Array and the disks. A RAID 5 with Three 1TB disks (2TB of Array Storage) will take about 10-12 hours to assemble and format.

I've seen a 3 disk (8TB) Array (16TB storage) take over 4 days. Based on not knowing the size of the members of the Array, 40 hours is still realistic.

Do you have a requirement for RAID? If not, there is always LVM2 or ZFS... Either can do parity and are dynamic while hot (mirroring, online changes, sizing, adding/removing/moving disks, snapshots, etc.) 

Just something to think about.

EDIT: if I did the guestimated math right on : "51324928 blocks super 1.2 level 5, 512" >>>  25.6TB Storage?

---

### Post by anneranch on 2021-06-09
[QUOTE=MAFoElffen;14042586]
Read the post again - after an hour or so it was 17 % complete assembling empty  disks. 
After reboot it is nowhere to be found. 
I am not sure how  knowledge of how long it took your example to assemble helps me, 
BTW these are "tiny" 20 GB empty test partitions. 
Back to drawing board and "thanks for watching..."

---

### Post by MAFoElffen on 2021-06-09
Only 20GB??? Yes, the "size" , in relation is the pertinent information difference...

Also if you had noted that, the important error is that now you cannot find the Array(?)

Now you are calling up past nightmares... LOL 

What happens is that sometimes when it is origianly created, the mdadm device will have a name like /dev/md0, /dev/md1, etc. and on reboot... the array will still be there in /dev, but be reassigned a name such as /dev/md1XX or such...

If that is what happened, just use the UUID to refer to it in your fstab. I do that anyways, just in case it is reassigned for any reason, because the UUID doesn't change. 

But... if you look back in your cli command history, look at your creation line, look at the members you added. Usually when that happens, it may be because the members might have been added as disks, instead of partitions. (I had done that "following" a tutorial years ago. I admit.) But then again, sometimes it still gets the name reassigned on boot. I just go with it now. (It's stranger name reassignments on hardware RAID...)

 A simple "fdisk -l" will list the disk devices.

---

