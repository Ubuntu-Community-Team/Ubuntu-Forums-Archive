---
title: "Partition resizing"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by gabng on 2006-06-13
Currently I have WinXP and ubuntu installed on my laptop, and I've been playing around with ubuntu recently that the space of the / partition is almost used up.  Here is my partition configuration laid out in order:

hda1 - winxp c: (NTFS 7Gb)
hda3 - / (ext3 4.76Gb)
hda2 - logical (extended 6.87Gb)
hda4 - swap (swap 251Mb)
hda5 - winxp d: (NTFS 6.63Gb)

hda2 contains hda4 and hda5. Since hda5 has 4Gb free space, I am thinking of freeing 2Gb from it and resize hda3 to take up that free space.  I also want to resize the swap partition to be larger.  This means moving back the logical partition, along with swap and d:, and expand the size of hda3 at its end.

I'd like to know if this is doable before I start resizing my windows d drive.  Or is there anything I'm missing?  Thanks!

---

### Post by wyohermit on 2006-06-13
If your list is truly in disk order, then no this is not possible. If you would open a terminal and enter "sudo fdisk -l" with out the quotes and then post the output here we could be sure.

Ken

---

### Post by gabng on 2006-06-14
Here is the output
```
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         914     7341673+   7  HPFS/NTFS
/dev/hda2            1536        2432     7205152+   f  W95 Ext'd (LBA)
/dev/hda3             915        1535     4988182+  83  Linux
/dev/hda5            1568        2432     6948081    7  HPFS/NTFS
/dev/hda6            1536        1567      256977   82  Linux swap / Solaris

Partition table entries are not in disk order
```

Other than hda4 actually being hda6, the disk order in my post should be right.  So it's not possible to resize it as in my original post?

---

### Post by wyohermit on 2006-06-14
I'm sorry to say that your original plan will not work.  However, I think you could accomplish the same result by shrinking hda5 and creating another ext3 partition on the end either as logical hda6 within the extended partition or as primary hda4.  Then copy either your /home or /usr directory there and then edit you fstab file so that directory would have its own mount point.  Hope this helps.

Ken

---

### Post by gabng on 2006-06-14
That's too bad then, thanks for letting me know.  However, could you tell me why this isn't possible, is moving the swap partition the problem?  Since moving the NTFS shouldn't be a problem to my knowledge.  And how about resizing the swap partition?  Is that doable?

---

### Post by wyohermit on 2006-06-14
[QUOTE=gabng]That's too bad then, thanks for letting me know.  However, could you tell me why this isn't possible, is moving the swap partition the problem?  Since moving the NTFS shouldn't be a problem to my knowledge.  And how about resizing the swap partition?  Is that doable?[/QUOTE]

Actually the problem is in being able to move the begining point of hda2/hda6.  You can take away from or add to the end of a partition but not the begining as far as I know.

Ken

---

### Post by gabng on 2006-06-14
[QUOTE=wyohermit]You can take away from or add to the end of a partition but not the begining as far as I know.
[/QUOTE]

Is that a restriction of linux, as in moving the beginning of a partition (even if it's just a swap partition) would cause problems for the OS?  Or is that just a limitation of the partition editor application in linux?

Because what I'm thinking is to use partition magic in WinXP to move the partitions, hoping it would not break ubuntu.

---

