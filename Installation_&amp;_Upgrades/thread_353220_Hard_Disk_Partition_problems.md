---
title: "Hard Disk Partition problems"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by xbo on 2007-02-04
This is my first venture in Linux and i have chosen Kubuntu, however i am struggling to get the thing installed.

I have 1 x 80GB hard drive and i have partitioned it as so :

32 gig Fat32 partition , 
30 gig Fat32 partition,
10 gig Fat32 partition 
2 gig swap partition.

So far i have  Installed windows XP on the 32 gig partition.

I intend to install kubuntu linux on the 30 gig partition and use the 2 gig swap as swap space, then i would  Install the grub boot loader on to either the 30 or the 32 gig partition and configure as appropriate to enable dual booting between windows and linux.

I have d/l the KUbuntu ISO, it boots up from the CD and when i attempt install Kubuntu to hda/2 (hda/1 has WinXP on it) i get the following error message 

"FAT and NTFS filesystems may not be used on filesystems used by the system"....its odd 'cos all my partitions are FAT32

Can anyone please advise, or point me to a noobs guide ? 

Thanks

thanks

---

### Post by taurus on 2007-02-04
The error said that you cannot install Ubuntu (or Kubuntu in this case) on a ntfs or fat32 filesystem.  Therefore, you need to tell the installer to format /dev/hda2 to ext3.

---

### Post by xbo on 2007-02-04
> **taurus said:**
> The error said that you cannot install Ubuntu (or Kubuntu in this case) on a ntfs or fat32 filesystem.  Therefore, you need to tell the installer to format /dev/hda2 to ext3.

I see...thanks. I thought i could install it to FAT32 ? Well thats what i was told anyway

---

### Post by taurus on 2007-02-04
Not sure who told you that but you can share files with Windows using fat32 filesystem.

---

### Post by xbo on 2007-02-04
> **taurus said:**
> Not sure who told you that but you can share files with Windows using fat32 filesystem.

that is exactly what i want to do......i

---

### Post by taurus on 2007-02-04
Then, install Ubuntu on the second partition, 30GB, and format it to ext3.  Mount the third partition, 10GB as vfat, somewhere like /media/hda3 and use that to share files between Windows and Ubuntu.

---

