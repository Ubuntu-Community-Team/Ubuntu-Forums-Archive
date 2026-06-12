---
title: "Ubuntu 11.04 not detecting Windows 7 partition (GPT issue)"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by orion2001 on 2011-04-30
Hi folks,

  After putting this off forever, I've finally decided to delete my old XP OS and install Ubuntu on it as a dualboot option along with my existing Windows 7 x64 install. However, I'm having a common issue in that both Gparted and fdisk do not detect the partitions of my main boot disk and shows the entire disk as unallocated.

I've read a number of similar threads with some great responses from many of the folks here on this forum. I've put together all the info I could think would be relevant.

1) I ran fdisk -l. Here is the output (This is from booting from the live CD). Sorry for the long logfile. I have a number of disks/partitions attached. **The relevant disk of interest is /dev/sdb/**

```
ubuntu@ubuntu:~$ sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gdisk
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0abc0abb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30402   244195328    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfff023c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        3826       15536    94067036    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf6c7069

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60555   486400000    7  HPFS/NTFS
/dev/sdd2           60555      121601   490358784    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           6       48163+  de  Dell Utility
/dev/sdc2   *           7       18966   152296200    7  HPFS/NTFS
/dev/sdc3           18967       19452     3903795   db  CP/M / CTOS / ...

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a2b75aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdg: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe61424b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       30402   244198552+   7  HPFS/NTFS

Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8454b38e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdj: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8454b38f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdl: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8454b38c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1               1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdk: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8454b38d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1               1      243202  1953512448    7  HPFS/NTFS


```2) When I ran GParted, it shows /dev/sdb/ as unallocated, and has the following Error/Warning message:

> Warning!

/dev/sdb contains GPT signatures, indicating that it has  a GPT table. However, it does not have a valid fake msdos partition  table, as it should. Perhaps it was corrupted -- possibly by a program  that does not understand GPT partition tables. Or perhaps you deleted  the GPT table, and are now using an msdos paritions table.

Invalid argument during seek for read on /dev/sdb3) And this is a picture of the disk unders Windows 7 Disk Management. "Disk 3" is my main boot drive with Windows 7 on C:\. The unallocated partition before it was where the old XP install was. I want to ideally install Ubuntu on that partition. Also, I should mention that "Disk 0" is a Drive from my old DELL PC that has a windows XP installation on it along with the boot info. I left it in there in case I wanted to swap it back into my old PC. However, it seems to confuse Ubuntu during the install as it detects only that XP installation but cannot read/detect the current Windows 7 install.

[[IMG]http://img151.imageshack.us/img151/4301/diskmanagement.th.jpg[/IMG]]("http://img151.imageshack.us/i/diskmanagement.jpg/")


Before I do anything, I'd like to get some advice from the more experienced folk here. I've seen a number of posts by srs5694 that are perhaps relevant (like this one): [http://ubuntuforums.org/showpost.php?p=9464066&postcount=3](http://ubuntuforums.org/showpost.php?p=9464066&postcount=3)

But I'd like to know if that is appropriate for my situation. Thanks for stopping by and I'd appreciate any help.

Cheers

---

### Post by srs5694 on 2011-04-30
Thanks for asking advice before proceeding! (There's another active thread from somebody who I think ran into problems by following advice intended for others -- it was probably appropriate for the others, but not for him.)

The post you referenced should fix your problem; however, there's now an easier way: You can run my [FixParts](http://www.rodsbooks.com/fixparts/) program, which will detect and delete (after you've given the OK) your old GPT data. Install the program, type "sudo fixparts /dev/sdb", answer "Y" to the question about deleting the GPT data, and then type "q" to quit without making further changes.

---

### Post by orion2001 on 2011-04-30
Hi srs,

 Thanks so much for all your support on the forums! I did indeed see the other thread you mentioned which is why I decided to take the cautious route and ask for advice before proceeding ahead :).

I'll give FixParts a whirl and report back. Just a quick question...can I install it within the Ubuntu LiveCD session and use it? If so, can I install it from commandline from a repo (sorry, completely a linux noob) or should I download it off the web page and then follow the instructions on your site?

Thanks a ton!

---

### Post by srs5694 on 2011-04-30
Yes, you can install FixParts in the Ubuntu live CD. There's also a Windows version, so you could use that if it's more convenient. AFAIK, FixParts hasn't yet been added to Ubuntu's repositories, so if you use the Linux version you'll need to download the .deb file for your architecture (i386 or amd64) and double-click it to install it.

---

### Post by orion2001 on 2011-04-30
Thanks and it seems to have done the trick! :) . For some reason, the latest version (0.7.1) would not install and gave a dependency error regarding libicu42 (I don't quite follow why that is the case as 11.04 seems to come with libicu44 which would anyway be a higher version?). I ended up installing the 0.7.0 version which worked. Did as you said and the partitions are showing correctly. 

I'm just going to reboot into Windows first to make sure it is still booting okay. If all goes well, I should be on my way to installing Ubuntu! Thanks a ton, and I'll be sure to come back to update this thread and the thread status.

Thanks!

---

### Post by orion2001 on 2011-05-01
Thanks a ton! This worked out perfectly. No issues with my Windows 7 install, didn't even need to resort to using a repair disk to fix anything. I'm marking this as SOLVED. Thanks again for all your help!

---

