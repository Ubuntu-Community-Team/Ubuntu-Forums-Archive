---
title: "LVM Root on Software Raid5 - Boot drops to buisybox"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by Cryptography on 2008-11-20
[SIZE="4"]**Very Short:**[/SIZE]
My system drops to (ramfs) buisybox on load because it fails to mount the root partition which is on an LVM on a Sata Software Raid 5 (not fakeraid). 

[SIZE="4"]** Extended Info **[/SIZE]
Upon investigation in ramfs I found that the /dev/md0 does not show up. Upon scrolling up I cannot find any instances of errors nor any mention of mdadm attempting to initialize the raid.

once the raid is assembled
```

mdadm --assemble /dev/md0 /dev/sda2 /dev/sdb2 /dev/sdc2

```
I can then do ctrl-d and the system boots properly. The raid is clean. 

I have looked at many threads, howtos, and fun information; however I have not been able to fix this issue. I could probably put the above command in the ramfs init script somewhere but that seems like a very bastardized way to fix this. 
[SIZE="4"]
**System Details:**[/SIZE]
     Asus A8N-SLI
     Nvidia Nforce 4 SATA Controller (the nvidia branded ones not the silicon image or others, not that I think this matters in this case...)

     3 HDD - All SATA - 2 Partitions on each drive. Both Primary. Partition 1 is 2gb, partition 2 is the rest of the disk / linux raid autodetect.

     On 1 disk partition 1 is ext3 /boot... on the other 2 that space makes up the system swap.

     LVM is setup on /dev/md0

     attached is the /etc/mdadm/mdadm.conf file

---

### Post by Cryptography on 2008-11-20
Well after working on this problem for the better part of 24 hours I have found my solution and am banging my head against a wall because it was so simple.

Problem... mdadm.conf was incorrect. Particularly the line starting with ARRAY. It should have been
```
ARRAY /dev/md0 level=raid5 num-devices=3 devices=/dev/sda2,/dev/sdb2,/dev/sdc2
```

Note the devices= ....

This was discovered by doing an mdadm -Es which parsed the config file then searching for the error ARRAY line /dev/md0 has no identity information. 

once that change was made I created a new init ramfs using the command ..
```
update-initramfs -k 2.6.27-7-generic -c -t
```

make sure to update that command for your kernel version.

Wee it works.

---

