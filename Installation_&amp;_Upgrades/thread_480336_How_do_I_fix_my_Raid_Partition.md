---
title: "How do I fix my Raid Partition?"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by lixjgrib on 2007-06-21
Newbie here. Hope someone can help.

I have an Alienware m9700 with XP preinstalled. I have dual nvidia video cards, and duel 80GB drives setup as a raid mirror. Everything went great with my install (after doing some workarounds for the video), but then the system would not boot. I really do not want to rebuild my XP system again (lots of software, data, etc.).

I can get in the with install CD and see all my data. The problem is that I did a standard install, which did not recognize my Raid. So, it resized the partition on one disk. I dont get any errors from dmraid testdisk or anything. I can still see both disks (after running dmraid) and browse my data. How can I get my two disks to appear as one again?! I just want to get the XP running on Raid again, as it was, and then I can do a proper linux install for the raid.

I'm looking at various tools and forums (FakeRaidHowto, FakeRaidEdgy, dmraid, etc.), but I cannot seem to find my exact problem. It seems that I simply need to repair the MBR on the disk that was not repartitioned, and get the other disk to rebuild from that.  But how? Any ideas? I'm thinking there must be a simple way.

Thanks.

---

### Post by lixjgrib on 2007-06-21
Here's a dmraid -r and fdisk -l from my system:

ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_bjdfidhe", mirror, ok, 156301486 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_bjdfidhe", mirror, ok, 156301486 sectors, data@ 0
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7176    57641188+   7  HPFS/NTFS
/dev/sdb2   *        7177        9617    19607332+  83  Linux
/dev/sdb3            9618        9729      899640    5  Extended
/dev/sdb5            9618        9729      899608+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

