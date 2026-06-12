---
title: "ubuntu 10.04 instalation error"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by ciscoboy on 2011-09-27
Hello,

I tried to install ubuntu 10.04 using a USB based ubuntu. In the instalation, I specified to format the hard drive and reinstall the operating system from scratch. After the instalation, I got a screen with the following message:

**[        0,681603]  Kernel panic-not syncing: VFS : unable to mount root fs on unknown - bloc (0,0)**


Any idea of what it means, and/or how to change it?


Thanks!

Ciscoboy


[B]
 [/B]

---

### Post by Hakunka-Matata on 2011-09-27
If you can boot into an ubuntu liveCD, then post the output of these commands please:
```
sudo fdisk -l && sudo sfdisk -luS
```

---

### Post by ciscoboy on 2011-09-27
unfortunately, I'm running the live USB on a laptop that doesn't have a CD drive. Can I set up that command on a live USB?

---

### Post by MAFoElffen on 2011-09-27
> **ciscoboy said:**
> unfortunately, I'm running the live USB on a laptop that doesn't have a CD drive. Can I set up that command on a live USB?
Yes... It's the same image / used the same way.

---

### Post by Hakunka-Matata on 2011-09-27
> **ciscoboy said:**
> unfortunately, I'm running the live USB on a laptop that doesn't have a CD drive. Can I set up that command on a live USB?
Yes you can run it, you must open a Shell/Terminal window, then put that command in.  Once it produces output, highlight, copy, and paste it into a reply for us to see.

---

### Post by ciscoboy on 2011-09-28
> If you can boot into an ubuntu liveCD, then post the output of these commands please:Okay, here are the results, as requested. I hope that this is what you meant, and I appologise if it isn't;


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc11c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18801   151012352   83  Linux
/dev/sda2           18801       19458     5275649    5  Extended
/dev/sda5           18801       19458     5275648   82  Linux swap / Solaris

Disk /dev/sdb: 16.5 GB, 16475226112 bytes
255 heads, 44 sectors/track, 2867 cylinders
Units = cylinders of 11220 * 512 = 5744640 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c069ba3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2868    16088428    c  W95 FAT32 (LBA)

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 302026751  302024704  83  Linux
/dev/sda2     302028798 312580095   10551298   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     302028800 312580095   10551296  82  Linux swap / Solaris

Disk /dev/sdb: 15712 cylinders, 64 heads, 32 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/255/44 (instead of 15712/64/32).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *      1320  32178175   32176856   c  W95 FAT32 (LBA)
        start: (c,h,s) expected (0,30,1) found (0,20,61)
        end: (c,h,s) expected (1023,254,44) found (978,254,44)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty




Thanks for your support!

Ciscoboy

---

### Post by ciscoboy on 2012-06-21
For anyone who had, has or will have this problem, I wanted to let know that I got an external CD drive and installed ubuntu on my computer, solving the problem I had.

---

