---
title: "swapless installation"
date: 2004-11-30
forum: Installation &amp; Upgrades
---

### Post by zyang on 2004-11-30
i installed ubuntu without a swap partition, i assume thats going to slow me down somewhat. so i want to get the swap partition installed, but i also fear that i might break ubuntu or windows which are all intalled on the same disk.

can someone please teach me how to install a swap partition safely?

thank you.

zee

---

### Post by jdong on 2004-11-30
Do you have the extra space, or will you have to resize an existing partition?

If you're resizing, what filesystem(s) are you using?

---

### Post by zyang on 2004-11-30
i got a 40g harddrive split into two partitions. partition c is 15gigs and its reserved for windows (ntfs). partition d is 25 gigs and reserved for ubuntu (ext3). i would prefer to resize the linux partition because i cant affort to break windows now that all my exams are coming up.

---

### Post by diebels on 2004-11-30
RTFresize2fsM :) It's well explained there. The rules are that you can move the end boundary of the filesystem and partition, the start is locked, and the filesystem size must never grow out of the partition size.

So in your case you:

1. sfdisk -l, print out
2. reboot with the install cd and let it run to the partition configuration loads, [alt] + [f2]
3. (resize2fs)shrink the ext3 partition a couple of hundred Mb
4. (fdisk)delete the partition from the partition table
5. (fdisk)make a new partition that is at least as big as the new shrinked size and starts at the exact same sector as the old one
6. (fdisk)make new partition for swap
7. sfdisk -l, check with the printout
8. (mkswap)make swap on the partition on the end of the disk
9. add swap mount point to /etc/fstab

---

### Post by az on 2004-12-01
Boot from your install cd

Make your way to the partitionner.

Select your linux partition.

Go on size.

Hit enter

Make is smaller. (like by 500 megs

(you can put like 14.5 Gig) 

Make your linux partition your root, but tell it to not overwite (do not format and keep existing data)

Make the free space into swap

Make it go.

Stop the installation after it is partitioned

Read fstab manpage and add your swap partition to your /etc/fstab

Good luck!

---

### Post by zyang on 2004-12-01
thank you, guys

---

