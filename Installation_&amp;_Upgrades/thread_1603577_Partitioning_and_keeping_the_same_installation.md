---
title: "Partitioning and keeping the same installation?"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by darkenvy6 on 2010-10-22
Okay so I remember back in the day using gparted and windows and partitioning my disk. I was told I could keep the same install only to discover windows became unbootable. (not bootdisk related, the os was corrupted)

How can I keep my install of Ubuntu on my 1TB HDD while allotting 400GB for another OS? (more linuxs :P)

---

### Post by drs305 on 2010-10-22
I wrote this guide for *expanding* the system partition, but the tips section would equally apply to shrinking / :
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

If you are merely changing the size your Ubuntu system shouldn't experience any problems as the UUIDs shouldn't change. The only issue would be if you placed another partition in front of the existing one, in which case the boot order might change. As long as Grub2 is configured with UUIDs, even that shouldn't be a problem.

You could mount your real Ubuntu partition on /mnt and  "grub-install --root-directory=/mnt /dev/sda" (no partition designation) from the LiveCD before rebooting. If you are really worried about the boot, when you are finished with the repartitioning you could chroot into your real Ubuntu system from the Live CD and update grub before rebooting. Neither of these should be necessary, and can be accomplished afterward if you *do* have any problems.

---

### Post by darkenvy6 on 2010-10-22
I'm not so much worried about grub failing to boot my existing ubuntu installation but having gparted erase my Ubuntu partition. Every time I shrunk a partition in the past (when using windows (haha) ) it took a chunk out of my installation.

Like as if my data is scattered across my disk and only a portion of the data is removed for the new partition. or is ubuntu's diskspace more linear? I don't know if defragging has anything to do with this.

---

### Post by drs305 on 2010-10-22
> **darkenvy6 said:**
> I'm not so much worried about grub failing to boot my existing ubuntu installation but having gparted erase my Ubuntu partition. Every time I shrunk a partition in the past (when using windows (haha) ) it took a chunk out of my installation.

Like as if my data is scattered across my disk and only a portion of the data is removed for the new partition. or is ubuntu's diskspace more linear? I don't know if defragging has anything to do with this.


Of course you should always have a backup of your important data, but GParted is an excellent tool. I've never had data loss and have used it at least 50 times. About the only problem people have with it on a regular basis is figuring out how to enable the options, which usually are disabled because not all the partitions are unmounted. Even with the LiveCD, you have to unmount the swap partition (select it, then Partition, swapoff).

---

### Post by darkenvy6 on 2010-10-23
hmmm I would just make a backup but I have no where to put it for a day :S. Ill have to figure that part out....

---

### Post by darkenvy6 on 2010-10-24
Update:

I just finished using Gparted, something I just noticed this time was  that I was able to see how much of the partition I used. I was also able  to shrink it down to exacly this amount. Honestly I don't know what  happened in the past but I think NTFS is just an inferior filesystem :P.

No problems at all but it did take 4 hours to do (and move the partition to the begining of the disk). Thanks drs305!

---

### Post by efflandt on 2010-10-24
Shrinking a FAT32 or NTFS partition does not take much time at all if you defragged it down to the beginning of the partition.  But moving the beginning of a partition takes time (and should not be interrupted) because I think all files are moved down to the same relative position they were in the partition.

For Vista or Win7 it is best to use its own tools to shrink its system partition.  For WinXP system partition, it is best to temporarily disable virtual memory, and reboot for that to take effect, before resizing with gparted.  Other than virtual memory limiting how far I could shrink an NTFS partition (using ntfsresize at that time), I have not had any problems using gparted to shrink partitions.

---

### Post by darkenvy6 on 2010-10-24
Im not a windows person anymore anyways. Main reason why is that I was tired of restarting the OS every 6 months. No matter how clean I kept the OS it just degrades on me quickly. 

Wine+VMware baby! :D Thats my EXE handlers!

Erm... how do I change the prefix to solved?

---

### Post by drs305 on 2010-10-24
> **darkenvy6 said:**
> 
Erm... how do I change the prefix to solved?

Via the 'Thread Tools' link to the top right of the first post.  :-)

---

