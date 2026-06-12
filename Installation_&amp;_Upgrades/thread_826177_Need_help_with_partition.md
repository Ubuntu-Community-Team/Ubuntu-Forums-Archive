---
title: "Need help with partition"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by rkinne01 on 2008-06-11
I am newbie to linux, but I've been learning a lot from the forums but have problem i need help with.  

I bought this computer from a friend with 400 Gig hard drive. I noticed that the drive has 3 partitions as seen here:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8f6105d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         538     4321453+   b  W95 FAT32
/dev/sda2   *         539       24446   192041010    7  HPFS/NTFS
/dev/sda3           24447       48641   194346337+   5  Extended

What I'd like to do is have the extended partition be absorbed back in the NTFS Vista partition then run kubuntu from there without having to use a different partition (if i like Linux at some point I may indeed install on its own partition). The Fat 32 partition is the recovery partition for XP, but i do have back up disks so it is expendable if need be.

Any ideas? Please keep in mind I am a new Linux user, talk down to me if needed (lol)!  Thanks in Advance.

---

### Post by overdrank on 2008-06-11
> **rkinne01 said:**
> I am newbie to linux, but I've been learning a lot from the forums but have problem i need help with.  

I bought this computer from a friend with 400 Gig hard drive. I noticed that the drive has 3 partitions as seen here:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8f6105d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         538     4321453+   b  W95 FAT32
/dev/sda2   *         539       24446   192041010    7  HPFS/NTFS
/dev/sda3           24447       48641   194346337+   5  Extended

What I'd like to do is have the extended partition be absorbed back in the NTFS Vista partition then run kubuntu from there without having to use a different partition (if i like Linux at some point I may indeed install on its own partition). The Fat 32 partition is the recovery partition for XP, but i do have back up disks so it is expendable if need be.

Any ideas? Please keep in mind I am a new Linux user, talk down to me if needed (lol)!  Thanks in Advance.
Hi and welcome, you should be about to delete the extended partition with the live cd and then resize the vista partition also with the partition editor located under system, administration. If you are speaking of install Kubuntu from with in vista I am assuming you mean Wubi

---

