---
title: "Can't boot into current setup and into live-usb"
date: 2009-11-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Joe_Bishop on 2009-11-15
So, I've upgraded to "lucid" by replacing karmic to lucid, then tried to boot into it, but failed. Then I tried to boot using my live usb (with 9.10), but failed too, the messages are the same as shown on attachment #2.

---

### Post by VMC on 2009-11-15
Here's one [discussion]("http://ubuntuforums.org/showthread.php?t=1282539") about recordfail=1, drs305 has possible solution.

---

### Post by Joe_Bishop on 2009-11-15
> **VMC said:**
> Here's one [discussion]("http://ubuntuforums.org/showthread.php?t=1282539") about recordfail=1, drs305 has possible solution.
No, it's another issue. My boot stops after the message from #2 while recordfail prevent booting at all. I wonder why my flash stops booting though.

---

### Post by Joe_Bishop on 2009-11-15
Hm, strange. I have the following situation:
Ext4 Partition + 60Gb of Windows NTFS partion on 750Gb drive
Ext4 Partition mounted as /home on 1Tb drive
Swap 3Gb partition + Ext4 30Gb partition mounted as / + 500Mb Ext4 partition mounted as /boot + Ext4 data partition which I've never use on another 1Tb drive.
I've realized the problem was in the partition table on the second 1Tb drive (with /). I could boot using usb flash after I removed all partitions on the second 1Tb drive.

---

### Post by ranch hand on 2009-11-16
Grasping at straws - have you checked the numbering of you drives?

Your listing calls for (hd2,6) and sdf6.

And, have you tried;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

to see what it would do?

It would be a good idea to post the results of this script;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

