---
title: "Moving/resizing ext3 and NTFS partitions"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by chrisccoulson on 2006-06-22
I currently have 2 * 250GB hard disks in a RAID 0. They are set up like this:

/dev/mapper/nvidia_dgcadeeg1 - 50GB - NTFS (Windows system)
/dev/mapper/nvidia_dgcadeeg2 - 385.72GB - Extended, containing:
- /dev/mapper/nvidia_dgcadeeg5 - 40GB - NTFS (Windows Data)
- /dev/mapper/nvidia_dgcadeeg7 - 40GB - ext3 (/home)
- /dev/mapper/nvidia_dgcadeeg8 - 304.71GB - ext3 (Contains videos/music)
- /dev/mapper/nvidia_dgcadeeg6 - 1GB - swap
/dev/mapper/nvidia_dgcadeeg3 - 30GB (Dapper root file system)
/dev/mapper/nvidia_dgcadeeg4 - 47.07MB (/boot)

Basically, I'm thinking of getting 2 more 250GB hard drives set up as RAID 1 for storage of all my videos and media. This will free up the 304.71GB partition on my RAID 0. What I would like to do is reduce this existing partition, so I can allocate more space for both Windows, the Dapper root file system and /home.

I haven't decided what sort of size I would be looking to change them to yet, but I want plenty of space for games etc. I know that having the root file system near the end of the disk is a bit of a pain as I've read that Linux file systems are fixed at the start and can only be altered at the end of the file system. So, what I'm asking is, what would be the best way to get more space for for these file systems without having to do a total re-install and start again?

What I'm thinking is that I will probably have to back up the partitions on my new drives first (should I choose to get them), and then delete the existing partitions and recreate them.

If I were to go down this route, what are the best tools to use, and how do I use them? Are there any tips you can give me? Or am I being a bit over ambitious?

Any help is appreciated.

Cheers

---

### Post by aysiu on 2006-06-22
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) may help.

---

