---
title: "partitioning"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by loewrida on 2010-05-13
Hi I got Lucid Lynx and i want to partition the drive into two harddrives when i install, like with windows i would have my harddrive made into C and D and i would have windows on the C and all my movies and stuff on D. I saw some things about making the rest of your space to store files in the /home files but i when i log into ubuntu after installing it shows the /home folder inside the disk. I dont know if it makes sense but, i was wondering if u can have it the way windows does it so it looks like two harddives and which options to select when i'm paraitioning. i really want to change over to ubuntu i just wanna work this out first cause i dont know so much yet haha. thanks

---

### Post by darkod on 2010-05-13
The parts on the same hdd are called partitions. You are allowed to have 3 primary and 1 extended which can have up to 16 logical partitions inside.

But if you make 4 primary then the limit will be 4 and you can't create more.

Home is just a folder because you need to use Manual Partitioning, make a separate partition and mount it as /home during the install.

Since you want also separate partition for movies and stuff, you might consider separate /data partition. I personally haven't used it (just separate /home) but read around about it for more details.

So, the idea would be like (just a suggestion):

First sit down and make a plan how big you want each partition. For root usually 10GB is plenty if you have separate /home because then all personal data is saved there. After you made your plan, boot the installer and select Manual partitioning.

Create one primary partition with the size you want for root, select ext4 filesystem, mount point /.

Then create a logical partition with the size for /home, select ext4, mount point /home.
Create another logical with size for /data (if you decided to have one), mount point /data.
Create logical for swap, there is no mount point for that, just filesystem type swap area.

I suggested using logical partitions because in the above situation you would have one primary (root), and one extended holding 3 logical partitions (/home, /data and swap).

So you have used up 2 out of possible 4 (1 primary + 1 extended). You can still add primary partitions later if needed. If you create all 4 partitions from above as primary, that's the limit.

This is only one general suggestion. Work around depending what you want to achieve.

PS. Also a separate /home will allow you to make clean install of a future version over the current root, but keeping all your data and settings in /home (because only the root partition will be formatted and /home is totally different partition). That is one of the main benefits of separate /home.

---

### Post by srs5694 on 2010-05-13
For the most part darkod has given good advice. I'd just like to make a few additional points....

> **darkod said:**
> The parts on the same hdd are called partitions. You are allowed to have 3 primary and 1 extended which can have up to 16 logical partitions inside.

Actually, the theoretical limit on the number of logical partitions is one less than half the number of sectors on the hard disk (about 2 billion on a 2 TiB disk -- but why anybody would need 2 billion 512-byte partitions is beyond me!). I'm not sure if there are more restrictive limits in the Linux kernel, but if there are, they're higher than 16. Here's evidence from a test disk, one which I've created 3 primary, 1 extended, and 18 logical partitions:

```

$ **ls /dev/sdc***
/dev/sdc    /dev/sdc12  /dev/sdc16  /dev/sdc2   /dev/sdc3  /dev/sdc7
/dev/sdc1   /dev/sdc13  /dev/sdc17  /dev/sdc20  /dev/sdc4  /dev/sdc8
/dev/sdc10  /dev/sdc14  /dev/sdc18  /dev/sdc21  /dev/sdc5  /dev/sdc9
/dev/sdc11  /dev/sdc15  /dev/sdc19  /dev/sdc22  /dev/sdc6
$ **sudo fdisk -l /dev/sdc**

Disk /dev/sdc: 16.2 GB, 16166944768 bytes
64 heads, 32 sectors/track, 15418 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xd3119a0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         501      513008   83  Linux
/dev/sdc2             502        1002      513024   83  Linux
/dev/sdc3            1003        1503      513024   83  Linux
/dev/sdc4            1504       15418    14248960    5  Extended
/dev/sdc5            1504        2004      513008   83  Linux
/dev/sdc6            2005        2505      513008   83  Linux
/dev/sdc7            2506        3006      513008   83  Linux
/dev/sdc8            3007        3507      513008   83  Linux
/dev/sdc9            3508        4008      513008   83  Linux
/dev/sdc10           4009        4509      513008   83  Linux
/dev/sdc11           4510        5010      513008   83  Linux
/dev/sdc12           5011        5511      513008   83  Linux
/dev/sdc13           5512        5989      489456   83  Linux
/dev/sdc14           5990        6490      513008   83  Linux
/dev/sdc15           6491        6991      513008   83  Linux
/dev/sdc16           6992        7492      513008   83  Linux
/dev/sdc17           7493        7993      513008   83  Linux
/dev/sdc18           7994        8494      513008   83  Linux
/dev/sdc19           8495        8995      513008   83  Linux
/dev/sdc20           8996        9496      513008   83  Linux
/dev/sdc21           9497        9997      513008   83  Linux
/dev/sdc22           9998       10498      513008   83  Linux

```

> Since you want also separate partition for movies and stuff, you might consider separate /data partition. I personally haven't used it (just separate /home) but read around about it for more details.

If this is to be a Linux-only system, I'd just store the "movies and stuff" in /home, with /home being a separate partition. There are reasons to complicate matters by creating a separate partition for user data side from /home, but loewrida hasn't provided any. The most common is if this is to be a dual-boot system, in which case a shared-data partition for Linux and Windows (or OS X or FreeBSD or DOS or whatever) can be very helpful. Most often, the shared-data partition should use a native filesystem for the other OS (FAT, NTFS, HFS+, etc.), although ext2fs or ext3fs can sometimes be a good choice. The shared-data partition can be mounted in /home (even if it is itself a separate partition), in a user's subdirectory in /home (say, /home/loewrida), or elsewhere (say, /shared). The /home partition itself should use a Linux-native filesystem (ext3fs, ext4fs, XFS, JFS, ReiserFS, or [if you're adventurous] Btrfs).

> First sit down and make a plan how big you want each partition. For root usually 10GB is plenty if you have separate /home because then all personal data is saved there.

Appropriate sizes for root (/) range from about 5GB to 20GB for most modern desktop installations; however, it can go lower or higher in extreme cases. What's most appropriate depends on available disk space and how much software you want to install. (If you split off /usr, / can be significantly smaller.) I've got about 18GB in root (/) on one of my systems -- but it's packed with a lot of software and several kernel source trees.

> Create one primary partition with the size you want for root, select ext4 filesystem, mount point /.

Then create a logical partition with the size for /home, select ext4, mount point /home.

This is certainly fine; however, Linux doesn't *require* any primary partitions; it can install to either primary or logical partitions. This fact is most important if you're trying to dual-boot with a system that already has three primary partitions (as many computers ship from their manufacturers today).

---

