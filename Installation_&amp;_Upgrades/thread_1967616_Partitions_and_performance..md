---
title: "Partitions and performance."
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by ToshibaLaptoplinux on 2012-04-28
Yet another partitioning question.

Can the way a drive is partitioned significantly effect the performance of a PC (ie: Partition order, placement of swap, etc). I noticed that I may have done a less than ideal partition and that my PC is running a bit clunky (slow boots etc) and am wondering if they are related.

I have attached a snapshot of gparted. Is there anything that is immediately noticeable to the partitioning wizards out there. Particularly with the sda3 extended partition as I can't really mess with the Win 7 stuff.

---

### Post by oldfred on 2012-04-28
Cannot get to you links. Better to use to screenshots, and then from the little paperclip icon in the edit panel above your message attach the screenshots.

Generally partitioning does not make a difference. Some discuss the difference in speed from inside to outside of drive but that is so small that it is not really relevant to a boot issue. By the same token a smaller / (root) means the hard drive does not have to search over as large of an area of drive for most used files, but that is also small. 

What is your definition of slow boot? My SSD went from 20sec from a clean install to 25sec with all the mounts and other changes(nVidia driver)  I do or 25% more. I find mounting NTFS partitions is slow and if the need a chkdsk mounting can be very slow. My rotating drives booted between 40 & 60sec with some difference with Ubuntu versions, but more with what I was mounting.

You can review logs with Log File Viewer to see if some driver takes a long time to load or some device tries to mount  repeatedly and then fails.

---

### Post by ToshibaLaptoplinux on 2012-04-29
> **oldfred said:**
> Cannot get to you links. Better to use to screenshots, and then from the little paperclip icon in the edit panel above your message attach the screenshots.

Generally partitioning does not make a difference. Some discuss the difference in speed from inside to outside of drive but that is so small that it is not really relevant to a boot issue. By the same token a smaller / (root) means the hard drive does not have to search over as large of an area of drive for most used files, but that is also small. 

What is your definition of slow boot? My SSD went from 20sec from a clean install to 25sec with all the mounts and other changes(nVidia driver)  I do or 25% more. I find mounting NTFS partitions is slow and if the need a chkdsk mounting can be very slow. My rotating drives booted between 40 & 60sec with some difference with Ubuntu versions, but more with what I was mounting.

You can review logs with Log File Viewer to see if some driver takes a long time to load or some device tries to mount  repeatedly and then fails.

Thanks for the info and sorry for the problem with links. I added the attachments per your suggestion.

---

### Post by oldfred on 2012-04-29
I do not see any issues with partitions. See my sdc.

What is slow?

---

