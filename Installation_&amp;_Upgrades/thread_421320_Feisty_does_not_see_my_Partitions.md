---
title: "Feisty does not see my Partitions"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by charliep8 on 2007-04-24
In preparation to install Ubuntu and finally migrate to Linux I partitioned my hard drive with the following partitions:

Windows XP    NTFS    27 GB
Data    NTFS    105 GB
Ubuntu    Ext3    12GB
BackTrack    Ext3    4 GB
Linux Swap         600MB (1G of RAM in the computer)

I installed Windows, then BackTrack, and all was okay. Then I went to go and install Ubuntu and when it gets to the part where it wants to detect the partition it wants to reformat my entire hard drive, which is not good. I treid deleting the partition for Ubuntu and leaving 12 GB of free space on the drive, this still doesn't work. Ubuntu would still not see the free space and wanted to format the entire drive. Please help!

---

### Post by sporkinum on 2007-04-24
I was hoping they had fixed that problem with feisty, and is the reason I don't run Ubuntu at home. I have run Mandrake/Mandriva for years, and wanted to run Ubuntu due to favorable exposure to it at work. No luck.. apparently the Ubuntu partitioner can't see existing linux partitions if it didn't create them first. 

Oh well.. downloading the ISO now, and will try it and see if they got it right yet. Not holding my breath though.

---

### Post by sporkinum on 2007-05-08
Same problem.. The skeezy gparted program still can't see existing linux partitons. That program is severely borked and is the primary reason I STILL don't run Ubuntu.

---

### Post by finalzero on 2007-05-08
I had the same issue.

I installed 6.10 first (keeping it a stock, no updates etc). Then I ran the upgrade process to go to 7.04 Feisty, after the installation had completed I could see my drives.

In a nutshell I had to use 6.10 Edgy to create my partitions correctly and then upgrade to 7.04 so it would see them.. not funny at all.

---

