---
title: "resize partition after deleting windows"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by Nostronna on 2014-12-22
Hello,
I have a Toshiba satellite U920T running Ubuntu 14.04 64 bit.
At the moment I have a dual boot with windows, but I want to get rid of that damn thing as I finally found a way to live without!
I want to proceed deleting the two partitions windows related (check attachment, NTFS partitions "system reserved" and "windows") with Gparted.

My question is....with the setting of partitions you can see in the attachment, will I then be able to reuse the newly freed space simply extending the extended partition that contains my ext4 (on which Ubuntu runs), my data partition and my swap partition?
reading here : [https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows) it seems it is not so easy, but I'm not really sure.

Thank you!

---

### Post by yancek on 2014-12-22
> My question is....with the setting of partitions you can see in the attachment, will I then be able to reuse the newly freed space simply extending the extended partition that contains my ext4 (on which Ubuntu runs), my data partition and my swap partition?

Although it is technically feasible, it will have a number of complications since your Ubuntu is on a logical partition inside and Extended partition and your windows partitions are primary.  If you don't have much experience or knowledge of partitioning, you would be better off deleting either sda1 or sda2 and resizing that partition to include the new unallocated space in the remaining partition and then format it as ext4.

---

