---
title: "Changing a partition from NTFS to FAT32"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by thomashenrydavies on 2007-01-25
Hello all.

I have just installed Edgy on my new Dell laptop, alongside XP. There are 4 partitions on the disk - the XP boot partition, the Linux boot partition, the linux swap partition, and the rest of the disk is a shared data partition, in NTFS, that both OSs see.

I've been advised that I should change the shared partition to FAT32, as there is less chance of Ubuntu doing something untoward to it. First question: is this true?

If so, how should I go about changing this? My approach would be to use Partition Magic in XP to reformat the partition as FAT32. What would I then need to do in Ubuntu-land to make it mount this partition?

Thanks
Tom

---

### Post by taurus on 2007-01-25
Actually, you should change it to ext3 since XP can read ext2/ext3 with [http://www.fs-driver.org](http://www.fs-driver.org) now.

Install gparted in Ubuntu and use it to convert it to fat32 or ext3, whichever one you want to use.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```
It will be in System -> Administration.  And don't forget to unmount the drive first before you format it.

---

### Post by thomashenrydavies on 2007-01-25
> **taurus said:**
> Actually, you should change it to ext3 since XP can read ext2/ext3 with [http://www.fs-driver.org](http://www.fs-driver.org) now.

Install gparted in Ubuntu and use it to convert it to fat32 or ext3, whichever one you want to use.

Interesting about the ext2/3 driver for XP. Is there any real-life advantage in doing this over choosing FAT32?

---

### Post by taurus on 2007-01-25
FAT32 can't handle files over 4GB.  Besides, ext3 is better filesystem to use if you plan to save a lot of stuff to it in Linux.

---

### Post by kahping on 2007-01-25
FAT32 sucks. Another way would be to use [NTFS-3g]("https://wiki.ubuntu.com/ntfs-3g") to access your NTFS partitions, but considering it's beta you're more likely to get better stability from the ext2 installable filesystem drivers from the link taurus posted.

Edit:

Seems like there's another thread discussing filesystems. This should give you some ides on the [pros and cons of FAT32 & ext2/3]("http://www.ubuntuforums.org/showthread.php?t=346086")

---

### Post by claesbrandt on 2007-07-03
I encountered a limit in the ext2/3 driver for windows xp, I think. I use vmware in both linux and windows, sharing my images on a usb disk. I divide my image files into chucks of max 2GB each. This all works fine from within linux on an ext3 partition. But when I open my vmware image in windows xp, using the ext2/3 driver, vmware reports that some of my files, on the ext2/3 partition, are too large. I wonder if this is a limit in the ext2/3 driver for xp. So for now I have switched to use FAT32 on my USB disk and it works in both operating systems. But I would prefer to have my partition as ext3.

---

