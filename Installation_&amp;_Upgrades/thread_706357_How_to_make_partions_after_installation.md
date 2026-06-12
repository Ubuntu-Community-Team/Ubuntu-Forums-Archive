---
title: "How to make partions after installation"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by smbtol on 2008-02-24
I want to allocate more space to the linux partition or to make another linux partition after I installed Ubuntu. I used Vista to get some unallocated space and now I want to use that space. I installed gparted but it does not want to do anything. The unallocated space cannot be made a new partition because I already have 4 primary partitions (3 primary partitions and one extended). Gparted does not want to move that space to the extended partition or to merge it with the ext3 partition.
What other program should I use?
I attached a picture with my issue.

---

### Post by logos34 on 2008-02-24
/ cannot be mounted, so you'll have to use Gparted on your ubuntu live cd (system>admin>parted).  

Resize the extended partition to the left into the unallocated space, then expand root to the left.  It takes a while.

---

### Post by justsomedude on 2008-02-24
1. You will not be able to resize your partition from within your install, because it cannot be done while the partition is mounted. Use the GParted Live CD instead.

2. Resizing and moving partitions is always a risk, so backup important data before doing that.

3. **Be careful**: If you expand your ext3 partition to the left, Grub will likely be unable to find a kernel to boot, so read the instruction how to fix Grub from a live CD first!!!

---

### Post by smbtol on 2008-02-24
Thank you guys. The problem was solved with the live cd. 
It took 21 min and 37 s to do the job :) .
For some reason the swap partition was locked, so I had to do a swapoff first.
My Ubuntu is working fine now. It seems that grub figured out how to boot it.
I think I have grub installed in the MBR (not sure though).

---

