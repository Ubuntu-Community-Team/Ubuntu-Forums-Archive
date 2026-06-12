---
title: "Safely shrinking Windows &amp; Expanding Ubuntu partitions"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by mlevin2 on 2013-02-11
I currently have a disk that is partitioned as follows:

[IMG]http://i.imgur.com/SfoqeH6.png[/IMG]

[FONT="Courier New"]Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x590e401d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6375    51097600   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3            6375       38130   255077256    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           38130       38914     6291457    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           38130       38914     6291456   82  Linux swap / Solaris[/FONT]

I'd like to shrink the Windows partition (it has a lot of free space) and expand the Ubuntu partition (it's very short on space).

What's the safest way to do this so as to not mess up my boot loader? I understand that I'll be shrinking /dev/sda3, then moving where that partition starts to the right, freeing up some space after /dev/sda2, which I'll then expand.

My question is, will moving the start position of /dev/sda3 cause me to not be able to boot into Windows anymore? Is there anything I need to do to move these things around safely so I don't end up with an unbootable machine?

Thanks

---

### Post by tgalati4 on 2013-02-11
Back up your personal data.  On the Windows side, empty trash, remove old programs through "Add/Remove Programs", use the disk cleaning tool to delete temporary files, then perform a defragmentation.  Once that is done, log back into Ubuntu and use gparted and just drag the partition slider.  Hit apply.

Back up your personal data.

How could you short change your linux partition?  That's like not feeding your pet.

---

### Post by ahallubuntu on 2013-02-12
~

---

