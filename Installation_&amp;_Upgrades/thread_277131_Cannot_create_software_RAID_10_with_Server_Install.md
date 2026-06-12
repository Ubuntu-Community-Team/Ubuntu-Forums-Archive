---
title: "Cannot create software RAID 10 with Server Install CD"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by ScottEllis on 2006-10-14
I am using the latest Server CD, and I want to setup a software RAID 10 array. I can create the two RAID 0 arrays, but I cannot then set those arrays to be of type raid members (cannot remember the exact term) so that I can then create the RAID 1 array.
According to the mdadm docs, RAID 10 is possible, and is done by this nested RAID on RAID approach. (There is a good howto around for setting this up for use in a MythTV system)

Possible solutions:
[LIST]
[*]Is it possible to use another installation tool to get the drive arrangement setup to the point where all this is setup, then stop and run the Ubuntu setup?
[*]I am going to put root onto a USB drive, and just have the /var and /tmp on the RAID drives, so should I just leave it until I have the system up and running, and then create the array using mdadm? Are there any issues with "moving" /var and /tmp while the system is running?
[/LIST]

To answer possible questions - why not use RAID 5 - mainly because RAID 10 is faster, and disks are not really expensive any more. The focus is speed and redundancy.

Thanks for any help.

Scott

---

